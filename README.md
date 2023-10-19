# Azure Communication Service - AI Forms

## Setup Instructions – Local environment  

#### 1. Create Azure resource from Azure AI, Azure OpenAI and Azure Communication Services

Create Azure resources for Azure AI, Azure OpenAI and Azure Communication Services in Azure.

Next, you'll need to do these steps manually in the [Azure portal](https://portal.azure.com)- 

- Add a Calling enabled telephone number to your Communication resource. [Get a phone number](https://aka.ms/Mech-getPhone).
- [Connect Azure AI service to Azure communication service resource](https://aka.ms/Mech-connectACSWithAI).
- Create a deployment for your Azure OpenAI resource. Recommend using `gpt-35-turbo-16k`. [Create and deploy an Azure OpenAI Service Resource](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/create-resource?pivots=web-portal)


#### 2. Update `appsettings.json`
Update the settings below in `appsettings.son` with values from your Azure deployment

```json
  "ACS_CONNECTION_STRING": "",
  "ACS_PHONE_NUMBER": "",
  "AZURE_COG_SERVICES_KEY": "",
  "AZURE_COG_SERVICES_ENDPOINT": "",
  "OPENAI_ENDPOINT": "",
  "OPENAI_KEY": "",
  "OPENAI_DEPLOYMENT_NAME": "",
```

#### 3. Setup and host your Azure DevTunnel
[Azure DevTunnels](https://learn.microsoft.com/en-us/azure/developer/dev-tunnels/overview) is an Azure service that enables you to share local web services hosted on the internet. Use the commands below to connect your local development environment to the public internet. This creates a tunnel with a persistent endpoint URL and which allows anonymous access. We will then use this endpoint to notify your application of chat and job router events from the Azure Communication Service.
```bash
devtunnel create --allow-anonymous
devtunnel port create -p 7284 --protocol https
devtunnel host
```
Make a note of the devtunnel URI. You will need it at later steps.

#### 4. Update dev tunnel uri `HOST_NAME` in `appsettings.json` 

##  Running the backend application locally
- Ensure your Azure Dev tunnel URI is active and points to the correct port of your localhost application.
- Run `dotnet run` to build and run the sample application.

