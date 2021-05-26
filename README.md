# AzureFunction_AzureML_Routing_Sample

Azure function demonstrating how to appropriately query data from backend data stores (Azure SQL) and route requests to an appropriate model endpoint based on the body of the original request.

![AzureFunction_AzureML_Routing_Sample](img/routing.png?raw=true "AzureFunction_AzureML_Routing_Sample")

## Environment Setup

Azure SQL, Azure Machine Learning (Deployed Python & R Models). Include links to deployed python/R models and references to associated datasets...

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
