# ReadMeFirst
Overview and set of usage guidelines stating the purposes of each Commerce Integration module/micro-service and how to use them to build out your desired inter-connected solutions.

Comprehensive Microsoft Azure Techstack: 
* Asp.Net MVC/.Net Core - All management applications will be written in C# and will be deployed to run as Azure WebApps.
* Azure Active Directory B2C - multitenant active directory with MFA and numerous authentication support including OAuth which we will standardize on.  Additionally Azure AD B2C supports custom extensions for claims of any type to be included.  The Azure AD B2C will serve to authenticate as well as authorize access to specific features of the Management Apps as well as the Azure services, including the Azure Functions.
* Azure Key Vault and Azure Managed Service Identity (MSI) - avoids storing passwords in our code to authenticate to services that support Azure Active Directory (AAD) authentication, including Key Vault.  See: https://4sysops.com/archives/use-azure-managed-service-identity-msi-to-store-passwords-in-your-code-securely/ and https://blogs.technet.microsoft.com/paulomarques/2016/05/27/safeguarding-your-passwords-when-deploying-azure-virtual-machines-with-azure-powershell-module-and-arm-templates-by-using-azure-key-vault/
* Azure CosmosDB - for when we want to work with unstructured non schema'd data.  Can be used just like Mongo (same commands and syntax), as well as a graph database.  Works perfect for faceted navigation in Azure Search!
* Azure Redis Cache - for quick data caching
* Azure SQL - when we want to work with structured data using relations, indexes, constraints, etc.
* Azure Table Storage - Azure storage table is great when we need to work with centralized structured data without relations and usually with large volumes... for example, when we store large volumes of data, storage table is a lot cheaper... think of logging for example.
* Azure Search - able to comprehensively search all used databases (Cosmos, Table and SQL) as well as blob files stored in Azure Storage.  Azure Search's capabilities are impressive in that multiple datastores and files can be amalgamated and searched simultaneously to yeild a single result query.
* Azure Service Bus - This will serve as the primary inter-service messaging queue
* Azure Storage - This will serve as blob (file) storage. Not only will Azure Storage serve as a repository for binary files (such as images, documents, etc.), but will also serve as JSON file stores for loading data, setting up accounts and provisioning users and preferences.  Such JSON files will be used as input using triggers to call specified Azure Functions upon file creation and update.
* Azure Service Bus queues - are part of a broader Azure messaging infrastructure that supports queuing as well as publish/subscribe, and more advanced integration patterns.
* Azure Storage queues - these feature a simple REST-based GET/PUT/PEEK interface, providing reliable, persistent messaging within and between services. These can act as triggers for Azure Functions.  See: https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-azure-and-service-bus-queues-compared-contrasted
* Azure Functions/Durable Functions - These will serve as our primary microservices and endpoints.
* Azure Bot Service - bots to interact naturally with our users on websites, apps, cognitive services (Cortana/Azure Cognitive Services), Skype, Slack, Facebook Messenger, and more.
* Azure Cognitive Services - so we can leverage and utilize the power of machine learning for vision, speech, knowledge, search and language needs. Also we can utilize the Computer Vision API to bring the power of machine learning to our apps for making them better over time. For example, if we want a feature that could identify images using our own custom classifiers (for example, identifying images of "Daisies", "Daffodils", and "Dahlias").
* Azure DDoS Protection - Protection for our Azure resources from denial of service threats

Goals

	1. Configure and manage Azure infrastructure (Infrastructure as code using Resource Manager templates) -  see: https://microsoft.github.io/techcasestudies/devops/2017/03/14/risco.html and https://github.com/orizohar/risco-hackfest
	
	setup new accounts, choose desired features, enter new information, generate new GitHub account repository and create new Azure subscriptions - see: https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal
	
	spin up and tear down entire Azure resource sets based on dynamically created ARM Powershell templates - see: https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-export-template
		
	auto-wire up CI/CD deployments for each GitHub repo to prescribed Azure services
	
	auto-build an MVC management (per Azure subscription) "front-end Azure management" app specifically for prescribed Azure environment
	Features will include:
		dynamically create/script azure functions code for GitHub repo and via CD subsequently to Azure
	
		deploy MVC management app to Azure prescribed subscription web app
		
		provision and pre-load any required data into data stores
	
		load data from file resources or data transfers from any prescribed data stores
		
	2.  End user deliverable software tools and services for prescribed environments (ie storefront, inventory, personnel, products, etc.)	
	
* use API Platform https://api-platform.com/	- ensures that SEO is done correctly for search engines
* use GatsbyJS https://www.gatsbyjs.org/ - for front facing consumer web apps to have extremely performant UX that is blazening fast. 

Audit Inventory of Azure Resources:
* To make it easier to assess the environment and gain a quick understanding of the landscape across all subscriptions we can export the data so we use it in Excel. There a few quick scripts to collect data across different resource types. The data for all collections includes the resource name, location, resource group and subscription, with each script for the specific resource type having more detailed information for that type of resource.  Please make sure you are using AzureRM PowerShell 4.3.1. You can find all the scripts here https://github.com/Merlus/powershell/tree/master/azure/Audit%20Resources.
