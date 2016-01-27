maven安装配置
==================
## 下载安装
* 从[maven](http://maven.apache.org/)下载.
* 直接解压,完成安装

## 配置环境变量
linux下编辑文件`/etc/profile`
    
    export M2_HOME=/usr/share/apache-maven-3.3.9
    export PATH=$PATH:$M2_HOME/bin

## maven规范的目录结构

    -src
        -main
            -java
        -test
            -java
    -resources

## 例子
* 按照maven规范建立目录,在java目录下书写源文件
* 在源文件书写代码,该源文件使用了第三方jar包
* 编辑pom.xml

pom.xml示例

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>

        <groupId>xyz.antsgroup.example</groupId>
        <artifactId>example-clean</artifactId>
        <version>1.0-SNAPSHOT</version>

        <dependencies>
            <!-- jdbc -->
            <dependency>
                <!-- maven中jar包坐标,在maven中所有资源用此方式进行唯一标识 -->
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>5.1.38</version>
            </dependency>
        </dependencies>
    </project>

* 编译:在项目根目录下`mvn compile`
* 运行测试用例:`mvn test`
* 打包:将项目打包为jar或war,`mvn package`

## 使用archetype插件
用于创建复合maven规范的目录骨架.

    $ mvn archetype:generate // 在项目根目录下使用.
    $ 6                      // 选择archetype版本号
    $ xyz.antsgroup.maven    // 输入groupId
    $ maven-example01        // 输入artifactId
    $ 1.0.0-SNAPSHOT         // 输入版本号
    $ xyz.antsgroup.maven    // 输入初始创建的包

或者 

    $ mvn archetype:generate -DgroupId=xyz.antsgroup.maven -DartifactId=maven-example01 -Dversion=1.0.0-SNAPSHOT -Dpackage=xyz.antsgroup.maven

## 坐标与仓库
坐标:在pom.xml中使用`groupId`,`artifactId`,`version`进行唯一标识资源.

仓库分为本地仓库和远程仓库,存放了各种jar包.编译项目时,maven首先在本地仓库查找jar包资源,如果未找到则在中央仓库去下载.默认的中央仓库是`http://repo.maven.apache.org/maven2`.中央仓库包含了绝大多数常用的jar包.

镜像仓库,全球仓库在国外,国内使用镜像仓库可以更快下载资源.镜像仓库位置可在maven安装目录下的`/conf/settings.xml`中`<mirrors>`设置.

修改本地仓库存放路径:修改`settings.xml`中`<localRepository>`

## maven生命周期
clean,test,site

package:依次执行compile,test

site:生成项目站点
