## 使用步骤
### 引入Parent
- [MAVEN](https://mvnrepository.com/search?q=happycoding) 
- 最新版本：```1.0.2.RELEASE``` 

```xml
<parent>
    <groupId>cool.happycoding</groupId>
    <artifactId>happy-code-parent</artifactId>
    <version>${happy-code.version}</version>
</parent>
```
!> happy-code-parent，定义了Spring Cloud、Spring Cloud Alibaba 和 Spring Boot版本号,引入后在添加happy-code,spring-boot,spring cloud,spring alibaba cloud 组件时均不需要再指定版本号，以parent里定义的版本号为主

### 引入组件依赖
工程初始化，根据开发需要需要引入以下组件依赖，建议采用配套的[脚手架](happy-code/bootstrap)来进行初始化

- 引入Web组件
```xml
<parent>
    <groupId>cool.happycoding</groupId>
    <artifactId>happy-code-starter-web</artifactId>
</parent>
```

- 引入校验组件
```xml
 <parent>
     <groupId>cool.happycoding</groupId>
     <artifactId>happy-code-starter-validator</artifactId>
 </parent>
 ```

- 引入Swagger组件
```xml
<parent>
    <groupId>cool.happycoding</groupId>
    <artifactId>happy-code-starter-swagger</artifactId>
</parent>
```

### 工程目录结构

```
└─src
    ├─main
    │  ├─java
    │  │  └─com
    │  │      └─xxx
    │  │          └─<module>
    │  │              ├──rest.v1
    │  │              │       └─XxxController.java
    │  │              ├──service
    │  │              │      ├─XxxService.java
    │  │              │      └─impl
    │  │              │          └─XxxServiceImpl.java
    │  │              ├─dto
    │  │              │  └─form
    │  │              │  │   └─XxxAddForm.java
    │  │              │  │   └─XxxQryForm.java
    │  │              │  │   └─XxxQryPageForm.java
    │  │              │  │   └─XxxUpdateForm.java
    │  │              │  └─XxxDto.java
    │  │              └─dao
    │  │              │  ├─entity
    │  │              │  │   └─Xxx.java
    │  │              │  ├─mapper
    │  │              │  |   └─XxxMapper.java
    │  │              │  └─cache 
    │  │              └─common // 公共定义(错误码、常量、工具类)
    │  │              │   └─<module>Status.java // 错误码定义
    │  │              └─XxxApplication.java
    │  │
    │  └─resources
    └─test
-pom.xml
-README.md
```