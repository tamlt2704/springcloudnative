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


4. Send a request to books rest api
```
python -m httpie POST :9001/books author="Lyra Silverstar" title="Nothern Lights" isbn="1234567891" price=9.90
HTTP/1.1 201
Connection: keep-alive
Content-Type: application/json
Date: Wed, 25 Jun 2025 14:51:24 GMT
Keep-Alive: timeout=15
Transfer-Encoding: chunked

{
"author": "Lyra Silverstar",
"isbn": "1234567891",
"price": 9.9,
"title": "Nothern Lights"
}

C:\Users\user>python -m httpie GET :9001/books/1234567891
HTTP/1.1 200
Connection: keep-alive
Content-Type: application/json
Date: Wed, 25 Jun 2025 14:54:26 GMT
Keep-Alive: timeout=15
Transfer-Encoding: chunked

{
    "author": "Lyra Silverstar",
    "isbn": "1234567891",
    "price": 9.9,
    "title": "Nothern Lights"
}
```

5. test validation
```
C:\Users\user>python -m httpie POST :9001/books author="John Snow" title="" isbn="123ABC56Z" price=9.9
HTTP/1.1 400
Connection: close
Content-Type: application/json
Date: Wed, 25 Jun 2025 15:03:06 GMT
Transfer-Encoding: chunked

{
    "isbn": "The ISBN format must be valid.",
    "title": "The book title must be defined."
}

```

6. Deployment pipeline: Build and test
Commit stage
* After developer commit the code
* build, unit test, integration test, static code analysis, packaging
* published artifact -> release candidate
* should be under 5 minutes

Acceptance stage
* deploy application to production-like environment
* normally test under one hour: functional test, non-functional (e.g: performance), security test, compliance test, mannual task like exploratory and usability

Production stage
* normally triggered manually



