# Useful Architectures

If you see this on github.com, please visit https://jugi92.github.io/useful_architectures/ for better visibility of the graphs.

This is a collection of useful architecture drawings, which solve one or multiple potential usecases, including comments or alternatives.

## Analytics

### Fabric
  Full view with Layers
  [Fabric](Fabric.html)


####  Fabric Assets animated
  ![Fabric Assets with Layers](Fabric_Overview.gif)


####  Fabric Assets
  ![Fabric Assets](Fabric.svg)


####  Fabric Hierarchy  
  ![Fabric Hierarchy](Fabric_hierarchy.svg)


####  Fabric Governance Types  
  ![Fabric Governance Types](Fabric_governance_type.svg)


####  Fabric Security & Networking
  ![Fabric Security & Networking](Fabric_Security_Networking.drawio.svg)


#### Fabric Data Access Management
  ![Fabric Data Access Management](Fabric_Data_Access_Management.drawio.svg)


#### Aligning goals with different speeds
  ![Fabric-Aligning goals with different speeds](Fabric_Aligning_goals_with_different_speeds.drawio.svg)


#### Fabric with Customer Managed Key / Bring your own Key
![Fabric with Customer Managed Key / Bring your own Key](Fabric_BYOK.drawio.svg)

## Fabric Asset Table
- Workspace  
  - Lakehouse  
    - Folders  
      - Files
    - Tables
  - Warehouse

## Migrate Azure Modern Data Platform to Microsoft Fabric Intelligent Data Platform
- Synapse -> Fabric [Overall Migration Guidance](https://blog.fabric.microsoft.com/en-us/blog/microsoft-fabric-explained-for-existing-synapse-users/)
  - Workspace -> One or more Fabric Workspaces (Multiple Dev / Feature Workspace, 1  Integration, 1 Production)
  - Data Explorer Database -> Fabric Real Time Database
  - Lakedatabase -> Lakehouse
  - Linked Services
    - Azure Blob Storage -> Migrate to OneLake OR Shortcut in Lakehouse
    - Azure Data Lake Storage -> Migrate to OneLake OR Shortcut in Lakehouse
    - Azure Data Explorer -> Migrate to Fabric Real Time Database OR Fabric Real Time Database Shortcut (Follower Database) OR Use connector in pipeline or Data Flow Gen2
    - SAP CDC Connector -> Mount Azure Data Factory into Fabric and keep using Mapping Data Flow
    - Key Vault
      - in pipelines & mapping data flows-> credentials are stored in connection via [Cloud Data Sources](https://learn.microsoft.com/en-us/power-bi/connect-data/service-create-share-cloud-data-sources)
      - in Spark -> use [mssparkutils](https://learn.microsoft.com/en-us/fabric/data-engineering/microsoft-spark-utilities#credentials-utilities)
    - other
  - Synapse Link for Cosmos DB -> Mirroring via [Fabric Mirroring for CosmosDB](https://learn.microsoft.com/en-us/fabric/database/mirrored-database/azure-cosmos-db)
  - Pipeline -> Fabric Data Pipeline
    - File Triggered pipelines -> [Storage Event Trigger via Data Activator](https://learn.microsoft.com/en-us/fabric/data-factory/pipeline-storage-event-triggers)
  - Mapping DataFlow -> no direct successor, rewrite to [Fabric Dataflow Gen2](https://learn.microsoft.com/en-us/fabric/data-factory/guide-to-dataflows-for-mapping-data-flow-users) OR rewrite to Fabric Notebook
  - Spark -> Fabric Data Engineering Experience ([Migrating from Azure Synapse Spark to Fabric](https://learn.microsoft.com/en-us/fabric/data-engineering/migrate-synapse-overview))
    - Notebook -> Fabric Notebook (consider [Repo](https://github.com/microsoft/fabric-migration))
    - Spark Pool -> Fabric Spark Pool (consider [Repo](https://github.com/microsoft/fabric-migration))
    - Spark Configuration
    - Spark Libraries
    - Job definition
  - dedicated SQL Pool -> Fabric Warehouse OR Fabric Lakehouse (see [Migration: Azure Synapse Analytics dedicated SQL pools to Fabric](https://learn.microsoft.com/en-us/fabric/data-warehouse/migration-synapse-dedicated-sql-pool-warehouse), [DWU Estimation](https://blog.fabric.microsoft.com/en-us/blog/mapping-azure-synapse-dedicated-sql-pools-to-fabric-data-warehouse-compute?ft=Data-warehouse:category))
  - Serverless SQL Pool -> Fabric Lakehouse SQL Analytics Endpoint
  - Integration Runtime
    - Azure Runtime / Azure Auto Resolve Runtime -> plain Fabric Compute Capacity 
    - Self hosted Integration Runtime -> VNet Data Gateway OR On-premises Data Gateway
  - Git configuration -> Migrate to Fabric Workspace Git configuration (previously 1:1 relation between workspace and repository, now 1:1 relation between workspace and branch)
  - Azure DevOps Deployment Pipelines -> Azure DevOps Deployment Pipelines + [Fabric Deployment Pipelines](https://learn.microsoft.com/en-us/fabric/cicd/deployment-pipelines/get-started-with-deployment-pipelines)
- Power BI -> Fabric 
  - [P SKU to F SKU](https://powerbi.microsoft.com/en-us/blog/important-update-coming-to-power-bi-premium-licensing/)
  - Power BI Workspaces -> Keep as PBI Workspaces
  - [Migrate Dataflow Gen1 to Gen2](https://learn.microsoft.com/en-us/fabric/data-factory/move-dataflow-gen1-to-dataflow-gen2) 
- Blob Storage -> Migrate to OneLake ([az copy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10?tabs=dnf)) OR keep and Shortcut in Lakehouse
- ADLS -> Migrate to OneLake OR Shortcut in Lakehouse
- Azure Data Explorer -> Fabric Real Time Database OR Fabric Real Time Database Shortcut (Follower Database)
- Azure Cosmos DB -> keep as is, run analytical workloads via [Fabric Mirroring for CosmosDB](https://learn.microsoft.com/en-us/fabric/database/mirrored-database/azure-cosmos-db)
- Azure Functions -> keep as Azure Function, adapt to Fabric
- Azure Event Hub -> keep as Azure Event Hub, integrate into Eventhouse via Eventstream

### Synapse Analytics
  Full view with Layers: 
  [Analytics-with-Azure Synapse](analytics-with-azuresynapse.drawio.html)

  ![Analytics-with-Azure Synapse](analytics-with-azuresynapse.drawio.svg)

If you have an additional one or more insights on the existing ones, feel free to submit a Pull Request.
