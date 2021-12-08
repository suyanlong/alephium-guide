# 目录结构说明

## 目录
```shell
~/github/alephium(master*) » tree -d -L 1   
```
```shell                                                                                                                                                                                  suyanlong@suyanlongdeMacBook-Pro-2
.
├── api       # openapi功能
├── app       # 服务入口
├── benchmark # 性能测试
├── conf      # 配置文件解析操作
├── crypto    # 密码库，加密算法、签名算法、哈希算法
├── docker    # docker 项关文件以及配置文件
├── flow      # 整个项目的核心，这个是重点，下文会详细介绍这个。
├── http      # http client 封装以及Swagger相关
├── io        # 缓存、数据库rockDB、trie底层结构功能操作
├── json      # json 相关解析操作
├── macros    # 常用宏定义
├── project   # 项目依赖、插件、代码风格配置文件等
├── protocol  # 协议：网络、VM、挖矿、以及区块链结构model
├── rpc       # jsonrpc2.0 协议规范相关操作
├── serde     # 类型序列化与反序列化
├── tools     # 调试工具
├── util      # 常用类型、函数库
└── wallet    # 钱包功能
```

## package作用说明
根据重要性以及作用，有选择的对如下几个package进行详细的介绍，其它未介绍的并不代表不重要，可以看做类库。

### flow
重点介绍对象

### app
服务的入口，定义main的地方。

### wallet

### protocol

### io



