
# zeppelin

A `debian:jessie` based Spark [Zeppelin](http://zeppelin.incubator.apache.org) Docker container.
This was forked from [dylanmei/docker-zeppelin](https://github.com/dylanmei/docker-zeppelin) with some slight modifications to get it up with spark 1.5

## usage
Run the Zeppelin container in Spark local mode, or in a Spark cluster.

### local

Build the image and run in local mode with data volume mounted
```
docker build -t zeppelin:1.5.0 .
mkdir /data && chmod -R 777 /data
docker run -d -v /data:/zeppelin/data -p 8080:8080 -p 8081:8081 zeppelin:1.5.0
```

Zeppelin will be running at `http://${YOUR_DOCKER_HOST}:8080`.

### cluster

Create a standalone cluster with [docker-compose](http://docs.docker.com/compose):

```
docker-compose up
```

The Spark Master UI will be running at `http://${YOUR_DOCKER_HOST}:8080` and Zeppelin will be running at at `http://${YOUR_DOCKER_HOST}:8090`. Zeppelin and the Spark Worker will mount the `./data` directory as a volume and share it's contents.

## customize

modify the install.sh script:

## license

MIT
