# 下载和安装live555
```
wget  http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar -xzvf live555-latest.tar.gz
cd live
./genMakefiles linux-64bit
make
```

# 下载测试文件
```
wget http://www.live555.com/liveMedia/public/264/test.264
```

# 启动server
```
./mediaServer/live555MediaServer
```

# 启动client
```
ffplay rtsp://127.0.0.1/test.264
```
