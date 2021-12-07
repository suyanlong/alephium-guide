# macos 全节点安装

## [官方文档](https://wiki.alephium.org/Full-Node-Starter-Guide.html)

## 笔记本硬件参数

```shell
Model Name: MacBook Pro
Model Identifier: MacBookPro16,1
Processor Name: 6-Core Intel Core i7
Processor Speed: 2.6 GHz
Number of Processors: 1
Total Number of Cores: 6
L2 Cache (per Core): 256 KB
L3 Cache: 12 MB
Hyper-Threading Technology: Enabled
Memory: 16 GB
```

## 安装环境

### 安装 java sdk 
```shell
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install java 11.0.11.hs-adpt
```

查看
```shell
java -version 
```
输出：
```shell
openjdk version "11.0.13" 2021-10-19
OpenJDK Runtime Environment Temurin-11.0.13+8 (build 11.0.13+8)
OpenJDK 64-Bit Server VM Temurin-11.0.13+8 (build 11.0.13+8, mixed mode)

```

### 安装scala编译器
```shell
sdk install scala
```
查看
```shell
scala -version 
```
输出：
```                                                                                                                 
Scala code runner version 3.1.0 -- Copyright 2002-2021, LAMP/EPFL
```


### 安装sbt
```shell
sdk install sbt 
```
或者
```shell
brew install sbt
```

查看
```shell
sbt -V 
```
输出：
```shell

WARNING: A terminally deprecated method in java.lang.System has been called
WARNING: System::setSecurityManager has been called by sbt.TrapExit$ (file:/Users/.../.sbt/boot/scala-2.12.14/org.scala-sbt/sbt/1.5.5/run_2.12-1.5.5.jar)
WARNING: Please consider reporting this to the maintainers of sbt.TrapExit$
WARNING: System::setSecurityManager will be removed in a future release
sbt version in this project: 1.5.5
sbt script version: 1.5.5

```
### 

## 下载源码
```shell
git clone https://github.com/alephium/alephium.git
```

## 编译
```shell
make assembly
```
拷贝运行文件：
```shell
app/target/scala-2.13/alephium-1.1.6+13-b30f05c5+20211207-1612-SNAPSHOT.jar
wallet/target/scala-2.13/alephium-wallet-1.1.6+13-b30f05c5+20211207-1612-SNAPSHOT.jar
```

##(二)github下载[最新版本](https://github.com/alephium/alephium/releases)
```shell
wget https://github.com/alephium/alephium/releases/download/v1.1.6/alephium-1.1.6.jar
wget https://github.com/alephium/alephium/releases/download/v1.1.6/alephium-wallet-1.1.6.jar
```

## 创建运行时配置信息
```shell
mkdir -p ~/.alephium &&  cd ~/.alephium #数据目录
echo "alephium.network.network-id = 10\nalephium.discovery.bootstrap = []\n" > ~/.alephium/user.conf # 配置文件
```

