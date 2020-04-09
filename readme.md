# Hexo使用

## 一、编写源文件

- 创建markdown文件

  - 方式一：

    在hexo根目录(402PC:  D:\weiyueqiang.github.io\\     MyPC:  D:\\blog\\)，打开git bash，输入一下命令：

    ```git
    hexo n filename
    ```

    filename不需要加后缀，他会自动加.md

    **这种方式会自动创建同名文件夹用来存放博客需要的资源文件。**

  - 方式二：

    在hexo 根目录(402PC:  D:\weiyueqiang.github.io\\     MyPC:  D:\\blog\\)，进入\source\\_posts\\。直接右键新建txt文档，重命名为filename.md 。

    **这种方式要自己创建一个与创建的文件名字相同的文件夹，用来存放博客需要的资源文件。**

- 编写文档

## 二、生成、部署到github

- 生成

  ```git
  hexo g
  ```

  生成后在hexo的public目录下在时间为文件夹名的里面应该有生成的html文件。

- 部署

  ```git
  hexo d
  ```

  部署就是将生成的文件，public文件夹上传到github。

- 这两部可以合为一步

  ```git
  hexo d -g
  等同于
  hexo g -d
  ```

## 三、备份Hexo环境文件(包括源文件)

- 第一次备份

  1. 在github的博客仓库创建一个Hexo(名字随意，我本人用的这个名字)。

  2. 将Hexo分支设置为默认分支。

  3. 在本地blog根目录，初始化git环境(blog的根目录是没有.git文件的，Hexo的部署有他自己内部的机制)

     `git init`

  4. 关联blog的远程仓库

     `git remote add Blog git@github.com:weiyueqiang/weiyueqiang.github.io.git`

  5. 修改.gitignore文件,除了这些文件剩下的都要备份

     .DS_Store
     Thumbs.db
     db.json
     \*.log
     node_modules/
     public/
     .deploy*/

     > Hexo的源文件说明：
     > 1、`_config.yml`站点的配置文件，需要拷贝；
     > 2、`themes/`主题文件夹，需要拷贝；
     > 3、`source`博客文章的.md文件，需要拷贝；
     > 4、`scaffolds/`文章的模板，需要拷贝；
     > 5、`package.json`安装包的名称，需要拷贝；
     > 6、`.gitignore`限定在push时哪些文件可以忽略，需要拷贝；
     > 7、`.git/`主题和站点都有，标志这是一个git项目，不需要拷贝；
     > 8、`node_modules/`是安装包的目录，在执行npm install的时候会重新生成，不需要拷贝；
     > 9、`public`是hexo g生成的静态网页，不需要拷贝；
     > 10、`.deploy_git`同上，hexo g也会生成，不需要拷贝；
     > 11、`db.json`文件，不需要拷贝。

  6. 命令

     `git add -A`

     把工作区的变化（包括已删除的文件）提交到暂存区

     ps:

     **·  git add -A  提交所有变化**

     **·  git add -u  提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)**

     **·  git add .  提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件**。

- 更新备份

  由于之前的配置，将Hexo的环境文件存在了该项目的 Hexo 分支，每一次上传新的blog，都要将环境文件push进行备份。Hexo部署与git push不分先后。

  运行下列git命令进行环境文件部署

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

## 四、在另一台PC同步hexo环境文件

没有Hexo环境的要先搭建Hexo环境，见之前的博客[搭建博客过程记录](<https://weiyueqiang.github.io/2019/08/07/%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2%E8%BF%87%E7%A8%8B%E8%AE%B0%E5%BD%95/>)。

直接敲命令

`git pull Blog Hexo`

如果显示冲突错误，即本地与远程有不一致，将提示的冲突文件或文件夹删除后，再进行 git pull。



**注：博客部署是用Hexo命令，环境备份与同步是git命令，相互完全不影响**