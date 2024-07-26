<p align="center">
  <strong>基于kettle的可视化数据集成平台</strong><BR/>
 
</p>

<p align="center">
    <a target="_blank" href="https://github.com/young-datafan/data-integration/blob/develop/LICENSE">
        <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?label=license" />
    </a>
    <a target="_blank" href="https://www.oracle.com/technetwork/java/javase/downloads/index.html">
        <img src="https://img.shields.io/badge/JDK-8+-green.svg" />
    </a>
</p>
<br/>

--------------------------------------------------------------------------------
# AD部分
  公司有整套数据中台源码出售，基于doris实现的数据仓库，支持PB级别是数据存储分析，功能模块如下：    
## 功能模块
###  1、数据源管理    
###  2、元数据管理
元模型、最新元数据 
###  3、数据标准管理
标准词根、标准字典、数据元、标准模型、发布、多版本维护、数据标准核对    
###  4、数据仓库管理
支持主题域、主题、数仓集群、维度建模、模型运维、模型审计、模型数据查看、数仓备份和恢复
###  5、数据质量
规则定义，任务执行，结果查看，统计分析，质量问题修复日志    
###  6、数据血缘
数据血缘，数据流向  
###  7、数据标签
标签对象、标签管理、置标任务、标签圈群、标签画像
###  8、数据服务
接口在线开发(支持通过JS脚本对数据进行处理后返回，支持动态SQL)，接口测试，接口发布，应用管理，应用授权    
##  9、资产目录 
目录编目，资产项授权，资产项查看，资产项申请    
###  10、数据集成
kettle调度，kettle 任务/转换 在线设计 ，datax任务在线构建 调度执行  drois多数据目录维护，简易ETL、FLINK 
###  11、数据可视化
数据集，报表管理，报表设计，报表查看
## 技术栈
后端：Java springboot2.7 springcloud/alibaba  mybatis plus hutool 等常见技术    
前端：vue  elementui  vite 等常见技术    
中间件：doris，mysql，redis，rabbitmq，minio，zookeeper。        
### 有演示环境和方案PPT，需要加V:abcd19920605
## 架构
![](./docs/img/jiagou.png)
# 本项目介绍正文开始

# 架构

![](./docs/img/di-framework.png)

--------------------------------------------------------------------------------

# 模块

* dataintegration-common : 公共模块
* dataintegration-group : 分组管理
* dataintegration-gateway : 服务网关
* dataintegration-project : 脚本管理
* dataintegration-run : 数据集成运行模块
* dataintegration-sso : sso单点登录模块
* dataintegration-sys : 系统管理模块
* dataintegration-model : 模型管理
* dataintegration-file-management : 文件管理
* dataintegration-ui : 前端vue模块

--------------------------------------------------------------------------------

# 功能特点

基于kettle实现的web版数据集成平台，致力于提供web可拖拽的数据集成平台。

其主要特点有：
* vue2+springCloud架构（后续支持vue3）
* 支持kettle本地引擎，后续扩展spark引擎
* 支持ftp/s3协议的文件读取

由于公司采用springcloud微服务架构开发整个数据中台产品，数据集成属于其中的一个子模块，所以暂时还是采用springcloud的架构进行开源，便于版本统一。

--------------------------------------------------------------------------------

# 用户界面截图

![home page](./docs/img/show-home.png)
![dag](./docs/img/show-dag.png)
![monitor](./docs/img/show-monitor.png)
![log](./docs/img/show-log.png)

--------------------------------------------------------------------------------

# 近期研发计划

新版也在同步研发中，后续会开放

--------------------------------------------------------------------------------

# 参与贡献

非常欢迎大家来参与贡献，贡献流程请参考：
TODO

--------------------------------------------------------------------------------

# 快速试用 Docker

可以参考：http://www.young-datafan.com/docs-data-integration/quick-start/installation-docker/. 这个文档部署演示

--------------------------------------------------------------------------------

# 如何构建
## 打包项目
```bash
mvn -B clean compile install -Prelease -Dmaven.test.skip=true -Dcheckstyle.skip=true
```
## 启动前置环境
* <a  href ="https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">Jdk1.8</a>
* <a  href ="https://www.mysql.com/">Mysql 5.7.+</a>
* <a  href ="https://docs.consulproject.org/docs/english-documentation/introduction/local_installation">consul</a>
* <a  href ="https://redis.io/">Redis</a>

### 创建数据库
> 使用数据库连接工具连接数据库，创建数据库dataintegration，将项目/install/sql/dataintegration.sql导入数据库中，初始化数据库文件。
### 服务启动
#### 修改配置
* dataintegration-gateway : 服务网关
* dataintegration-group : 分组管理
* dataintegration-project : 脚本管理
* dataintegration-run : 数据集成运行模块
* dataintegration-sso : sso单点登录模块
* dataintegration-sys : 系统管理模块
* dataintegration-model : 模型管理
* dataintegration-file-management : 文件管理

``` bash
 依次修改 application-local.yaml
 spring.cloud.consul.host: 127.0.0.1 ,ip改为启动的consul IP
 spring.cloud.consul.port: 8500 ,ip改为启动的consul 端口
 spring.datasource.url: jdbc:mysql://192.168.10.211:13306/ 修改启动的mysql url
 spring.datasource.username:  修改启动的mysql的账号
 spring.datasource.password:  修改启动的mysql的密码
 使用idea或者其他工具运行服务 dataintegration-**-provider
```

#### 启动前端ui
> 终端进入 dataintegration-ui 目录

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```
> 访问前端页面：http://127.0.0.1:8081/dataintegration-ui/#/  默认的用户是admin，默认的密码是Prime@2020

###



--------------------------------------------------------------------------------


## 版权

请参考 [LICENSE](https://gitee.com/fhs-opensource/data-center/blob/master/LICENSE) 文件.

--------------------------------------------------------------------------------

## 原项目链接

https://github.com/young-datafan-ooooo1/data-integration
