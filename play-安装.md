# play框架的安装
简单记录下play框架的安装

## 参考资料
>* 官网: https://www.playframework.com
>* 下载: https://www.playframework.com/download
>* typesafe github: https://github.com/typesafehub/activator


## 1. 准备
在官网下载play安装，现在比较新的版本都是使用activator管理，所以先下载activator，
然后再慢慢下，速度不快，而且东西比较多，所以可能会比较慢，稍微早一点的版本可以直接下载后解压就好了，
只是创建工程的方式有点不同

## 2. 创建hello
### command line
activator创建新的project的命令如下：

    > activator new
创建过程有些选择语言（Scala，Java）以及模版的情况，自己喜欢什么选什么

运行一个工程，首先需要进入到工程目录下：
    
    > activator run
    
在工程目录下进入activator交互：

    > activator
这样就进入了命令行交互，直接使用run就可以启动工程，activator在工程目录下回自动载入工程
    
    $ run
    
### Activator ui and tutorials
在terminal中启动activator ui
    
        > activator ui
其他操作都可以在web界面中进行    

### old command line
在比较老一点的版本中，可以直接使用play命令，前提是要把play的bin目录加入到环境变量中
    
    > play new hello # 创建一个hello工程，回车后可能会让你继续输工程名称，可以输，也可以直接回车
    > cd hello # 进入刚才创建的hello工程目录
    > play run # 运行工程
其实play的命令也是封装了activator,activator依然可以使用


## 3. 将工程装换成eclipse或者IDEA项目
这个转换官网有例子：
>* https://www.playframework.com/documentation/2.4.x/IDE

IDEA中可以直接创建play的项目，不过由于sbt的原因，创建过程异常缓慢，要下载很多文件包括Scala的jar包，
而且很多需要翻墙，最重要的是即便翻墙了还是慢，源就不是很好，没办法

所以，现在可以创建好了直接用sublime text打开，编辑，安装一个play2的插件，也还是可以用的，不过就需要多看
多查API了，提示不很给力，都要自己记住还是挺累的


