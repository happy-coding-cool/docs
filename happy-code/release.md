## 版本更新

### 1.0.3.RELEASE
- feat: 升级SC和SCA版本
- feat: 重构log组件补充feign调用场景下traceId的传递以及审计功能
- feat: 重构log组件将审计记录功能通过事件进行异步处理以提高效率
- feat: 增加分布式锁组件
- feat: 增加多数据源组件
- feat: 引入Sentinel逐渐并对BlockException进行了统一配置处理
- refactor: 重构新增UserDetailService接口定义，并逐渐废弃UserContextService接口的使用
- fix: 修校验组件性别校验的bug
- fix: 修复user组件requestWrapper类出现的集合操作异常
- fix：修复从error控制器中复抛异常时request path获取不准确的问题

#### 依赖版本升级
- Spring Cloud 2020.0.2
- Spring Cloud Alibaba 2020.0.RC1
- Spring boot 2.4.3

### 1.0.2.RELEASE
- feat: 在banner打印中添加happy-code的版本号
- fix: 修复打印Exception 出现errMessage丢失的问题
- fix: 修复出现404时的处理逻辑(404报500的问题)

### 1.0.1.RELEASE
- feat: 引入jetcache完善cache组件
- feat: 完善mybatis组件引入乐观锁定义支持
- feat: 完善log组件
- feat: 引入 transmittable-thread-local
- feat: 定义默认线程池(happyThreadPoolExecutor)，解决线程切换时上下文传递问题
- feat: web组件提供自定fastjson 序列化/反序列化配置扩展FastJsonConfigCustomizer
- refactor: 更改组件依赖的继承体系，该改动会造成依赖不兼容的问题，按照新的配置方式进行调整即可
- refactor: 参照cola架构对异常和返回值封装进行优化
- fix: 修复cache组件@EnableHappyCache组合注解无法创建缓存代理导致方法上的@Cached注解失效的问题

### 1.0.0.RELEASE 
- feat: 初始版本
- feat: 规范依赖体系和版本
- feat: 封装web组件规定序列化/反序列化方式，封装前后端交互规范、全局异常处理规范
- feat: 封装validator组件，用于请求的入参校验
- feat: 封装swagger组件，用于接口文档的管理
- feat: 封装user组件，提供一个用于封装用户信息的UserContext
- feat: 封装mybatis组件，引入mybatis-plus，实现Entity对象规范定义
- feat: 封装log组件，规范log配置

## 框架选型
- spring Cloud Hoxton.SR8
- spring Cloud Alibaba 2.2.3.RELEASE

## 主要依赖
- lombok 1.18.12
- hutool 5.3.9
- fastjson 1.2.73
- guava 28.0-jre
- knife4j 3.0.2
- jetcache 2.6.0
- fastjson 1.2.75
- transmittable-thread-local 2.9.0