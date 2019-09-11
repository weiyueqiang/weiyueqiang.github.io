# 我自己的Hexo使用

## 一、编写源文件

* 创建markdown文件

  * 方式一：

    在hexo根目录(D:\weiyueqiang.github.io\\)，打开git bash，输入一下命令：

    ```git
    hexo n filename
    ```

    filename不需要加后缀，他会自动加.md

    **这种方式会自动创建同名文件夹用来存放博客需要的资源文件。**

  * 方式二：

    在hexo 根目录(D:\weiyueqiang.github.io\\)，进入\source\\_posts\\。直接右键新建txt文档，重命名为filename.md 。

    **这种方式要自己创建一个与创建的文件名字相同的文件夹，用来存放博客需要的资源文件。**

* 编写文档

## 二、生成、部署到github

* 生成

  ```git
  hexo g
  ```

  生成后在hexo的public目录下在时间为文件夹名的里面应该有生成的html文件。

* 部署

  ```git
  hexo d
  ```

  部署就是将生成的文件，public文件夹上传到github。

* 这两部可以合为一步

  ```git
  hexo d -g
  等同于
  hexo g -d
  ```

## 三、备份hexo源文件

由于之前的配置，将hexo的源文件存在了该项目的 Hexo 分支。

* 运行下列git命令进行备份

  ```git
  git add .
  git commit -m "备份hexo"
  git push Hexo Hexo
  ```

  这里解释下：

  通过下面命令可以知道远程仓库的地址和命的名字，**上面第三行代码的第一个Hexo给远程仓库git连接命的名字，第二个Hexo是该仓库的分支名.**

  ```git
  git remote show
  或
  git remote -v
  ```

  



