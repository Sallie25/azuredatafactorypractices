# Azure Data Factory Practices

A comprehensive learning repository containing practical examples and implementations of **Azure Data Factory (ADF)** for batch processing, data integration, and ETL workflows.

## 📌 Overview

This repository showcases hands-on practice work in understanding how to perform batch processing in Azure Data Factory. It includes multiple real-world data pipeline examples that demonstrate core ADF concepts including:

- **Pipelines**: End-to-end data workflows
- **Linked Services**: Connections to various data sources and destinations
- **Datasets**: Data structure definitions for sources and sinks
- **Data Flows**: Advanced data transformation and processing
- **Triggers**: Pipeline execution scheduling
- **Factory Configuration**: ADF factory setup and configuration

---

## 📂 Repository Structure

```
azuredatafactorypractices/
│
├── README.md                      # This file
├── publish_config.json            # ADF publish configuration
│
├── pipeline/                      # ADF Pipeline definitions
│   ├── BookSales_dataflow_pipeline.json
│   ├── Pen_Sales_dataflow_pipeline.json
│   ├── fitnessgympipeline.json
│   ├── food_delivery_pipeline.json
│   └── typicode_api_pipeline.json
│
├── linkedService/                 # Data source/destination connections
│   ├── API_RestServices_LS.json
│   ├── deeptech_AzureBlobStorage_LS.json
│   └── deeptech_AzureSqlDatabase_LS.json
│
├── dataset/                       # Dataset definitions (18+ datasets)
│   ├── API_csv_sink_data.json
│   ├── API_json_sink_data.json
│   ├── BookSales_April_data.json
│   ├── Booksalesdata.json
│   ├── PenSales_data.json
│   ├── fitness_gym_input_dataset.json
│   ├── food_delivery_input_dataset.json
│   └── ... (and more)
│
├── dataflow/                      # Data flow transformations
├── trigger/                       # Pipeline triggers
└── factory/                       # Factory configurations
```

---

## 🔑 Key Components

### Pipelines (5 Examples)

| Pipeline | Purpose | Source | Sink |
|----------|---------|--------|------|
| **BookSales_dataflow_pipeline** | Process book sales data | CSV/Blob | Database |
| **Pen_Sales_dataflow_pipeline** | Analyze pen product sales | CSV/Blob | Database |
| **fitnessgympipeline** | Fitness gym member data processing | CSV | SQL Database |
| **food_delivery_pipeline** | Food delivery order processing | CSV | SQL Database |
| **typicode_api_pipeline** | REST API data ingestion | HTTP API | Blob/SQL |

### Linked Services (3 Examples)

| Service | Type | Purpose |
|---------|------|---------|
| **API_RestServices_LS** | REST API | Connect to external REST APIs |
| **deeptech_AzureBlobStorage_LS** | Azure Blob Storage | Connect to cloud storage |
| **deeptech_AzureSqlDatabase_LS** | Azure SQL Database | Connect to SQL Database |

### Datasets (18+ Examples)

**Source Datasets:**
- `API_source_data.json` - REST API endpoints
- `fitness_gym_input_dataset.json` - Fitness data sources
- `food_delivery_input_dataset.json` - Food delivery data
- `Booksalesdata.json`, `PenSalesdata.json` - Sales data

**Sink Datasets:**
- `API_csv_sink_data.json` - CSV output
- `API_json_sink_data.json` - JSON output
- `food_delivery_sql_sink_dataset.json` - SQL output
- `fitnessgym_sink_dataset.json` - Fitness sink

---

## 🎯 Use Cases Covered

### 1. **Book & Pen Sales Analytics**
Demonstrates data consolidation and transformation of sales data across multiple months:
- April sales (BookSales_April_data)
- May sales (bookSalesMay)
- June sales (bookSalesJune_data)

### 2. **Fitness Gym Management**
Process gym membership and performance data with transformations.

### 3. **Food Delivery Operations**
ETL pipeline for order processing and analytics from food delivery platforms.

### 4. **REST API Data Ingestion**
Integration with external APIs (Typicode) to pull and transform public data.

---

## 🚀 Getting Started

### Prerequisites

