# play 连接数据库
关于基本的连接数据库的配置，这里的配置使用mysql和EBean

## 1. application.conf
配置数据库基本信息：

    db.default.driver=com.mysql.jdbc.Driver
    db.default.url="jdbc:mysql://host:3306/play?characterEncoding=UTF-8"
    db.default.user=root
    db.default.password="xxx"
    
    ebean.default = ["models.*"]

## 2. build.sbt
添加数据库驱动的jar包，一句话配置 `"mysql" % "mysql-connector-java" % "5.1.27"`：
    
    libraryDependencies ++= Seq(
      javaJdbc,
      cache,
      javaWs,
      "mysql" % "mysql-connector-java" % "5.1.27"
    )
    
为了使用EBean, 还需要在这里配置 `PlayEbean`，具体如下：

    lazy val root = (project in file(".")).enablePlugins(PlayJava, PlayEbean)

## 3. project/plugins.sbt
在plugins.sbt中添加：

    addSbtPlugin("com.typesafe.sbt" % "sbt-play-ebean" % "1.0.0")
这样就配置好了ebean


## 4. models
在上面步骤完成后，可能需要重启一下，有时候不能正确识别配置的信息
然后在这个基础上添加model

1. 在app目录下创建models文件夹
2. 在models目录下新建java类，Post
3. Post类内容如下：

        package models;
        import com.avaje.ebean.Model;
        import javax.persistence.Entity;
        import javax.persistence.Id;
        import javax.persistence.Table;
        
        @Entity
        @Table(name="simple_post")
        public class Post extends Model{
            @Id
            public Long id;
            public String title;
            public String content;
        
            public static final Finder<Long,Post> find = new Finder<>(Post.class);
        }
    
5. 重新运行程序，会出现创建数据的提示，直接apply就可以，这样就会自动在数据库中创建对应的表
以后的增删改查的操作都是在Model中有定义的

老的版本中使用的Model在 `play.db.ebean`这个包中，不过新版本已经更换了，变成了`com.avaje.ebean.Model`
具体关于EBean的内容可以参看：
>https://ebean-orm.github.io/docs



