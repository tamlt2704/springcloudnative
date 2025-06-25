1. Init project

```
curl https://start.spring.io/starter.zip -d groupId=com.polarbookshop -d artifactId=catalog-service -d name=catalog-service -d packageName=com.polarbookshop.catalogservice -d dependencies=web -d javaVersion=17 -d bootVersion=3.5.3 -d type=gradle-project -o catalog-service.zip
```

2. Build
```
gradlew bootJar
```

3. Run application
```commandline
java -jar build/libs/catalog-service-0.0.1-SNAPSHOT.jar 
```

By adding dependencies {
implementation 'org.springframework.boot:spring-boot-starter-web'
..
} 
it will start tomcat server
