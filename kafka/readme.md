# kafka in kind

create kafka cluster with one master and three workers
```
kind create cluster --config ./kafka/kind-config.yml
```

create namespace
```
kubectl create namespace kafka
```

deploy kafka
```
kubectl apply -f kafka/kind-kafka-deployment.yaml
```

To test:
kafka uses topic to identify messages
1. get a command line in of broker

create a topic
start k9s. get into shell of one kafka instance:
```
kafka-topics.sh --create --topic kebin-test-msg --bootstrap-server kafka-svc:9092
```



Consumer side
```
root@kafka-1:/# kafka-console-consumer.sh --bootstrap-server kafka-svc:9092 --topic kebin-test-msg
one test
another
^CProcessed a total of 2 messages
root@kafka-1:/# kafka-console-consumer.sh --bootstrap-server kafka-svc:9092 --topic kebin-test-msg --from-beginning
one test
another
test offline
how about now
```

Producer:
```
root@kafka-2:/# kafka-console-producer.sh --bootstrap-server kafka-svc:9092 --topic kebin-test-msg
>one test
>another
>test offline
>how about now
```