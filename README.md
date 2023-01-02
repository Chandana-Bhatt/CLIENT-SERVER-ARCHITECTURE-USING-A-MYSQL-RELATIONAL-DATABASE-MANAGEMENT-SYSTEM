# Project 2

# CLIENT-SERVER-ARCHITECTURE-USING-A-MYSQL-RELATIONAL-DATABASE-MANAGEMENT-SYSTEM

Client-Server refers to an architecture in which two or more computers are connected together over a network to send and receive requests between one another.

In their communication, each machine has its own role: the machine sending requests is usually referred as "Client" and the machine responding (serving) is called "Server".

If we extend this concept further and add a Database Server to our architecture, we can get this picture:

![IMG-9292](https://user-images.githubusercontent.com/119781770/210189351-b57baf2c-5ef1-40a4-9d57-a59eec3670a4.jpg)

In this case, our Web Server has a role of a "Client" that connects and reads/writes to/from a Database (DB) Server (MySQL, MongoDB, Oracle, SQL Server or any other),
and the communication between them happens over a Local Network (it can also be Internet connection, 
but it is a common practice to place Web Server and DB Server close to each other in local network).

In this project, two databases (one being the client and the other being the server) interact with each other.

Two EC2 instances are created with Ubuntu 20.04 LTS. One instance as a client and the other acts as a sever. 
What differentialtes the client and the server are the installations on each of the instance. Upon logging in to each of the instances via SSH, we install mysql client on one instance and my-sql server on the other. 

On the server EC2 instance, an additional 'Customer TCP' protocol based security group(inbound rules) is created to open the port 3306 as shown below:
![722F12A8-74AC-4317-AA37-99AAAEFB4999 (2)](https://user-images.githubusercontent.com/119781770/210189615-1e9f0159-c950-43f9-98da-1f894a4a134b.jpeg)

On mysql server Linux Server MySQL Server software is installed and on client, MySQL Client software is installed.

On MySQL server instance, configure MySQL server to allow connections from remote hosts.

  ```
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```

Replace ‘127.0.0.1’ to ‘0.0.0.0’ like this:
![IMG-9231](https://user-images.githubusercontent.com/119781770/210190548-3326d060-f5de-48b3-a7ee-450196f15c0b.jpg)

Again, on the server, a user and database is created like this:

![IMG-9228](https://user-images.githubusercontent.com/119781770/210190638-1c1b1d83-acc0-4443-af2e-e27848716cae.jpg)

 From mysql client Linux Server we try to connect to mysql server Database Engine remotely without using SSH. Mysql utility is used to perform this action as shown below:
 
 

7. Checking successful connection is established to a remote MySQL server and can perform SQL queries:


```
Show databases;
```
![IMG-9235](https://user-images.githubusercontent.com/119781770/210190847-41f01dff-8d5a-4dfe-adee-ff4d7f81d488.jpg)

Querying on client instance shown below:

![IMG-9237](https://user-images.githubusercontent.com/119781770/210190851-d5d1bb14-d9e2-4826-b4de-a0a9b7e07ee9.jpg)
