# ArangoDB 在线实验环境

## 软件简介

ArangoDB是一个多模型的开源数据库，具有用于文档，图形和键值的灵活数据模型。使用方便的类似SQL的查询语言或JavaScript扩展来构建高性能应用程序。如果需要，请使用ACID交易。水平和垂直缩放，只需点击几下鼠标。支持的数据模型可以在查询中进行混合，并允许ArangoDB成为数据请求的聚合点。

所属类别是数据库
## 软件官网

https://www.arangodb.com/
特点:

1.多功能

2.提供 Graph 储存方式

3.可扩展的 AQL 语言
## Dockerfile 使用方法

### 如何使用
启动ArangoDB实例

为了启动ArangoDB实例运行
```
unix> docker run -e ARANGO_RANDOM_ROOT_PASSWORD=1 -d --name arangodb-instance arangodb
```
将创建并启动arangodb docker实例作为后台进程。打印过程的标识符。默认情况下，ArangoDB在端口8529上侦听请求，并且映像包括EXPOSE 8529。如果链接应用程序容器，它将在链接的容器中自动使用。请参见以下示例。

为了让IP arango在运行时听：
```
unix> docker inspect --format '{{ .NetworkSettings.IPAddress }}' arangodb-instance
```
### 使用实例
为了从应用程序使用正在运行的实例，请链接容器
```
unix> docker run -e ARANGO_RANDOM_ROOT_PASSWORD=1 --name my-app --link arangodb-instance:db-link arangodb
```
这将使用具有名称的实例并将其arangodb-instance链接到应用程序容器中。应用程序容器将包含环境变量
```
DB_LINK_PORT_8529_TCP=tcp://172.17.0.17:8529
DB_LINK_PORT_8529_TCP_ADDR=172.17.0.17
DB_LINK_PORT_8529_TCP_PORT=8529
DB_LINK_PORT_8529_TCP_PROTO=tcp
DB_LINK_NAME=/naughty_ardinghelli/db-link
```
这些可以用于访问数据库。

## 资源链接

- https://www.arangodb.com/tutorials/
- https://www.arangodb.com/documentation/
- https://hub.docker.com/_/arangodb/
