## 观潮 :id=start
> 苏轼

庐山烟雨浙江潮，未至千般恨不消。<br/>
到得还来别无事，庐山烟雨浙江潮。

## 作者简介
- 入行九载、始终未脱离研发一线
- 干的了开发（5年以上）、做的了架构（3年以上）
- 目前就职于某集团企业的科技子公司负责Devops平台建设
- 主要感兴趣领域：微服务、云原生、Devops
- 喜欢整洁的系统架构，致力于通过技术手段来解决研发人员的"被动"处境
- 非常喜欢苏东坡的人生态度

## 框架介绍
根据作者多年的项目研发经验发现大部分的研发人员在开发过程中遇到的"奇奇怪怪"的问题，90%以上基本都可以通过一些良好技术组件规避掉，因此有了这套技术框架。
它的目的是希望将日常开发中一些优秀实践封装起来，降低常见功能使用复杂度，以微服务技术组件的形式赋能开发，致力于让代码变得简洁优雅，让开发变得简单高效，减少996，实现 **按时下班、回家吃饭** 的正常生活！

如果您觉得本框架具有一定的参考价值和借鉴意义，请帮忙在页面右上角 [Star] 为作者加油助力！

## 技术选型

>Spring Cloud provides tools for developers to quickly build some of the common patterns in distributed systems (e.g. configuration management, service discovery, circuit breakers, intelligent routing, micro-proxy, control bus, one-time tokens, global locks, leadership election, distributed sessions, cluster state). Coordination of distributed systems leads to boiler plate patterns, and using Spring Cloud developers can quickly stand up services and applications that implement those patterns. They will work well in any distributed environment, including the developer’s own laptop, bare metal data centres, and managed platforms such as Cloud Foundry.	
-- 摘自 Spring Cloud官网

目前SpringCloud已经成为构建微服务架构的事实标准，因此框架的技术选型上，主要以Spring Cloud技术体系为主同时会结合Spring Cloud Alibaba技术栈。

|  服务   | Spring Cloud官方  | Spring Cloud Netflix  | Spring Cloud Alibaba  | Happy Code  |
|:----|:----|:----|:----|:----  |
| 配置中心  | Spring Cloud Config | Archaius | Nacos Config | Nacos Config | 
| 服务注册/发现  | -- | Eureka | Nacos Discovery | Nacos Discovery | 
| 服务熔断/降级  | -- | Hystrix | Sentinel | Sentinel |
| 服务网关  | Spring Cloud Gateway | Zuul | Dubbo + Servlet | Spring Cloud Gateway |
| 服务调用  | OpenFeign/RestTemplate | Feign | Dubbo RPC | OpenFeign/RestTemplate |
| 负载均衡  | -- | Ribbon | Dubbo LoadBalance | Ribbon |
| 分布式消息  | RabbitMQ Binder | -- | RocketMQ Binder | RocketMQ Binder |
| 消息总线  | RabbitMQ Bus | -- | RocketMQ Bus | RocketMQ Bus |
| 分布式事务  | -- | -- | Seata | Seata |
| 缓存  | -- | -- | -- | Jetcache |
| 定时调度  | -- | -- | -- | XXL-JOB |

## 工程清单
工程目录：
- happy-code-base
- happy-code-dependencies
- happy-code-parent 
- happy-code-starters 核心组件(持续扩充...)
  - happy-code-starter-log
  - happy-code-starter-mybatis
  - happy-code-starter-user
  - happy-code-starter-swagger
  - happy-code-starter-validator
  - happy-code-starter-web
  - happy-code-starter-cache
  - happy-code-starter-mq

### 重要依赖
- spring Cloud Hoxton.SR8
- spring Cloud Alibaba 2.2.3.RELEASE
- lombok 1.18.12
- hutool 5.3.9
- fastjson 1.2.73
- guava 28.0-jre
- knife4j 3.0.2
- jetcache 2.6.0
- fastjson 1.2.75
- transmittable-thread-local 2.9.0

## 封装逻辑
![](_media/happy-code.png ':id=happy-code-art')

## 参考资料

- [Spring-Cloud-Alibaba版本说明](https://github.com/alibaba/spring-cloud-alibaba/wiki/%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E)
- [transmittable-thread-local](https://github.com/alibaba/transmittable-thread-local)
- [Nacos](https://nacos.io/zh-cn/docs/quick-start.html)
- [Seata](http://seata.io/zh-cn/docs/user/quickstart.html)
- [knife4j](https://gitee.com/xiaoym/knife4j)
- [hutool](https://hutool.cn/)
- [mybatis](https://mybatis.org/mybatis-3/zh/index.html)
- [mybatis-plus](https://baomidou.com/guide/#%E7%89%B9%E6%80%A7)
- [jetcache](https://github.com/alibaba/jetcache/wiki/Home_CN)
- [COLA](https://github.com/alibaba/COLA)
- [XXL-JOB](https://www.xuxueli.com/xxl-job/#%E3%80%8A%E5%88%86%E5%B8%83%E5%BC%8F%E4%BB%BB%E5%8A%A1%E8%B0%83%E5%BA%A6%E5%B9%B3%E5%8F%B0XXL-JOB%E3%80%8B)



