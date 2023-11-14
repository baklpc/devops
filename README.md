# [mysql](mysql)

```

helm upgrade --install mysql ./mysql -f example/mysql-values.yaml 

```

# [redis](redis)

```

helm upgrade --install redis ./redis -f example/redis-values.yaml 

```

# [nacos](nacos)

```

helm upgrade --install nacos ./nacos -f example/nacos-values.yaml 

```

# [minio](minio)

```

helm upgrade --install minio ./minio -f example/minio-values.yaml 

```

# [weserv](weserv)
```

helm upgrade --install weserv ./weserv -f example/weserv-values.yaml 

```


# [rocketmq](rocketmq)

```

helm upgrade --install rocketmq ./rocketmq -f example/rocketmq-values.yaml 

```

# [xxl-job](xxl-job)

```

helm upgrade --install xxl-job ./xxl-job -f example/xxl-job-values.yaml 

```

# [seata](seata)

```

helm upgrade --install seata ./seata -f example/seata-values.yaml 

```

# [skywalking](skywalking)

```

helm upgrade --install skywalking oci://registry-1.docker.io/apache/skywalking-helm --version 4.3.0 -f example/skywalking-values.yaml 

```

# [harbor](harbor)

```

helm upgrade --install harbor ./harbor -f example/harbor-values.yaml 

```

seata es 还未部署