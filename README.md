# aws-lift-and-shift

## About the Project

- Multi-tier Web Application Stack deployment on AWS.
- Application Stack includes MySql, Memcache, RabbitMQ and Apache Tomcat microservices.
- Host and run the application on the AWS Cloud for Production.


## Architecture of this project

1. **EC2** instances for Tomcat, RabbitMQ, Memcache and MySql database servers.
2. **Elastic Load Balancer**
3. **Auto Scaling Service**, which will automatically scale out and scale in EC2 instances, which will automatically control our resources and also our cost.
4. For storage, **S3** 
5. **Route 53** for a private DNS service.

## Flow of Execution
1. Create Key Pairs
2. Create Security Groups
3. Launch Instances with user data [Shell scripts]
4. Update private IP to name mapping in Route 53 and update the `application.properities` file
5. Build Application from source code.
6. Upload artifact to S3 bucket
7. Download artifact to Tomcat ec2 instance
8. Setup Elastic Load Balancer with HTTPS [Certificate from Amazon Certificate Manager]
9. Map Elastic Load Balancer Endpoint to a domain.

---

## Prerequisites
- JDK 11 
- Maven 3 
- MySQL 8

### Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- Tomcat
- MySQL
- Memcached
- Rabbitmq
- ElasticSearch
### Database
Here,we used Mysql DB 
sql dump file:
- /src/main/resources/db_backup.sql
- db_backup.sql file is a mysql dump file.we have to import this dump to mysql db server
- > mysql -u <user_name> -p accounts < db_backup.sql