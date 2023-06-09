# Docker

Docker provides a relatively straightforward container service and had a very wide range of pre-made container images.

Docker works best on Linux, although should run on MacOSX and Windows, perhaps with a bit of encouragement.

Docker images can be pulled onto a local development environment and used or customised as needed.

## Docker compose

[Deploy applications on Amazon ECS using Docker Compose](https://aws.amazon.com/blogs/containers/deploy-applications-on-amazon-ecs-using-docker-compose/){target=_blank .md-button}


## Building Apps Locally


### Leiningen project

```docker
FROM clojure:openjdk-8-lein-slim-buster

RUN apt-get update

WORKDIR /app

COPY project.clj .

# We need to fetch all dependencies as otherwise the `lein compile` command will download them anyway
RUN lein with-profile dev deps
RUN lein with-profile test deps

COPY . .

RUN lein compile

CMD lein with-profile prod run -m practicalli.game-statistics.core
```

### Database

```docker
CREATE ROLE gameadmin LOGIN SUPERUSER PASSWORD 'TrustNo1';
CREATE DATABASE game-stats
    WITH
    OWNER = practicalli;
```
