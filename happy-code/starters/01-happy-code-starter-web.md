## Web组件
#### 使用约定

已经引入了 happy-code-parent 父级依赖

#### 引入方式

- Maven

```
<dependency>
   <groupId>cool.happycoding</groupId>
   <artifactId>happy-code-starter-web</artifactId>
</dependency>
```    

- Gradle

```
compile 'cool.happycoding:happy-code-starter-web'
```

#### 说明
- 定义了序列化/反序列化规范，默认为:fastjson,可通过配置切换为jackson2
    - 针对日期类型做了字符串的序列化/反序列的定义
    - 针对Long/BigDecimal类型数据在进行序列化时做了转字符串的处理
    
- 定义了rest接口的交互格式规范   
    - BaseResult<T> 适用于返回单个对象的场景
    - ListResult<T> 适用于返回列表对象的场景
    - PageResult<T> 适用于返回分页对象的场景  
    
- 定义统一的异常封装处理，并做了如下约定
    - 每一个异常都必须要定义明确的错误编码，异常信息的封装请实现 ResultCode 接口
    - 业务异常直接使用BizException即可，如需自定义，请继承该异常
    - 建议使用抛异常的方式来代替业务状态的维护(即：在进行业务逻辑校验时，不合法的逻辑，直接按异常处理)
    - 如无必要一般不要在业务里捕获异常
    - 抛出异常时，不需要再打印日志(统一的异常处理逻辑会统一打印日志信息)
    
- 定义了一个默认的异步线程池：happyThreadPoolExecutor

#### 配置项

```
    ## 启用统一的日期序列化，默认：启用
    happy.code.web.serializer.enable-date
    ## 日期序列化格式，默认：yyyy-MM-dd HH:mm:ss
    happy.code.web.serializer.date-format
    ## 启用序列化时将BigDecimal类型转字符串，默认：启用 
    happy.code.web.serializer.enable-big-decimal-as-plain
    ## 启用序列化时将Long类型转字符串，默认：启用 
    happy.code.web.serializer.enable-long-as-plain
    ## 启用日期反序列化统一处理，支持几乎所有常见的日期格式，默认：启用
    happy.code.web.deserializer.enable-date
    ## 序列化/反序列化工具 默认为：fastjson
    happy.code.web.converter-type
    ## 线程池配置
    happy.code.web.pool.core-pool-size
    happy.code.web.pool.maxPoolSize
    happy.code.web.pool.allow-core-thread-time-out
    happy.code.web.pool.keep-alive-time
    happy.code.web.pool.queue-capacity
```

#### 扩展
- 采用fastjson作为序列化/反序列化工具时,可以通过 FastJsonConfigCustomizer 扩展指定数据类型的序列化/反序列化实现
- 采用jackson2作为序列化/反序列化工具时,可以通过 Jackson2ConfigCustomizer 扩展指定数据类型的序列化/反序列化实现


### 参考链接
- [代码示例](https://github.com/happy-coding-cool/happy-code-samples/tree/main/happy-code-starter-web-sample)
