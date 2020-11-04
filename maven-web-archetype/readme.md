## 制作maven自定义骨架

### 1.编写一个模板工程

​	编写一个自己心仪的项目模板出来.比如包含 service dao pojo 等等基本包结构的项目

​	例如:

​		![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/1.png)

### 2.添加archetype插件

```xml
  
<!--添加 maven archetype 插件 -->
<build>
    <finalName>maven-web-archetype</finalName>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-archetype-plugin</artifactId>
        <version>3.1.2</version>
      </plugin>
    </plugins>
  </build>
```

### 3.使用archetype插件生成骨架项目

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/2.png)

### 4.修改骨架项目

​	运行之后在模板项目的target目录下出现一个生成的原型项目

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/3.png)

删除一些无用的文件

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/4.png)

添加需要目录结构 可以自己复制 修改完毕之后

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/5.png)



修改pom文件

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/6.png)

在该文件中添加资源打包插件

```xml
<build>
  	<!-- 此处添加的资源插件 start -->
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-resources-plugin</artifactId>
        <version>2.7</version>
        <configuration>
          <includeEmptyDirs>true</includeEmptyDirs>
        </configuration>
      </plugin>
    </plugins>
  	<!-- 此处添加的资源插件 end -->
    <extensions>
      <extension>
        <groupId>org.apache.maven.archetype</groupId>
        <artifactId>archetype-packaging</artifactId>
        <version>3.1.2</version>
      </extension>
    </extensions>

    <pluginManagement>
      <plugins>
        <plugin>
          <artifactId>maven-archetype-plugin</artifactId>
          <version>3.1.2</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
```

修改骨架的元信息文件 

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/7.png)

修改如下:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<archetype-descriptor xsi:schemaLocation="https://maven.apache.org/plugins/maven-archetype-plugin/archetype-descriptor/1.1.0 http://maven.apache.org/xsd/archetype-descriptor-1.1.0.xsd" name="maven-web-archetype"
    xmlns="https://maven.apache.org/plugins/maven-archetype-plugin/archetype-descriptor/1.1.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <fileSets>
    <fileSet filtered="true" packaged="true" encoding="UTF-8">
      <directory>src/main/java</directory>
      <includes>
        <include>**/**</include>
      </includes>
    </fileSet>
    <fileSet filtered="true" packaged="true" encoding="UTF-8">
      <directory>src/main/resources</directory>
      <includes>
        <include>**/**</include>
      </includes>
    </fileSet>
    <fileSet filtered="true" encoding="UTF-8">
      <directory>src/main/webapp</directory>
      <includes>
        <include>**/*.jsp</include>
        <include>**/*.xml</include>
      </includes>
    </fileSet>
  </fileSets>
</archetype-descriptor>

```

### 5.安装骨架项目

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/8.png)

命令行敲入如下命令:

```sh
mvn install
```

安装完成之后 在maven的本地仓库目录下可以找到 安装好的骨架项目

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/9.png)

描述文件的内容 该文件中记录了 该骨架项目的信息

```xml
<?xml version="1.0" encoding="UTF-8"?>
<metadata>
  <groupId>com.jk1123</groupId>
  <artifactId>maven-web-archetype</artifactId>
  <versioning>
    <versions>
      <version>1.0-SNAPSHOT</version>
    </versions>
    <lastUpdated>20201104141310</lastUpdated>
  </versioning>
</metadata>
```



### 6.使用骨架

打开idea 开始添加自己的骨架

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/10.png)

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/11.png)

![](https://github.com/huyoufu/maven-corner/tree/master/maven-web-archetype/img/12.png)

接下来的使用骨架的方法 就跟使用自带的骨架一样的方式了