### Deepin MongoDB 安装

#### 导入 MongoDB 公钥
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
```

#### 创建 MongoDB 的软件源 /etc/apt/sources.list.d/mongodb-org-4.0.list
```bash
echo "deb http://repo.mongodb.org/apt/debian stretch/mongodb-org/4.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
```

#### 更新
```bash
sudo apt-get update
```
![Imgur](https://i.imgur.com/D9kEKYM.jpg)

出现了红框中的错误，不要紧张，执行下面的命令：
```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 68818C72E52529D4
```
再次执行：
```bash
sudo apt-get update
```

#### 安装 MongoDB 软件包
```bash
sudo apt-get install -y mongodb-org
```

#### 防止版本更新(可选)
为防止意外升级，要将 MongoDB 的版本固定为当前安装的版本
```bash
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```

#### 解决没有 /home/mongodb 目录的问题
```bash
sudo mkdir /home/用户名/mongodb
sudo chown -R mongodb:mongodb /home/用户名/mongodb
```

#### 运行 MongoDB

启动一下 mongod 后台守护进程
```bash
sudo service mongod start
```
启动 MongoDB 的 mongod 服务项:
```bash
sudo systemctl start mongod 
```
#### 验证 MongoDB 是否安装成功

查看MongoDB的日志文件/var/log/mongodb/mongod.log，可以看到类似这样的描述信息
![](https://pic3.zhimg.com/80/v2-3275a76221f058c3bbc78270873df032_hd.jpg)

也可以通过命令过滤查看信息
```bash
cat /var/log/mongodb/mongod.log | grep port
```
默认端口是`27017`

`<port>`是mongod监听的端口，可以修改配置文件/etc/mongod.conf中的net.port设置来配置端口。

#### 停止 MongoDB 服务

```bash
sudo systemctl stop mongod
```

#### 重启 MongoDB 服务

```bash
sudo systemctl restart mongod
```

#### 设置开机启动或者警用开机自启

```bash
sudo systemctl enable mongod #开机自启
sudo systemctl disable mongod #禁用开机自启
```

#### 使用 mongo

确保 mongod 在运行状态的前提下，在命令行窗口输入 `mongo` 进入交互模式。`Ctrl+C` 或者 `exit()` 退出命令窗口。

```bash
mongo
```
![](https://pic4.zhimg.com/80/v2-48c9611731e7dd6d07cd1413c32c7087_hd.jpg)

`WARNING: Access control is not enabled for the database.` 
关于这个警告，新版本的 MongDB 增加了安全性设计，推荐用户创建使用数据库时进行验证。如果用户想建立简单连接，则会提示警示信息。

解决方案:  
创建管理员并设置密码  

```bash
>use admin
>db.createUser(
  {
    user: "admin", //用户名
    pwd: "passwd", //密码
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] //设置权限
  }
)
```

重启数据库服务器
```bash
mongod --auth --port 27017 
```
“–auth”命令即表示访问数据库需要认证。此处可不指定端口，则默认为27017。 
启动后即可看到不再提示报警信息。

#### 参考
[教程 | Deepin MongoDB安装](https://zhuanlan.zhihu.com/p/55958396)  
[MongoDB数据库安装指南](https://wiki.deepin.org/index.php?title=MongoDB%E6%95%B0%E6%8D%AE%E5%BA%93%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97&language=zh)  
[mongodb连接服务器失败](https://bbs.deepin.org/forum.php?mod=viewthread&tid=157489&highlight=MongoDB)