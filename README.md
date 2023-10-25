## CSCI 5408 Group Project - Distributed Database - By DPG9 ##
Building a simple and portable distributed database, DDBMS, and analytics systems

###
The group was required to create a light-weight distributed database management system (e.g. metadata management, data structure design, data storing, retrieval, building database and logs, analysis, and security), with custom database structure for in memory operations using various data structures such as Arrays, Tree, Linked Lists etc., and custom file design for persistent storage.

In this project, the team built a simple distributed database management system (D2_DB) that operated in 2 Linux virtual instances in the Google Cloud Platform. The team explored and implemented data structure concepts for creating the databases, its management system, and security.
In addition, the team built an analytics engine to perform basic data analytics. The database could handle requests handle from 2 users (one user for each VM instance). The database management system layer provided a command-line interface and perform various functionalities of database management system listed below.

Module 1: DB Design
  1. You need to identify one or two linear data structure(s), which can be used for query, and data processing.
  2. Once the data is processed it can be stored in a customized file format, which will be considered as your persistent storage Customized File Format cannot be in any of these formats - JSON/XML/CSV/Serialized or binary
  3. You need to maintain data dictionary or meta data file for each local DBMS, and a global metadata file; You can use same customized file format to maintain the data dictionary.

Module 2: Query Implementation
  Your application should validate and execute the following operations. (Standard SQL command and queries only)
  a. Create database
  b. Use database
  c. Create table
  d. Insert into table
  e. Select from table with single where condition (AND || OR || NOT are not required)
  f. Update one column with single where condition (AND not required)
  g. Delete a row with single where condition

Module 3: Transaction Processing
  1. Your system should identify what is a transaction and what is a normal query.
  2. In case of transaction, you cannot write the data immediately to persistent storage, you need to perform the operation in the linear data structure.
  3. Transaction follows ACID properties, so you need to consider that. [Hint: It can be achieved by scanning logs]
  {You do need to work on concurrency control. Single distributed transaction is sufficient}

Module 4: Log Management
  You need to create 3 Logs – JSON format is allowed for Logs
  1. General Logs: query execution time, state of the database (e.g. how many tables are there with number of records at a given time)
  2. Event Logs: changes in database, concurrent transactions, crash reports, etc.
  3. Query Logs: capture user queries and timestamp of query submission
  {Do not use any in-build package or libraries; You need to perform normal file read write operations to capture the query, timestamp, login details, data change etc.}

Module 5: Data Modelling – Reverse Engineering
  1. Your application should provide option for generating an ERD based on current database state.
  2. User will provide the database name, and the application will create ERD based on the metadata, and data files.
  {You do not have to create any graphical ERD, a text file containing tables, columns, relationships, cardinality will be sufficient}

Module 6: Export Structure & Value
  1. Your application should provide an option for exporting structure and values (in standard SQL format) for each database, which is selected by the end user.
  2. This is like SQL dump (structure+value) created by any standard DBMS Export option.
  3. You cannot use any external packages, and as mentioned, your export format must be in SQL
  4. Your data dump must capture the current state of the database (E.g. if there is any update performed on a data, it must be reflected in the data dump. Do not write create or insert statements from console input to a file as the SQL export. You must dynamically generate it)

Module 7: Analytics<br>
  1. The D2_DB application should provide some basic analytics – The results must be written in files, and displayed on screen<br>
     a. How many queries (valid + invalid) are submitted by Database. (E.g. ran in VM1 instance)<br>
     E.g.: >> count queries;<br>
         “user SDEY submitted 10 queries for DB1 running on Virtual Machine 1”<br>
         “user Alex submitted 3 queries for DB2 running on Virtual Machine 2”<br>
     b. How many Update operations are successfully executed by Tables<br>
     E.g. >> count update DB1;<br>
         “Total 9 Update operations are performed on Employee”<br>
         “Total 3 Update operations are performed on Department”<br>
                
Module 8: User Interface & Login Security<br>
  1. Your user interface design should be basic console-based<br>
  2. It must provide access to the valid user only.<br>
  3. User interface can be menu driven, and provide options for registration or login<br>
  4. For registration, it should accept the userID, password, and security questions/answers - and store all information in the User_Profile text file<br>
      a. Use some hashing like md5, Sha1 etc. and store the hashed UserID, hashed password in the file. (you can use Java libraries for hashing)<br>
      b. You do not have to encrypt security question/answer.<br>
  5. If a registered user wants to access the system he/she/they needs to provide valid UserID, and password, which will be hashed, and checked with the entry available in the User_Profile text file. The security answer will also be asked at login. Since you are building a distributed database management system, User_Profile text file needs to be present in both vistual machine instances.<br>
  6. Once the users gain access, they get 5 options.<br>
      E.g.<br>
      1. Write Queries<br>
      2. Export<br>
      3. Data Model<br>
      4. Analytics<br>
  7. The “Write Queries” option should work for both normal queries and transaction.



### Developers ###
1. Aravind Jayanthi
2. Minal Khona
3. Nirav Radadiya
4. Sanika Tamhankar
5. Chanpreet Singh

### Steps to Run the Application ###

1. `mvn clean install`
2. `java -jar target\DPG9-DistributedDb.jar`
