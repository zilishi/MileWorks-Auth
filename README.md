# MileWorks-Auth - 基于OAuth2 \ JWT 认证授权模块  
研究现有基于Spring Cloud框架研究一段时间之后，其中整个框架的系统认证、授权模块是其中一大核心功功能模块。在前后端分离之后，这个功能在整个系统中是可以单独剥离，并且独立运行的。决定了整个系统资源使用、API调用的权限使用等等问题。

整理这套东西前期是研究了很多对应文章和代码之后总结的一套，并且是可以复用到任何微服务功能中去。

前期研究有代表性文章：
- [https://www.renren.io/guide](https://www.renren.io/guide)
- [https://segmentfault.com/a/1190000009164779](https://segmentfault.com/a/1190000009164779)
-  [http://blueskykong.com/2017/10/19/security1/](http://blueskykong.com/2017/10/19/security1/)

主流现在包括Java 、Go 语言中涉及Token相关的问题都会于JWT相关联处理。针对JWT相关的教程参考如下：  
-  [https://www.jdon.com/artichect/json-web-tokens.html](https://www.jdon.com/artichect/json-web-tokens.html)

大致流程如下：
![avatar](https://user-images.githubusercontent.com/1064859/42557268-943551c8-8520-11e8-9c38-e1c518cd6ed3.jpg)

其中在整个微服务中的定位：
![avatar](https://user-images.githubusercontent.com/1064859/42986178-32b3d7cc-8c27-11e8-9dd8-d216fc1bb962.png)


现在针对现有工程进行说明解释：
- 系统结构如下：
```
MileWorks-Auth
├─src
│  ├─main
│  │  ├─java
│  │  │  └─com
│  │  │      └─mileworks
│  │  │          └─authsys
│  │  │              ├─config : Oauth相关配置
│  │  │              ├─controller : API 入口
│  │  │              ├─exception
│  │  │              ├─model
│  │  │              │  └─audit
│  │  │              ├─payload : 数据传输相关
│  │  │              ├─repository
│  │  │              ├─security : JWT 和 Oauth相关业务等处理
│  │  │              ├─service
│  │  │              └─util 
│  │  └─resources : 资源配置相关
│  │      ├─db
│  │      └─static
│  │          └─static
│  │              ├─css
│  │              ├─js
│  │              └─media
│  └─test
│      └─java
│          └─com
│              └─mileworks
│                  └─authsys

```

针对每块核心功能做详细介绍:
