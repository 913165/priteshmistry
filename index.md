## Sample Installation

### Kafka Docker setup URL
- [https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html](https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html)

### mysql docker setup with remote connection with root user

- make sure to open port in cloud
- docker run --name=mk-mysql -p3306:3306 -v mysql-volume:/var/lib/mysql -e MYSQL_ROOT_HOST=% -e MYSQL_ROOT_PASSWORD=root -d mysql/mysql-server:8.0.20
