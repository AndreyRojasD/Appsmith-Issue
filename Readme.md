# Appsmith [issues](https://discord.com/channels/725602949748752515/1022081904087941130)
--------------------------
### Steps to follow to reproduce the issues.
1. Start the appsmith [self-host.](https://docs.appsmith.com/getting-started/setup/installation-guides/docker)
2. Start a docker container with MySQL.
```yaml
version: '3.3'
services:
  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: 'db'
      MYSQL_USER: 'user'
      MYSQL_PASSWORD: 'password'
      MYSQL_ROOT_PASSWORD: 'password'
    ports:
      - '3306:3306'
    expose:
      - '3306'
    volumes:
      - my-db:/var/lib/mysql
volumes:
  my-db:
```
3. First, create a new directory on the host machine.
```console
sudo mkdir -p /root/docker/[container_name]/conf.d
```
4. Create a customized MySQL configuration file inside that directory.
```console
sudo nano /root/docker/[container_name]/conf.d/my-custom.cnf
```
5. Add this configuration and save it.
```nano
[mysqld]
max_connections=2
```
6. Drop the docker-compose.
7. Add this line to the docker-compose volumes.
```console
- /root/docker/f3627439c80a/conf.d:/etc/mysql/conf.d

```
8. Up the docker container.
` Note: To make the connections,use ngrok.`
9. Connect to the database with DBeaver and Execute a query.
10. Connect to appsmith and see the error.
` Note: disable ssl in appsmith.`

```conosle
Credentials
Database Name: mysql
Username: root
password: password
```

[Back-end logs.](https://www.udrop.com/7lqM/backend-2c38e872f1a0.log)