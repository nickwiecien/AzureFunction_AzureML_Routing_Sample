# AzureFunction_AzureML_Routing_Sample

Azure function demonstrating how to appropriately query data from backend data stores (Azure SQL) and route requests to an appropriate model endpoint based on the body of the original request. The solution presented here accepts an incoming HTTP request containing a `model_type` attribute which is used to route the request. Using other variable parameters in the request body, data is queried from an Azure SQL Database and sent to a real-time Azure ML model endpoint before being returned to the original requestor. 

![AzureFunction_AzureML_Routing_Sample](img/routing.png?raw=true "AzureFunction_AzureML_Routing_Sample")

## Environment Setup

Execution of this solution requires access to an Azure SQL Database having tables (``, ``) containing the associated data in the `` directory.
Further, it requires access two deployed, real-time, ML endpoints. For the purposes of this demo, the two endpoints were deployed using the demos linked below.
[Azure ML Real-Time R Model Endpoint - Iris Dataset](https://github.com/Azure/azureml-sdk-for-r/tree/master/samples/deployment/deploy-to-aci)
[Azure ML Real-Time Python Model Endpoint - Diabetes Dataset](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/deployment/deploy-to-cloud/model-register-and-deploy.ipynb)

#### Azure Function Environment Variables

Before running this project, create a `local.settings.json` file in the root directory. This file needs to have the following entries under the `values` section:

| Key                                 | Value                                    |
|-------------------------------------|------------------------------------------|
| AzureWebJobsStorage                 | The connection string to the storage account used by the Functions runtime.  To use the storage emulator, set the value to UseDevelopmentStorage=true |
| FUNCTIONS_WORKER_RUNTIME            | Set this value to `python` as this is a python Function App |
| R_MODEL_ENDPOINT | Endpoint URI for a R model deployed using Azure Machine Learning |
| PYTHON_MODEL_ENDPOINT     | Endpoint URI for a Python model deployed using Azure Machine Learning  |
| SQL_SERVER     | Name of the Azure SQL Server containing data of interest |
| SQL_DATABASE     | Name of the Azure SQL Database containing data of interest |
| SQL_USERNAME     | Username credential for accessing Azure SQL |
| SQL_PASSWORD     | Password credential for accessing Azure SQL |
