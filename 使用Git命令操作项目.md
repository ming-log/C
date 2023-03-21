<font size=20><b>使用Git命令操作项目（图文教程）</b></font>

# 配置Github密钥

为了向远程仓库提交代码，需要生成密钥，并在github上进行配置

## 使用git生成密钥

打开`Git Bash`

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321181511461.png" alt="image-20230321181511461" style="zoom:50%;" />

进入`~/.ssh`目录

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321181638412.png" alt="image-20230321181638412" style="zoom:50%;" />

输入以下代码生成密钥

```shell
# your email 表示自己的邮箱
ssh-keygen -t rsa -C "your email"(这里需要换成自己的邮箱)
```

在`~/.ssh`生成了两个文件，`id_rsa`和`id_rsa.pub`其中`id_rsa.pub`为公钥，打开并**复制文件中所有内容**。

## 将密钥内容添加到`Github`

点击`Settings`设置

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321182127789.png" alt="image-20230321182127789" style="zoom:50%;" />

点击`SSH and GPG keys`

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321182251211.png" alt="image-20230321182251211" style="zoom: 50%;" />

点击`New SSH key`

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321182407487.png" alt="image-20230321182407487" style="zoom:50%;" />

添加完成

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321182445239.png" alt="image-20230321182445239" style="zoom:50%;" />



测试`SSH key `是否设置成功

```shell
ming_log@Ming-Log MINGW64 ~/.ssh
$ ssh -T git@github.com
```

```shell
The authenticity of host 'github.com (192.30.253.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
```

<img src="https://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321182718749.png" alt="image-20230321182718749" style="zoom: 67%;" />

返回以上内容说明`SSH`设置成功。

# 提交新项目至Github

## 打开要上传的工程

![image-20230321193855819](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321193855819.png)

## 为该工程创建Git仓库

右键文件夹空白处点击`Git Bash Here`

![image-20230321193945629](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321193945629.png)

在开启的窗口中输入`git init`进行初始化

![image-20230321194352427](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321194352427.png)

## 添加文件至仓库

输入`git add .` 命令将该文件夹下的所有文件加入到`git`仓库。

![image-20230321194533700](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321194533700.png)

可输入`git status`查看当前提交状态。

![image-20230321194610852](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321194610852.png)

## 将项目提交给本地仓库

输入以下代码 `git commit -m "first commit"`

![image-20230321195325569](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195325569.png)

使用以下命令`git branch -M main`创建一个main分支

![image-20230321195427554](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195427554.png)

## 在Github中创建远程仓库

### 打开Github点击Repositories，然后再点击New

![image-20230321195144673](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195144673.png)

### 输入仓库名称点击创建即可

![image-20230321195225910](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195225910.png)

## 关联本地仓库与远程仓库

使用以下命令将本地仓库与远程仓库进行关联

```shell
log_ming@DESKTOP-M5MISQV MINGW64 /f/tipdm_cup/11th/test (main)
$ git remote add origin git@github.com:ming-log/test_resp.git
```

![image-20230321195511988](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195511988.png)

## 推送本地仓库到远程仓库

```shell
git push -u origin main
```

![image-20230321195753815](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195753815.png)

## 打开Github查看仓库是否发生改变

![image-20230321195837048](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321195837048.png)

# 克隆远程仓库到本地

刚才我们已经成功将本地创建的仓库上传到Github远程仓库，接下来尝试将刚刚上传的远程的Github仓库，克隆到本地。

克隆的方法很简单，只需使用命令`git clone git@github.com:ming-log/test_resp.git`即可克隆到当前文件夹。

![image-20230321200251513](http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200251513.png)

打开文件夹也可以查看到克隆下来的工程。

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200320742.png" alt="image-20230321200320742" style="zoom:50%;" />

# 修改已克隆的仓库内容后再次上传到远程仓库

## 打开刚刚克隆下来的工程，修改README.md文件

原文件

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200452640.png" alt="image-20230321200452640" style="zoom:25%;" />

修改后的文件

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200517205.png" alt="image-20230321200517205" style="zoom:25%;" />

如果我们上传后远程仓库中对应的位置出现了我们想要的文字，就说明再次上传成功。

## 在工程中创建一个文件

然后再新建一个文件夹，把文件夹也同步到远程仓库

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200652290.png" alt="image-20230321200652290" style="zoom:50%;" />

## 将项目提交到本地仓库

直接输入`git commit -m "second commit"`，发现发生了报错。

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321200846167.png" alt="image-20230321200846167" style="zoom:50%;" />

出现错误的原因是因为我们在这里不仅是修改了文件内容，还新建了文件。在提交前需要将新建的文件添加到本地仓库。

使用以下命令`git add .`进行添加，添加完毕后再次进行提交。

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321201024943.png" alt="image-20230321201024943" style="zoom:50%;" />

提交成功。

## 推送本地仓库内容到远程仓库

输入`git push`进行推送。

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321201331350.png" alt="image-20230321201331350" style="zoom:50%;" />

## 在远程仓库中进行查看是否发生变化

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321201640647.png" alt="image-20230321201640647" style="zoom:50%;" />

可以发现确实发生了变化。

# 修改远程仓库内容，本地仓库进行拉取同步

## 修改远程仓库文件内容

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321201811634.png" alt="image-20230321201811634" style="zoom:50%;" />

## 在本地仓库中进行同步

输入命令`git pull`进行同步

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321202034826.png" alt="image-20230321202034826" style="zoom:50%;" />

在本地文件夹中查看文件是否发生变化

<img src="http://ming-log.oss-cn-hangzhou.aliyuncs.com/img/image-20230321202058160.png" alt="image-20230321202058160" style="zoom:33%;" />

文件内容已发生变化，同步成功。