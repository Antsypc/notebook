Maven Dependency Scope
=======
- compile : 默认选项.可以保证打包后的 APP 独立运行.任何时候都会被加入 classpaths.
- provided : 如果 APP 发布后的运行环境已经有该依赖的jar包,那么在项目打包时就不需要把该依赖加入.所以,如果依赖是 provided, 项目打包后可以发现其中没有对应的jar.需要运行时环境提供 jar 包支持,比如: web 容器已经有 servlet 的支持.只有在编译和测试会被加入 classpaths.
- runtime : 表示依赖在编译时不需要加入 classpaths,即不需要编译.只是在运行时和测试会被加入 classpaths.如 JDBC.
- test : 表明该依赖在正式的 APP 中是不需要的,只有测试的编译和运行时需要加入 classpaths.如 JUnit.
- system : system 范围依赖与 provided 类似，但是你必须显式的提供一个对于本地系统中JAR 文件的路径。这么做是为了允许基于本地对象编译，而这些对象是系统类库的一部分。这样的构件应该是一直可用的，Maven 也不会在仓库中去寻找它。如果你将一个依赖范围设置成系统范围，你必须同时提供一个 systemPath 元素。注意该范围是不推荐使用的（你应该一直尽量去从公共或定制的 Maven 仓库中引用依赖）。
- import : 只能被用于 <dependencyManagement> 的 <pom> 中,该依赖的配置会替换掉当前项目的一些参数,如 version.完成导包后,该依赖就完成了所有工作,不会参与之后的工作.如 spring-framework-bom.

> 下面这个该怎么翻译....

Each of the scopes (except for import) affects transitive dependencies in different ways, as is demonstrated in the table 
below. If a dependency is set to the scope in the left column, transitive dependencies of that dependency with the scope 
across the top row will result in a dependency in the main project with the scope listed at the intersection. If no scope 
is listed, it means the dependency will be omitted.

|compile | provided | runtime | test |
|--------|---------|---------|-------|
|compile | compile(*) | - | runtime | - |
|provided | provided | - | provided	| - |
|runtime | runtime | | - | runtime | - |
|test | test | - | test | - |

(*) Note: it is intended that this should be runtime scope instead, so that all compile dependencies must be explicitly 
listed - however, there is the case where the library you depend on extends a class from another library, forcing you to
have available at compile time. For this reason, compile time dependencies remain as compile scope even when they are
transitive.

