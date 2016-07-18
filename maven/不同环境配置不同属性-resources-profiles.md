利用 resources,profiles,filter 实现不同环境使用不同属性
====================
一般开发会有三种环境需要配置各自不同的变量:开发环境,测试环境和生产环境.
使用 Maven 可以方便实现不用改来改去完成这样的操作.

## 方法
在 pom.xml 文件中添加
```
<build>
    <resources>
        <!-- 指定资源文件 -->
        <resource>
            <directory>src/main/resources</directory>
            <includes>
                <include>config/*</include>
                <include>spring/*</include>
                <include>*.properties</include>
                <include>*.xml</include>
                <include>*.ini</include>
            </includes>
            <filtering>false</filtering>
        </resource>
        <!-- 下面资源文件中的${key}属性将会被替换或覆盖 -->
        <resource>
            <directory>src/main/resources</directory>
            <includes>
                <include>config/</include>
                <include>*.ini</include>
            </includes>
            <filtering>true</filtering>
        </resource>
    </resources>
    <!-- 使用下面文件中的属性替换上面需要被替换的属性, ${profileName}是 profiles 中的值 -->
    <filters>
        <filter>src/main/resources/filter/${profileName}.properties</filter>
    </filters>
</build>

<profiles>
    <!-- 定义环境变量 id -->
    <!-- 如果不指定,这个环境即默认环境,使用它的配置文件 -->
    <profile>
        <id>dev</id>
        <activation>
            <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
            <profileName>dev</profileName>
        </properties>
    </profile>
    <profile>
        <id>test</id>
        <properties>
            <profileName>test</profileName>
        </properties>
    </profile>
    <profile>
        <id>prod</id>
        <properties>
            <profileName>product</profileName>
        </properties>
    </profile>
</profiles>
```

编译打包方法,例如使用生产环境的变量: `mvn clean package -Pproduct`

## 说明
在`src/main/resources`下有 database.properties 文件:
```
user=${database.user}
password=${database.password}
jdbcUrl=${database.jdbcUrl}
driverClass=com.mysql.jdbc.Driver
```

上述文件中的属性就会被`src/main/resources/filter/product.properties`替换,如果有新属性也会直接加入.
```
database.user=app
database.password=app
database.jdbcUrl=jdbc:mysql://localhost:3306/appstore?useUnicode=true&characterEncoding=utf8
```
