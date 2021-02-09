---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://yizhanyun.cn'>一站云</a>
  - 上海蓝伞科技有限责任公司
  -  <a href="https://beian.miit.gov.cn/">沪ICP备19035838号-6 </a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: false

code_clipboard: true
---

# 简介

欢迎使用一站云虚拟数据中心API。

每个虚拟数据中心API使用REST协议，遵循相同的安全认证方法和命名格式，返回状态码使用HTTP协议状态码。具体endpoint、方法、传递数据和响应数据，在每个endpoint文档中详细说明。

# 安全认证

> 使用JavaScript fetch API示例：

```JavaScript

const endpoint = 'https://yizhanyun/vdc-api/v1/message'

const requestOption = {
      method: 'POST', // *GET, POST, PUT, DELETE, etc.
      cache: 'no-cache',
      headers: {
        'Content-Type': 'application/json',
        'x-yz-vdc-id': 'a42f7e72-25b4-46b3-8b56-b3ca872e5bab`',
        'x-ns-token': 'ykxV_mz6bJu54EFn6bdoKiMZgS0',
      },
      body: JSON.stringify({

      }), // 每个API的数据
    }

const resp = await fetch(endpoint, option)

```

一站云虚拟数据中心API使用两个自定义的HTTP头，分别为`x-yz-vdc-id`，代表虚拟数据中心的ID，`x-yz-vdc-token`，代表访问该虚拟数据中心的token。您可以在每个虚拟数据中心的管理台获取虚拟数据中心ID，生成token，并设置token的权限。

一站云要求每个API请求均设置这两个头。

`x-yz-vdc-id: a42f7e72-25b4-46b3-8b56-b3ca872e5bab `

`x-yz-vdc-token: ykxV_mz6bJu54EFn6bdoKiMZgS0`

此外，还需要设置 `Content-Type`为 `application/json`。

<aside class="notice">
务必将示例中的<code>x-yz-vdc-id</code>与<code>x-yz-vdc-token</code>的值设为您的虚拟数据中心ID和token。
</aside>

# API服务器

一站云服务器为 `https://yizhanyun.cn/`


# 核心概念

## 虚拟数据中心类型

每类虚拟数据中心有一个独一无二的类型标识，以下简称`type`。

目前以上线的标准数据中心如下:

1. 文章中心 - `type: article`
2. 案例中心 - `type: cases`
3. 留言中西 - `type: message`
4. 图片中心 - `type: gallery`
5. 产品信息中心 - `type: product`

## 虚拟数据中心Schema

数据中心的字段定义及规范。

Schema决定了数据中心使用哪些字段，每个字段的类新，可能的取值。

一站云管理后台提供数据中心schema配置工具，定制数据。

## 虚拟数据中心分支

为了支持数据，特别是文章等类型数据的不同编辑状态，数据中心有不同的分支，以下简称`branch`。

目前支持三个分支:

1. `published` - 正式发布分支
2. `edit` - 修改中分支
3. `draft` - 草稿分支

根据数据中心特点，不是所有数据中心都有分支。标准数据中心中 `article` 、`product`和 `cases`具有三个分支。

留言中心和图片中心只有一个 `published`分支。

## 虚拟数据中心ID

每个虚拟数据中心有一个独一无二的ID，以下简称 `vid`，用于全系统唯一标识数据中心。

## 虚拟数据中心数据细胞Cell

每个虚拟数据中心的每条数据，被称为数据细胞，以下简称 `cell`，每个数据细胞有一个唯一的ID，以下如无特殊说明，`id`代指每个Cell的id。

每个数据中心的不同分支的细胞，id可能相同。同一数据中心、同一分支细胞，id不会重复。

# 标准API

## 获得数据中心Schema

### GET /vdc-api/v1/_schema/[type]

## 新建Cell

### POST /vdc-api/v1/_action/[type]/[branch]/[vid]

创建新的细胞。

目前仅留言中心支持通过API创建细胞。


## 搜索、列举数据

### POST /vdc-api/v1/_query/[type]/[branch]

## 按ID获得详细数据

### GET /vdc-api/v1/_cell/[type]/[branch]/[vid]/[id]
