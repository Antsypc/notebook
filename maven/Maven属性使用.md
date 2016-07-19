Maven属性使用
=================
Maven 提供了三个隐式的属性env, project, settings,分别用于引用环境变量,pom信息,settings信息.

## env
通过 env 可访问系统环境变量,如 `${env.PATH}` 可引用到环境变量中的`PATH`.

> 查看系统环境变量 mvn help:system

## project
以 project 开头可引用到 pom 文件中的节点元素.
例如: `{project.XXX}` XXX 为 pom 文件中的任意节点,可跨多级节点访问,如`${project.build.finalName}`, 如`${project.groupId}`则引用到 pom 文件中配置的 groupId 的值.

## settings
以 settings 打头可引用到 Maven settings 信息,即 maven 的`settings.xml`文件.如`${settings.offline}`会引用`~/.m2/settings.xml`文件中`offline`元素的值.



> 另外maven还内置其他的变量,如 `${basedir}` : 项目根目录
