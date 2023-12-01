---
title: "liquibase使用指导"
date: 2023-12-01T21:42:30+08:00
draft: false
---

liquibase.properties文件使用说明

以OpenGauss为例：

```properties
changeLogFile=changelog.xml
liquibase.command.url=jdbc:opengauss://${ip}:${port}/${db}?currentSchema=${schema}
liquibase.command.username: ${user}
liquibase.command.password: ${password}
driver: org.opengauss.Driver
```