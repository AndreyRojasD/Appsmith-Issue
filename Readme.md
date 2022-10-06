
# Appsmith [issues](https://discord.com/channels/725602949748752515/1022081904087941130)
--------------------------
### Steps to follow to reproduce the issues.
1. Start the appsmith [self-host.](https://docs.appsmith.com/getting-started/setup/installation-guides/docker)
2. Start a [docker-compose](mysql/docker-compose.yaml) with MySQL.
```yaml
version: '3.3'
services:
  db:
    image: mysql:5.7
    command:
        --max_connections=2
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
3. Up the docker container: `sudo docker-compose up `

` Note: To make the connections,use ngrok.`

4. Connect to the database with DBeaver and Execute a query.
5. Connect to appsmith and see the error.
` Note: disable ssl in appsmith.`

```conosle
Credentials
Database Name: mysql
Username: root
password: password
```

[Back-end logs.](https://www.udrop.com/7lr5/backend-2b407002a5c7.log)
