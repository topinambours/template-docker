# Template-Docker
<img src="https://travis-ci.com/topinambours/template-docker.svg?branch=master"> <a href="https://hub.docker.com/r/topinambours/template-docker" target="_blank"><img src="https://img.shields.io/docker/cloud/automated/topinambours/template-docker.svg"></a> <img src="https://img.shields.io/badge/language-Java-important.svg">

Docker link : https://hub.docker.com/r/topinambours/template-docker

  docker pull topinambours/template-docker
  docker run topinambours/template-docker

To deploy with travis :
```
language: java
sudo: false

jdk:
  - openjdk10

jobs:
  include:
    - stage: test
      script:
        - mvn test
    - stage : deploy
      script :
        - docker build -t topinambours/template-docker .
        - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
        - docker push topinambours/template-docker:latest
```
Travis-Ci Environment Variables : DOCKER_USERNAME , DOCKER_PASSWORD
