罗宋汤
=====

罗宋汤是一个支持多平台的端口转发工具。

端口转发
-------
```
./rs_linux_amd64 -t proxy -h 0.0.0.0 -p 6379 -hd 192.168.1.2 -pd 6379
```
以上命令把本地端口6379转发到192.168.1.2的6379端口


内网穿透
-------
服务端配置(公网ip: 112.74.200.115)
```
./rs_linux_amd64 -t server -h 0.0.0.0 -p 6379 -pb 1998 -pc 1999
```
客户端配置
```
./rs_linux_amd64 -t client -h 112.74.200.115 -pb 1998 -pc 1999 -hd 192.168.1.2 -pd 6379
```
以上命令把公网主机的6379端口转发到内网192.168.1.2的6379端口


yaml配置文件
-----------
用yaml文件配置多个端口转发，`vi config.yaml`
```
servers:
  - type: server
    host: 0.0.0.0
    port: 6379
    port_b: 1998
    port_c: 1999

  - type: client
    host: 112.74.200.115
    port_b: 1998
    port_c: 1999
    host_d: 192.168.1.2
    port_d: 6379

  - type: proxy
    host: 0.0.0.0
    port: 6379
    host_d: 192.168.1.2
    port_d: 6379
```
运行罗宋汤 `./rs_linux_amd64 -c config.yaml`

下载
----
linux 64位
```
wget googlebridge.com/rs_linux_amd64
```

mac
```
wget googlebridge.com/rs_mac
```

windows 64位
```
wget googlebridge.com/rs_windows_adm64.exe
```


项目故事
-------
纪念17年有段时间吃了一个多月的罗宋汤，直到现在还是恋恋不忘～ repo就是在那段时间创建的，写过2个版本python、go，自测了1年多😂