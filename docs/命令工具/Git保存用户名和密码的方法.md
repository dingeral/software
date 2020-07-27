在使用Git 的时候，经常会遇到需要频繁输入密码的情况，每次 `git push` 和 `git pull` 都要求输入用户名和密码，如果提交频繁的话就十分不方便。

那么怎么解决Git保存用户名和密码呢？

1、进入Git 配置文件。

```bash
vim ~/.gitconfig
```

2、修改配置文件，添加下面内容。

```bash
[credential]
helper = store
```

然后使用的时候，输入一次用户名和密码之后，就不会出现再提交用户名和密码。

**参考资料：[Ubuntu下解决Git保存用户名和密码的方法](https://blog.csdn.net/zhengqijun_/article/details/63298202)**
