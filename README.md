# sqoop-interview
# Q1.What is Sqoop and its features?
Ans: -   Apache Sqoop is a bigdata tool for transferring data between Hadoop and relational data base servers, Sqoop is used to transfer data from RDBMS (Relational data base management system) like MySQL and Oracle to HDFS. (Hadoop Distributed File system).
# Q2.  Default mapper in Sqoop.
Ans 4(We can increase based on the connection available in RDBMS).
# Q3. Controlling import/Export?
There are two types of Controlling imports.
1.	Where - can be applied over the sqoop command using --- where “city=’chennai’”.
2.	Query   can be applied over the sqoop command for joining multiple tables.
 

# Q3. Default file format in sqoop.
Ans: - Text file.
# Q4. What is Sqoop eval?
Ans: - It allows users to execute user-defined queries against respective database servers and preview the result to the console.  So, the user can expect the resultant table data to import. Using eval we can evaluate any type of SQL query that can be either DDL or DML.

 

For insert:
 
For Update:
 
Delete operation.
 



#Q5. Sqoop Incremental Append Import:
Sqoop Incremental Append imports helps to import only the newly added data at the RDBMS table. We can handle by using following command as.
--incremental append
--check-column
--last-value 10

We can handle incremental using – int, date, timestamp column as incremental column.. 
06.Sqoop incremental modified impot.
Ans :- Sqoop also has feature to import modified imports by running two jobs, One to import the data and other to apply the changes to the existing part file.

We can achieve sqoop modified import by following attributes in sqoop.
--incremental last modified.
--check-column date
--last-value 2222-03-04.
--merge-key id 
07. Sqoop job incremental automation.
Ans: -
We can automate sqoop incremental jobs using 
sqoop job –create jobname
sqoop job –exec jobname.
sqoop job –list or –show to see the job details.
For every import it will save the last value itself. It would help the next imports. You can see the jobs details under .sqopp/metastore.db.script file.
Q: What is Password file in sqoop?
Ans: - We can manage to have password file consists of password can be passed to the sqoop using command –password-file <location of the file>.
Q: Sqoop password authentication?
Ans: -
We can JCEKS for password authentication (Java crypto Encrypted key Store).  But in my case, I have password file.
Q: Sqoop Staging Exports.
Ans: -
Sqoop helps to export to the staging table first in case of any issues, Only staging table gets affected instead of target SQL table during partial export issue.

Q: Sqoop import all tables.
Yes, Sqoop can import all tables from a data base and exclude few if required.

Example: -
$sqoop import-all-tables –connect jdbc:mysql://localhost/database_name –username root –password cloudera –warehouse-dir “/user/cloudera/alltables” –exclude-table <table1>,<table2>
 

Q: MapColum java in Sqoop.
Ans: - MapColumn java is used in Sqoop to type cast the column during the imports. For example, During Avro import date columns doesn’t support. So, we can use map column java to import as a string using the following commands.

--map-column-java “tdate=string”
 

Q: Sqoop Hcatalog?
Ans: - Hcatalog is a table and the storage management service for Apache Hadoop , which enables the users with different data processing tools such as Hive, Pig, MapReduce
 to read and write on a grid with ease.

For example: -
sqoop import –connect <jdbc-url> -table <table-name> --hcatlog-table <emp> …. others Sqoop options.

 

Q: Performance (Fetch Size, Mappers, Direct Mode, Export Performance).
Import performance: -

Fetch Size: -   Sqoop import default 1000 rows as at a time. It could be increased by using –fetch-size 5000.
For example: -
$sqoop import connect <> --fetch-size 5000.
Mappers: - Default numbers of Mapper used in Sqoop is 4 however we can increase like -m 20 depends on the connection availability in 
RDBMS. It would performance boundary query and divide data into each mapper.

Direct Mode: - By using direct mode (--direct) in sqoop. It would be uses its native library for import for mysql and PostgreSQL instead of JDBC driver which enables for faster imports. How ever its available only for Mysql and PostgreSQL.

Sqoop import connect <> --fetch-size 5000 <Other statements> --direct

Export Performance: -
sqoop export -Dsqoop.export.statements.per.transaction = 1000
Dsqoop.export.records.per.statements = 1000 –connect.

 

 

 
Note Paraquet file format is used in Target system because of it columnar file format.






