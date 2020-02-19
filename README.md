# Java练习：Spring Boot与Auto configuration

这个项目包含两个Maven工程：

- `my-starter`包含一个Spring Boot Starter定义
- `my-app`包含一个Spring Boot应用

请在`my-starter`中实现一个Spring Starter，使得任何引用它的项目都能自动获得其中的Bean定义等Spring配置

它实现的功能是：对于任何被`@MyResponseBody`注解修饰的`Controller`方法，其返回值都能被自动包裹在一个`{"status":"ok", "data": XXX}`中。

例如，如下代码：

```
@Controller
public class Controller {
  @GetMapping("/users")
  @MyResponseBody
  public List<User> getUsers() {
    return Arrays.asList(new User(1, "ABC"));
  }
}
```

由于该方法被`@MyResponseBody`所修饰，所以返回的JSON会被自动转换为:`{"status":"ok", "data": [{"id":1, "name": "ABC"}]}`

在提交Pull Request之前，你应当在本地确保所有代码已经编译通过，并且通过了测试(`mvn clean verify`)

-----
注意！我们只允许你修改以下文件，对其他文件的修改会被拒绝：
- [my-starter/src/](https://github.com/hcsp/auto-configure-spring-boot/blob/master/my-starter/src/)
- [my-starter/pom.xml](https://github.com/hcsp/auto-configure-spring-boot/blob/master/my-starter/pom.xml)
-----

