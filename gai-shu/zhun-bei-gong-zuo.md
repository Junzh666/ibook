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
* SSL证书：可以购买权匹配的专业ssl证书，也可以使用FreeSSL和阿里云的免费SSL证书。



{% hint style="info" %}
阿里云原来提供的免费证书为一年期限，现在调整为3个月，请注意更新证书。[公告链接](https://help.aliyun.com/zh/ssl-certificate/product-overview/notice-on-adjustment-of-service-policies-for-free-certificates)
{% endhint %}

## 防火墙相关



{% hint style="warning" %}
* 本文档为方便演示，将所有服务安装在同一台服务器上，正式环境不建议这么做。
* 大陆地区80、443端口需要备案后才可使用；如没有完成备案，需使用其他端口代替。
{% endhint %}

本架构所涉及到的端口如下，请根据实际情况选择是否对外开放：

<table data-header-hidden data-full-width="false"><thead><tr><th width="244.33333333333331"></th><th></th><th></th></tr></thead><tbody><tr><td>服务</td><td>端口</td><td>软件</td></tr><tr><td>ssh</td><td>22</td><td>ssh</td></tr><tr><td>https</td><td>44444</td><td>Roundcubemail</td></tr><tr><td>smtp</td><td>25</td><td>Postfix</td></tr><tr><td>submission</td><td>587</td><td>Postfix</td></tr><tr><td>pop3</td><td>110</td><td>Dovecot</td></tr><tr><td>pop3s</td><td>995</td><td>Dovecot</td></tr><tr><td>imap</td><td>143</td><td>Dovecot</td></tr><tr><td>imaps</td><td>993</td><td>Dovecot</td></tr><tr><td>https</td><td>44443</td><td>Rocket.Chat</td></tr><tr><td>https</td><td>44445</td><td>NextCloud</td></tr><tr><td>https</td><td>8888</td><td>GitLab</td></tr></tbody></table>



