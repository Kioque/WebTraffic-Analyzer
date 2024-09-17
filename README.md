# WebTraffic Analyzer

## Demo
- Public internet access
  ![](https://media.giphy.com/media/vHud5QvH609KU0Mnle/giphy.gif)

- Hover the mouse to view the corresponding data
  ![](https://media.giphy.com/media/7CT1VlM78Cp7Floe6J/giphy.gif)

- Can also select data view mode
  ![](https://media.giphy.com/media/7eFh58dNpRgmx656Ai/giphy.gif)



## Server

### Tech Stack

- SpringBoot
- MyBatisPlus
- MySQL

### Dev Environment

- CentOS7

### Data Processing

Hadoop：

- Hive: Data computing and storaging
- Sqoop: Data migration. This project mainly loads data from Hive to the local database
- Flume: Log collection
- Azkaban: Used for batch workflow task scheduling

### References

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.6.2/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/2.6.2/maven-plugin/reference/html/#build-image)
* [Spring Web](https://docs.spring.io/spring-boot/docs/2.6.2/reference/htmlsingle/#boot-features-developing-web-applications)
* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* https://spring.io/guides/tutorials/bookmarks/)



## Client

### Tech Stack

- HTML/CSS
- Vue.js
- Echarts

### Run the web dashboard

First run:

```
npm install
```

Then run the project in development stage:

```
npm run serve
```

Or build the project in production stage:

```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



