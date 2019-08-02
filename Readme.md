```
mkdir buffme && cd buffme
git clone git@github.com:avevlad/docker-buff.git
git clone gbuff-service
git clone service-common
```

```
➜  projects tree buffme -L 1
buffme
├── buff-mongo-dump
├── docker-buff
├── gbuff-service
└── service-common
```


### Conf gbuff-service


```
cd gbuff-service
cp conf/jndi.properties.example conf/jndi.properties
```

`conf/jndi.properties:4` -> `java.naming.provider.url = failover:(nio://activemq:61616)`
`conf/application.conf:98` -> `mongodb.uri = "mongodb://mongodb:27017/gbuff"`
 


### Docker image (scala + sbt), hseeberger/scala-sbt

https://github.com/hseeberger/scala-sbt

```
docker build \
  --build-arg BASE_IMAGE_TAG="8u212-b04-jdk-stretch" \
  --build-arg SBT_VERSION="0.13.17" \
  --build-arg SCALA_VERSION="2.11.6" \
  -t hseeberger/scala-sbt \
  github.com/hseeberger/scala-sbt.git#:debian
```

```
docker images | grep "scala"
```

### Docker
```
cd docker-buff
docker-compose up
docker-compose stop gbuff-service
docker-compose start gbuff-service
docker-compose ps
```