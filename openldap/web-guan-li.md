---
description: OpenLDAP会在iRedMail安装过程中自动安装。
---

# Web管理

## phpldapadmin

phpLDAPadmin是一个基于Web的LDAP客户端，它小巧且易于部署，这里使用docker的方式部署。

创建docker-compose.yml文件：

{% tabs %}
{% tab title="docker-compose.yml" %}
```yaml
version: "3"
services:
  phpldapadmin:
    container_name: phpldapadmin-single
    image: osixia/phpldapadmin:0.9.0-amd64
    restart: always
    ports:
      - 8099:80
    volumes:
      - /etc/localtime:/etc/localtime
    extra_hosts:
      - "host.docker.internal:host-gateway"

    environment:
      - PHPLDAPADMIN_LDAP_HOSTS=host.docker.internal
      - PHPLDAPADMIN_HTTPS=false
    deploy:
      resources:
        limits:
           memory: 1G
        reservations:
           memory: 256M
```
{% endtab %}
{% endtabs %}

创建容器：`docker compose up -d`

打开浏览器，输入地址：`http://<ip>:8099` 访问LDAP管理页面。

{% hint style="warning" %}
OpenLDAP不建议暴露在公网，请从内网访问和管理。
{% endhint %}
