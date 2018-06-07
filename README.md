# MongoDB

A Docker Image for MongoDB which makes it easy to create an Admin, a Database and a Database User when the container is first launched.

# Customization

There are a number of environment variables which you can specify to customize the username and passwords of your users.

- With Dockerfile

```docker
  // Auth Configuration.
  // These environment variables can also be specified through command line or docker-compose configuration
  # ENV AUTH yes

  # ENV MONGODB_ADMIN_USER root
  # ENV MONGODB_ADMIN_PASS password

  # ENV MONGODB_APPLICATION_DATABASE your_db
  # ENV MONGODB_APPLICATION_USER user
  # ENV MONGODB_APPLICATION_PASS password
```

- With docker-compose.yml

```yaml
  services:
    db:
      image: yolk/mongo:latest
      environment:
        - AUTH=yes
        - MONGODB_ADMIN_USER=admin
        - MONGODB_ADMIN_PASS=admin123
        - MONGODB_APPLICATION_DATABASE=mongodb
        - MONGODB_APPLICATION_USER=ramaneek
        - MONGODB_APPLICATION_PASS=ramaneek123
      ports:
        - "27017:27017"
  // more configuration
```

- With command line

```bash
  docker run -it \
    -e AUTH=yes \
    -e MONGODB_ADMIN_USER=admin \
    -e MONGODB_ADMIN_PASS=adminpass \
    -e MONGODB_APPLICATION_DATABASE=mytestdatabase \
    -e MONGODB_APPLICATION_USER=testuser \
    -e MONGODB_APPLICATION_PASS=testpass \
    -p 27017:27017 yolk/mongo:latest
```