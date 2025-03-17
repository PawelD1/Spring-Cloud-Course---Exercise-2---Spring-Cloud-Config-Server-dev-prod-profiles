In this application profile dev enables using H2 database (data stored in memory) with initial data loaded from sql file. 
Connection details are configured in private repository in file car-ms-dev.properties, imported from Spring Cloud Config Server.

File car-ms-dev.properties:

spring.datasource.url=jdbc:h2:mem:devdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=admin
spring.datasource.password=admin
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.sql.init.schema-locations=classpath:schema.sql
spring.sql.init.data-locations=classpath:data.sql
spring.sql.init.mode=always
spring.h2.console.enabled=true


Profile prod enables using MySQL database without initial Data. 
Connection details are also configured in the same private repository in file car-ms-prod.properties, imported from Spring Cloud Config Server as well. 

File car-ms-prod.properties:


eureka.client.service-url.defaultZone=http://localhost:8761/eureka/
spring.datasource.url=${MYSQL_URL}
spring.datasource.username=${MYSQL_USERNAME}
spring.datasource.password=${MYSQL_PASSWORD}
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.sql.init.mode=never
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect


Credentials necessary for GitHub account's details (username, password) and data necessary for working MySQL database and H2 database are stored in Environment Variables.
MySQL database can be launched by running docker-compose.yaml.
