---
title: Spring-Cloud基础微服务搭建(springboot2)
date: 2019-10-20 17:15:54
categories:
- Java
tags:
- spring-cloud
- 微服务
- 框架搭建
---

### 目录
* [1.缘由](#1-缘由)
* [2.目的](#2-目的)
* [3.具体实施](#3-目的)
    * [3.1 事前准备](#3-1事前准备)
    * [3.2 实施并验证](#3-2实施并验证)
		* [3.2.1 使用maven打包各服务](#3-2-1使用maven打包各服务)
		* [3.2.2 按照一定顺序启动各服务](#3-2-2按照一定顺序启动各服务)
* [4.相关说明](#4-相关说明)
* [5.FQA](#5-FQA)

## 1.缘由

之前写过springboot1的简单服务搭建，这次完善一下springboot2的搭建方式。

之前写的springboot1是采用两台虚拟机来做的，本次使用单机不同端口来做，可用于测试环境。需要多节点的可以移步[springboot1](https://fiendoghx.github.io/2019/10/16/Spring-Cloud%E5%9F%BA%E7%A1%80%E5%BE%AE%E6%9C%8D%E5%8A%A1%E6%90%AD%E5%BB%BA/)

## 2.目的

能够根据文档搭建一套简单的微服务框架，并成功访问具体微服务。

## 3.具体实施

spring-boot版本：2.1.9.RELEASE

## 3.1事前准备

[Jdk8](https://www.oracle.com/technetwork/java/archive-139210.html)
* 开发环境工具：
[maven3+](https://maven.apache.org/) \ [Git](https://git-scm.com/)
* spring-cloud-frame工程: 
[下载demo工程](https://github.com/fiendoghx/spring-cloud-frame/tree/base-springboot2)

PS: demo工程配置了哪些内容：
1. 网关服务和具体服务访问eureka注册中心Security用户名密码校验
2. 服务里的负载ribbon超时重试，以及hystrix熔断配置，以及短路配置
3. 网关服务的总连接数，路由连接数及采用策略配置
4. 各服务于注册中心的心跳和续约时间，超期及时剔除服务配置
5. 配置了logback日志info于warn、error分开按日期存放

服务器以及构建工具的事前准备不在本文讨论范围，请自行搜索准备

## 3.2实施并验证

### 3.2.1使用maven打包各服务

```
#打包注册中心Eureka:
cd <下载的目录>/spring-cloud-frame/base-eureka
mvn install
#打包网关Zuul
cd <下载的目录>/spring-cloud-frame/base-zuul
mvn install
#打包HelloWorld服务
cd <下载的目录>/spring-cloud-frame/service-helloworld
mvn install
```

### 3.2.2 按照一定顺序启动各服务

java -jar base-eureka-1.0.jar
java -jar base-gateway-1.0.jar
java -jar service-helloworld-1.0.jar

### 3.2.3 访问接口验证

直接访问接口 http://127.0.0.1:13001/helloworld

通过gateway网关访问接口 http://127.0.0.1:12002/SERVICE-HELLOWORLD/helloworld


