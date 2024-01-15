# 准备工作



{% hint style="warning" %}
本安装文档将包含所有办公套件的安装和配置过程，某些服务和组件安装和配置较为复杂且极易产生各种错误，请根据具体日志信息处理。
{% endhint %}

## 系统要求

* 主流Linux LTS发行版，本文中采用的是[ Ubuntu 22.04 LTS](https://ubuntu.com/download/server)。
* 大部分组件为docker方式安装，请提前安装好服务器的[docker](https://docs.docker.com/engine/install/ubuntu/)环境。
* 不建议使用ARM架构的服务器。

## 硬件要求

* 不建议将所有服务安装在同一台物理机上。
* 即使在硬件极端紧缺的情况下，也应该让iRedMail极其相关组件安装在一台独立的服务器上，以方便后期维护。
* 单应用的硬件最低配置为：2核4G

## 其他要求

* 域名：完全权限的顶级域名，本文以ppsuper.com为例。
* SSL证书：可以购买权匹配的专业ssl证书，也可以使用FreeSSL和阿里云的免费SSL证书\[^1]。

## 防火墙相关

本架构所涉及到的端口如下，请根据实际情况选择是否对外开放：

| 软件            | 服务         | 端口    |
| ------------- | ---------- | ----- |
| ssh           | ssh        | 22    |
| Roundcubemail | https      | 44444 |
| Postfix       | smtp       | 25    |
| Postfix       | submission | 587   |
| Dovecot       | pop3       | 110   |
| Dovecot       | pop3s      | 995   |
| Dovecot       | imap       | 143   |
| Dovecot       | imaps      | 993   |
| Rocket.Chat   | https      | 44443 |
| NextCloud     | https      | 44445 |
| GitLab        | https      | 8888  |



> \[^1]: 阿里云原来提供的免费证书为一年期限，自 起调整为3个月，请注意更新证书。[https://help.aliyun.com/zh/ssl-certificate/product-overview/notice-on-adjustment-of-service-policies-for-free-certificates](https://help.aliyun.com/zh/ssl-certificate/product-overview/notice-on-adjustment-of-service-policies-for-free-certificates)

