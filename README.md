




## 项目简介

novel 是一套基于时下**最新** Java 技术栈 Spring Boot 3 + Vue 3 开发的前后端分离**学习型**
小说项目，开发上线一套生产级别的 Java系统，由小说门户系统、作家后台管理系统、平台后台管理系统等多个子系统构成。包括小说推荐、作品检索、小说排行榜、小说阅读、小说评论、作家专区、新闻发布等功能。

## 项目地址

- 项目地址：[GitHub](https://github.com/724213274/novel)

## 开发环境

- MySQL 8.0
- Redis 7.0
- Elasticsearch 8.2.0（可选）
- RabbitMQ 3.10.2（可选）
- XXL-JOB 2.3.1（可选）
- JDK 17
- Maven 3.8
- IntelliJ IDEA 2021.3（可选）
- Node 16.14

**注：Elasticsearch、RabbitMQ 和 XXL-JOB 默认关闭，可通过 application.yml 配置文件中相应的`enable`配置属性开启。**

## 后端技术选型

| 技术                  |       版本       | 说明                  | 官网                                |
|---------------------|:--------------:|---------------------| --------------------------------------- |
| Spring Boot         | 3.0.0-SNAPSHOT | 容器 + MVC 框架         | https://spring.io/projects/spring-boot  |
| MyBatis             |     3.5.9      | ORM 框架              | http://www.mybatis.org                  |
| MyBatis-Plus        |     3.5.1      | MyBatis 增强工具        | https://baomidou.com/                   |
| JJWT                |     0.11.5     | JWT 登录支持            | https://github.com/jwtk/jjwt            |
| Lombok              |    1.18.24     | 简化对象封装工具            | https://github.com/projectlombok/lombok |
| Caffeine            |     3.1.0      | 本地缓存支持              | https://github.com/ben-manes/caffeine                |
| Redis               |      7.0       | 分布式缓存支持             | https://redis.io                   |
| Redisson            |      3.17.4       | 分布式锁实现              | https://github.com/redisson/redisson                   |
| MySQL               |      8.0       | 数据库服务               | https://www.mysql.com                   |
| ShardingSphere-JDBC |      5.1.1       | 数据库分库分表支持           | https://shardingsphere.apache.org                   |
| Elasticsearch       |     8.2.0      | 搜索引擎服务              | https://www.elastic.co                   |
| RabbitMQ            |     3.10.2     | 开源消息中间件             | https://www.rabbitmq.com                   |
| XXL-JOB             |     2.3.1      | 分布式任务调度平台           | https://www.xuxueli.com/xxl-job                   |
| Sentinel            |     1.8.4      | 流量控制组件              | https://github.com/alibaba/Sentinel                  |
| Springdoc-openapi   |     2.0.0-M4-SNAPSHOT      | Swagger 3 接口文档自动生成  | https://github.com/springdoc/springdoc-openapi                  |
| Spring Boot Admin   |     3.0.0-M1      | 应用管理和监控             | https://github.com/codecentric/spring-boot-admin                  |
| Undertow            |  2.2.17.Final  | Java 开发的高性能 Web 服务器 | https://undertow.io |
| Docker              |       -        | 应用容器引擎              | https://www.docker.com/                 |
| Jenkins             |       -        | 自动化部署工具             | https://github.com/jenkinsci/jenkins    |
| Sonarqube           |       -        | 代码质量控制              | https://www.sonarqube.org/              |

## 前端技术选型

| 技术               |  版本   | 说明                       | 官网                                |
| :----------------- | :-----: | -------------------------- | --------------------------------------- |
| Vue.js        |  3.2.13  | 渐进式 JavaScript 框架 | https://vuejs.org  |
| Vue Router            |  4.0.15  | Vue.js 的官方路由                    | https://router.vuejs.org                  |
| axios       |  0.27.2  | 基于 promise 的网络请求库               | https://axios-http.com                  |
| element-plus               | 2.2.0  | 基于 Vue 3，面向设计师和开发者的组件库   | https://element-plus.org            |

## 编码规范

- 规范方式：严格遵守阿里编码规约。
- 命名统一：简介最大程度上达到了见名知意。
- 分包明确：层级分明可快速定位到代码位置。
- 注释完整：描述性高大量减少了开发人员的代码阅读工作量。
- 工具规范：使用统一jar包避免出现内容冲突。
- 代码整洁：可读性、维护性高。
- 依赖版本：所有依赖均使用当前最新可用版本以便新技术学习。

## 包结构

```
io
 +- github
     +- xxyopen   
        +- novel
            +- NovelApplication.java -- 项目启动类
            |
            +- core -- 项目核心模块，包括各种工具、配置和常量等
            |   +- common -- 业务无关的通用模块
            |   |   +- exception -- 通用异常处理
            |   |   +- constant -- 通用常量   
            |   |   +- req -- 通用请求数据格式封装，例如分页请求数据  
            |   |   +- resp -- 接口响应工具及响应数据格式封装 
            |   |   +- util -- 通用工具   
            |   | 
            |   +- annotation -- 自定义注解类
            |   +- aspect -- Spring AOP 切面
            |   +- auth -- 用户认证授权相关
            |   +- config -- 业务相关配置
            |   +- constant -- 业务相关常量         
            |   +- filter -- 过滤器 
            |   +- interceptor -- 拦截器
            |   +- json -- JSON 相关的包，包括序列化器和反序列化器
            |   +- task -- 定时任务
            |   +- util -- 业务相关工具 
            |   +- wrapper -- 装饰器
            |
            +- dto -- 数据传输对象，包括对各种 Http 请求和响应数据的封装
            |   +- req -- Http 请求数据封装
            |   +- resp -- Http 响应数据封装
            |
            +- dao -- 数据访问层，与底层 MySQL 进行数据交互
            +- manager -- 通用业务处理层，对第三方平台封装、对 Service 层通用能力的下沉以及对多个 DAO 的组合复用 
            +- service -- 相对具体的业务逻辑服务层  
            +- controller -- 主要是处理各种 Http 请求，各类基本参数校验，或者不复用的业务简单处理，返回 JSON 数据等
            |   +- front -- 小说门户相关接口
            |   +- author -- 作家管理后台相关接口
            |   +- admin -- 平台管理后台相关接口
            |   +- app -- app 接口
            |   +- applet -- 小程序接口
            |   +- open -- 开放接口，供第三方调用 
```

## 截图

1. 首页

![img](https://s3.ax1x.com/2020/12/27/r5400A.png)

2. 分类索引页

![img](https://oscimg.oschina.net/oscnet/up-d0b2e03129bfae47b8bb96a491b73d383c5.png)

3. 搜索页

![img](https://s3.ax1x.com/2020/12/27/r5TO8x.png)

![img](https://oscimg.oschina.net/oscnet/up-ed5f689557718924acac76bc3ebca36afcb.png)

4. 排行榜

![img](https://oscimg.oschina.net/oscnet/up-78d5a68586cd92a86c669311f414508f922.png)

5. 详情页

![img](https://oscimg.oschina.net/oscnet/up-8be2495a2869f93626b0c9c1df6f329747a.png)

6. 阅读页

![img](https://oscimg.oschina.net/oscnet/up-517c84148d2db8e11717a8bbecc57fa1be7.png)

7. 用户中心

![img](https://oscimg.oschina.net/oscnet/up-805a30e7a663a3fd5cb39a7ea26bc132a01.png)

8. 作家专区

![img](https://oscimg.oschina.net/oscnet/up-30766372cc7f56480ff1d7d55198204f6ea.png)

![img](https://s3.ax1x.com/2020/11/17/DVFiQI.png)

![img](https://s1.ax1x.com/2020/11/09/B7X5oF.png)

![img](https://s1.ax1x.com/2020/11/09/B7XLsx.png)

10. 购买

![img](https://oscimg.oschina.net/oscnet/up-ce0f585efd82a9670335f118cf5897c85e9.png)

![img](https://oscimg.oschina.net/oscnet/up-f849960f4c1303fea77d26e64fc505a7180.png)

11. 接口文档

![img](https://youdoc.github.io/img/novel/SwaggerUI.png)

