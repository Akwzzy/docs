---
title: 备份迁移
description: 关于备份和迁移的最佳实践
---

:::info
在开始之前，我们推荐你先阅读 [《写在前面》](../getting-started/prepare.md) 的名词解释部分。
:::

## 备份

### 数据备份

目前 Halo 在后台的小工具中提供了数据导出的功能，此功能的作用为导出数据库的所有数据，格式为 `JSON`。通常可以作为切换数据库类型的时候使用。需要注意的是，此备份仅仅为备份数据，不包含其他诸如主题、附件等资料。如下图：

![halo-data-export.png](/img/halo-data-export.png)

点击右下角的备份按钮即可导出所有数据，之后点击备份文件的标题即可下载。

### 整站备份

通过 [《写在前面》](../getting-started/prepare.md) 的名词解释部分我们可以知道，Halo 的所有数据都是存放在当前用户目录的工作目录（.halo）下的（使用 MySQL 数据库除外，你还需要导出 MySQL 数据）。**所以我们备份整站的数据仅需备份这个目录即可**，不管你使用何种方式。不过，为了操作方便，我们也在后台的小工具中提供了备份整站数据的功能，和上面所说的数据备份一致，点击备份按钮即可打包工作目录文件夹。如下图：

![halo-workspace-export.png](/img/halo-workspace-export.png)

## 迁移

### 导入数据

此功能为导入上面所说的数据备份产生的数据文件（JSON 格式），并非整站备份的工作目录文件。需要注意的是，此功能仅在站点初始化的时候支持。如下图：

![halo-data-import.png](/img/halo-data-import.png)

上传文件之后，点击导入即可。

### 整站迁移

此操作通常用于迁移服务器，基于上面 **整站备份** 所说，Halo 的所有数据都是存放于当前用户目录的工作目录（.halo）下的。当然，这仅限于使用 **H2 Database** 的情况下，如果你使用的 MySQL，那么还需要手动导出 MySQL 数据。所以，我们迁移服务器仅仅需要将工作目录的备份文件上传到新服务器的用户目录下解压，然后按照 [《安装指南》](../getting-started/install/docker-compose.md) 重新安装即可。MySQL 用户还需要做的就是手动导出 MySQL 数据，并在新服务器上导入。