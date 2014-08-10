![alt text](http://whiteandreetto.com/wp-content/uploads/2014/08/logo.full_.black_.png "White Andreetto Consulting")

# A Data Vault implementation
## -subtitle-
================

## -intro-

This is the implementation of ...

## Environment

## Build

[Gradle] (build.gradle) and [Maven] (pom.xml) build mechanisms are available.

## Spring

### Dependencies

```xml

        <!-- Spring Framework - Core -->
        
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>${spring.version}</version>
        </dependency>

        <!-- Spring Framework - Integration -->
        <dependency>
            <groupId>org.springframework.integration</groupId>
            <artifactId>spring-integration-core</artifactId>
            <version>${spring.integration.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>commons-logging</groupId>
                    <artifactId>commons-logging</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.springframework.integration</groupId>
            <artifactId>spring-integration-mongodb</artifactId>
            <version>${spring.integration.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>commons-logging</groupId>
                    <artifactId>commons-logging</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
```

### XML-less configuration

This prototype uses java-based Spring configuration items.
Configuration entry point is [AppConfig.java] (src/main/java/com/whiteandreetto/prototypes/simplebus/AppConfig.java).

AppConfig.java, imports @Configuration declarations from this [package] (src/main/java/com/whiteandreetto/prototypes/simplebus/cfg) which has two configuration classes, one implementing the general message flow, the other responsible for all things Mongo.

```java

@Configuration
@EnableIntegration
@IntegrationComponentScan
@ComponentScan({"com.whiteandreetto.prototypes.simplebus", "com.whiteandreetto.prototypes.simplebus.dbevents"})
@Import({MongoDBConfiguration.class, PlumbingConfiguration.class})

```
### Mongo DB configuration
[MongoDBConfiguration.java] (src/main/java/com/whiteandreetto/prototypes/simplebus/cfg/MongoDBConfiguration.java) defines a [MongoDbFactry](http://docs.spring.io/spring-data/mongodb/docs/current/api/org/springframework/data/mongodb/MongoDbFactory.html) to allow access to the Mongo DB server.


### Process Flow

[PlumbingConfiguration.java] (src/main/java/com/whiteandreetto/prototypes/simplebus/cfg/PlumbingConfiguration.java) defines the pipelines for message handling as it follows:






 


