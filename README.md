# kafka

## Referências

- https://medium.com/trainingcenter/apache-kafka-codifica%C3%A7%C3%A3o-na-pratica-9c6a4142a08f

## Comandos de teste

```shell
# Cria um novo tópico
docker-compose exec kafka kafka-topics --create --topic meu-topico-legal --partitions 1 --replication-factor 1 --if-not-exists --zookeep er localhost:2181

# Verifica se o tópico foi criado
docker-compose exec kafka  kafka-topics --describe --topic meu-topico-legal --zookeeper localhost:2181

# Produzindo 100 mensagens no tópico criado
docker-compose exec kafka bash -c "seq 100 | kafka-console-producer --request-required-acks 1 --broker-list localhost:9092 --topic meu-topico-legal && echo 'Produced 100 messages.'"

# Consumindo as 100 mensagens produzidas
docker-compose exec kafka kafka-console-consumer --bootstrap-server localhost:9092 --topic meu-topico-legal --from-beginning --max-messages 100
```