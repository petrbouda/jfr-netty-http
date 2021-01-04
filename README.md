# JFR Events for Reactor Netty - HTTP SERVER

### How to enable it in SpringBoot

```
@Bean
public NettyServerCustomizer nettyServerCustomizer() {
    return server -> server.metrics(true, JfrHttpServerMetricsRecorder::new);
}
```

An application needs to have registered Micrometer Support, otherwise, Metrics Support in SpringBoot is not enabled. 

```
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-core</artifactId>
</dependency>
```


