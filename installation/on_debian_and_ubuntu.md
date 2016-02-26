# 在 Debian 或 Ubuntu

在 Debian 及其派生的发行版中，你可以使用Crystal官方的源进行安装与升级。

## 配置源

首先你需要把源加入到你的APT配置当中。运行以下命令即可简单完成：

```
  curl http://dist.crystal-lang.org/apt/setup.sh | sudo bash
```

这样就在你的源的设置中添加了一个注册key。如果你更喜欢亲自动手设置，你可以这样做：

```
apt-key adv --keyserver keys.gnupg.net --recv-keys 09617FD37CC06B54
echo "deb http://dist.crystal-lang.org/apt crystal main" > /etc/apt/sources.list.d/crystal.list
```

## 安装
源被正确配置以后你就可以着手安装 Crystal 了：

```
sudo apt-get install crystal
```

## 更新

当有新的 Crystal 版本发布以后你可以使用系统命令升级：

```
sudo apt-get update
sudo apt-get install crystal
```
