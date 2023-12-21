<h1 align='center'>  DE - 🏎 F1 Dataflow- Ashish Sahu </h1>
<p align="center">
  <img src="/Users/ashish/Library/Mobile Documents/com~apple~CloudDocs/Sync/AshishGithub/tempwork/Waqar-F1/racing-formula-1-pit-lane-ferrari.jpeg" width="800" height="400" />
</p>

## Summary 

In this project, we used the [Azure Cloud Services](https://azure.microsoft.com/en-us/products/cloud-services) to design and orchestrate a data pipeline to perform data engineering operations (Ingestion, Transformation, Analysis, Load) on a Formula 1 Racing Dataset. It begins with data extraction from the Ergast Developer API and harnesses Azure components such as Azure Active Directory, Service Principal, Azure Databricks, Key Vault, Azure Data Factory, and Azure Data Lake Gen2 to orchestrate this process efficiently. Within Azure Databricks, powered by Apache Spark, data undergoes the ETL (Extract, Transform, Load) process. The data begins its journey in the 'ingestion' folder, where it is initially received. It then proceeds to the 'transformations' folder, where it is refined and enhanced. Finally, the data finds its destination in the 'analysis' folder, where it is carefully organized and prepared for analysis. The orchestration of this data journey is managed through Azure Data Factory, representing a structured and efficient approach to data engineering and analysis.


### The repository directory structure is as follows:

```
├── README.md          <- The top-level README for developers using this project. 
| 
├── Raw           <- Contains script to define table schemas
| 
├── Transformations         <- Scripts to aggregate and transform data
│  
├── analysis         <- Basic analysis of data from the transformations folder.  
| 
│ 
├── include                <- Configuration folder 
│   ├── common_functions.py    <- Common functions used throughout the ETL process.
│   │ 
│   ├── configuration.py       <- Houses configuration settings such as variables.
│      
|         
|
├── ingestion          <- Ingestion scripts for data files from ADLS Gen 2.
│      
├── resources          <- Resources for readme file.
|
├── set-up             <- Script for mounting ADLS Gen 2 to Databricks
|         
├── utils              <- SQL scripts for incremental load.
```

## Data Source

The data for all the Formula 1 races from 1950s onwards is obtained from an open source API called [Ergast Developer API](http://ergast.com/mrd/). The structure of the database is shown in the following ER Diagram and explained in the [Database User Guide](http://ergast.com/docs/f1db_user_guide.txt)

![ERDiagram](http://ergast.com/images/ergast_db.png)

## Tools

- [Python](https://www.python.org/)
- [PySpark](https://spark.apache.org/docs/latest/api/python/)
- [Azure Databricks](https://azure.microsoft.com/en-us/products/databricks/)
- [Azure Data Factory (ADF)](https://azure.microsoft.com/en-us/products/data-factory)
- [Azure Data Lake Storage Gen2 (ADLS)](https://azure.microsoft.com/en-us/solutions/data-lake/)
- [Delta Lake](https://learn.microsoft.com/en-us/azure/databricks/delta/)


# Architecture

The solution used in this project is based on the ["Modern analytics architecture with Azure Databricks"](https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/articles/azure-databricks-modern-analytics-architecture) from the Azure Architecture Center:

<p align="center">
  <img src="https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/media/azure-databricks-modern-analytics-architecture-diagram.png" width="70%" height="70%" />
</p>


# Project Structure

1. data - contains sample raw data from Ergast API.
2. set-up - notebooks to mount ADLS storages (raw, ingested, presentaton) in Databricks.
3. raw - contains SQL file to create ingested tables using Spark SQL.
4. ingestion - contains notebooks to ingest all the data files from raw layer to ingested layer. Handles the incremental data for files results, pitstopes, laptimes and qualifying.
5. trans - contains notebooks to transform the data from ingested layer to presentation layer. Notebook performs transformations to setup for analysis.
6. analysis - contains SQL files for finding the dominant drivers and teams and to prepare the results for visualization.
7. includes - includes notebooks containing helper functions used in transformations.
8. utils - contains SQL file to drop all databases for incremental load.

## ERD

The database structure is shown in the following ER Diagram and explained in the <a href='http://ergast.com/docs/f1db_user_guide.txt'> Database User Guide </a>.

<p align='center'>
  <img src='https://github.com/waqarg2001/Formula1-Insights-DE/blob/master/resources/erd.png' width=600 height=470>
</p>  

## License

<a href = 'https://creativecommons.org/licenses/by-nc-sa/4.0/' target="_blank">
    <img src="https://i.ibb.co/mvmWGkm/by-nc-sa.png" alt="by-nc-sa" border="0" width="88" height="31">
</a>



[def]: http://ergast.com/images/ergast_db.png