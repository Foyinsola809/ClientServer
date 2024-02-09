# ClientServer

## Understanding Client server architecture with MySQL as RDBMS

### Project Task - Implement a Client Server Architecture using MySQL Database Management System (DBMS)

#### For this task I will aim to  create and configure 2 linux based  virtual servers (EC2 instances in AWS). One named 'MYSQLSERVER' and the other named 'MYSQLCLIENT'. On the first one I'd install mySQLserver software and the second I'd install mySQL Client software. Then use IP address of MYSQLSERVER to connect from MYSQLCLIENT

Step 1
Create an instance EC2 instance and name it `MYSQLCLIENT`
![alt text](img/01.5.INSTANCE-C.png)



##### Note - the security group of the instance is shown below


![alt text](img/02.Securitygroup-c.png)



The instance should have inbound rules allowing access only on necessary port (port 22) for management purposes.

![alt text](img/03.port22-c.png)

Step 3



Open Ubuntu and connect. Then update using `apt update`

![alt text](img/04.aptupdate.png)

Step 4 

Install mysql client using `apt install mysql  client`

![alt text](img/05.aptinst-c.png)


Step 5
Create an instance EC2 instance and name it `MYSQLSERVER`
![alt text](img/06.5.INSTANCE-S.png)



##### Note - the security group of the instance is shown below. This MUST not be the same as the security group of the MYSQLCLIENT

![alt text](img/07.secgroup-s.png)



Step 6
Create a security group allowing inbound traffic on port 3306 from the specific local IP address of MYSQLCLIENT ( Note -ensure you select "MySQL/Aurora" from the "Type" dropdown menu.)

![alt text](img/08.5.3306PORT.png)



Step 7

Open Ubuntu and connect. Then update using `apt update`

![alt text](img/09.aptupdate-s.png)



Step 8

Install mysql server using `apt install mysql  server`

![alt text](img/10.aptinstal-s.png)


Step 9 

Configure MySQL Server: On the MYSQLSERVER instance, ensure MySQL is configured to allow remote connections by editing the MySQL configuration.
Open this in the editor as shown below
![alt text](img/11.vicode.png)


Step 10 
Once in, find the line bind-address and change it to 0.0.0.0 to bind MySQL to all available network interfaces.- Save and exit the editor

![alt text](img/12.config.png)


Step 11

On `MYSQLSERVER` log in to MySQL and create a new user with password, and grant the user the neccessary priveleges

![alt text](img/14.PREPARESERVER.png)


Step 12

On `MYSQLCLIENT` server connect to the`MYSQLSERVER` remotely as shown below;

![alt text](img/15.CONNECT.png)



