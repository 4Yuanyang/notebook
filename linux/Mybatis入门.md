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

![image-20250713185253877](./imgs/image-20250713185253877.png)

单例模式：这里通过创建一个工具类来将SqlSessionFactory实现为单例模式。后续在学习spring时，可以通过依赖注入中的

![image-20250713190118287](./imgs/image-20250713190118287.png)

### SqlSession

![image-20250713212430563](./imgs/image-20250713212430563.png)

![image-20250713212117138](./imgs/image-20250713212117138.png)

