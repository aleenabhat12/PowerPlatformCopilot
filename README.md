# Experimental: Copilot/AI Assistant for Microsoft Power Platform

This is an experimental project to explore the use of Azure AI services with Microsoft Power Platform. 
It is based on the [Dataverse Web API](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/webapi/overview) and the [Azure Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services/) with use of [Azure AI Functions](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/function-calling).

It can be used as a starting point for building your own Copilot/AI Assistant for Microsoft Power Platform. ConsoleTestApp is a sample console application that demonstrates how to use it. You can add more skills to DataverseAIClient class or derive from it to create your own client. During runtime, the client will automatically discover all skills and their parameters.

## Demos

[Watch Short Demos](src/docs/Demos.md)

- [Find Dataverse Solution and send email to owner](src/docs/Demos.md#send-email)
- [Translate Table Descriptions](https://github.com/petrochuk/PowerPlatformCopilot/blob/main/src/docs/Demos.md#translate-table-descriptions)
- [Ask questions about Table Properties](https://github.com/petrochuk/PowerPlatformCopilot/blob/main/src/docs/Demos.md#table-properties)
- [Ask questions about Canvas Apps](https://github.com/petrochuk/PowerPlatformCopilot/blob/main/src/docs/Demos.md#canvas-app-properties)
- [Save Canvas Apps as msapp file to local folder](https://github.com/petrochuk/PowerPlatformCopilot/blob/main/src/docs/Demos.md#save-msapp-file)

## Contributing

This project is welcoming contributions. If you have any questions, feel free to start a [discussion](https://github.com/petrochuk/PowerPlatformCopilot/discussions).

## Copilot/AI Assistant Skills implemented as AI Functons

The following skills are implemented as Azure AI Functions in [DataverseAIClientSkills.cs](src/DataverseAzureAI/DataverseAIClientSkills.cs):

| Skill | Description |
| ----- | ----------- |
| FindTableByName | Find Dataverse table or entity by exact or partial name |
| ListOfTablesByPropertyValue | Returns filtered list of tables based on specified property value |
| GetTablePropertyValue | Returns property value for specified table |
| ListOfModelDrivenAppsByPropertyValue | Returns filtered list of Model-driven PowerApps based on specified property value |
| FindCanvasApp | Finds a canvas app based on specified property value
| ListOfCanvasAppsByPropertyValue | Returns filtered list of canvas PowerApps based on specified property value |
| GetCanvasAppPropertyValue | Returns property value for a canvas app |
| ListOSolutionsByPropertyValue | Returns filtered list of Dataverse solutions based on specified property value and optional user |
| ListOSolutionComponents | Returns list of components inside Dataverse solutions. It can filter on component type, name or other properties |
| GetSolutionPropertyValue | Returns property value for specified Dataverse solution |
| SendEmailOrShareLinkWithSomeone | Sends an email or shares a link to an item, record or anything else inside PowerPlatform including but not limited to app, solution, table, component |
| SaveToFileSystem | Save to file system: text output, apps, solutions, lists or any other Power Platform component |
| CreateItemInsidePowerPlatform | Creates new items, records or anything else inside PowerPlatform including but not limited to apps, solutions, tables, users, components |

## Running the project

Open appSettings.json and update the following settings:

| Section | Setting | Description |
| ------- | ------- | ----------- |
| TestApp | EnvironmentId | Dataverse environment id |
| AzureAI | OpenApiEndPoint | Azure AI Open API endpoint |
| AzureAI | OpenApiKey | Azure AI Open API key |
| AzureAI | OpenApiModel | Azure AI Open API model which supports Azure AI Functions version **0613** of gpt-35-turbo, gpt-35-turbo-16k, gpt-4, and gpt-4-32k |
| PowerPlatform | AzureAppId | Entra ID Applicatinon that has access to Power Platform |
| PowerPlatform | GraphAppId | Entra ID Applicatinon that has access to Microsoft Graph (can be same application) |
