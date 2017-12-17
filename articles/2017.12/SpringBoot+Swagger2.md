# Spring Boot + Swagger2

由于Spring Boot能够简化配置、快速开发等特性，已经逐渐取代SpringMVC成为下一代框架。其中，Controller大多采用RESTful API的方式来处理请求，从而达到前后端分离的目的。然而，当项目较大，存在大量的RESTful API时，就需要花费大量的时间和精力来沟通每个接口的功能，请求方法和参数类型。Swagger2可以很好地解决这一问题，通过与Spring Boot整合，就可以很方便的管理并测试RESTful API。这是Swagger2的[官方网站](https://swagger.io/)，大家有兴趣可以看一下。当然，Swagger2与SpringMVC也可以集成，在这里我是以Spring Boot为例说明。

根据我的使用经验，swagger的好处有(可能我现在用的还比较浅，欢迎大家补充~)：

- 前后端分离开发时，减少了RESTful API沟通的时间
- 可以得到RESTful API清晰的可视化界面
- 方便对Controller的测试。当请求方式为GET时，可以直接在浏览器上访问，请求方式为POST时，可以使用postman工具，但当参数比较多时，swagger2的优势就非常明显
- Spring Boot与Swagger2的集成非常简单

下面开始具体的配置

### 1：添加依赖

在pom.xml中添加：

```xml
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger2</artifactId>
   <version>2.2.2</version>
</dependency>
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger-ui</artifactId>
   <version>2.2.2</version>
</dependency>
```

### 2：新建Swagger2配置类

在application.java主程序的同级目录下新建Swagger2配置类，内容为：

```java
@Configuration
@EnableSwagger2
public class Swagger2Configuration {
    @Bean
    public Docket createRestApi() {

        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
          // handler的包名
                .apis(RequestHandlerSelectors.basePackage("com.spring.controller"))
                .paths(PathSelectors.any())
                .build();
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("Spring Boot中使用Swagger2构建RESTful APIs")
                .description("第一个Spring Boot项目")
                .contact("cherry")
                .version("1.0")
                .build();
    }
}
```

### 3：在主程序中引入注解@EnableSwagger2来启动swagger注解

```java
@SpringBootApplication
@EnableSwagger2
public class CherryApplication {

   public static void main(String[] args) {
      SpringApplication.run(CherryApplication.class, args);
   }
}
```

### 4：在Controller中添加文档内容

在类上添加：

```java
@Api(value = "测试swagger2是否成功")
```

在方法上添加：

```java
@ApiOperation(value="say hello", notes="测试hello方法")
```