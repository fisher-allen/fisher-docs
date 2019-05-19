# fisher项目如何启动

## 项目结构说明
- fisher-center Eureka服务注册中心,该工程已经删除
  注册中心已替换成Nacos
- fisher-common 公共模块
- fisher-auth  Oauth2 认证服务器 提供token
- fisher-back 后台管理模块
- fisher-transcation 基于mq最终一致性实现可靠消息的分布式事务方案
  - fisher-transaction-message 独立消息服务微服务
  - fisher-transaction-sample 基于支付宝转账的演示
  - fisher-transaction-web消息补偿管理后台
- fisher-monitor Spring boot admin监控以及Skywalking监控
- fisher-log 日志中心模块
- fisher-file 文件上传服务,这个服务可以暂时不起，因为前端还没有对接
- fisher-gen 代码生成模块
- fisher-starter 自定义封装各种starer 目前封装了日志处理
- fisher-gateway 后端统一入口，提供动态路由，oauth2的资源服务器

## 项目运行
```
git clone https://github.com/fanxinglong/fisher
先配置数据库，然后reids，需要启动rabbitmq,启动nacos,启动sentinel
启动顺序：最好按顺序启动，不按顺序启动，至少要把网关放到最后启动
注意：Nacos先修改配置连自己本地数据库，并把nacos的配置数据库导入到自己本地数据库
导入之后，检查nacos各个微服务相关配置的mysql，redis,rabbitmq配置是否正确
fisher-auth
fisher-back
fisher-log
fisher-gen
fisher-monitor
fisher-transcation
fisher-file 
fisher-gateway

前端启动参照前端项目
```