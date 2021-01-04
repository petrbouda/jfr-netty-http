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

Add GITHUB repository to your settings.xml 

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

    <activeProfiles>
        <activeProfile>github</activeProfile>
    </activeProfiles>

    <profiles>
        <profile>
            <id>github</id>
            <repositories>
                <repository>
                    <id>central</id>
                    <url>https://repo1.maven.org/maven2</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
                <repository>
                    <id>jfr-netty-http</id>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                    <url>https://maven.pkg.github.com/petrbouda/jfr-netty-http</url>
                </repository>
            </repositories>
        </profile>
    </profiles>

    <servers>
        <server>
            <id>jfr-netty-http</id>
            <username>petrbouda</username>
            <password>23587653b547d2f96652514197b1f0a67cc117b6</password>
        </server>
    </servers>
</settings>
```

```
<dependency>
  <groupId>pbouda.jfr</groupId>
  <artifactId>netty-http-recorder</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```

