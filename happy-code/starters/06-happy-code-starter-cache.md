### 缓存组件
#### 使用约定

已经引入了 happy-code-parent 父级依赖

#### 引入方式

- Maven

```
<dependency>
   <groupId>cool.happycoding</groupId>
   <artifactId>happy-code-starter-cache</artifactId>
</dependency>
```    

- Gradle

```
compile 'cool.happycoding:happy-code-starter-cache'
```

#### 说明
- 引入JetCache (jetcache-starter-redis-springdata) 组件
- 简化注解使用和配置
- 二级缓存使用redis并采用lettuce客户端连接(该方式为Spring boot 2.x连接redis的默认方式)
- JetCache 理论上是支持两级缓存的，即本地缓存(Caffeine)+加远端缓存(Redis)
- 扩展了并解决了在分布式环境下会存在本地和远端缓存的数据一致性问题（原生组件不支持）

#### 配置项
连接配置，采用spring-data-redis原生配置即可：

```
    ## 单机模式
    spring.redis.url
   
    ## 主从模式
    ## Redis服务器的名称
    spring.redis.sentinel.master
    ## 主机：端口对的逗号分隔列表
    spring.redis.sentinel.nodes
    
    ## 集群模式
    spring.redis.cluster.nodes
    # spring.redis.cluster.nodes=127.0.0.1:7000,127.0.0.1:7001,127.0.0.1:7002
    # 在群集中执行命令时要遵循的最大重定向数目,默认按照集群服务数量设置即可
    spring.redis.cluster.max-redirects
   
    ## 当有密码时配置
    spring.redis.password
```
   
连接池配置

```
    # 参考
    spring.redis.lettuce.pool.max-active
    spring.redis.lettuce.pool.min-idle
```
    

     
其他配置项
```
    ## 统计间隔 默认 30 min 等同于 jetcache.statIntervalMinutes
    happy.code.cache.stat-interval-minutes
    ## 等同于 jetcache.hiddenPackages
    happy.code.cache.hidden-packages
    ## 以毫秒为单位，指定多长时间没有访问，就让缓存失效，默认30min，当前只有本地缓存支持，等同于：jetcache.local.defalut.expireAfterAccessInMillis
    happy.code.cache.local-default-expire-after-access-in-millis

```

注：以上配置针对：default区设置，如需要更多的缓存区设置，请参照Jetcache的原生配置   
    
#### 使用
##### 入门
- 在启动类上添加 @EnableHappyCache启用cache能力
- 通过@CreateCache注解创建一个缓存实例，默认超时时间是100秒
```
@CreateCache(name="test" expire = 100)
private Cache<Long, TestDto> testCache;
```
用起来就像map一样
```
TestDto test = testCache.get(123L);
testCache.put(123L, user);
testCache.remove(123L);
```
- 创建一个两级（内存+远程）的缓存，内存中的元素个数限制在50个
```
@CreateCache(name = "TestService.testCache", expire = 100, cacheType = CacheType.BOTH, localLimit = 50)
private Cache<Long, TestDto> testCache;
```

##### 方法缓存
在Spring环境下，使用@Cached注解可以为一个方法添加缓存，@CacheUpdate用于更新缓存，@CacheInvalidate用于移除缓存元素,加注解的类必须是一个spring bean，例如：

```
public interface TestService {
    @Cached(name="testCache.", key="#testId", expire = 3600)
    User getById(long testId);

    @CacheUpdate(name="testCache.", key="#test.testId", value="#test")
    void update(TestDto test);

    @CacheInvalidate(name="testCache.", key="#testId")
    void delete(long testId);
}
```
注意事项：
- Cache里存放的对象类型必须实现 Serializable 接口
- 使用@CreateCache 注解时应当配置name属性（该属性为影响缓存的key值，如不指定则组件会自动生成，会影响缓存在多个类中共享），以便缓存能够在多个类中访问
- @CacheUpdate和@CacheInvalidate的name和area属性必须和@Cached相同，name属性还会用做cache的key前缀
- 使用@CacheUpdate和@CacheInvalidate的时候，可能会失败（比如网络IO错误）导致缓存未能更新或失效，所以指定缓存的超时时间是非常重要的
- 注解可以加在接口上也可以加在实现类上(建议统一添加到实现类上),当注解添加在接口时，必须遵循接口依赖注入的方式使用（因为实现类的注入将可能导致接口上的cache定义失效,为避免出错，建议统一加到实现类上）
  
#### 参考资料
- [JetCache](https://github.com/alibaba/jetcache/wiki/Home_CN) 
- [lettuce](https://lettuce.io/docs/getting-started.html)  
- [代码示例](https://github.com/happy-coding-cool/happy-code-samples/tree/main/happy-code-starter-cache-sample)
 
    

