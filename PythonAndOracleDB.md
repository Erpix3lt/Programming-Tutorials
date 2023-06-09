# Working with python and oracleDB
Creating a new Podman/ Docker Container containing the Oracle/database/express image. Thereafter we can check the connection with any sql tool. Finally with the help of the oracleDB package we can access our very own database and insert some basic data. 

## Setting up our Podman/ Docker container
All of the podman commands can easily be interchanged with docker.
<br>
>Pull the podman image. <br>
``` bash
podman container-registry.oracle.com/database/express:latest
```

>Start the container providing a name, a port and a custom password. <br>
``` bash
podman container create `
   -it `
   --name oracle-test `
   -p 1521:1521 `
   -e ORACLE_PWD=<PW>
   container-registry.oracle.com/database/express:latest
```

## Test the running container using a sql tool
Create a new connection using the following arguments:
```
host: localhost
port: 1521
username: system
password: <PW>
sid: xe
```

You can now test the connection. In order to perfom a simple hello world, type in the following SLQ statement:
```SQL 
SELECT SYSDATE
FROM dual;
```
You should then be greeted with the current date.

## Install and initialize the oracleDB package
https://python-oracledb.readthedocs.io
In order to use pythons capabilities and communicate with our newly setup database we need to install the python-oracledb package. Simply type: <br>
```bash
pip install oracledb
```
Proceed with creating a new python file. We now have to initialize the connection to our database: 
```python
import oracledb as oracledb

userpwd = '<PW>'

connection = oracledb.connect(user="system", password=userpwd,
                              dsn="localhost:1521/xe")
```
You can now ping the connection and test if is working:
```python
# check connection status
connection.ping()
```
The following creates an example table and already inserts some smaple data: 
```python
# insert basic example data
cursor = connection.cursor()

# create table
cursor.execute("CREATE TABLE Persons (PersonID int, LastName varchar(255), FirstName varchar(255), Address varchar(255), City varchar(255))")

# insert data
cursor.execute("INSERT INTO Persons VALUES (1, 'Smith', 'John', 'Some Street 0', 'Some City')")
cursor.execute("INSERT INTO Persons VALUES (2, 'Doe', 'John', 'Some Street 1', 'Some City')")
cursor.execute("INSERT INTO Persons VALUES (3, 'Smith', 'Jane', 'Some Street 2', 'Some City')")
cursor.execute("INSERT INTO Persons VALUES (4, 'Doe', 'Jane', 'Some Street 3', 'Some City')")
cursor.execute("INSERT INTO Persons VALUES (5, 'Smith', 'John', 'Some Street 4', 'Some City')")
```
We can now access and print each row:
```python
# fetch and print data
for row in cursor.execute("SELECT * FROM Persons"):
    print(row)
```
Finnally you might want to close the running connection: 
```python
# close connection
connection.close()
```