# Basic Concepts

## What is Model Deployment?

* Model deployment can be defined as the process of making models available in production environments, where they can provide predictions to other software systems. It is arguably the most important stage in the Machine Learning Lifecycle and also the most challenging.

* It shares challenges with traditional software, including:
    * **Reliability:** The ability of the software to consistently produce the intended result and be robust against errors.
    * **Reusability:** The ability of the software to be used across different systems and projects.
    * **Maintainability:** The ease with which the software can be maintained over time.
    * **Flexibility:** The ability to add or remove functionality from the software.

* Additional challenges specific to machine learning include:
    * **Reproducibility:** The ability to produce the same result given the same data across different systems.

* To maximize the value of a model, we need to ensure that its predictions can be shared with other systems.

![MLOps basic cycle](/section-01-theory/mlops-diagram1.png "Machine Learning Cycle")

## Research and Production Environments

* The term environment refers to the setting or state of a computer where software or other products are developed or put into operation. This includes software, hardware, programs, and operating systems.

* The *Research Environment* is a setting with tools, programs, and software suitable for data analysis and the development of machine learning models, such as Jupyter, Scikit-learn, pandas, and NumPy.

* The *Production Environment* is a real-time setting with running programs and hardware setups that support the organization's daily operations. It's where the machine learning model is actually available for business use. Through the production environment, we make ML models available for live consumption by end-users.

## Building Reproducible Machine Learning Pipelines

* An ML pipeline is the series of steps that occur from the moment we retrieve the data until the moment we make a prediction.
* Here, reproducibility is crucial. It helps reduce financial costs and saves time. If we cannot replicate results, it becomes difficult to determine whether a new model is truly better than the previous one.
* We understand reproducibility as the ability to duplicate a machine learning model exactly.
* A common problem is that databases are constantly updated and overwritten. However, saving a snapshot of the training data can improve stability.
* Other common mistakes that affect reproducibility include replacing missing data with randomly extracted values, removing values based on percentages, and calculating statistical values using future data (data leakage).
* Good practices in coding and versioning will always be very helpful. It’s important to record features, transformations, hyperparameters, and always use a seed to avoid randomness.
* Very often, the features used to train the models are not available in the live environment. Live populations also don’t match those used for training. To address this, we need to use containers and track software specifications (requirements). Before building the model, understand how it will be integrated with other systems. Understand how the business system will consume the model!