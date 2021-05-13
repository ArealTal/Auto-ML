# Auto-ML
**Description of project**

This is an automated machine learning tool that acts as a guide through the ML process by logging what each step of the process is along with an explanation of why the step is needed as the step is demonstrated. This includes:
 - Choosing what ML algorithm to use 
 - Tuning the hyperparameters of the chosen algorithm 
 - Running the ML algorithm 
 - Validating the results 
 - Identifying failures in the model 
 - Potentially suggesting fixes for failures of the model 
 
By demonstrating each part of the process and explaining why each step is taken, users are educated and the ML is explainable.

The auto ML tool will use more granular validation than overall model metrics in order to more properly diagnose model failures. Evaluating clusters of data where a model has performed most poorly will help the user diagnose types of model failure that could otherwise go unnoticed. It will also help the user identify bias and help the user understand what to do in order to remove bias from the model. 

**Overall Strategy**

Model Training:
After asking the user some questions about the dataset, the tool will classify the type of problem (e.g., Regression, Classification, Clustering, or Dimensionality Reduction). Then the tool will identify which ML algorithm the user should run to solve the problem prior to the tool running the algorithm itself.
 
Model Validation:
Validation on how the model performed on clusters of data will be done to show the user how to diagnose model failures. The tool will identify clusters of data (which may just be data associated with each value of each categorical column of the dataset) and will then perform validation for the trained model on each cluster of the data (note that these clusters are not necessarily mutually exclusive). 

If the model performs poorly on any clusters of data, then the tool will attempt to identify possible causes for model failure. Depending on what went wrong, the user will be guided through potential next steps (e.g., run a different algorithm if the model did not perform better than a model that always gives the same prediction, augment the dataset by generating synthetic data if there is a load balancing issue within the data, and amend data to overcome a bias within the dataset, etc.).

**Details Of Strategy**

The following list of machine learning algorithms will be used for training:
•	Linear SVC
•	Naïve Bayes
•	K Nearest Neighbors
•	SVC
•	SGD Classifier
•	Kernel Approximation
•	Randomized PCA
•	K Means
•	GMM
•	Spectral Clustering
•	Mean Shift
•	VBGMM
•	SGD Regressor
•	Lasso Regression
•	ElasticNet Regression
•	Ridge Regression
•	Linear SVR

For each of the above algorithms, the following actions will take place:
 - Create a log of all actions taken by the tool and all output 
 - Write an algorithm to choose the best ML algorithm for a given dataset & model pairing
 - Explain to the user why the algorithm was chosen
 - Obtain datasets and a reasonable model to be able to run the algorithm
 - Automatically tune hyperparameters 
 - Run each of the algorithms (using scikit-learn)
 
To validate results of ML and diagnose problems, the following will be included within the validation tool:
-  Cross validatation
 - Clustering data into data segments
 - Validating model on each data segment
 - Formulating definition specifications for multiple possible diagnoses
 - Building an algorithm that follows definition specifications for each possible diagnosis
 - Providing an explanation to the user for why the model failed on the segment of data on which the model performed most poorly
 - Data Augmentation for load balancing issues
 - Data Augmentation for a bias that must be fixed