- **Azure Account** with active subscription
- **Azure Data Factory** instance created
- **Linked Services** configured:
  - Azure Storage Account (for Blob Storage)
  - Azure SQL Database (for data warehouse)
  - REST API connectivity (if applicable)
- **Git** for repository management

### Setup Instructions

#### 1. Clone the Repository

```bash
git clone https://github.com/Sallie25/azuredatafactorypractices.git
cd azuredatafactorypractices
```

#### 2. Configure Azure Data Factory

Navigate to your ADF instance in Azure Portal:

1. **Create Linked Services**:
   - Import `linkedService/*.json` configurations
   - Update connection strings and credentials
   - Validate connections

2. **Create Datasets**:
   - Import all `dataset/*.json` files
   - Update paths and parameters as needed

3. **Create Pipelines**:
   - Import `pipeline/*.json` configurations
   - Link to your resources (linked services, datasets)
   - Configure parameters if needed

4. **Set Up Triggers** (if applicable):
   - Configure schedule or event-based triggers
   - Set up notifications and alerts

#### 3. Publish to Your Factory

Use the `publish_config.json` configuration:

```json
{
  "publishBranch": "adf_publish",
  "enableGitComment": true
}
```

This enables:
- Git integration for version control
- Publish branch management
- Automated comments on pull requests

---

## 📊 Data Flow Architecture

### Typical ETL Flow

```
Source Data (CSV/API)
        │
        ▼
Linked Service Connection
        │
        ▼
Dataset Definition (Schema)
        │
        ▼
Data Flow / Transformation
        │
        ▼
Sink Dataset
        │
        ▼
Target (Blob Storage / SQL DB)
```

---

## 🔄 Pipeline Execution

### Manual Trigger
```bash
# In Azure Portal
1. Navigate to Data Factory
2. Open Pipeline
3. Click "Add Trigger" → "Now"
4. Monitor pipeline run
```

### Scheduled Trigger
Configure in `trigger/` directory with cron expressions for automated scheduling.

### Monitoring
- **Monitor Tab**: View pipeline runs, activity logs
- **Alerts**: Set up email/webhook notifications
- **Analytics**: Track performance metrics

---

## 💡 Learning Path

### Beginner
1. Start with **BookSales_dataflow_pipeline** - Simple data copying
2. Understand dataset and linked service configuration
3. Monitor basic pipeline execution

### Intermediate
1. Explore **fitnessgympipeline** and **food_delivery_pipeline** - More complex transformations
2. Practice data validation and error handling
3. Learn about parameterization

### Advanced
1. Study **typicode_api_pipeline** - REST API integration
2. Implement custom data flows with SQL transformations
3. Set up complex scheduling and monitoring

---

## 📋 Datasets Overview

### Sales Data Pipelines
- **BookSales**: Track book product sales across months
- **PenSales**: Monitor pen product performance
- **Combined Cost Data**: Integrate cost information

### Domain-Specific Pipelines
- **Fitness Gym**: Member engagement and facility metrics
- **Food Delivery**: Order processing and logistics
- **Public API**: External data integration (Typicode)

---

## 🛠️ Configuration Files

### `publish_config.json`
```json
{
  "publishBranch": "adf_publish",
  "enableGitComment": true
}
```

**Purpose:**
- Manages ADF collaboration mode settings
- Enables Git branch publishing
- Allows pull request comments

---

## 🔐 Security Best Practices

- **Linked Services**: Store credentials in Azure Key Vault
- **Datasets**: Parameterize sensitive information
- **Access Control**: Use managed identities where possible
- **Audit Logging**: Enable ADF diagnostics for monitoring

---

## 📈 Performance Optimization

- **Batch Size**: Optimize dataset batch processing
- **Parallel Activities**: Configure concurrent pipeline runs
- **Integration Runtime**: Choose appropriate compute resources
- **Data Partitioning**: Partition large datasets for efficiency

---

## 🐛 Common Issues & Troubleshooting

### Issue: Linked Service Connection Failed
```
Solution:
1. Verify connection string credentials
2. Check firewall rules (especially for SQL DB)
3. Test connection in Linked Service UI
4. Review Activity Logs for detailed errors
```

