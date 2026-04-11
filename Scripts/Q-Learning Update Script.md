
```R

## Q-Learning Implementation in R
## Based on the reinforcement learning formula from Lockwood et al. (2016)

# Load required libraries
library(ggplot2)
library(dplyr)
library(tidyr)


# Define the Q-learning update function
# Q_{t+1}(a) = Q_t(a) + α * [r_t - Q_t(a)]
q_learning_update <- function(q_current, alpha, reward) {
  # Calculate prediction error (PE)
  prediction_error <- reward - q_current
  
  # Update Q-value using the learning rule
  q_new <- q_current + alpha * prediction_error
  
  # Return both the new Q-value and the prediction error for analysis
  return(list(
    q_new = q_new,
    prediction_error = prediction_error
  ))
}


# Simulate a learning experiment
simulate_learning <- function(n_trials = 50, 
                              true_prob = 0.75,  # True reward probability
                              alpha = 0.3,        # Learning rate
                              initial_q = 0.5) {  # Initial Q-value
  
  # Initialize storage for results
  results <- data.frame(
    trial = 1:n_trials,
    q_value = numeric(n_trials),
    reward = numeric(n_trials),
    prediction_error = numeric(n_trials),
    choice_prob = numeric(n_trials)
  )
  
  # Set initial Q-value
  current_q <- initial_q
  
  # Run simulation
  for (trial in 1:n_trials) {
    # Store current Q-value
    results$q_value[trial] <- current_q
    
    # Generate reward based on true probability (with some noise)
    results$reward[trial] <- rbinom(1, 1, true_prob)
    
    # Update Q-value
    update <- q_learning_update(current_q, alpha, results$reward[trial])
    current_q <- update$q_new
    results$prediction_error[trial] <- update$prediction_error
    
    # Calculate choice probability using softmax (optional visualization)
    # Using beta = 2 as temperature parameter
    results$choice_prob[trial] <- exp(current_q / 2) / (exp(current_q / 2) + exp(0.5 / 2))
  }
  
  return(results)
}

# Set random seed for reproducibility
set.seed(42)

# Simulate learning with different parameter values
# Simulation 1: Standard learning
sim1 <- simulate_learning(n_trials = 100, alpha = 0.3, true_prob = 0.75)
sim1$condition <- "Standard (α = 0.3)"

# Simulation 2: Fast learning
sim2 <- simulate_learning(n_trials = 100, alpha = 0.8, true_prob = 0.75)
sim2$condition <- "Fast (α = 0.8)"

# Simulation 3: Slow learning
sim3 <- simulate_learning(n_trials = 100, alpha = 0.1, true_prob = 0.75)
sim3$condition <- "Slow (α = 0.1)"

# Combine simulations
all_sims <- rbind(sim1, sim2, sim3)

# Create visualization 1: Q-value evolution over trials
p1 <- ggplot(all_sims, aes(x = trial, y = q_value, color = condition)) +
  geom_line(size = 1.2) +
  geom_hline(yintercept = 0.75, linetype = "dashed", alpha = 0.5) +
  labs(
    title = "Q-Learning: How Beliefs Update Over Time",
    subtitle = "Dashed line shows true reward probability (0.75)",
    x = "Trial Number",
    y = "Q-value (Expected Reward)",
    color = "Learning Rate"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "bottom"
  ) +
  scale_color_manual(values = c("Standard (α = 0.3)" = "#2E86AB", 
                                "Fast (α = 0.8)" = "#A23B72", 
                                "Slow (α = 0.1)" = "#F18F01"))

# Create visualization 2: Prediction errors over time
p2 <- ggplot(sim1, aes(x = trial)) +
  geom_line(aes(y = prediction_error), color = "#2E86AB", size = 1) +
  geom_hline(yintercept = 0, linetype = "solid", alpha = 0.5) +
  geom_point(aes(y = reward - 0.5), alpha = 0.3, size = 2) +
  labs(
    title = "Prediction Errors During Learning",
    subtitle = "Points show actual rewards (shifted for visibility)",
    x = "Trial Number",
    y = "Prediction Error",
    caption = "Positive PE = better than expected, Negative PE = worse than expected"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 14, face = "bold"))

# Create visualization 3: Single trial demonstration
# Show one example update step-by-step
example_trial <- data.frame(
  stage = c("Before", "After"),
  q_value = c(0.6, 0.72),
  label = c("Q_t(a) = 0.6", "Q_t+1(a) = 0.72")
)

p3 <- ggplot(example_trial, aes(x = stage, y = q_value, fill = stage)) +
  geom_col(width = 0.5) +
  geom_text(aes(label = label), vjust = -0.5, size = 5) +
  ylim(0, 1) +
  labs(
    title = "Example Q-Learning Update",
    subtitle = "α = 0.3, reward = 1, PE = 0.4",
    x = "",
    y = "Q-value"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "none"
  ) +
  scale_fill_manual(values = c("Before" = "#E8E8E8", "After" = "#2E86AB"))

# Display plots
print(p1)
print(p2)
print(p3)

# Demonstrate the function with specific examples
cat("\n=== Q-Learning Examples ===\n\n")

# Example 1: Positive prediction error
cat("Example 1: Positive Prediction Error\n")
cat("Initial Q-value: 0.4, Reward: 1, Learning rate: 0.3\n")
result1 <- q_learning_update(q_current = 0.4, alpha = 0.3, reward = 1)
cat(sprintf("New Q-value: %.3f, Prediction error: %.3f\n\n", 
            result1$q_new, result1$prediction_error))

# Example 2: Negative prediction error
cat("Example 2: Negative Prediction Error\n")
cat("Initial Q-value: 0.8, Reward: 0, Learning rate: 0.3\n")
result2 <- q_learning_update(q_current = 0.8, alpha = 0.3, reward = 0)
cat(sprintf("New Q-value: %.3f, Prediction error: %.3f\n\n", 
            result2$q_new, result2$prediction_error))

# Create a summary table of learning dynamics
summary_stats <- all_sims %>%
  group_by(condition) %>%
  summarise(
    final_q = last(q_value),
    trials_to_converge = which.max(abs(q_value - 0.75) < 0.05),
    mean_abs_pe = mean(abs(prediction_error)),
    .groups = 'drop'
  )

cat("=== Learning Summary ===\n")
print(summary_stats)

# Additional visualization: Learning trajectories with rewards
p4 <- ggplot(sim1[1:30,], aes(x = trial)) +
  geom_point(aes(y = reward), shape = 21, fill = "lightgreen", size = 3, alpha = 0.7) +
  geom_line(aes(y = q_value), color = "#2E86AB", size = 1.5) +
  geom_segment(aes(xend = trial, y = q_value, yend = reward), 
               alpha = 0.3, linetype = "dashed") +
  labs(
    title = "Q-Learning Process: Rewards and Value Updates",
    subtitle = "Points = actual rewards, Line = Q-value evolution",
    x = "Trial",
    y = "Value"
  ) +
  theme_minimal() +
  theme(plot.title = element_text(size = 14, face = "bold"))

print(p4)

```