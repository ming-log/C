<font size=20><b>使用Git命令操作项目</b></font>

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

