### Mybatis组件
#### 使用约定

已经引入了 happy-code-parent 父级依赖

#### 引入方式

- Maven

```
<dependency>
   <groupId>cool.happycoding</groupId>
   <artifactId>happy-code-starter-mybatis</artifactId>
</dependency>
```    

- Gradle

```
compile 'cool.happycoding:happy-code-starter-mybatis'
```

#### 说明
- 组件集成了mybatis-plus并预留了扩展
- 定义了DTO/Entity/Form基类对象
    - BaseDTO
    - BaseEntity
    - BaseForm
- 自动填充字段
```
    ## 记录创建人 默认：system
    createdBy
    ## 记录创建人Id 默认：-1
    createdById
    ## 记录创建时间 默认：now
    createdTime
    ## 记录更新人 默认：system
    updatedBy    
    ## 记录更新人 默认：-1
    updatedById
    ## 记录更新时间 默认：now
    updatedTime   
```
 
 
#### 配置项
```
    ## 查询最大条数限制，-1为不限制，默认：-1 即不限制
    happy.code.mybatis.limit
    ## 溢出总页数后是否进行处理，默认 false即查询超出总页数返回空；若为true则按照第1页处理
    happy.code.mybatis.overflow
    ## 配置主键生成策略，默认：ASSIGN_ID
    happy.code.mybatis.id-type
    ## 乐观锁策略，默认关闭
    happy.code.enable-version
    ## 多租户支持，默认关闭
    happy.code.enable-tenant
    ## 开启多租户支持时，指定租户字段，默认：tenant_id
    happy.code.tenant-id-column
    ## 开启多租户支持时，需要忽略的表，类型数组
    happy.code.ignore-tables
```   
    
#### 参考资料
- [Mybatis-plus 文档](https://baomidou.com/)  
- [代码示例](https://github.com/happy-coding-cool/happy-code-samples/tree/main/happy-code-starter-mybatis-sample)
    