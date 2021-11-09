# Docker com MongoDB e MongoExpress
### Rodando Docker | MongoDB | Mongo Express

## 1 Imagem Mongo Express
https://hub.docker.com/_/mongo-express

## 2 - Criando o volume
É preciso criar um volume para que os dados permanessão 
...

docker volume create mongo_db
...
## 3 - Criar a rede de comunicação entre os containers

docker network create net_mongo

## 4 Criando a imagem do Mongo

docker container run --name mongoDB -v "mongo_db:/dados" -d mongo:latest

## 5 - Vinculando a imagem na rede
docker network connect net_mongo <ID da imagem>

## 6 - Criando a imagem do Mongo-Express
docker container run --network NetMongo \
-e ME_CONFIG_MONGODB_SERVER=mongoDB \
-p 8081:8081 mongo-express:0.54.0

## 7 - Mongo Express
![Mongo Express](img/mongo-express.png)
