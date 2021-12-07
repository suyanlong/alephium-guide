# macos 全节点安装

## 笔记本硬件参数

```aidl
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

```

## github下载[最新版本](https://github.com/alephium/alephium/releases)
```shell
wget https://github.com/alephium/alephium/releases/download/v1.1.6/alephium-1.1.6.jar
wget https://github.com/alephium/alephium/releases/download/v1.1.6/alephium-wallet-1.1.6.jar
```

## 创建运行时配置信息
```shell
mkdir -p ~/.alephium &&  cd ~/.alephium #数据目录
echo "alephium.network.network-id = 10\nalephium.discovery.bootstrap = []\n" > config.conf # 配置文件
```

## 运行
```shell

```

## 查看状态

## 开启挖坑

## 


## Q&A


