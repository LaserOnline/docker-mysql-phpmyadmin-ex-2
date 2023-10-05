Dcoker-Compose.yml

```bash
version: '1.1'
services:
  docker-databases-mysql:
    container_name: docker-databases-mysql
    image: mysql:latest
    environment:
      MYSQL_DATABASE: databases_mysql
      MYSQL_ROOT_PASSWORD: password
      MYSQL_USER: user
      MYSQL_PASSWORD: pass
    ports:
      - "3306:3306"
    networks:
      - networks-host

networks:
  networks-host:
    driver: bridge
```
