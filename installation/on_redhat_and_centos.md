# 在 RedHat 或 CentOS

在 RedHat 及其衍生的发行版下，你可以使用 Crystal 官方的源。

## 配置源

首先你需要在你的 YUM 设置中添加源，运行以下命令即可简单完成：

```
  curl http://dist.crystal-lang.org/rpm/setup.sh | sudo bash
```

这样就在你的源的设置中添加了一个注册key。如果你更喜欢亲自动手设置，你可以这样做：

```
rpm --import http://dist.crystal-lang.org/rpm/RPM-GPG-KEY

cat > /etc/yum.repos.d/crystal.repo <<END
[crystal]
name = Crystal
baseurl = http://dist.crystal-lang.org/rpm/
END
```

## 安装
源被正确配置以后你就可以着手安装 Crystal 了：

```
sudo yum install crystal
```

## Upgrade

当有新的 Crystal 版本发布以后你可以使用系统命令升级：

```
sudo yum update crystal
```
