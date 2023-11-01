FROM apache/skywalking-java-agent:9.0.0-java17 AS skyBuilder

RUN curl -O https://arthas.aliyun.com/arthas-boot.jar

FROM openjdk:17-ea-jdk-slim

COPY --from=skyBuilder /skywalking/agent /skywalking

COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-jackson-2.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-mybatis-3.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-nacos-client-2.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-resttemplate-6.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-sentinel-1.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-spring-cloud-gateway-3.x-plugin-9.0.0.jar /skywalking/plugins

RUN rm /skywalking/plugins/apm-activemq-*
RUN rm /skywalking/plugins/apm-postgresql-*
RUN rm /skywalking/plugins/apm-aerospike-plugin-*
RUN rm /skywalking/plugins/apm-pulsar-*
RUN rm /skywalking/plugins/apm-armeria-*
RUN rm /skywalking/plugins/apm-quasar-plugin-*
RUN rm /skywalking/plugins/apm-rabbitmq-plugin-*
RUN rm /skywalking/plugins/apm-avro-plugin-*
RUN rm /skywalking/plugins/apm-cassandra-java-driver-*
RUN rm /skywalking/plugins/apm-clickhouse-*
RUN rm /skywalking/plugins/apm-rocketmq-3.x-*
RUN rm /skywalking/plugins/apm-rocketmq-4.x-*
RUN rm /skywalking/plugins/apm-cxf-3.x-*
RUN rm /skywalking/plugins/apm-dubbo-2*
RUN rm /skywalking/plugins/dubbo-2.7.x*
RUN rm /skywalking/plugins/apm-servicecomb-java-chassis*
RUN rm /skywalking/plugins/apm-sharding-sphere-*
RUN rm /skywalking/plugins/apm-shardingsphere-4.0.x*
RUN rm /skywalking/plugins/apm-elastic-job-*
RUN rm /skywalking/plugins/apm-elasticsearch-5.x*
RUN rm /skywalking/plugins/apm-elasticsearch-6.x*
RUN rm /skywalking/plugins/apm-solrj-7.x*
RUN rm /skywalking/plugins/apm-finagle*
RUN rm /skywalking/plugins/apm-spring-cloud-feign-1.x*
RUN rm /skywalking/plugins/apm-grizzly*
RUN rm /skywalking/plugins/apm-spring-kafka*
RUN rm /skywalking/plugins/apm-hbase*
RUN rm /skywalking/plugins/apm-spymemcached*
RUN rm /skywalking/plugins/apm-struts2*
RUN rm /skywalking/plugins/apm-impala-jdbc*
RUN rm /skywalking/plugins/apm-vertx-core*
RUN rm /skywalking/plugins/apm-xmemcached*
RUN rm /skywalking/plugins/apm-jersey*
RUN rm /skywalking/plugins/apm-jetty-*
RUN rm /skywalking/plugins/baidu-brpc-*
RUN rm /skywalking/plugins/dbcp-*
RUN rm /skywalking/plugins/druid-*
RUN rm /skywalking/plugins/graphql-*
RUN rm /skywalking/plugins/apm-light4j-*
RUN rm /skywalking/plugins/apm-mariadb-*
RUN rm /skywalking/plugins/apm-mssql-*
RUN rm /skywalking/plugins/micronaut-*
RUN rm /skywalking/plugins/motan-*
RUN rm /skywalking/plugins/apm-nutz-*
RUN rm /skywalking/plugins/apm-play-*
RUN rm /skywalking/plugins/websphere-*
RUN rm /skywalking/plugins/sofa-rpc-*
RUN rm /skywalking/plugins/resteasy-*
RUN rm /skywalking/plugins/tomcat-*
RUN rm /skywalking/plugins/nats-*
RUN rm /skywalking/plugins/apm-mongodb-2.x-*
RUN rm /skywalking/plugins/apm-mongodb-3.x-*
RUN rm /skywalking/plugins/apm-mongodb-4.x-*
RUN rm /skywalking/plugins/apm-springmvc-annotation-3.x*
RUN rm /skywalking/plugins/apm-springmvc-annotation-4.x*
RUN rm /skywalking/plugins/apm-kylin-jdbc*
RUN rm /skywalking/plugins/jsonrpc4j-*
RUN rm /skywalking/plugins/jedis-2*
RUN rm /skywalking/plugins/apm-okhttp-3*
RUN rm /skywalking/plugins/apm-tomcat-*
RUN rm /skywalking/plugins/apm-mysql-5*
RUN rm /skywalking/plugins/apm-mysql-6*
RUN rm /skywalking/plugins/apm-elasticjob*
RUN rm /skywalking/plugins/apm-resttemplate-3*
RUN rm /skywalking/plugins/apm-resttemplate-4*
RUN rm /skywalking/plugins/apm-httpclient-3*
RUN rm /skywalking/plugins/apm-httpClient-4*

WORKDIR /app

COPY --from=skyBuilder /skywalking/arthas-boot.jar /app/arthas-boot.jar

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

ENV LANG="zh_CN.UTF-8"

ENV JAVA_TOOL_OPTIONS=-javaagent:/skywalking/skywalking-agent.jar
