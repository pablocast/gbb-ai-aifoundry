# <img src="./docs/azure_logo.png" alt="Azure Logo" style="width:30px;height:30px;"/> Azure AI Foundry SDK Tutorial

In this tutorial, you use the Azure AI Foundry SDK (and other libraries) to build, configure, and evaluate a chat app for your retail company called Contoso Trek. Your retail company specializes in outdoor camping gear and clothing. The chat app should answer questions about your products and services. For example, the chat app can answer questions such as "which tent is the most waterproof?" or "what is the best sleeping bag for cold weather?".

* [Features](#features)
* [Deploying the environment](#deploying-the-environment)
* [Build a custom knowledge retrieval (RAG) app with the Azure AI Foundry SDK](#build-custom-rag-with-azure-ai-foundry-sdk)
* [Evaluate a custom chat application with the Azure AI Foundry SDK](#evaluate-custom-rag-with-azure-ai-foundry-sdk)

## Features
* **UI interface**: The streamlit app to query the GraphRag Index .
* **Graph RAG Indexing**: Using the [graphrag](https://github.com/microsoft/graphrag) python package, aligned with the [GraphRAG Knowledge Mode](https://microsoft.github.io/graphrag/index/architecture/)
* **Graph RAG Retrieval**: Using the query engine from [graphrag](https://github.com/microsoft/graphrag) python package.
* **Citations**: The app shows the search results that were used to generate the response.

⚠️ *Warning: GraphRAG indexing can be an expensive operation, please start small.*


## Deploying the Environment

1. Install the required tools:
   * [Azure Developer CLI](https://aka.ms/azure-dev/install)
   * [Python=3.11](https://www.python.org/downloads/)
      * **Important**: Python and the pip package manager must be in the path in Windows for the setup scripts to work.
      * **Important**: Ensure you can run `python --version` from console
   * [Git](https://git-scm.com/downloads)

The steps below will provision Azure resources, set up the environment and configure the GraphRag pipeline.

2. Login to your Azure account:

    ```shell
    azd auth login
    ```

3. Create a new azd environment:

    ```shell
    azd env new
    ```
    Enter a name that will be used for the resource group.
    This will create a new folder in the `.azure` folder, and set it as the active environment for any calls to `azd` going forward.


4. Run this single command to provision the resources and set up the environment:

   ```shell
   azd up
   ````

   * **Important**: Beware that the resources created by this command will incur costs. You can run `azd down` or delete the resources manually to avoid unnecessary spending.

   * You will be prompted to select two locations, one for the majority of resources and one for the OpenAI resource, which is currently a short list. That location list is based on the [OpenAI model availability table](https://learn.microsoft.com/azure/ai-services/openai/concepts/models#global-standard-model-availability) and may become outdated as availability changes.


5. Edit the [.env](src/.env/) that was created by the previous step. You should add your Azure OpenAi Key:

    ```text
    AIPROJECT_CONNECTION_STRING=<your_connection_string>
    AISEARCH_INDEX_NAME="example-index"
    EMBEDDINGS_MODEL="text-embedding-ada-002"
    INTENT_MAPPING_MODEL="gpt-4o"
    CHAT_MODEL="gpt-4o"
    EVALUATION_MODEL="gpt-4o"
    ```

##  Build Custom Rag With Azure AI Foundry SDK

##  Evaluate Custom Rag With Azure AI Foundry SDK
