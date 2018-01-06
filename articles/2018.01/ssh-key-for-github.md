# 如何将本机ssh密钥添加到github

经过测试，如下步骤适用于windows、mac os、ubuntu系统，唯一的区别在于文件路径不同，下面会详细说明。

### 1、查看密钥是否存在

**mac os和ubuntu**：

```
cd ~/.ssh
```

**windows**：

```
C:\Users\Administrator\.ssh
```

如果存在该文件，说明密钥也存在

### 2、生成新的密钥

```
ssh-keygen -t rsa -C "youremail@example.com"
```

这里的email指的是你注册github账号时用的邮箱！！不能随便用一个邮箱！！

然后一路回车

![ssh-key](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/2018.01/ssh-key.jpg?raw=True)

到这一步，你的密钥就生成好了。

### 3、添加密钥

要注意的是，我们只需要添加公钥，也就是.ssh目录下的id_rsa.pub，id_rsa为私钥，尽量不要公开。

打开github的Settings界面，添加公钥。

![](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/2018.01/add-key.jpg?raw=true)

至此，添加成功，可以成功访问github上的远程仓库了。