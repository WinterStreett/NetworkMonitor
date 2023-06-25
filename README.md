# NetworkMonitor
### 介绍
这是一个对本地IP和远程IP之间的网络流量进行监控的bpftrace程序。输出效果如下：

SADDR            DADDR                      TX_KB           RX_KB      latency_ms 
10.177.21.139    220.185.184.4                 0               0              35 
10.177.21.139    202.120.193.3                 0               0               1 
10.177.21.139    202.120.193.3                 0               3               1 
10.177.21.139    121.194.10.213                0               0              27 
10.177.21.139    49.4.17.138                   0               0              33 
10.177.21.139    49.4.45.146                   0               4              29 
10.177.21.139    49.4.45.146                  20               5              29 
10.177.21.139    121.194.10.213                0               0              26 
10.177.21.139    182.61.62.49                  1              21              35 

程序会不停地输出源IP和目的IP之间的网络监控信息，包括接收流量统计、发送流量统计和网络延迟。

### 用法
需要安装bpftrace，安装方法可参照官方文档。
在ubuntu20.04中安装bpftrace：
```shell
sudo apt-get install -y bpftrace
```
启动程序使用如下命令：
```shell
sudo bpftrace monitor.bt
```
程序正常运行需要root权限。

### 已知问题
安装bpftrace后，可能还需要安装[bpftrace debugging symbols](https://wiki.ubuntu.com/Debug%20Symbol%20Packages)才能正常启动bpftrace程序。
安装文档完成Getting -dbgsym.ddeb packages部分的操作，最后执行：
```shell
sudo apt-get install bpftrace-dbgsym
```
