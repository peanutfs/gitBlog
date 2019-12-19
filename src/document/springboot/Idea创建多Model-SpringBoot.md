### 1.简介
本文主要介绍使用Idea创建一个多Model工程的SpringBoot项目
### 2.创建步骤
#### 2.1 新建Maven工程
> 打开Idea
> > 1. 操作路径：File-> new -> project
> > ![新建Maven工程_1](../../resources/images/springboot/createMavenProject_1.png)
> > 2. 选择maven，点击next
> > ![选择maven](../../resources/images/springboot/createMavenProject_2.png)
> > 3. 填写工程信息，点击next
> > ![填写工程信息](../../resources/images/springboot/createMavenProject_3.png)
> > 4. 确认工程名后点击finish将看到已建好的工程
> > ![点击Finish](../../resources/images/springboot/createMavenProject_4.png)

#### 2.2 创建Model
> 删除maven工程的src文件夹，并在pom.xml增加
> ````xml 
> <packaging>pom</packaging>
> ````
> ![删除src文件夹](../../resources/images/springboot/createMavenProject_5.png)
>> 1. 在根项目上点击右键，选择new-> Model
>> ![新增Model](../../resources/images/springboot/createModel_1.png)
>> 2. 选择Spring Initializr，点击next
>> ![选择Spring Initializr](../../resources/images/springboot/createModel_2.png)
>> 3. 填写model信息，点击next
>> ![填写model信息](../../resources/images/springboot/createModel_3.png)
>> 4. 选择依赖项，点击next
>> ![选择依赖项](../../resources/images/springboot/createModel_4.png)
>> 5. 确认Model信息后点击finish
>> ![确认Model信息](../../resources/images/springboot/createModel_5.png)
>> 完成之后的目录结构如下
>> ![完成目录结构](../../resources/images/springboot/createModel_6.png)

> 按照上述五个步骤继续创建下一个Model，全部创建完成之后目录结构类似如下
>
> > ![完整的目录结构](../../resources/images/springboot/createModel_7.png)

#### 2.3 添加Model依赖
1. 父工程的pom配置
首先声明该父工程包含的子模块已经Springboot相关配置，下面展示一些通用配置，具体含义可以对照注释
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <!--基本信息-->
    <description>权限管理系统</description>
    <modelVersion>4.0.0</modelVersion>
    <packaging>pom</packaging>

    <!--工程说明-->
    <groupId>com.crossrainbow</groupId>
    <artifactId>purview-manage</artifactId>
    <version>1.0-SNAPSHOT</version>

    <!--继承说明：SpringBoot父工程-->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.0.5.RELEASE</version>
        <relativePath/>
    </parent>

    <!-- 模块说明：声明多个子模块 -->
    <modules>
        <module>pm-common</module>
        <module>pm-server</module>
        <module>pm-web</module>
    </modules>

    <!--版本说明：统一管理依赖的版本号-->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.crossrainbow</groupId>
                <artifactId>pm-web</artifactId>
                <version>0.0.1-SNAPSHOT</version>
            </dependency>
            <dependency>
                <groupId>com.crossrainbow</groupId>
                <artifactId>pm-server</artifactId>
                <version>0.0.1-SNAPSHOT</version>
            </dependency>
            <dependency>
                <groupId>com.crossrainbow</groupId>
                <artifactId>pm-common</artifactId>
                <version>0.0.1-SNAPSHOT</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
    
</project>
```
![主pom版本管理](../../resources/images/springboot/mavenDependency_1.png)

2. 子Model依赖配置 
以示例工程为例，我们将 
> * pm-web作为Web层
> * pm-server作为服务层
> * pm-common作为公共层  

三者的依赖关系为：
> * pm-web依赖pm-server
> * pm-web依赖pm-common
> * pm-server依赖pm-common

首先我们在三个model的pom文件中增加父工程配置
```xml
 <parent>
     <groupId>com.crossrainbow</groupId>
     <artifactId>purview-manage</artifactId>
     <version>1.0.0-RELEASE</version>
     <relativePath>../pom.xml</relativePath>
</parent>
```
![配置父工程依赖](../../resources/images/springboot/mavenDependency_2.png)

然后在web和server的pom文件新增依赖配置
>* pm-web下的pom文件增加
>>```xml
>><dependency>
>>	<groupId>com.crossrainbow</groupId>
>>	<artifactId>pm-server</artifactId>
>></dependency>
>><dependency>
>>	<groupId>com.crossrainbow</groupId>
>>	<artifactId>pm-common</artifactId>
>></dependency>
>>````
>>![pm-web依赖](../../resources/images/springboot/mavenDependency_3.png)
>* pm-server下的pom文件增加
>>````xml
>><dependency>
>>	<groupId>com.crossrainbow</groupId>
>>	<artifactId>pm-common</artifactId>
>></dependency>
>>```
>>![pm-server依赖](../../resources/images/springboot/mavenDependency_4.png)


