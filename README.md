# xchain-monitor

xchain-monitor是用来监控[xuperunion](https://github.com/xuperchain/xuperunion)区块链系统运行状态(包括机器、节点进程、节点业务信息)的开源监控系统。

-----------

## 监控指标，如下：

### 业务相关信息监控

* TrunkHeight
  - 节点当前最新区块高度；采用Graph表示；
* MaxBlockSize
  - 系统当前最大区块大小限制；采用Singlestat表示；
* AccountNewAmount
  - 创建一个合约账号需要消耗的资源；采用Singlestat表示；
* SetAclAmount
  - 设置权限ACL需要消耗的资源；Singlestat表示；
* TotalUtxoAmount
  - 当前系统utxo总量；采用Graph表示；
* UnconfirmedTxAmount
  - 当前节点未确认交易数量；采用Gauge表示；
* PostTxTPS
  - 当前节点交易TPS；采用Gauge表示；
* IrreversibleSlideWindow
  - 系统不可逆区块的窗口值；采用Singlestat表示；
* IrreversibleBlockHeight
  - 系统不可逆区块高度；采用Singlestat表示；
* UtxoLastBlockHash
  - 系统当前utxo最新区块ID；
* LedgerLastBlockHash
  - 系统当前ledger最新区块ID；
* AverageLatency
  - 系统平均延时；采用Graph表示；
  
### 进程相关信息监控（TODO）

* CPU
  - 节点当前CPU消耗情况；
* Memory
  - 节点当前Mem消耗情况；
* Disk
  - 节点当前Disk消耗情况；
* File descriptor
  - 节点当前文件描述符使用情况；
* IO
  - 节点当前IO消耗情况；
* 网络带宽
  - 节点当前网络带宽消耗情况；
* go routine
  - 节点当前go routine消耗情况；
* 连接数
  - 节点当前连接数；
  
### 机器相关信息监控（TODO）
  
* CPU
  - 机器整体CPU消耗情况
* Memory
  - 机器整体Memory消耗情况
  
  
## 仪表盘(Dashboard)截图

节点业务相关信息监控
![xchain-node-info](https://github.com/ToWorld/xuperchain-image/blob/master/xchain-node-info.png)


## 许可证

xchain-monitor使用的许可证是Apache 2.0

------------------

## 安装

### 前置条件

* Python

### 启动agent

* 启动xchain-httpgw  
```
 nohup ./xchain-httpgw --gateway_endpoint localhost:6718 --http_endpoint :8097 &
 其中，--gateway_endpoint为xchain对外rpc端口，http_endpoint为xchain-httpgw为对外服务访问端口
 ```

* 启动fetch_xchain_node_info.py
```
python fetch_xchain_node_info.py
```
### 启动server

* 启动prometheus 
```
./prometheus --config.file=./prometheus.yaml --web.listen-address="0.0.0.0:8090"
```
* 启动grafana