### Issue: Dataset Schema Mismatch
```
Solution:
1. Validate source data format
2. Update dataset schema definition
3. Test with sample data
4. Check column mappings
```

### Issue: Pipeline Run Timeout
```
Solution:
1. Increase timeout duration
2. Optimize data flow transformations
3. Check Integration Runtime capacity
4. Consider data partitioning
```

---

## 📚 Azure Data Factory Concepts

### Core Components

| Component | Purpose |
|-----------|---------|
| **Linked Service** | Connection configuration to data stores |
| **Dataset** | Structured representation of data |
| **Pipeline** | Workflow orchestrating data movement |
| **Activity** | Individual unit of work (Copy, Data Flow, etc.) |
| **Trigger** | Event or schedule that initiates pipeline run |
| **Data Flow** | Visual transformation engine |
| **Integration Runtime** | Compute infrastructure for execution |

### Activity Types Used

- **Copy Activity**: Move data between sources and sinks
- **Data Flow Activity**: Transform data with visual mappings
- **Lookup Activity**: Query reference data
- **Wait Activity**: Introduce delays between activities

---

## 🎓 Learning Resources

- **Azure Data Factory Documentation**: https://docs.microsoft.com/azure/data-factory/
- **ADF Visual Editor**: Interactive pipeline design
- **Monitoring & Alerts**: Built-in ADF monitoring capabilities
- **Integration Runtime**: Managed and self-hosted options

---

## 📝 How to Use This Repository

1. **Reference Implementation**: Study pipeline structures and best practices
2. **Template Starting Point**: Adapt existing pipelines for your use cases
3. **Learning Resource**: Understand ADF concepts through examples
4. **Practice Scenarios**: Replicate workflows in your environment

---

## 🚀 Next Steps

### Enhance Your ADF Knowledge

- [ ] Deploy each pipeline to your ADF instance
- [ ] Modify datasets to connect to your data sources
- [ ] Set up automated scheduling and monitoring
- [ ] Implement error handling and retry logic
- [ ] Create custom data transformations
- [ ] Integrate with Azure Functions for advanced processing
- [ ] Set up alerts and notifications

### Advanced Topics

- Parameter passing between pipelines
- Recursive pipeline execution
- Integration with Synapse Analytics
- Custom activity development
- Mapping Data Flow optimization

---

## 📄 File Descriptions

### Pipelines
Each pipeline JSON defines:
- Activities (Copy, Data Flow, etc.)
- Dependencies and sequencing
- Parameter definitions
- Error handling policies

### Linked Services
Each linked service JSON contains:
- Connection type and protocol
- Authentication method
- Service endpoint configuration
- Integration runtime specification

### Datasets
Each dataset JSON specifies:
- Data format (CSV, JSON, SQL, etc.)
- Location/path information
- Schema/column definitions
- Linked service reference

---

## 🤝 Contributing

To enhance this learning repository:

1. Create feature branches for new pipelines
2. Document your pipeline purposes
3. Test configurations before committing
4. Update this README with new examples
5. Share learning insights

---

## 📞 Support & Questions

For questions about specific pipelines or configurations:

1. Review the pipeline JSON comments
2. Check Azure Data Factory documentation
3. Validate linked services and datasets
4. Monitor activity logs for error details

---

## 📜 License

This repository is intended for educational and learning purposes.

---

## 🎯 Key Takeaways

This repository demonstrates:

✅ **Data Integration Patterns**: Multiple sources to various sinks
✅ **Transformation Techniques**: Data flows for complex operations
✅ **Real-World Scenarios**: Business use cases (sales, fitness, food delivery)
✅ **Best Practices**: Proper configuration and organization
✅ **Scalability**: Handling varying data volumes
✅ **Maintainability**: Version-controlled, documented pipelines

---

## 📌 Version Information

- **Repository Created**: November 25, 2025
- **Last Updated**: November 27, 2025
- **ADF Version Targeted**: 2024+
- **Status**: Active Learning Repository

---

**Happy Learning! 🚀 Continue exploring Azure Data Factory's powerful data integration capabilities!**
