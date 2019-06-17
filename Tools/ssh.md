# 复制公钥到远程机器中
    ssh-copy-id -i .ssh/id_rsa.pub <username>@<remote SSH server>
    cat ~/.ssh/id_rsa.pub | <username>@<remote SSH server> "mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys"
# 转发本地端口7080到远程机器端口80
    ssh -N -L7080:localhost:80 <username>@<remote SSH server>
# 通过中间主机建立SSH连接，当不能直接访问某台机器时可通过中间主机间接访问
    ssh -t reachable_host ssh unreachable_host
# 创建到目标主机的持久化连接
    ssh -MNf <user>@<host>
# 通过SSH将MySQL数据库复制到新服务器
    mysqldump –add-drop-table –extended-insert –force –log-error=error.log -uUSER -pPASS OLD_DB_NAME | ssh -C user@newhost "mysql -uUSER -pPASS NEW_DB_NAME"
# 实时SSH网络吞吐量测试
    yes | pv | ssh $host "cat > /dev/null"
# 通过SSH W/ WIRESHARK分析流量
    ssh root@server 'tshark -f "port !22" -w -' | wireshark -k -i –
    ssh root@server tcpdump -w – 'port !22' | wireshark -k -i –
# 保持SSH会话永久打开
    autossh -M50000 -t server.example.com 'screen -raAd mysession'
# 使用cstream控制带宽
    tar -cj /backup | cstream -t 777k | ssh host ‘tar -xj -C /backup’
# 压缩文件到远程机器
    tar -zc dir | ssh 10.0.2.2 "cat - > ~/dir"
# ssh 反向代理
    第一步，在需要方向代理机器上连接跳板机
    ssh -Nf -R 9022:127.0.0.1:22 server@47.88.48.207
    第二步，可在跳板机上通过转发的端口，连接被反向代理的机器
    ssh -p 9022 client@127.0.0.1
# 建立SOCKS5代理
    ssh -f -N -D 127.0.0.1:1080 qioixiy@47.88.48.207
    google-chrome --proxy-server="socks://127.0.0.1:1080"
# 三种转发方式：本地转发，远程转发，动态转发 [url](http://blog.creke.net/722.html)
    ssh -C -f -N -g -L listen_port:DST_Host:DST_port user@Tunnel_Host
    ssh -C -f -N -g -R listen_port:DST_Host:DST_port user@Tunnel_Host
    ssh -C -f -N -g -D listen_port user@Tunnel_Host
## 转发实例
    ssh -N -f -D 1080 123.123.123 # 将端口绑定在127.0.0.1上
    ssh -N -f -D 0.0.0.0:1080 123.123.123.123 # 将端口绑定在0.0.0.0上
# ssh proxy
- ssh -f -C2qTnN -D localport <username>@<remote SSH server>
- ssh -f -C2qTnN -D 8000 ubuntu@54.65.203.95 -i ubuntu-pem-key.pem
```
-f 后台运行
-C 压缩
-2 只支持版本2协议
-q 静默模式
-T 禁用伪终端分配
-n 阻止从标准输入读取。后台运行的话，必须使用
-N 不执行远程命令
-D [bind_address : ] port 本地动态应用级端口转发。没有指定address将监听在127.0.0.1上
```
# ssh gateway ports
```
/etc/ssh/sshd_config
GatewayPorts yes
```

# url
- [ssh user](https://www.fastssh.com/page/secure-shell-servers)
