## Redis安装

`1.Redis的安装及简单使用：`[Redis实战：Redis的安装及简单使用-腾讯云开发者社区-腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/2343208)

`2.Redis的apt安装和删除：`[redis学习--安装_apt安装redis-CSDN博客](https://blog.csdn.net/Vibugs/article/details/127364353)

`apt默认安装位置`: ![image-20250925084055443](./imgs/image-20250925084055443.png)

## Redis配置

![image-20250925084410305](./imgs/image-20250925084410305.png)

![image-20250925084328570](./imgs/image-20250925084328570.png)

## Redis命令行客户端

![image-20250925091612202](./imgs/image-20250925091612202.png)

## Redis图形化桌面客户端

![image-20250925091934089](./imgs/image-20250925091934089.png)

`图形化桌面客户端`：[Releases · lework/RedisDesktopManager-Windows (github.com)](https://github.com/lework/RedisDesktopManager-Windows/releases)

## Redis命令

### redis数据结构

![image-20250925101805670](./imgs/image-20250925101805670.png)

### 官方命令文档

[Commands | Docs (redis.io)](https://redis.io/docs/latest/commands/)

> #### 查看某个命令的使用方式：
>
> ![image-20250925102859786](./imgs/image-20250925102859786.png)

### 通用命令

![QQ_1758768372339](./imgs/QQ_1758768372339.png)

### String类型

![image-20250925105327023](./imgs/image-20250925105327023.png)

![image-20250925105355489](./imgs/image-20250925105355489.png)    

> ![image-20251007113753508](./imgs/image-20251007113753508.png)
>
> ![image-20250925105907753](./imgs/image-20250925105907753.png)
>
> ![image-20251007114050367](./imgs/image-20251007114050367.png)

### redis中的key的层级结构

![image-20251007114313765](./imgs/image-20251007114313765.png)

![image-20251007114411310](./imgs/image-20251007114411310.png)

### Hash类型

![image-20251007135130878](./imgs/image-20251007135130878.png)

![image-20251007135146787](./imgs/image-20251007135146787.png)

> ![image-20251007135741181](./imgs/image-20251007135741181.png)

### List类型

![image-20251007140049723](./imgs/image-20251007140049723.png)![image-20251007140102780](./imgs/image-20251007140102780.png)

> ![image-20251007141113932](./imgs/image-20251007141113932.png)

### Set类型

![image-20251007141735455](./imgs/image-20251007141735455.png)

![image-20251007142029252](./imgs/image-20251007142029252.png)

> ![image-20251007142049527](./imgs/image-20251007142049527.png)
>
> ![image-20251007142214145](./imgs/image-20251007142214145.png)

### SortedSet类型

![image-20251007142252963](./imgs/image-20251007142252963.png)

![image-20251007142513035](./imgs/image-20251007142513035.png)

> ![image-20251007142711070](./imgs/image-20251007142711070.png)
>
> ![QQ_1759818672839](./imgs/QQ_1759818672839.png)
>
> ![image-20251007143110879](./imgs/image-20251007143110879.png)
>
> ![image-20251007143603539](./imgs/image-20251007143603539.png)

## Redis的java客户端

![image-20251007144353648](./imgs/image-20251007144353648.png)

![image-20251007144531919](./imgs/image-20251007144531919.png)

### Jedis

#### 基本用法

![image-20251007144604056](./imgs/image-20251007144604056.png)

![image-20251007144726251](./imgs/image-20251007144726251.png)

#### 连接池

![image-20251007144812194](./imgs/image-20251007144812194.png)

![image-20251007145136718](./imgs/image-20251007145136718.png)

### SpringDataRedis

`官网地址`：[Spring Data Redis](https://spring.io/projects/spring-data-redis)

![image-20251007145246139](./imgs/image-20251007145246139.png)

![image-20251007145949925](./imgs/image-20251007145949925.png)

![image-20251007152945931](./imgs/image-20251007152945931.png)

1. springboot默认集成lettuce，如果想使用Jedis，需要自己引入相关依赖

2. 手动写了pool的相关配置，连接池才会生效。

![image-20251007153009191](./imgs/image-20251007153009191.png)

![image-20251007155630129](./imgs/image-20251007155630129.png)

#### RedisTemplate

1. 麻烦，需要自己处理序列化器

#### StringRedisTemplate

![image-20251007155153321](./imgs/image-20251007155153321.png)

1. ==操作普通字符串==

![image-20251007155607079](./imgs/image-20251007155607079.png)

2. ==操作Hash==

![image-20251007160019828](./imgs/image-20251007160019828.png)

![image-20251007160147710](./imgs/image-20251007160147710.png)