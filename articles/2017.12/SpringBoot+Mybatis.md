# SpringBoot+MyBatis

由于SSM框架的广泛使用，大家对MyBatis应该已经非常熟悉了。但现在SpringBoot正在快速发展，并且发展势头很好，尤其是它化繁为简的特性，使其成为了下一代框架。所以，我们今天就来看一下怎么在SpringBoot中使用MyBatis。

### 添加依赖

在pom.xml中添加如下几行：<dependency>

```xml
<dependency>		
	<groupId>org.mybatis.spring.boot</groupId>
	<artifactId>mybatis-spring-boot-starter</artifactId>
  	<version>1.2.1</version>
</dependency>
```
### 编辑实体类

以数据表girl为例，分别有三个字段，id、name、age

Girl.java：

```java
public class Girl {

    private Integer id;
    private String name;
    private Integer age;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }
}
```

### 编辑mapper类

一系列的增删改查操作

```java
@Mapper
public interface GirlMapper {

    @Select("select * from girl")
    List<Girl> selectAll();

    @Insert("insert into girl(name, age) values (#{name}, #{age})")
    void addGirl(@Param("name") String name, @Param("age") Integer age);

    @Select("select * from girl where id = #{id}")
    Girl selectById(@Param("id") Integer id);

    @Update("update girl set age = #{age} where id = #{id}")
    void updateGirlById(@Param("id") Integer id, @Param("age") Integer age);

    @Delete("delete from girl where id = #{id}")
    void deleteGirlById(@Param("id") Integer id);
}
```

### 在主配置文件中添加注释

```java
@SpringBootApplication
@MapperScan("com.spring.mapper")
public class CherryApplication {

   public static void main(String[] args) {
      SpringApplication.run(CherryApplication.class, args);
   }
}
```

### 在Controller中调用

到这里，就配置成功了，真的很简单，没有mybatis-config.xml的配置，没有spring与mybatis整合的配置，没有mapper.xml，最重要的就是mapper接口，把方法和sql语句直接对应起来了！