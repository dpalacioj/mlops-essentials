# What is YAML?

Is a data serialization language that is often used for writing configuration files. It is human-readable and easy to understand. It can also be used in conjunction with other programming languages.

For instance, the following YAML code can be used to orchestrate the different stages of your machine learning pipeline, ensuring that each step is executed in the correct order with specified inputs and outputs.

```yaml
# pipeline-config.yaml

pipeline:
  name: simple-ml-pipeline
  steps:
    - name: data_preprocessing
      script: preprocess.py
      inputs:
        - data/raw_data.csv
      outputs:
        - data/processed_data.csv
    
    - name: model_training
      script: train.py
      inputs:
        - data/processed_data.csv
      outputs:
        - models/trained_model.pkl
      params:
        epochs: 10
        learning_rate: 0.001

    - name: model_evaluation
      script: evaluate.py
      inputs:
        - models/trained_model.pkl
        - data/test_data.csv
      outputs:
        - results/metrics.json
```
## Basic Rules

* It uses Python style identation to indicate nesting.
* Whitespaces for indentation and Tab are not allowed.
* No format symbols like braces, square brackets, or quotation tags.
* Uses .yml or .yaml file extension

## YAML Structures

* Maps allows us to associate key-value pairs.
* Keys are Unique, and the order doesn't matter.
* A map in YAML needs to be resolved befor it can be closed, and a new map is created.
* A structure of a YAML file is a map or a list

## YAML Data Types

* Scalars (strings, integers, dates, numbers or boolean).
* A list and it can start with a dash, with indentation separating the parent.
* New Map can be created by either increasing indentation level or by resolving the previous map.


## General Use Cases of YAML

1. **Application configuration**
2. **Infrastructure as Code:** Tools like Terraform, Kubernetes and Ansible use YAML, enabling and repeatable resource creation and managament.
3. **Workflow Definition:*** In continuous integration and continous delivery systems like GitHub Actions. It defines the steps and actions in a pipeline.
4. **Kubernetes:** Is used to define manifests, describing the rconfiguration of resources like pods, deployments, services, congifmaps, etc.

### YAML Use Cases in the MLOps Lifecycle:

1. CI/CD Pipeline
2. Infrastructure Configuration
3. Hyperparameter and Training Configuration
4. Versioning and Reproducibility
5. Workflow Definition in Orchestrators
6. Model Monitoring and Management

Here is a small example of how YAML can be used in conjunction with Apache Airflow to define a simple workflow:

```yaml
# airflow_dag.yml

dag:
  dag_id: 'example_ml_workflow'
  schedule_interval: '0 12 * * *'  # Daily at noon
  start_date: '2024-08-24'
  default_args:
    owner: 'user'
    retries: 1
    retry_delay: '5m'

tasks:
  - task_id: 'data_ingestion'
    bash_command: 'python scripts/data_ingestion.py'
  
  - task_id: 'data_preprocessing'
    bash_command: 'python scripts/data_preprocessing.py'
    trigger_rule: 'all_success'

  - task_id: 'model_training'
    bash_command: 'python scripts/train_model.py'
    trigger_rule: 'all_success'

  - task_id: 'model_evaluation'
    bash_command: 'python scripts/evaluate_model.py'
    trigger_rule: 'all_success'

  - task_id: 'model_deployment'
    bash_command: 'python scripts/deploy_model.py'
    trigger_rule: 'all_success'
```