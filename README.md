# spring-boot-eureka-zuul-demo

项目基于项目基于Spring Boot 1.5.9.RELEASE（在使用时spring-security-oauth2没有搞定，所以先去掉了），只是提供了一个简单的框架，没有复杂的功能，如果需要可以以本项目为基础进行丰富

本项目使用了zuul和Eureka。项目分三个module：client、server和zuul，其中client和server分别为Eureka对应的client和server。  
运行示例(都在本地机器idea中执行)：
## server启动  
可直接执行server中demo.EurekaServerApplication的main方法
## client启动  
client执行时需要指定server.port和spring.application.name。  
运行如下：  
cd client  
mvn spring-boot:run -Dspring.application.name=foo -Dserver.port=8081  
端口和名称可以进行指定，但是在使用zuul进行访问时需要执行已有的spring.application.name  

访问url：http://localhost:8761/  
如图所示：  
![节点图](https://github.com/asd51731/spring-boot-eureka-zuul-demo/blob/master/doc/server.png)  

## zuul启动
可直接执行zuul中demo.ZuulProxyApplication的main方法

## 访问
可以访问http://localhost:9999/foo/whoami，查看serverPort的变化。

主要foo来自于client启动时指定的spring.application.name