# Data Engineering Learning Roadmap

## Essential skills
- **SQL & Databases**: querying and managing data
- **Data Modeling**: designing efficient schemas
- **ETL/ELT**: building and maintaining data pipelines
- **Big Data**: working with tools like Spark, Hadoop, Flink etc
- **Cloud Platforms**: AWS, GCP or Azure
- **Data Warehousing**: understanding concepts and tools (such as BigQuery or Redshift) for centralizing, optimizing, and querying large volumes of business data
- **Orchestration**: Airflow, Prefect, Dagster
- **Programmin**: mainly Python or Scala
- **Data Governance**: quality, security, compliance
- **Monitoring**: performance and error tracking

## Learning the Fundamentals
- [Problem Solving with Algorithms and Data Structures using Python](https://runestone.academy/ns/books/published/pythonds/index.html)
- Git
- Linux
- Networking
- [Sistemas Distribuídos: Conceito e Definições](https://medium.com/sicreditech/sistemas-distribu%C3%ADdos-conceito-e-defini%C3%A7%C3%B5es-f2baa4efc88d)
---
## Workflow
[Data Generation](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#1-data-generation) > [Data Storage](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#2-data-storage) > [Data Ingestion](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#3-data-ingestion) > [Data Serving](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#4-data-serving)

## 1. Data Generation
Data is generated in two primary forms: analog and digital. Analog data is continuous, real-world information representing physical quantities like temperature or sound. In contrast, digital data is either converted from analog sources (e.g., images, videos) or is natively produced by digital systems, such as mobile application logs or synthetic data.
### Sources
Data sources are the origins from which data is collected and are categorized by their nature and origin. By nature, sources are primary (firsthand data from surveys, experiments, sensors) or secondary (data collected by others, such as reports, databases, and web data). By origin, they are classified as internal (from within the organization) or external (from outside sources). They can be:
| Source  | Definition |
| ------------- |:-------------:|
| APIs       | APIs (Application Programming Interfaces) are fundamental tools for data engineers, primarily used for data collection. They are sets of protocols and rules that enable different software applications to communicate and exchange data seamlessly. By providing defined endpoints, APIs allow data engineers to interact with external services and platforms to collect, exchange, and manipulate data efficiently and securely, without needing to understand the underlying system's internal code.     |
| Database      | A database is an organized, structured collection of electronic data stored and managed by a computer system, typically through a Database Management System (DBMS). It centralizes diverse data types—from text and numbers to images and videos—enabling efficient retrieval, updating, and modification. This structured access supports a wide range of applications, from maintaining customer records to analyzing business operations.     |
| Logs      | Logs are chronological records that capture events, activities, and operations within a system. They contain detailed information such as timestamps, event details, errors, performance metrics, and user actions. Logs serve as a vital historical record, essential for troubleshooting issues, monitoring system health and security, and analyzing user behavior.     |
| Mobile apps      | Mobile apps are software programs designed for smartphones and tablets, typically distributed through app stores. They are developed primarily in three forms: native (built for a specific OS), hybrid (using web technologies wrapped in a native shell), or cross-platform (using frameworks like React Native). These apps leverage device-specific features like GPS and cameras to provide diverse functionalities, from gaming to e-commerce. The hallmarks of a well-designed mobile application are a focus on user-friendly design, fast performance, offline functionality, and robust security.     |
| IoT      | IoT (Internet of Things) refers to a network of physical devices that are connected to the internet and interact with their environment. These devices go beyond traditional computers to include a wide range of objects, from smart home thermostats to industrial robots. Their primary function is to measure and collect environmental data, and many are also capable of performing predefined actions, such as automatically adjusting a system.     |
### Data Normalization
Database Normalization is a process in database design that organizes data to reduce redundancy and improve data integrity. The core goal is to structure a database into tables and columns in such a way that data is stored logically and efficiently.
This is achieved by applying a series of rules, known as normal forms, which guide the segmentation of data into related tables and the establishment of relationships between them. The primary benefits are the elimination of duplicate data, minimization of data modification issues, and the simplification of queries.
### Data Modelling
A data model is a visual specification of data structures and business rules that illustrates the relationships between data elements. The technique used depends on the system's complexity and goals. The most common techniques include:
| Model  | Definition |
| ------------- |:-------------:|
| Entity-Relationship (ER) Modeling      | A standard technique using entities (objects), attributes (properties), and relationships to represent a system's data structure.     |
| Dimensional Modeling      | Used primarily in data warehousing and analytics, it organizes data into facts (measures) and dimensions (context) within star or snowflake schemas for simplified querying.     |
| Object-Oriented Modeling      | Represents complex systems by encapsulating data and its associated behaviors into objects, ideal for applications with intricate, interrelated data.     |
| NoSQL Modeling      | Employs flexible, schema-less approaches for databases where data structures are not rigid and may evolve over time.     |
### OLTP x OLAP
- **Online Transaction Processing (OLTP)** systems are designed for managing high-volume, routine transaction operations like data entry and retrieval. They are optimized for a large number of short, fast transactions (e.g., INSERT, UPDATE, DELETE) while ensuring data integrity and consistency in multi-user environments. Databases like PostgreSQL support OLTP through features such as ACID compliance and MVCC, which guarantee reliable and concurrent processing.
- **Online Analytical Processing (OLAP)** systems, in contrast, are designed for complex querying and data analysis. They are optimized to handle large-scale data aggregations from multiple sources, enabling business intelligence and decision-making. While OLTP focuses on running the business, OLAP is used for analyzing it.
### CAP Theorem
The CAP Theorem, or Brewer's Theorem, is a fundamental principle in distributed systems stating that it is impossible for a distributed database to simultaneously provide all three of the following guarantees:
- Consistency (C): Every read receives the most recent data.
- Availability (A): Every request gets a response, even if it's not the latest data.
- Partition Tolerance (P): The system continues to operate despite network failures.
The theorem dictates that during a network partition, a system must choose between Consistency and Availability. This trade-off is crucial for designing and selecting appropriate distributed databases for specific use cases.
### Data Collection Considerations
Before designing a technology architecture, it is crucial to consider the following factors that dictate how data is collected and ingested:
1. **Bounded vs. Unbounded Data**
  - **Bounded Data**: A finite, complete dataset with defined start and end points (e.g., a daily sales report). It is best suited for batch processing.
  - **Unbounded Data**: A continuous, potentially infinite stream of data with no predefined limits (e.g., user clickstreams, sensor data). It requires stream or real-time processing.
2. **Ingestion Frequency**
  - The process for storing data can be batch (periodic chunks), micro-batch (small, frequent chunks), or real-time (immediate), depending on business needs for data freshness.
3. **Synchronous vs. Asynchronous Ingestion**
  - **Synchronous**: The system waits for a response from the source before proceeding. This ensures acknowledgment but can create delays.
  - **Asynchronous**: Data is ingested without waiting for a response. This improves performance and decouples systems but offers less immediate guarantee of delivery.
4. **Throughput and Scalability**
  - The ingestion pipeline must be able to scale to handle growing data volumes.
  - **Risks of Poor Scalability**:
    - **Bottlenecks**: Components cannot process data fast enough, causing delays.
    - **Data Loss**: Systems become overwhelmed and discard or corrupt data.
5. **Reliability and Durability**
  - **Reliability**: Ensuring data is accurate and consistent as it enters the pipeline from various sources.
  - **Durability**: Guaranteeing that data is not lost or corrupted during the collection process.
---
## 2. Data Storage
Data storage is the process of preserving digital information on physical or cloud media for future access. It involves technologies like hard drives and cloud platforms to ensure data can be saved and retrieved later.

### Database Fundamentals
- **Database**: A structured collection of useful data, organized to serve as an asset to an organization.
- **Database Management System (DBMS)**: Software designed to maintain and facilitate the extraction of data from large collections in a timely manner.

There are two primary types of databases:
1. [_Relational Databases_](https://github.com/clazinski/data-engineering-studies/blob/main/README.md#1-relational-databases)
    - Store data in a series of related tables.
    - Provide access to data points that are linked to one another.
2. [_NoSQL Databases_](https://github.com/clazinski/data-engineering-studies/blob/main/README.md#2-nosql-databases)
    - Use a data model different from the traditional relational approach.
    - Typically prioritize horizontal scaling, eventual consistency, speed, and flexibility.
    - Commonly used for big data and real-time streaming applications.

#### Slowly Changing Dimensions (SCDs)
Slowly Changing Dimensions (SCDs) are a data warehousing technique for managing and tracking historical changes to dimension data (e.g., customer address, product price) over time.
- _Purpose_: To preserve historical accuracy by not simply overwriting old data when changes occur.
- _Benefit_: Enables accurate historical analysis and reporting by maintaining a record of how attributes looked at any point in the past.

#### Horizontal and Vertical Scaling
| Scaling  | Definition | Method |
| ------------- |:-------------:| ------------- |
| Horizontal Scaling      | Adding more machines or nodes to an existing system to distribute the workload and handle increased demand.     | "Scaling out" by adding more servers.      |
| Vertical Scaling      |  Increasing the computing power (e.g., CPU, RAM) of an existing machine in a system.     | "Scaling up" by upgrading hardware on a single server.      |

#### Star Schema and Snowflake Schema
| Feature  |	Star Schema	| Snowflake Schema |
| ------------- |:-------------:| ------------- |
| **Structure**	| A central fact table (with measurable data) surrounded by denormalized dimension tables (with descriptive details). Forms a star-like shape. |	Dimension tables are normalized into multiple related sub-dimension tables. Forms a more complex, snowflake-like structure. 
| **Key Focus**	| Simplicity and query performance for fast data analysis.	| Storage efficiency and data organization for managing complex relationships. |
| **Ideal Use Case** | When priority is fast data extraction and analysis.	| When priority is managing detailed, complex data with a focus on reducing redundancy. |

### Relational Databases and NoSQL Databases
### 1. Relational Databases:
  - MySQL
  - PostgreSQL
  - MariaDB
  - Aurora DN
  - Oracle
  - MS SQL

### 2. NoSQL Databases
  - **Document**: a type of NoSQL database designed for storing and managing semi-structured data. Data is stored in flexible formats like JSON, BSON, or XML, enabling hierarchical and variable data structures.
    - Key Characteristics:
      - Dynamic Schema: No need for a predefined, rigid schema.
      - Scalability: Designed for horizontal scaling and distribution.
      - Developer-Friendly: Data models map intuitively to application code.
    - Examples: MongoDB, ElasticSearch, CosmosDB, COuchDB

  - **Column**: a type of NoSQL database that stores data by columns rather than by rows. All the values for a single column are stored together, unlike traditional row-based databases which store all data for a single record together.
    - Key Characteristics:
      - This architecture dramatically speeds up analytical queries and saves storage space.
      - It's faster for queries that only need a few columns (e.g., calculating an average), the database can scan only the relevant columns instead of reading entire rows.
    - Examples: Cassandra, BigTable, HBase
  
---
## 3. Data Ingestion
Data ingestion is the process of collecting and importing data from various sources into a centralized database or repository. As a key step in the data engineering lifecycle, its goal is to clean and store data in an accessible, consistent format to prepare it for organizational processing and analysis.

## 4. Data Serving
Data serving is the final step in the data engineering process, where prepared and stored data is delivered to downstream applications and users to create value. It involves making coherent, transformed data accessible for various business purposes, such as training machine learning models, business intelligence (BI) analytics, and reverse ETL operations.

## AWS Certification Studies: Data Engineer — Associate
- [AWS Certified Data Engineer: Study Guide](https://itbooks.ir/assets/files/books/cloud-computing/aws-certified-data-engineer-study-guide.pdf)
- [AWS DEA-C01 certification prep course](https://www.udemy.com/course/aws-data-engineer/learn/lecture/40392584?start=0#overview)
