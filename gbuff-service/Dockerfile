FROM hseeberger/scala-sbt

RUN mkdir -p /buff

WORKDIR /buff

RUN ls -la

COPY service-common/src /buff/service-common/src
COPY service-common/project /buff/service-common/project
COPY service-common/build.sbt /buff/service-common

WORKDIR /service-common
RUN ls -la
RUN sbt publishLocal
RUN ls -la

#COPY gbuff-service/app /buff/gbuff-service/app
#COPY gbuff-service/conf /buff/gbuff-service/conf
#COPY gbuff-service/project /buff/gbuff-service/project
#COPY gbuff-service/test /buff/gbuff-service/test
#COPY gbuff-service/build.sbt /buff/gbuff-service
#COPY gbuff-service/README.md /buff/gbuff-service
#COPY gbuff-service/akka_multitail.conf /buff/gbuff-service
#COPY gbuff-service/Global.scala /buff/gbuff-service
#
#RUN ls -la

#

#
#WORKDIR /root
#RUN ls -la
#
#
#WORKDIR /gbuff-service
#
#RUN ls -la
#RUN cat conf/application.conf
#RUN cat conf/jndi.properties
##RUN ls -la
##

