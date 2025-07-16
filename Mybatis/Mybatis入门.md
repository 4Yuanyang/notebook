# MyBatis

## 持久化与ORM

<span style="font-size:1.2rem;color:red;">持久化是程序数据在瞬时状态和持久状态间转化的过程（内存 -> 数据库）</span>

![image-20250713164051191](./imgs/image-20250713164051191.png)

![image-20250713164407447](./imgs/image-20250713164407447.png)

## Mybatis简介

![image-20250713173628751](./imgs/image-20250713173628751.png)

### Mybatis开发步骤

![image-20250713174532224](./imgs/image-20250713174532224.png)



## Mybatis核心对象

### SqlSessionFactoryBuilder

![image-20250713184915469](./imgs/image-20250713184915469.png)

### SqlSessionFactory

![image-20250714235103622](./imgs/image-20250714235103622.png)

单例模式：这里通过创建一个工具类来将SqlSessionFactory实现为单例模式。后续在学习spring时，可以通过依赖注入中的

![image-20250713190118287](./imgs/image-20250713190118287.png)

### SqlSession

![image-20250713212430563](./imgs/image-20250713212430563.png)

![image-20250713212117138](./imgs/image-20250713212117138.png)

## Mybatis核心配置文件

![image-20250713225127563](./imgs/image-20250713225127563.png)

### 配置properties文件

#### 方式一

![image-20250713225544962](./imgs/image-20250713225544962.png)

#### 方式二

![image-20250713225610444](./imgs/image-20250713225610444.png)

### settings配置

![QQ_1752418779389](./imgs/QQ_1752418779389.png)

![image-20250713225851448](./imgs/image-20250713225851448.png)

### typeAliases配置

![image-20250713230718358](./imgs/image-20250713230718358.png)

<span style="font-size:1.2rem;color:red;">如果存在多个类需要取别名：</span>

1. 将\<typeAlias>复制多份，比较费时麻烦。
2. 通过==包扫描==方式来让mybatis帮我们自动取别名，类全限定名的别名就是类名，首字母小写
   \<package name='包名'/>g
3. 对于基础类型不需要取别名

![image-20250713230224867](./imgs/image-20250713230224867.png)

### environments配置

![image-20250713230817446](./imgs/image-20250713230817446.png)

![image-20250713230948210](./imgs/image-20250713230948210.png)

#### transactionManager

![image-20250713231141143](./imgs/image-20250713231141143.png)

#### dataSource

![QQ_1752421816390](./imgs/QQ_1752421816390.png)

### mappers



![image-20250714200641154](./imgs/image-20250714200641154.png)
