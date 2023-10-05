Dcoker-Compose.yml

```bash
version: '1.1'
services:
  docker-databases-mysql:
    container_name: docker-databases-mysql
    image: mysql:latest
    environment:
      MYSQL_DATABASE: db_mysql
    env_file:
      - .env
    volumes:
      - ./upload_data:/docker-entrypoint-initdb.d/
      - ./data:/var/lib/mysql
    ports:
      - "3306:3306"
    networks:
      - networks-host

  docker-phpmyadmin:
    container_name: docker-phpmyadmin
    image: phpmyadmin/phpmyadmin
    environment:
      PMA_HOST: docker-databases-mysql
    env_file:
      - .env
    ports:
      - "8080:80"
    depends_on:
      - docker-databases-mysql
    networks:
      - networks-host

networks:
  networks-host:
    driver: bridge
```
ENV
```bash
MYSQL_ROOT_PASSWORD=1988
MYSQL_USER=laseronline
MYSQL_PASSWORD=1988
```
