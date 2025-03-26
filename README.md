# Azure Cosmos DB and Key Vault MCP Server

<div align="center">
  <img src="./src/img/logo.png" alt="Azure Cosmos DB MCP server logo" width="400"/>
</div>

## What is this? 🤔

This is a server that lets your LLMs (like Claude) talk directly to your Azure Cosmos DB data and Azure Key Vault secrets! Think of it as a friendly translator that sits between your AI assistant and your database and key vault, making sure they can chat securely and efficiently.

### Quick Example
```text
You: "What were our top 10 customers last month?"
Claude: *queries your Azure Cosmos DB database and gives you the answer in plain English*

You: "Retrieve the secret value for 'mySecret'"
Claude: *fetches the secret value from Azure Key Vault and provides it to you*
```

## How Does It Work? 🛠️

This server leverages the Model Context Protocol (MCP), a versatile framework that acts as a universal translator between AI models and databases and key vaults. Although MCP is built to support any AI model, it is currently accessible as a developer preview in Claude Desktop.

Here's all you need to do:
1. Set up project (see below)
2. Add your project details to Claude Desktop's config file
3. Start chatting with your Azure Cosmos DB data and Azure Key Vault secrets naturally!

### What Can It Do? 📊

- Run Azure Cosmos DB queries by just asking questions in plain English
- Retrieve secret values from Azure Key Vault
- Check whether a certificate in Azure Key Vault is nearly expired

## Quick Start 🚀

### Prerequisites
- Node.js 14 or higher
- Azure Cosmos DB NOSQL account or Azure Cosmos DB Emulator
- Azure Key Vault
- Claude Desktop 

### Set up project

- Obtain Azure Cosmos DB NOSQL account URI and the KEY from the keys section and create an '.env' file with the below key and replace the values

```
COSMOSDB_URI=
COSMOSDB_KEY= 
KEYVAULT_URI=
```

### Getting Started

1. **Install Dependencies**  
   Run the following command in the root folder to install all necessary dependencies:  
   ```bash
   npm install
   ```

2. **Build the Project**  
   Compile the project by running:  
   ```bash
   npm run build
   ```

3. **Start the Server**  
   Navigate to the `dist` folder and start the server:  
   ```bash
   npm start
   ```

4. **Confirmation Message**  
   You should see the following message:  
   ```
   Azure Cosmos DB and Key Vault Server running on stdio
   ```

### Add your project details to Claude Destkop's config file

Open Claude Desktop and Navigate to File -> Settings -> Developer -> Edit Config and open the `claude_desktop_config` file and replace with the values below,

```json
{
  "mcpServers": {
    "cosmosdb": {
      "command": "node",
      "args": [ "C:/Cosmos/azure-cosmos-mcp/dist/index.js" ] // Your Path for the Azure Cosmos DB MCP server file,
      "env": {
        "COSMOSDB_URI": "Your Cosmos DB Account URI",
        "COSMOSDB_KEY": "Your Cosmos DB KEY",
        "KEYVAULT_URI": "Your Key Vault URI"
      }
    }
  }
}
```

You should now have successfully configured the MCP server for Azure Cosmos DB and Azure Key Vault with Claude Desktop. This setup allows you to seamlessly interact with Azure Cosmos DB and Azure Key Vault through the MCP server as shown below.

### Examples

#### Retrieving a Secret from Azure Key Vault

```text
You: "Retrieve the secret value for 'mySecret'"
Claude: *fetches the secret value from Azure Key Vault and provides it to you*
```

#### Checking Certificate Expiry in Azure Key Vault

```text
You: "Check if the certificate 'myCertificate' is nearly expired"
Claude: *checks the expiry date of the certificate in Azure Key Vault and informs you of the days remaining until expiry*
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
