# ReviewBot workers

This repository contains a docker image to spin up reviewbot workers. It should
be spin up reviewbot and isolate it's resources and all the rest that comes
with docker :P.

## Running

There are three methods of running this, either with a default RabbitMQ
instance or with specifying the broker URL, or as a testing instance with
`docker-compose`

### Testing instance

This requires an actual checkout of the repository. `cd` into the directory
then run

```bash
docker-compose -d up
```

### Default RabbitMQ

```bash
$ docker run -d --name rabbitmq rabbitmq
$ docker run --rm --link rabbitmq linkinpark342/docker-reviewbot worker
```

### Specifying a Broker

```bash
$ docker run --rm -e "BROKER_URL=amqp://guest:guest@localhost:5672//" linkinpark342/docker-reviewbot worker
```