## 运行
```shell
java -jar -Xmx500m alephium-1.1.6.jar
```
输出信息：
```shell
2021-12-07 16:33:27,437 [main]          INFO  o.a.f.s.Configs$                       - Using user configuration file at /Users/suyanlong/.alephium/user.conf 
2021-12-07 16:33:27,477 [main]          INFO  o.a.f.s.Configs$                       - Using system configuration file at /Users/suyanlong/.alephium/network-10/system.conf 
2021-12-07 16:33:27,495 [main]          INFO  o.a.f.s.Configs$                       - Using network configuration file at /Users/suyanlong/.alephium/network-10/network.conf 
2021-12-07 16:33:36,947 [-dispatcher-5] INFO  a.e.s.Slf4jLogger                      - Slf4jLogger started
2021-12-07 16:33:37,390 [main]          INFO  o.a.f.c.BlockFlow$                     - Initialize storage for BlockFlow
2021-12-07 16:33:37,611 [-dispatcher-8] INFO  o.a.f.n.CliqueManager                  - Start intra and inter clique managers, cliqueId: 03d2a3663b58240b564e5221a4cff784d67f9cc8eb0e9312c106c6ca263dfd8591
2021-12-07 16:33:37,617 [-dispatcher-7] INFO  o.a.f.n.CliqueManager                  - Intra clique manager is ready
2021-12-07 16:33:37,624 [-dispatcher-7] INFO  o.a.f.n.TcpController                  - Node bound to /0:0:0:0:0:0:0:0:9973
2021-12-07 16:33:37,629 [-dispatcher-5] INFO  o.a.f.h.TxHandler                      - Start to load persisted pending txs
2021-12-07 16:33:37,636 [-dispatcher-8] INFO  o.a.f.n.DiscoveryServer                - UDP server bound to /0.0.0.0:9973
2021-12-07 16:33:37,647 [dispatcher-11] INFO  o.a.f.h.TxHandler                      - Load persisted pending txs completed, valid: #0, invalid: #0 (not precise though..)
2021-12-07 16:33:37,678 [main]          INFO  o.a.app.BootUp                         - Build info: name: alephium-app, scalaVersion: 2.13.6, sbtVersion: 1.3.10, commitId: 0b4ed6cc51eccfd4ca0d3218e83bd49a64a310f2, branch: 0b4ed6cc51eccfd4ca0d3218e83bd49a64a310f2, releaseVersion: 1.1.6
2021-12-07 16:33:37,683 [main]          INFO  o.a.app.BootUp                         - Genesis digests: eacb96e0-f9d22f41-a55a2ac2-1284af43-9019ffb4-c0687225-a7ce72b6-28dc3897-05e623b8-5ce78379-9817461a-9c277d3b-11591e8c-5dcec0fd-8004ddfe-76fa9d1f
2021-12-07 16:33:44,416 [ext-global-49] INFO  o.a.a.WebSocketServer                  - Listening ws request on 11973
2021-12-07 16:33:44,416 [ext-global-46] INFO  o.a.app.RestServer                     - Listening http request on 12973
2021-12-07 16:33:44,421 [dispatcher-10] INFO  o.a.f.m.MinerApiController             - Miner API server bound to /127.0.0.1:10973
2021-12-07 16:34:07,655 [dispatcher-10] INFO  o.a.f.n.DiscoveryServer                - Initial P2P discovery is done: #0 neighbors
...


```
##安装jq
jq为json格式化工具
```shell
brew install jq
```

## [钱包命令指南](https://wiki.alephium.org/Wallet-Guide.html)

## 创建钱包 
POST /wallets
```shell
curl -X 'POST' 'http://127.0.0.1:12973/wallets' -H 'accept: application/json' -H 'Content-Type: application/json' -d '{"password": "12345","walletName": "wallet","isMiner": true}' ｜ jq
```
返回结果：
```shell
{
  "walletName": "wallet",
  "mnemonic": "target lake hawk duck laundry range okay series speed pistol admit focus dove lumber erupt century express van city proof walnut nerve motion potato"
}
```

## 获取地址
```shell
curl -X 'GET' 'http://127.0.0.1:12973/wallets/wallet/addresses' -H 'accept: application/json' | jq
```
返回结果：
```shell
{
  "activeAddress": "12GdsUnKHjqtEPkUb4SECL3eH7YAm17n9kvgmTCBBd5Ue",
  "addresses": [
    {
      "address": "12LTuUf6GiQbdAW8NTbzXUHabX91dmMKuKZfCfhDrCPoW",
      "group": 0
    },
    {
      "address": "19Lxf3cDVUrG523p6RH6XZheePdKKxGyyBDeo2SVCnwZf",
      "group": 1
    },
    {
      "address": "19QzkWWc5MVShxA46cJTmPEtCXTYXZSmsgPxjiDDqDgB6",
      "group": 2
    },
    {
      "address": "12GdsUnKHjqtEPkUb4SECL3eH7YAm17n9kvgmTCBBd5Ue",
      "group": 3
    },
    {
      "address": "1Bs7533GTwyJKPViA7pnH4Sz7LQj6syHrK3gmWcbeVczU",
      "group": 0
    },
    {
      "address": "1H3oQuYuDSnp2YL5hjTwsPNEvw8gN6U2VHLqqALBE8vhe",
      "group": 1
    },
    {
      "address": "1Dqj5JEpWDPFnYDYsAVNJhq3LA6kWji7Uvtw9QDi7qeJx",
      "group": 2
    },
    {
      "address": "15zMhmzhipn42nXEZZfAeDwhSMSdF2TpvaNNC5aSSrGP3",
      "group": 3
    }
  ]
}
```

## 创建挖矿地址

```shell
curl -X POST 'http://127.0.0.1:12973/wallets/wallet/derive-next-miner-addresses' -H 'accept: application/json' | jq
```
备注：REST API路径上钱包名字`wallet`替换成自己的。
返回结果：
```shell
[
  {
    "address": "1Bs7533GTwyJKPViA7pnH4Sz7LQj6syHrK3gmWcbeVczU",
    "group": 0
  },
  {
    "address": "1H3oQuYuDSnp2YL5hjTwsPNEvw8gN6U2VHLqqALBE8vhe",
    "group": 1
  },
  {
    "address": "1Dqj5JEpWDPFnYDYsAVNJhq3LA6kWji7Uvtw9QDi7qeJx",
    "group": 2
  },
  {
    "address": "15zMhmzhipn42nXEZZfAeDwhSMSdF2TpvaNNC5aSSrGP3",
    "group": 3
  }
]
```
备注：默认生成四个地址，即4*4个分片链。

