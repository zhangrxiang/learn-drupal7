# Drupal

#### 安装的目录结构

> includes ：包含了Drupal常用的函数库。

> misc：用来存储Drupal安装中可用的JavaScript，和其它各种图标和图片文件。

> modules：包含了所有核心模块，其中一个模块对应一个文件夹。最好不要乱动这个文件夹（包括profiles和sites以外的其它目录）下面的任何东西，你要添加的其它模块须放到sites目录下

> profiles：包含一个站点的不同安装轮廓。如果在这个子目录下面，除了默认的轮廓以外，还有其它的轮廓，那么在你第一次安装你的Drupal站点时，Drupal将向你询问想要安装哪一个轮廓。安装轮廓的主要目的是，用来自动的启用核心的或者第3方的模块。比如一个电子商务轮廓，它将自动把Drupal安装成为一个电子商务平台。

> scripts：包含了许多脚本，这些脚本可用于语法检查，代码清洁，从命令行运行Drupal，使用cron处理特定情况等等。在Drupal的请求生命周期中，用不到它；里面包含一些shell和Perl的实用脚本。

> sites：包含对Drupal所进行的修改，设置、模块、主题等形式。从第3方模块库中下载的模块，或者自己编写的模块，都放在sites/all/modules下面。这使得对Drupal所进行的任何修改都保存在单个文件夹里。在目录sites下面有一个名为default的子目录，里面包含Drupal站点的默认的设置文件--- default.settings.php。Drupal安装器，将会基于你提供的信息来修改这些原始设置，并为你的站点创建一个settings.php文件。站点的部署人员，通常会拷贝默认目录，并将其重命名为你站点的URL，所以你最终的设置文件就位于[sites/www.example.com/settings.php].

> sites/default/files：Drupal默认是不包含这个文件夹，但是当你需要上传文件接着提供对外访问时，就需要用到这个目录了。一些示例包括，定制的logo，启用用户头像，或者向站点上传其它媒体文件时，就用到了这个文件夹。运行Drupal的web服务器需要具有对这个子目录进行读和写的权限。如果可以的话，Drupal的安装器将会自动的创建这个子目录，并检查是否设置了相应的权限。

> themes：包含了Drupal的模板引擎和默认主题。你下载的或者创建的其它主题，不能放在这里；应该放在sites/all/ themes中

> cron.php：用来执行周期性任务，比如清理过期缓存数据，以及计算统计信息。

> index.php：处理请求的主入口。

> install.php： Drupal安装器的主入口。

> update.php： Drupal版本升级后，用来更新数据库模式（schema）。

> xmlrpc.php： 用来接收XML-RPC请求，如果你的网站不打算接收XML-RPC请求的话，那么可以将其从中删除。

> robots.txt：它是搜索引擎爬虫排除标准的默认实现。

#### 服务一个请求
- [http://example.com/foo/bar](url)

>- 首先，基于Drupal的.htaccess文件中的mod_rewrite规则，对输入URL进行检查，并将基路径从路径中分离出去。在我们的例子中，路经就为foo/bar。

>- 将这个路径指定给URL查询参数q。

>- 最终的URL就为[http://example.com/index.php?q=foo/bar]。

>- Drupal把foo/bar作为Drupal内部路径，并在index.php中开始进行处理。

###### **Drupal对**http://example.com/foo/bar和http://example.com/index.php?q=foo/bar的处理方式是一样的，因为对于Drupal来说，这两者的内部路径是一样的。这就使得Drupal可以使用不带“?q=”的URL了。这些URL被称为简洁URL。

#### 引导指令流程

##### 引导指令流程
