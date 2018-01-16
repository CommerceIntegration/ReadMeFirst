# ReadMeFirst
Overview and set of usage guidelines stating the purposes of each Commerce Integration module/micro-service and how to use them to build out your desired inter-connected solutions.

Comprehensive Microsoft Azure Techstack: 
* Asp.Net MVC/.Net Core - All management applications will be written in C# and will be deployed to run as Azure WebApps.
* Azure Active Directory B2C - multitenant active directory with MFA and numerous authentication support including OAuth which we will standardize on.  Additionally Azure AD B2C supports custom extensions for claims of any type to be included.  The Azure AD B2C will serve to authenticate as well as authorize access to specific features of the Management Apps as well as the Azure services, including the Azure Functions.
* Azure CosmosDB - for when we want to work with unstructured non schema'd data.  Can be used just like Mongo (same commands and syntax), as well as a graph database.  Works perfect for faceted Azure Search!
* Azure SQL - when we want to work with structured data using relations, indexes, constraints, etc.
* Azure Table Storage - Azure storage table is great when you need to work with centralized structured data without relations and usually with large volumes... for example, when we store large volumes of data, storage table is a lot cheaper... think of logging for example.
* Azure Search - able to comprehensively search all used databases (Cosmos, Table and SQL) as well as blob files stored in Azure Storage.  Azure Search's capabilities are impressive in that multiple datastores and files can be amalgamated and searched simultaneously to yeild a single result query.
* Azure Service Bus - This will serve as the primary inter-service messaging queue
* Azure Storage - This will serve as blob (file) storage. Not only will Azure Storage serve as a repository for binary files (such as images, documents, etc.), but will also serve as JSON file stores for loading data, setting up accounts and provisioning users and preferences.  Such JSON files will be used as input using triggers to call specified Azure Functions upon file creation and update.
* Azure Service Bus queues - are part of a broader Azure messaging infrastructure that supports queuing as well as publish/subscribe, and more advanced integration patterns.
* Azure Storage queues - these feature a simple REST-based GET/PUT/PEEK interface, providing reliable, persistent messaging within and between services. These can act as triggers for Azure Functions.  See: https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-azure-and-service-bus-queues-compared-contrasted
* Azure Functions/Durable Functions - These will serve as our primary microservices and endpoints.
