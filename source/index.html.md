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


<h1 id="message"> 留言数据中心 </h1>

留言数据中心提供一个轻量级销售机会留言、投诉留言的数据服务及管理后台。留言数据中心只发布一个API，即新建留言的API。

## 新建留言

使用本API新建留言。

### HTTP Request

`POST /vdc-api/message`

### 数据

字段 | 类型 | 必须 | 描述
--------- | ------- | ------ | -----------
department | string |否 | 部门
product | string |否 | 产品
category | string |否 | 类型
name | string |否 | 姓名
company | string |否  | 公司
title | string |否 | 职务
email | string |否 | 电子邮箱
website | string|否  | 网站
extra | string |否 | 额外内容，由API调用者自由使用
clientId | string|否  | 客户编号
phone | string |否 | 电话
mobile | string |否 | 手机号
fax | string |否 | 传真
address | string|否  | 地址
zip | string |否 | 邮政编码
message | string|是  | 留言

```
{
 "product": "大家电",
 "category": "代理资格",
 "company": "上海第一电气连锁",
 "website": "www.yizhanyun.cn",
 "email": "info@yizhanyun.cn",
 "mobile": "1370xxxxxx",
 "message": "我公司希望代理贵公司的大家电。请尽快与我联系",
 "name": "武松",
 "title": "渠道经理"
}
```
