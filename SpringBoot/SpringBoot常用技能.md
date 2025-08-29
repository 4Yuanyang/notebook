# SpringBoot常用技能

## @ConfigurationProperties

### @Value

> ![QQ_1756259218321](./imgs/QQ_1756259218321.png)
>
> ![QQ_1756259273077](./imgs/QQ_1756259273077.png)
>
> ![QQ_1756261613389](./imgs/QQ_1756261613389.png)



### @ConfigurationProperties(...)

> ![image-20250827103313820](./imgs/image-20250827103313820.png)

## Junit测试

![QQ_1756262116577](./imgs/QQ_1756262116577.png)

> ==目标：== 使用Junit进行单元测试，并测试User是否属性注入成功
>
> ![image-20250827105336910](./imgs/image-20250827105336910.png)
>
> 1. 获取该bean -> 依赖于ApplicationContext -> 写一个工具类实现ApplicationContextAware接口，实现setApplicationContext方法 -> 该工具类加上@Component，由IOC容器管理（这样IOC容器会自动执行setApplicationContext方法）![image-20250827113219812](./imgs/image-20250827113219812.png)
>
>    ![image-20250827113336819](./imgs/image-20250827113336819.png)
>
> 2. 在测试方法中测试
>
> ![image-20250827113451647](./imgs/image-20250827113451647.png)

## 多配置环境

![image-20250827114750555](./imgs/image-20250827114750555.png)

### properties

![image-20250827114948563](./imgs/image-20250827114948563.png)

最后在application.properties中通过`spring.profiles.active=xxx`来确定具体的配置

![image-20250827115004341](./imgs/image-20250827115004341.png)

### yml

~~~yml
#spring
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/newsmanagerdb?serverTimezone=GMT%2B8&characterEncoding=UTF-8
    username: xyy
    password: 123123
  jackson:
    time-zone: GMT+8
    date-format: yyyy-MM-dd HH:mm:ss

#mybatis
mybatis:
  type-aliases-package: com.xyy.entity
  mapper-locations: classpath:com/xyy/dao/*.xml


~~~

## 自动配置

![QQ_1756429874836](./imgs/QQ_1756429874836.png)

> 1. **`@Configuration(proxyBeanMethods = false)`**:
>
> - 表明这是一个配置类，Spring 容器会处理它来定义 Bean。
> - `proxyBeanMethods = false`是一个性能优化，表示配置类中的 `@Bean`方法不会被 CGLIB 代理。适用于配置类内部不相互调用 `@Bean`方法的情况（这里确实没有相互调用）。
>
> 2. **`@EnableConfigurationProperties({ServerProperties.class})`**:
>
> - 启用对 `ServerProperties`类的配置属性绑定。这意味着 `ServerProperties`的实例将被创建，并且其属性值将从 `application.properties`/`application.yml`文件（或其他配置源）中以 `server.*`为前缀的属性注入进来。
>
> 3. **`@ConditionalOnClass({CharacterEncodingFilter.class})`**:
>
> 条件注解。只有当项目的 classpath 中存在 `CharacterEncodingFilter`类（属于 `spring-web`模块）时，这个自动配置才会生效。这确保了所需的类可用。
>
> 
>
> 4. **`@ConditionalOnProperty(prefix = "server.servlet.encoding", value = {"enabled"}, matchIfMissing = true)`**:
>
> - 条件注解。它检查配置属性 `server.servlet.encoding.enabled`。
> - 如果该属性存在且值为 `true`，则条件满足。
> - 如果该属性不存在（`matchIfMissing = true`），则条件**也满足**（即默认启用）。
> - 只有当该属性明确设置为 `false`时，条件才不满足，整个自动配置会失效。

![image-20250829100446099](./imgs/image-20250829100446099.png)

![QQ_1756433087770](./imgs/QQ_1756433087770.png)

![image-20250829100323578](./imgs/image-20250829100323578.png)

## 关闭自动配置

![image-20250829104619606](./imgs/image-20250829104619606.png)

通过exclude，得保证该类能被springboot正确识别为一个自动配置类，所以仿照之前自动配置类创建一个spring.factories文件，将类信息写入。此时就能被正确识别为一个自动配置类。

![image-20250829105543937](./imgs/image-20250829105543937.png)

排除后，就无法自动配置，所以sayHello就无法注入

![image-20250829105405561](./imgs/image-20250829105405561.png)

## 接管Spring自动配置

![image-20250829105619018](./imgs/image-20250829105619018.png)

## xml配置

![image-20250829111225238](./imgs/image-20250829111225238.png)

## 小结



