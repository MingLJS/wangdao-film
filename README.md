# wangdao-film

本项目为王道Java实战项目4——Meeting院线的父模块，只用作组织项目结构，除非有特殊情况，**不要提交任何变更到本仓库**

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
3. 参照`guns-rest`初始化自己模块的结构。

不要选择直接从`File -> New -> Project From Version Control -> Git`，它不会组织Maven项目结构。

任务初步分配：
1. 影院管理：6 朱明轩 范恩华 刘浩然
2. 影片管理：8 谢陈成 段晓慧 徐梓淳 
3. 用户管理：1 徐梓淳 

具体任务安排以小组讨论结果为准