## 更新挖矿地址
```shell
curl -X 'PUT' 'http://127.0.0.1:12973/miners/addresses' -H 'Content-Type: application/json' \
-d '{ "addresses": ["1Bs7533GTwyJKPViA7pnH4Sz7LQj6syHrK3gmWcbeVczU", "1H3oQuYuDSnp2YL5hjTwsPNEvw8gN6U2VHLqqALBE8vhe", "1Dqj5JEpWDPFnYDYsAVNJhq3LA6kWji7Uvtw9QDi7qeJx", "15zMhmzhipn42nXEZZfAeDwhSMSdF2TpvaNNC5aSSrGP3"]}'
```

## 查看挖矿地址
```shell

```
备注：地址替换成自己的。

## [CPU挖矿指导](https://wiki.alephium.org/CPU-Miner-Guide.html)
## 开启挖矿
```shell
curl -X 'POST' 'http://127.0.0.1:12973/miners?action=start-mining' -H 'accept: application/json' | jq
```
返回结果：
```shell
true
```

## 是否开启挖矿
```shell

```

## 关闭挖矿
```shell
/miners?action=stop-mining

```

## 解锁钱包
POST /wallets/{wallet_name}/unlock
```shell
curl -X 'POST' 'http://127.0.0.1:12973/wallets/wallet/unlock' -H 'Content-Type: application/json' -d '{"password": "12345"}'
```

## 锁定钱包
POST /wallets/{wallet_name}/lock
```shell
curl -X 'POST' 'http://127.0.0.1:12973/wallets/wallet/lock' -H 'Content-Type: application/json' -d '{"password": "12345"}'
```

## 获取钱包余额
GET /wallets/{wallet_name}/balances
```shell
curl -X 'GET' 'http://127.0.0.1:12973/wallets/wallet/balances' -H 'accept: application/json' 
```
返回结果：
```shell
{
  "totalBalance": "9750000022351741790",
  "totalBalanceHint": "9.75000002235174179 ALPH",
  "balances": [
    {
      "address": "12LTuUf6GiQbdAW8NTbzXUHabX91dmMKuKZfCfhDrCPoW",
      "balance": "0",
      "balanceHint": "0 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "19Lxf3cDVUrG523p6RH6XZheePdKKxGyyBDeo2SVCnwZf",
      "balance": "0",
      "balanceHint": "0 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "19QzkWWc5MVShxA46cJTmPEtCXTYXZSmsgPxjiDDqDgB6",
      "balance": "0",
      "balanceHint": "0 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "12GdsUnKHjqtEPkUb4SECL3eH7YAm17n9kvgmTCBBd5Ue",
      "balance": "0",
      "balanceHint": "0 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "1Bs7533GTwyJKPViA7pnH4Sz7LQj6syHrK3gmWcbeVczU",
      "balance": "1950000004470348358",
      "balanceHint": "1.950000004470348358 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "1H3oQuYuDSnp2YL5hjTwsPNEvw8gN6U2VHLqqALBE8vhe",
      "balance": "3900000008940696716",
      "balanceHint": "3.900000008940696716 ALPH",
      "lockedBalance": "1950000004470348358",
      "lockedBalanceHint": "1.950000004470348358 ALPH"
    },
    {
      "address": "1Dqj5JEpWDPFnYDYsAVNJhq3LA6kWji7Uvtw9QDi7qeJx",
      "balance": "1950000004470348358",
      "balanceHint": "1.950000004470348358 ALPH",
      "lockedBalance": "0",
      "lockedBalanceHint": "0 ALPH"
    },
    {
      "address": "15zMhmzhipn42nXEZZfAeDwhSMSdF2TpvaNNC5aSSrGP3",
      "balance": "1950000004470348358",
      "balanceHint": "1.950000004470348358 ALPH",
      "lockedBalance": "1950000004470348358",
      "lockedBalanceHint": "1.950000004470348358 ALPH"
    }
  ]
}
```

## 转账
POST /wallets/{wallet_name}/transfer
```shell

```

## 恢复钱包
PUT /wallets
```shell

```

## Q&A


