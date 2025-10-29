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
- [A Thorough Introduction to Distributed Systems](https://www.freecodecamp.org/news/a-thorough-introduction-to-distributed-systems-3b91562c9b3c/)

## Workflow
[Data Generation](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#1-data-generation) > [Data Storage](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#2-data-storage) > [Data Ingestion](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#3-data-ingestion) > [Data Serving](https://github.com/clazinski/data-engineering-studies/tree/main?tab=readme-ov-file#4-data-serving)

### 1. Data Generation
Data is generated in two primary forms: analog and digital. Analog data is continuous, real-world information representing physical quantities like temperature or sound. In contrast, digital data is either converted from analog sources (e.g., images, videos) or is natively produced by digital systems, such as mobile application logs or synthetic data.
### Sources
Data sources are the origins from which data is collected and are categorized by their nature and origin. By nature, sources are primary (firsthand data from surveys, experiments, sensors) or secondary (data collected by others, such as reports, databases, and web data). By origin, they are classified as internal (from within the organization) or external (from outside sources). They can be:
- Database
- APIs
- Logs
- Mobile Apps
- IoT
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
- **Online Analytical Processing (OLAP**) systems, in contrast, are designed for complex querying and data analysis. They are optimized to handle large-scale data aggregations from multiple sources, enabling business intelligence and decision-making. While OLTP focuses on running the business, OLAP is used for analyzing it.

### 2. Data Storage
Data storage is the process of preserving digital information on physical or cloud media for future access. It involves technologies like hard drives and cloud platforms to ensure data can be saved and retrieved later.

### 3. Data Ingestion
Data ingestion is the process of collecting and importing data from various sources into a centralized database or repository. As a key step in the data engineering lifecycle, its goal is to clean and store data in an accessible, consistent format to prepare it for organizational processing and analysis.

### 4. Data Serving
Data serving is the final step in the data engineering process, where prepared and stored data is delivered to downstream applications and users to create value. It involves making coherent, transformed data accessible for various business purposes, such as training machine learning models, business intelligence (BI) analytics, and reverse ETL operations.
  
## AWS Certification Studies: Data Engineer — Associate
- [AWS Certified Data Engineer: Study Guide](https://itbooks.ir/assets/files/books/cloud-computing/aws-certified-data-engineer-study-guide.pdf)
- [AWS DEA-C01 certification prep course](https://www.udemy.com/course/aws-data-engineer/learn/lecture/40392584?start=0#overview)
