# if you want to add specific files to your container then you can write multiple sources and after that write destination

- docker build -f Dockerfile.dev -t my-dev-image2 .
- docker images
- docker inspect my-dev-image2
- docker run -d --name todo-app -p 8001:8000 my-dev-image2
- docker logs todo-app
- docker logs todo-app -f # to see live log

# to find out the names or IDs of the containers currently running

- docker ps # to list running containers
docker ps -a # to list all running containers

# test poetry run pytest

# to override the Startup Command for test

# to test container

# when complete then delete it by itself => --rm

- docker run -it --rm my-dev-image2 /bin/bash -c "poetry run pytest"

# -it => intrctve Trmnl -c => command

- docker run -it my-dev-image2 /bin/bash -c "poetry run pytest"
- docker run -d --rm my-dev-image2 /bin/bash -c "poetry run pytest"
- docker logs id

# after runningg container stop by 18 line

docker ps -a
  *  delete the contanier
- docker rm id 

Using the
# docker exec -it command, you can interact with a running Docker container by opening a bash shell inside it.
useful for debugging, running administrative tasks, or exploring the container's filesystem and processes

# docker exec -it <container_name_or_id> /bin/bash

Remote Explorer

- Open Folder in Container
- pre defined container configuration
- Dockerfile
  after entering in container

* new terminal in vscode
* - - Gift : Linux > Python + Poetry + codebase live

# poetry install

# ls

# ls -a

# poetry run uvicorn do_app.main:app --reload

to come out of dev container

- click on Remote Explorer
- right click on container -> reopen folder locally

# https://www.youtube.com/watch?v=h32qw986-tI&t=1696s 45:00

if you want to add things in dev container like

- open extension -> python --> install in dev container
  right click on python -> Add to devcontainer.json

Data serialization 1-yaml 2-json
compose.yml - json -> notation (key value) - yml -> superset of json , also with additional things

            # docker compose version

# docker compose.yml

- Left Side (External Port)

- Right Side (Internal Port)

# https://github.com/panaverse/learn-generative-ai/tree/main/05_microservices_all_in_one_platform/14_docker/04_compose

- in single file we can make multiple images and containers

# in compose file after writting to check whether file is written correct or not

 - docker compose config
*  first open docker
 - docker compose ps
 - docker compose up
 - docker compose up -d

* and if some error occur then docker compose down

in compose.yaml

-> first create db then fastaPI will use it
so we will create depends_on variable

depends_on: - postgres_db

  *   priority db then fastapi

 - docker compose ps

postgres -> server, is a software in which db is running , to access we need Client software -> pgAdmin to Access db , what type of data is being placed

# download

- postgresql for window
- pgadmin

-> connect your pgAdmin with your env file by entering 
* DATABASE_URL=postgresql://username:your_password@Containername:5432/mydatabase


database-> databasename ->schema -> public -> tables

# After making changes in any file

* for rebuilding

 - docker compose up -d --build
 - docker exec -it containerId /bin/bash


# APACHE Kafka

* to install kafka
  - docker pull apache/kafka:3.7.0
* start the kafka container
<!-- -p means publish  : internal port always remember -->
   - docker run -p  9092:9092 apache/kafka:3.7.0
   - docker ps
* to connect to container
  - docker exec -it contrId1st4ltrs /bin/bash
  - ls
* Kafka commands are in this directory in container
  - /opt/kafka/bin  so *    cd  /opt/kafka/bin
  - ls
 * before creating 1st Event you must create a "topic" in another terminal
  - /opt/kafka/bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092

* to display usage information
  - /opt/kafka/bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092
* write some events into the topic
   - /opt/kafka/bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092

* Open a terminal and access your Docker container
  - docker exec -it cntrId /bin/bash
 
* run kafka console consumer client 
                            #  to read event you have just created
  -  /opt/kafka/bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
