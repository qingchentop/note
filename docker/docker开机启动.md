## 配置Docker以在启动时启动

大多数当前的Linux发行版（RHEL，CentOS，Fedora，Ubuntu 16.04及更高版本）用于[`systemd`](https://docs.docker.com/install/linux/linux-postinstall/#systemd)管理系统启动时启动的服务。Ubuntu 14.10及以下使用[`upstart`](https://docs.docker.com/install/linux/linux-postinstall/#upstart)。

### `systemd`

```shell
$ sudo systemctl enable docker
```

要禁用此行为，请`disable`改用。

```shell
$ sudo systemctl disable docker
```

如果需要添加HTTP代理，为Docker运行时文件设置不同的目录或分区，或进行其他自定义，请参阅 [自定义systemd Docker守护程序选项](https://docs.docker.com/engine/admin/systemd/)。

### `upstart`

Docker自动配置为在启动时启动 `upstart`。要禁用此行为，请使用以下命令：

```shell
$ echo manual | sudo tee /etc/init/docker.override
```

### `chkconfig`

```shell
$ sudo chkconfig docker on
```