FROM apache/skywalking-java-agent:9.0.0-java17 AS skyBuilder

RUN curl -O https://arthas.aliyun.com/arthas-boot.jar

FROM openjdk:17-ea-jdk-slim

# 安装 fontconfig 和 ttf-dejavu字体
RUN apk add fontconfig && apk add --update ttf-dejavu && fc-cache --force

COPY --from=skyBuilder /skywalking/agent /skywalking

COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-jackson-2.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-mybatis-3.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-nacos-client-2.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-resttemplate-6.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-sentinel-1.x-plugin-9.0.0.jar /skywalking/plugins
COPY --from=skyBuilder /skywalking/agent/optional-plugins/apm-spring-cloud-gateway-3.x-plugin-9.0.0.jar /skywalking/plugins

RUN cd /skywalking/plugins/ && rm apm-activemq-* \
&& rm apm-postgresql-* \
&& rm apm-aerospike-plugin-* \
&& rm apm-pulsar-* \
&& rm apm-armeria-* \
&& rm apm-quasar-plugin-* \
&& rm apm-rabbitmq-plugin-* \
&& rm apm-avro-plugin-* \
&& rm apm-cassandra-java-driver-* \
&& rm apm-clickhouse-* \
&& rm apm-rocketmq-3.x-* \
&& rm apm-rocketmq-4.x-* \
&& rm apm-cxf-3.x-* \
&& rm apm-dubbo-2* \
&& rm dubbo-2.7.x* \
&& rm apm-servicecomb-java-chassis* \
&& rm apm-sharding-sphere-* \
&& rm apm-shardingsphere-4.0.x* \
&& rm apm-elastic-job-* \
&& rm apm-elasticsearch-5.x* \
&& rm apm-elasticsearch-6.x* \
&& rm apm-solrj-7.x* \
&& rm apm-finagle* \
&& rm apm-spring-cloud-feign-1.x* \
&& rm apm-grizzly* \
&& rm apm-spring-kafka* \
&& rm apm-hbase* \
&& rm apm-spymemcached* \
&& rm apm-struts2* \
&& rm apm-impala-jdbc* \
&& rm apm-vertx-core* \
&& rm apm-xmemcached* \
&& rm apm-jersey* \
&& rm apm-jetty-* \
&& rm baidu-brpc-* \
&& rm dbcp-* \
&& rm druid-* \
&& rm graphql-* \
&& rm apm-light4j-* \
&& rm apm-mariadb-* \
&& rm apm-mssql-* \
&& rm micronaut-* \
&& rm motan-* \
&& rm apm-nutz-* \
&& rm apm-play-* \
&& rm websphere-* \
&& rm sofa-rpc-* \
&& rm resteasy-* \
&& rm tomcat-* \
&& rm nats-* \
&& rm apm-mongodb-2.x-* \
&& rm apm-mongodb-3.x-* \
&& rm apm-mongodb-4.x-* \
&& rm apm-springmvc-annotation-3.x* \
&& rm apm-springmvc-annotation-4.x* \
&& rm apm-kylin-jdbc* \
&& rm jsonrpc4j-* \
&& rm jedis-2* \
&& rm apm-okhttp-3* \
&& rm apm-tomcat-* \
&& rm apm-mysql-5* \
&& rm apm-mysql-6* \
&& rm apm-elasticjob* \
&& rm apm-resttemplate-3* \
&& rm apm-resttemplate-4* \
&& rm apm-httpclient-3* \
&& rm apm-httpClient-4*

WORKDIR /app

COPY --from=skyBuilder /skywalking/arthas-boot.jar /app/arthas-boot.jar

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

ENV LANG="zh_CN.UTF-8"

ENV JAVA_TOOL_OPTIONS=-javaagent:/skywalking/skywalking-agent.jar
