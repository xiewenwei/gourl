
# GoURL 短链接服务

## 简要介绍

使用 Go 语言实现的一个短链接服务，Go 练手项目

## 核心功能需求：

* 登记 `url`，获取短链接
* 根据短链码获取原始 `url`
* 短链接访问跳转
* 系统安全控制，限定用户访问登记接口

## 扩展功能需求

* 提供访问计数，通过接口获取访问计数
* 提供后台管理功能，可以管理应用，短链接，查看访问统计

## 服务设计

### 接口设计

对外访问接口说明

* 登记 `url` 接口

'POST /short_urls'
post data
   url: your url
   token: your token
'GET /short_urls?url=<your escaped url>&token=<your token>'

example

request
  'GET /short_urls?url=http://www.boohee.com&token=testtoken'

response

```json
{
  url_code: "ef",
  short_url: "http://t.com/ef",
  first_add: true
}
```

* 根据短链码获取原始 `url` 接口

'GET /origin_urls?url_code=<short url code>'

example

request
  'GET /origin_urls?url_code=df'

response

```json
{
  url_code: "df",
  short_url: "http://t.com/df",
  origin_url: "http://www.boohee.com"
}
```

* 短链接访问跳转

"GET http://t.com/df"

response

redirect to "http://www.boohee.com"

### 系统设计

* 接口访问层
* 链接数据存储
* 短链码生成算法
* 访问计数
* 注册接口访问控制
* 后台管理

