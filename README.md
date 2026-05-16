# DeviceCloud

一个轻量级的物联网设备云服务，使用C语言实现设备接入、数据转发和远程控制。

## 主要功能

- **设备接入服务**：基于TCP Socket的设备连接管理，支持多线程并发处理
- **MQTT协议桥接**：通过Paho MQTT库实现设备与MQTT服务器的数据交互
- **设备在线管理**：使用哈希表高效管理设备ID与连接的映射关系
- **双向通信**：设备数据上报 + 远程控制指令下发

## 技术栈

- 编程语言：C
- 网络库：POSIX Socket
- MQTT库：Eclipse Paho MQTT Async
- 编译工具：GCC + Make

## 编译运行

```bash
make
./ds
```

## 通信协议

- 设备端连接：TCP 8866端口
- MQTT服务：默认连接 localhost:1883
- 数据格式：`{device_id}/{topic} {payload}`
- 控制指令：订阅 `+/cmd` 主题，转发至对应设备

## 项目结构

```
device_cloud-master/
├── main.c           # 程序入口
├── device_server.c  # 设备服务器实现
├── device_server.h  # 设备服务器头文件
├── mqtt_client.c    # MQTT客户端实现
├── mqtt_client.h    # MQTT客户端头文件
├── hash_table.c     # 哈希表实现
├── hash_table.h     # 哈希表头文件
├── Makefile         # 编译配置
└── .gitignore       # Git忽略文件
```
