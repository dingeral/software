### 全程记录通过换源将深度从unstable版升级到stable版

> 群众的力量是无穷的，官方没有好办法，深粉搞出办法，厉害！

1）更改源文件，将 panda 更改为 lion 。  
打开源文件的命令：
```bash
sudo vim /etc/apt/sources.list
```
 将里面的 panda 改成l ion ，保存并退出。 

2）更新stable源：
```bash
 sudo apt-get update
```

3）升级到stable版：
```bash
sudo apt-get dist-upgrade
```

4）如果提示 linux-firmware 不能更新，则使用命令
```bash
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.173.2_all.deb 
```
可以强制更新。

5）如果出现控制中心秒退，则通过
```bash
sudo aptitude install dde-kwin/lion
```
键入3次 n ，第4次键入 y（到底是到第几次键入 Y ，我可能记得不太对，大家多尝试下）

完成后，重启深度，控制中心就可以正常显示了。

目前可能有小问题，最好重装。

#### 参考

[全程记录通过换源将深度从unstable版升级到stable版](https://bbs.deepin.org/forum.php?mod=viewthread&tid=181062&extra=)