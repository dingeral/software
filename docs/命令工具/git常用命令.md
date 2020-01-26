#### 基本操作

**安装**：

```bash
$ sudo apt-get install git
```
**配置用户名和电子邮件**
```bash
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
**初始化**(在目标文件地址下)
```bash
$ git init
```
**创建SSH Key**

```bash
$ ssh-keygen -t rsa -C "youremail@example.com"
```

`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥。
