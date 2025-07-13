### MyBatis Mapper 接口参数形式详解

MyBatis 的 Mapper 接口是 MyBatis 动态代理实现的核心，其参数传递方式直接影响 SQL 的编写和参数绑定。以下是常见的参数形式及使用场景：

------

#### 一、**单参数传递**

**场景**：方法仅接收一个参数。
​**​规则​**​：直接通过 `#{任意名称}` 引用参数值，名称无需与参数名一致。
​**​示例​**​：

```java
// Mapper 接口
User selectById(Integer id);
```

```xml
<!-- XML -->
<select id="selectById" resultType="User">
  SELECT * FROM user WHERE id = #{idAlias}  <!-- 名称可自由定义 -->
</select>
```

------

#### 二、**多参数无注解（默认绑定）**

**场景**：多个参数未使用 `@Param` 注解。
​**​规则​**​：MyBatis 默认通过以下两种方式绑定参数：

1. **索引别名**：`arg0`, `arg1`, ... （Java 反射默认参数名）
2. **位置别名**：`param1`, `param2`, ...
   ​**​示例​**​：

```java
// Mapper 接口
User selectByUsernameAndPassword(String username, String password);
```



```xml
<!-- XML -->
<select id="selectByUsernameAndPassword" resultType="User">
  SELECT * FROM user 
  WHERE username = #{arg0} AND password = #{param2}
  <!-- 等价于 #{arg0} = username, #{param2} = password -->
</select>
```

**问题**：可读性差，易出错，不推荐生产使用。

------

#### 三、**使用 `@Param` 注解**

**场景**：显式指定参数名，提高代码可读性。
​**​规则​**​：通过 `@Param("key")` 定义参数别名，SQL 中使用 `#{key}` 引用。
​**​示例​**​：



```java
// Mapper 接口
User selectByCredentials(
  @Param("name") String username, 
  @Param("pwd") String password
);
```



```xml
<!-- XML -->
<select id="selectByCredentials" resultType="User">
  SELECT * FROM user 
  WHERE username = #{name} AND password = #{pwd}
</select>
```

**优点**：代码自解释性强，参数名与 SQL 解耦。

------

#### 四、**对象参数（POJO 或 JavaBean）**

**场景**：传递一个对象，通过属性名访问字段。
​**​规则​**​：直接使用 `#{属性名}` 访问对象的 getter 方法。
​**​示例​**​：



```java
// Mapper 接口
void insertUser(User user);  // User 类有 getUsername() 和 getPassword()
```



```xml
<!-- XML -->
<insert id="insertUser">
  INSERT INTO user (username, password) 
  VALUES (#{username}, #{password})
</insert>
```

**注意**：属性名必须与对象的 getter 方法名匹配（驼峰转下划线自动兼容）。

------

#### 五、**Map 参数**

**场景**：动态传递键值对参数。
​**​规则​**​：通过 `#{mapKey}` 直接访问 Map 中的值。
​**​示例​**​：



```java
// Mapper 接口
void updateUser(Map<String, Object> params);
```



```xml
<!-- XML -->
<update id="updateUser">
  UPDATE user 
  SET username = #{newName}, password = #{newPwd}
  WHERE id = #{id}
</update>
```

**调用方式**：



```java
Map<String, Object> params = new HashMap<>();
params.put("newName", "Alice");
params.put("newPwd", "123");
params.put("id", 1);
userMapper.updateUser(params);
```

**适用场景**：动态条件查询，但牺牲类型安全。

------

#### 六、**集合/数组参数**

**场景**：传递 `List`、`Set` 或数组进行批量操作。
​**​规则​**​：通过 `foreach` 动态生成 SQL，使用默认名称 `list` 或 `array`。
​**​示例​**​：



```java
// Mapper 接口
List<User> selectByIds(List<Integer> ids);
```



```xml
<!-- XML -->
<select id="selectByIds" resultType="User">
  SELECT * FROM user 
  WHERE id IN 
  <foreach collection="list" item="id" open="(" separator="," close=")">
    #{id}
  </foreach>
</select>
```

**名称规则**：

- `List` → `list`
- `数组` → `array`
- 或通过 `@Param` 指定名称。

------

#### 七、**混合参数类型**

**场景**：同时传递对象和基本类型参数。
​**​规则​**​：结合 `@Param` 和对象属性访问。
​**​示例​**​：



```java
// Mapper 接口
void updateUserProfile(
  @Param("user") User user,
  @Param("status") Integer status
);
```



```xml
<!-- XML -->
<update id="updateUserProfile">
  UPDATE user 
  SET username = #{user.username}, status = #{status}
  WHERE id = #{user.id}
</update>
```

------

### 常见问题与解决方案

1. **参数绑定异常**

   - **现象**：`Parameter 'xxx' not found. Available parameters are [...]`
   - **原因**：未正确使用 `@Param` 或参数名不匹配。
   - **解决**：检查方法签名和 SQL 中的 `#{}` 名称是否一致。

2. **启用 `-parameters` 编译参数**

   - **作用**：让 MyBatis 自动获取方法参数名（无需 `@Param`）。

   - **配置（Maven）：**

     ```xml
     <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-compiler-plugin</artifactId>
       <configuration>
         <compilerArgs>
           <arg>-parameters</arg>
         </compilerArgs>
       </configuration>
     </plugin>
     ```

   - **限制**：仅支持 Java 8+，且需编译器支持。

------

### 最佳实践总结

1. **多参数场景**：优先使用 `@Param` 注解，提升可读性。
2. **复杂参数**：封装为 POJO 或 Map，避免参数爆炸。
3. **动态查询**：结合 `foreach` 和 Map 实现灵活条件拼接。
4. **参数检查**：始终在 XML 中测试参数名称是否匹配。

通过合理选择参数形式，可以让 MyBatis Mapper 接口更清晰、更易维护。