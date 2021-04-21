## maven本地仓库设置

```
<localRepository>E:/Apache/maven/maven_repository</localRepository>
```



## maven 阿里云仓库

https://maven.aliyun.com/mvn/guide

| 仓库名称 | 阿里云仓库地址                              | 阿里云仓库地址(老版)                                        | 源地址                          |
| -------- | ------------------------------------------- | ----------------------------------------------------------- | ------------------------------- |
| central  | https://maven.aliyun.com/repository/central | https://maven.aliyun.com/nexus/content/repositories/central | https://repo1.maven.org/maven2/ |

| public | https://maven.aliyun.com/repository/public | https://maven.aliyun.com/nexus/content/groups/public | central仓和jcenter仓的聚合仓 |
| ------ | ------------------------------------------ | ---------------------------------------------------- | ---------------------------- |
|        |                                            |                                                      |                              |

#### maven 配置指南

##### 打开 maven 的配置文件（ windows 机器一般在 maven 安装目录的 **conf/settings.xml** ），在<mirrors></mirrors>标签中添加 mirror 子节点:

```
<mirrors>
 <!-- 阿里云仓库 -->
        <mirror>
        <id>aliyunmaven</id>
		<mirrorOf>*</mirrorOf>
		<name>阿里云公共仓库</name>
		<url>https://maven.aliyun.com/repository/public</url>
		</mirror>
        <!-- 中央仓库1 -->
        <mirror>
            <id>repo1</id>
            <mirrorOf>central</mirrorOf>
            <name>Human Readable Name for this Mirror.</name>
            <url>http://repo1.maven.org/maven2/</url>
        </mirror>
    
        <!-- 中央仓库2 -->
        <mirror>
            <id>repo2</id>
            <mirrorOf>central</mirrorOf>
            <name>Human Readable Name for this Mirror.</name>
            <url>http://repo2.maven.org/maven2/</url>
        </mirror>


</mirrors>
```

- #### maven编译环境配置

```
<profiles>
    <profile>
          <id>jdk-1.8</id>
          <activation>
          <activeByDefault>true</activeByDefault>
            <jdk>1.8</jdk>
          </activation>
          <repositories>
            <maven.compiler.source>1.8</maven.compiler.source>    
            <maven.compiler.target>1.8</maven.compiler.target>    
            <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
          </repositories>
    </profile>
</profiles>
```

