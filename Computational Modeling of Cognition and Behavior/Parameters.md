
- Parameters can be understood as "turning knobs" that fine-tune the behavior of a model once its architecture has been specified
- In our random-walk model, *drift* was one important parameters. Varying irs value affects the overall performance of the model; as drift increases, the model's ability to differentiate one response from another increases
- Changing the values of the parameters does not change the architecture of the model or the simulation, but it certainly changes its behavior

### Types of parameters
- Free Parameters:
	- Are usually estimated from the data that the model seeks to explain
	- We find those values that maximally align the model's prediction with the data
	- Generally we seek to limit the numer of free parameters because the larger their number, the greater the model's flexibility, and we want to *place boundaries on that flexibility*
- Fixed parameters:
	- This are NOT estimated from the data and are *invariant* across datasets
	- The *role* of fixed parameters is primarily to "get the model off the ground" by providing some meaningul values for its components where necessary
	- Modelers are less concerned about the number of fixed parameters than free ones

"Building a computational model forces us to be explicit about the nuts and bolts of the cognitive mechanisms that we talk abour in our theories" (p. 41)