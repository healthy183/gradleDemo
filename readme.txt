--1,创建主模块
mkdir gradleDemo && cd gradleDemo
gradle init

--2,创建多个子模块
mkdir -p core/src/main/java
mkdir -p core/src/test/java
mkdir -p web/src/main/java
mkdir -p web/src/test/java

--3,根目录settings.gradle 文件，引入子模块：
include 'core','web'

--4,修改根目录下的 build.gradle：
具体看gradleDemo/build.gradle


--5,web 模块需要依赖 core 模块，故定义 web/build.gradle;
具体看web/build.gradle

--6 查看所有 jar
$ gradle listJars

--7 查看各个模块的依赖：
$ gradle :core:dependencies
$ gradle :web:dependencies

--8  编译所有模块
gradle build

其他

1,指定 build 输出目录和版本号
buildDir = "target"
version = '1.0'

2 Gradle 命令时如何指定参数
gradle task -P profile=development

3 Gradle 和 idea 集成时如何不自动下载依赖源码和javadoc
idea {
    module {
        downloadJavadoc = false
        downloadSources = false
    }
}

4 自定义maven私服
repositories {
    maven {
        credentials {
            username 'user'
            password 'password'
        }
        url "http://repo.mycompany.com/maven2"
    }
}
