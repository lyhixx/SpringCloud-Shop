# 基于Spring Boot、Spring Cloud的微服务应用

本项目内容基于Spring Boot、Spring Cloud开发。实现电商应用基础服务，包括用户服务，商品服务，订单服务,功能包括用户注册，用户鉴权，商品列表，商品详情，下单，查看订单列表，订单详情。

- 使用Spring Boot, Spring JPA实现底层服务的CRUD 
- 单元测试，API测试 
- 符合RESTful API规范 
- 实现服务注册发现组件
- 实现服务网关组件
- 实现服务的高可用

## 开发环境及项目框架介绍
* IDE: Intellij IDEA
* 缓存服务器(数据库): Redis
* 数据库: MySQL([数据库代码dbkeda.sql](https://github.com/suxiongwei/SpringCloud-Shop/blob/master/web/src/main/resources/static/db/dbkeda.sql))
* 代码管理: Git
* 项目框架: Spring Boot + Spring Cloud

## 服务介绍
- api-gateway      : 服务网关       
- eureka-server    : 服务注册中心   
- config-server    : 分布式配置中心 
- category-service : 商品服务       
- order-service    : 订单服务       
- user-service     : 用户服务       
- web-app          : web服务        

## 演示步骤
- 1、开启Redis和MySQL服务

- 2、分别启动各个微服务：EurekaServerApplication、ApiGatewayApplication、ConfigServerApplication、CategoryApplication、OrderApplication、UserApplication、WebApplication

- 接口访问示例

  - 商品服务-查看商品详情功能[GET]：http://localhost:8080/web-app/category/introduction/1?accessToken=test

    返回Json

    ```json
    {
        "code": 0,
        "msg": "成功",
        "data": {
            "id": 1,
            "level": 1,
            "parentId": null,
            "childs": [
                {
                    "id": 2,
                    "level": 1,
                    "parentId": 1,
                    "childs": [],
                    "name": "ZEK 原味海苔",
                    "orderNumber": 2,
                    "price": 8.9,
                    "img": "/eureka-web/img/cp2.jpg",
                    "detail": "ZEK 原味海苔 详情"
                },
                {
                    "id": 3,
                    "level": 1,
                    "parentId": 1,
                    "childs": [],
                    "name": "萨拉米 1+1小鸡腿",
                    "orderNumber": 3,
                    "price": 29.99,
                    "img": "/eureka-web/img/cp.jpg",
                    "detail": "萨拉米 1+1小鸡腿 详情"
                }
            ],
            "name": "海味",
            "orderNumber": 1,
            "price": 29.99,
            "img": "/eureka-web/img/cp.jpg",
            "detail": ""
        }
    }
    ```
    
  - 用户服务-登录功能[POST]：http://localhost:8080/web-app/users/login?name=admin&password=123456

    返回Json

    ```json
      {
        "code": 0,
        "msg": "成功",
        "data": null
      }
    ```

  - 订单服务-添加订单[POST]：http://localhost:8080/web-app/order/addOrder?categoryId=1&summoney=10.0&accessToken=test

    返回Json

    ```json
      {
        "code": 0,
        "msg": "成功",
        "data": null
      }
    ```
    
  - 其它的服务参见代码路由，在这里不再赘述

## 学习记录
- [微服务框架](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/micro_service.md)
- [Spring Boot](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/spring_boot.md)
- [Redis在Window 下的安装](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/redis/redis.md)
- [Spring Session的集成](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/spring_session.md)
- [Spring Boot配置事务管理](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/transactional.md)
- [Spring Cloud:注册中心Eureka](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/eureka.md)
- [Spring Cloud:负载均衡Ribbon](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/ribbon.md)
- [Feign声明式服务调用](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/feign.md)
- [Zuul实现微服务网关](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/zuul.md)
- [Config分布式统一配置中心](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/config.md)
- [SpringData-JPA的集成](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/spring/springData-jpa.md)
- [编码规范](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/other/coding_standards.md)
- [基于ACCESS TOKEN的权限解决方案](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/other/access_token.md)
- [集成redis做缓存](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/redis/redis_cache.md)
- [修改github上仓库的项目语言](https://github.com/suxiongwei/suxiongwei.github.io/tree/master/article/other/github_language.md)
- [@RequestBody](https://github.com/suxiongwei/suxiongwei.github.io/blob/master/article/spring/%40RequestBody.md)
- [springboot自定义控制台输出](https://github.com/suxiongwei/suxiongwei.github.io/blob/master/article/spring/springboot_banner_text.md)
- [SpringBoot项目在IntelliJ IDEA中实现热部署](https://www.cnblogs.com/winner-0715/p/6666579.html)
- [Java 微服务框架选型（Dubbo 和 Spring Cloud？）](https://www.cnblogs.com/xishuai/archive/2018/04/13/dubbo-and-spring-cloud.html)

## 参考博客
- [Spring Boot基础教程](http://blog.didispace.com/Spring-Boot%E5%9F%BA%E7%A1%80%E6%95%99%E7%A8%8B/)
- [Spring-Cloud基础教程](http://blog.didispace.com/Spring-Cloud%E5%9F%BA%E7%A1%80%E6%95%99%E7%A8%8B/ )

## 感谢
本项目是本人在实习期考核的项目，不是很完善，但还是收到了很多朋友的Star，十分感谢。
