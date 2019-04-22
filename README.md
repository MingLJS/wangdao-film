# wangdao-film

本项目为王道Java实战项目4——Meeting院线的父模块，只用作组织项目结构，除非有特殊情况，**不要提交任何变更到本仓库**

父模块：
[王道项目4——Meeting院线](https://github.com/ThasGit/wangdao-film)

网关模块：
[王道项目4——Meeting院线——API网关](https://github.com/ThasGit/wangdao-film-gateway)

5个网关模块与服务子模块的公共依赖接口：
1. [王道项目4——Meeting院线——影院管理公共接口子模块](https://github.com/ThasGit/wangdao-film-cinema-api)
2. [王道项目4——Meeting院线——影片管理公共接口子模块](https://github.com/ThasGit/wangdao-film-film-api)
3. [王道项目4——Meeting院线——用户管理公共接口子模块](https://github.com/ThasGit/wangdao-film-user-api)
4. [王道项目4——Meeting院线——支付管理公共接口子模块](https://github.com/ThasGit/wangdao-film-pay-api)
5. [王道项目4——Meeting院线——订单管理公共接口子模块](https://github.com/ThasGit/wangdao-film-order-api)

涉及的5个子模块均已做成git子模块，对应的github项目为：
1. [王道项目4——Meeting院线——影院管理子模块](https://github.com/ThasGit/wangdao-film-cinema)
2. [王道项目4——Meeting院线——影片管理子模块](https://github.com/ThasGit/wangdao-film-film)
3. [王道项目4——Meeting院线——用户管理子模块](https://github.com/ThasGit/wangdao-film-user)
4. [王道项目4——Meeting院线——支付管理子模块](https://github.com/ThasGit/wangdao-film-pay)
5. [王道项目4——Meeting院线——订单管理子模块](https://github.com/ThasGit/wangdao-film-order)

本次开发采用微服务形式，各子模块之间**不要有任何项目依赖的关系**，它们之间的接口调用只允许通过dubbo调用。

push的时候只需要push自己开发的子模块即可。

本地项目初始化：
1. 执行`git clone https://github.com/ThasGit/wangdao-film.git  --recursive`命令，将git项目克隆到本地，`--recursive`代表递归克隆子模块，不加这个命令得手动clone子模块，会很麻烦。
2. 打开`IDEA`,选择`File -> New -> Project From Existing Sources...`，选择父模块的pom文件，即`wangdao-film`模块的pom文件，这样将会初始化整个项目，包括附属的子模块。
3. 选择 `Settings -> Version Control`, 将父模块`wangdao-film`移除。这是因为`IDEA`对git子模块的支持不到位。每一个子模块都是独立的git仓库，在模块上右键选择`git`进行操作。
4. 参照`guns-rest`初始化自己模块的结构。

不要选择直接从`File -> New -> Project From Version Control -> Git`，它不会组织Maven项目结构。

任务初步分配：
1. 影院管理：6表4接口 刘浩然 谢陈成  徐梓淳 
2. 影片管理：8表4接口 朱明轩 范恩华 段晓慧 
3. 用户管理：1表6功能 谢陈成 

基础包`com.cskaoyan.wangdaofilm.` + `模块名`。

代码**不要全部放在自动生成的默认的`com.stylefeng.guns`下面**，`IDEA`对全限定名完全一致的类处理上有bug，可能你改了自己的一个类名，别人的模块中的相同类名的类也被跟着改掉。

另外spring扫包时，会扫描到其他模块下的相同包，如果包下还存在相同名称的类，会造成重复注入的问题。

包结构，参考guns：
```
com.cskaoyan.wangdaofilm.user
 -- common 模块无关的类或工具
      -- persistence 持久层，dao层及模型
 -- config 配置相关
 -- modular 模块相关
      -- 模块名
           -- controller 模块控制器
                 -- dto 表现层对象传输模型
           -- service 服务层
                 -- dto 服务层对象传输模型
```

网关模块和微服务子模块的公共接口和传输对象统一放在`wangdao-film-*-api`模块中，共同依赖。注意传输对象一定实现`java.io.Serializable`接口。

Dubbo暴露服务的接口设置为-1即可，自动选择端口。扫描包一定要配置`dubbo.scan.base-packages`，否则dubbo服务不会注册到zookeeper。

子模块因为因为依赖了`guns-core`模块，不得不启动`tomcat`容器，`server.port`同样设置为-1，以免多模块同时启动时端口冲突。

本地环境配置放在`application-local.yml`文件中，根据maven选定的`profile`会启用对应的spring环境。不要修改`application.yml`公共文件。

