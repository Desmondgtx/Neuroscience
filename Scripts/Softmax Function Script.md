
```R

# Softmax Function Implementation in R
# Based on the choice probability formula from Lockwood et al. (2016)

# Load required libraries
library(ggplot2)
library(dplyr)
library(tidyr)
library(gridExtra)

# Define the softmax function
# This implements: P_t[a|Q_t(a)] = e^{[Q_t(a)/β]} / Σ_a' e^{[Q_t(a')/β]}
softmax <- function(q_values, beta) {
  # Handle edge cases
  if (beta == 0) {
    # When beta = 0, choose action with highest Q-value deterministically
    probs <- rep(0, length(q_values))
    probs[which.max(q_values)] <- 1
    return(probs)
  }
  
  # Calculate exponentials
  exp_values <- exp(q_values / beta)
  
  # Calculate probabilities
  probabilities <- exp_values / sum(exp_values)
  
  return(probabilities)
}

# Demonstrate the softmax function with specific examples
cat("=== Softmax Function Examples ===\n\n")

# Example 1: Basic two-choice scenario
cat("Example 1: Two choices with different Q-values\n")
q_values <- c(0.8, 0.3)  # Q-values for options A and B
beta <- 0.5
probs <- softmax(q_values, beta)
cat(sprintf("Q-values: A=%.1f, B=%.1f\n", q_values[1], q_values[2]))
cat(sprintf("Beta (temperature): %.1f\n", beta))
cat(sprintf("Choice probabilities: A=%.3f, B=%.3f\n\n", probs[1], probs[2]))

# Example 2: Effect of different beta values
cat("Example 2: Same Q-values, different temperatures\n")
betas <- c(0.1, 0.5, 1.0, 2.0, 5.0)
for (b in betas) {
  probs <- softmax(q_values, b)
  cat(sprintf("Beta=%.1f: P(A)=%.3f, P(B)=%.3f\n", b, probs[1], probs[2]))
}

# Create visualization 1: Softmax transformation
# Show how Q-value differences translate to choice probabilities
q_diff_range <- seq(-2, 2, by = 0.1)
beta_values <- c(0.2, 0.5, 1.0, 2.0)

# Generate data for different beta values
softmax_data <- expand.grid(
  q_diff = q_diff_range,
  beta = beta_values
) %>%
  rowwise() %>%
  mutate(
    q_a = 0.5 + q_diff/2,
    q_b = 0.5 - q_diff/2,
    prob_a = softmax(c(q_a, q_b), beta)[1]
  ) %>%
  ungroup()

p1 <- ggplot(softmax_data, aes(x = q_diff, y = prob_a, color = factor(beta))) +
  geom_line(size = 1.2) +
  geom_hline(yintercept = 0.5, linetype = "dashed", alpha = 0.5) +
  geom_vline(xintercept = 0, linetype = "dashed", alpha = 0.5) +
  labs(
    title = "Softmax Function: Q-value Difference to Choice Probability",
    subtitle = "How temperature (β) affects choice consistency",
    x = "Q-value Difference (Q_A - Q_B)",
    y = "Probability of Choosing A",
    color = "Beta (β)"
  ) +
  theme_minimal() +
  scale_color_manual(values = c("0.2" = "#e41a1c", "0.5" = "#377eb8", 
                               "1" = "#4daf4a", "2" = "#984ea3")) +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "right"
  )

# Create visualization 2: Beta parameter effects
# Show exploration vs exploitation trade-off
beta_range <- seq(0.1, 5, by = 0.1)
q_vals <- c(0.8, 0.3)  # Fixed Q-values

beta_effect_data <- data.frame(
  beta = beta_range
) %>%
  rowwise() %>%
  mutate(
    prob_best = softmax(q_vals, beta)[1],
    entropy = -sum(softmax(q_vals, beta) * log(softmax(q_vals, beta)))
  ) %>%
  ungroup()

p2a <- ggplot(beta_effect_data, aes(x = beta, y = prob_best)) +
  geom_line(size = 1.2, color = "#2E86AB") +
  geom_hline(yintercept = 1.0, linetype = "dashed", alpha = 0.5) +
  labs(
    title = "Effect of Temperature on Choice Consistency",
    subtitle = "Q-values: A=0.8, B=0.3",
    x = "Beta (Temperature Parameter)",
    y = "P(Choose Best Option)"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 12, face = "bold"))

p2b <- ggplot(beta_effect_data, aes(x = beta, y = entropy)) +
  geom_line(size = 1.2, color = "#A23B72") +
  labs(
    title = "Effect of Temperature on Choice Entropy",
    subtitle = "Higher entropy = more exploration",
    x = "Beta (Temperature Parameter)",
    y = "Choice Entropy"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 12, face = "bold"))

# Create visualization 3: Multi-option scenario
# Demonstrate softmax with more than 2 choices
multi_q <- c(0.9, 0.6, 0.3, 0.1)
option_names <- c("A", "B", "C", "D")
betas_multi <- c(0.2, 0.5, 1.0, 2.0)

multi_data <- expand.grid(
  option = option_names,
  beta = betas_multi
) %>%
  mutate(
    q_value = rep(multi_q, length(betas_multi)),
    prob = unlist(lapply(betas_multi, function(b) softmax(multi_q, b)))
  )

p3 <- ggplot(multi_data, aes(x = option, y = prob, fill = option)) +
  geom_bar(stat = "identity") +
  facet_wrap(~paste("β =", beta), nrow = 1) +
  labs(
    title = "Softmax with Multiple Options",
    subtitle = "Q-values: A=0.9, B=0.6, C=0.3, D=0.1",
    x = "Option",
    y = "Choice Probability"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "none"
  ) +
  scale_fill_manual(values = c("#e41a1c", "#377eb8", "#4daf4a", "#984ea3"))

# Create visualization 4: Interactive simulation
# Simulate choices over trials with different beta values
set.seed(123)
n_trials <- 100

simulate_choices <- function(q_values, beta, n_trials) {
  choices <- numeric(n_trials)
  for (i in 1:n_trials) {
    probs <- softmax(q_values, beta)
    choices[i] <- sample(1:length(q_values), 1, prob = probs)
  }
  return(choices)
}

# Simulate with different betas
sim_data <- data.frame()
for (b in c(0.1, 0.5, 1.0, 2.0)) {
  choices <- simulate_choices(c(0.8, 0.3), b, n_trials)
  sim_data <- rbind(sim_data, data.frame(
    trial = 1:n_trials,
    choice = choices,
    beta = b,
    chose_best = choices == 1
  ))
}

# Calculate running proportion of choosing best option
sim_data <- sim_data %>%
  group_by(beta) %>%
  mutate(
    cumulative_best = cumsum(chose_best) / row_number()
  ) %>%
  ungroup()

p4 <- ggplot(sim_data, aes(x = trial, y = cumulative_best, color = factor(beta))) +
  geom_line(size = 1) +
  geom_hline(yintercept = softmax(c(0.8, 0.3), 0.5)[1], 
             linetype = "dashed", alpha = 0.5) +
  labs(
    title = "Simulated Choice Behavior Over Time",
    subtitle = "Running proportion of choosing the better option (Q=0.8 vs Q=0.3)",
    x = "Trial Number",
    y = "Proportion Choosing Best",
    color = "Beta"
  ) +
  theme_minimal() +
  scale_color_manual(values = c("0.1" = "#e41a1c", "0.5" = "#377eb8", 
                               "1" = "#4daf4a", "2" = "#984ea3")) +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "right"
  )

# Display all plots
print(p1)
grid.arrange(p2a, p2b, ncol = 2)
print(p3)
print(p4)

# Advanced example: Combining Q-learning with softmax
cat("\n\n=== Combined Q-Learning and Softmax Example ===\n")

# Function that combines both Q-learning and softmax
rl_step <- function(q_values, choice, reward, alpha, beta) {
  # Update Q-value for chosen option
  q_values[choice] <- q_values[choice] + alpha * (reward - q_values[choice])
  
  # Calculate new choice probabilities
  probs <- softmax(q_values, beta)
  
  return(list(q_values = q_values, probs = probs))
}

# Example: One learning step
q_start <- c(0.5, 0.5)  # Initial Q-values
choice <- 1  # Chose option A
reward <- 1  # Got rewarded
alpha <- 0.3
beta <- 0.5

result <- rl_step(q_start, choice, reward, alpha, beta)
cat("Initial Q-values:", q_start, "\n")
cat("Choice: A, Reward: 1\n")
cat("Updated Q-values:", result$q_values, "\n")
cat("New choice probabilities:", result$probs, "\n")

# Create a heatmap showing how different alpha-beta combinations affect learning
alpha_beta_grid <- expand.grid(
  alpha = seq(0.1, 0.9, by = 0.1),
  beta = seq(0.1, 2, by = 0.1)
)

# For each combination, simulate learning and measure performance
performance_data <- alpha_beta_grid %>%
  rowwise() %>%
  mutate(
    final_performance = {
      # Run mini simulation
      q_vals <- c(0.5, 0.5)
      total_reward <- 0
      for (i in 1:50) {
        probs <- softmax(q_vals, beta)
        choice <- sample(1:2, 1, prob = probs)
        reward <- ifelse(choice == 1, rbinom(1, 1, 0.75), rbinom(1, 1, 0.25))
        q_vals[choice] <- q_vals[choice] + alpha * (reward - q_vals[choice])
        total_reward <- total_reward + reward
      }
      total_reward / 50
    }
  ) %>%
  ungroup()

p5 <- ggplot(performance_data, aes(x = alpha, y = beta, fill = final_performance)) +
  geom_tile() +
  scale_fill_gradient2(low = "red", mid = "yellow", high = "green", 
                       midpoint = 0.5, name = "Avg Reward") +
  labs(
    title = "Learning Performance: Alpha-Beta Parameter Space",
    subtitle = "Average reward over 50 trials (true probs: 0.75 vs 0.25)",
    x = "Learning Rate (α)",
    y = "Temperature (β)"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 14, face = "bold"))

print(p5)

```
