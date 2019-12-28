### SSMparent

出现初始化异常  

```
beans.factory.BeanDefinitionStoreException: IOException parsing XML document from class path resource [springmvc.xml]; nested exception is java.io.FileNotFoundException: class path resource [springmvc.xml] cannot be opened because it does not exist
```



原因：由于建web骨架，没有java和resources文件夹，且web.xml文件头也与老师的不一样。将java和resources的文件加上颜色后  无法扫描正确路径。

处理方法1：将resources文件夹变成普通文件夹，将db.porperties,spring-mvc.xml的相关xml加到WEB-INF下

处理方法2：web.xml中classpath*:spring-mvc.xml   加一个*  * 号默认从src下所有的文件夹里读取相关配置文件。

### 热部署

1.加依赖

```xml
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
 </dependency>
```

或者 创建springboot的时候勾选 devtools

2.setting,other setting中设置 Build,Execution,Deployment->Compiler->勾选**Build porject automatically**

3.Ctrl + shift+alt+/ ---->Registy-> 寻找compiler.automake.allow.when.app.running勾选-close

4.这个需要注意的是一旦更改相关依赖需要将IDEA重启后

5.这个真的翻译很慢

<font color=red>我还不会用</font> 单元测试

### 使用测试类 报错

1.不能有参数，不能有返回值，直接注入Dao

2.类型转换问题，整型转换。我在Dao层输入的参数是 String id  但事实上  数据库中是Integer id

```
Parameter value [4] did not match expected type [java.lang.Integer (n/a)]
```



##### bug描述

spring 和shiro整合的时候提示

```
Failed to start component [StandardEngine[Tomcat].StandardHost[localhost]]


org.apache.catalina.LifecycleException: A child container failed during start
```

```xml
<dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.1</version>
            <scope>provided</scope>--------------<<<<
        </dependency>
```

依赖中分别加了<scope>provided</scope>上述错误提示消失，

但：

```
The eventual following stack trace is caused by an error thrown for debugging purposes as well as to attempt to terminate the thread which caused the illegal access, and has no functional impact
```

```

最后的堆栈跟踪是由一个错误引发的，该错误用于调试以及尝试终止导致非法访问的线程，对功能没有影响
```

