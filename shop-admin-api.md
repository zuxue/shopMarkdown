## 应用管理
#### 应用列表
GET
`domain + ?s=/admin/application.application/list`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| page | number | N | 页码数(不传默认1) | 5 |
| num | number | N | 每页条数(不传默认10) | 15 |
| search_name | string | N | 搜索关键字(应用名) |  |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.app_id | number | 应用ID |
| data.app_name | number | 应用名称 |
| data.app_status | number | 应用状态(0下架1上架2故障) |
| data.sales_num | string | 总销售 |
| data.sort | number | 排序(0-100值越大越靠前) |
| data.icon_id | number | 图标ID |
| data.icon_url | string | 图标url地址 |
| data.create_time | string | 数据创建时间 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "total": 1,
        "per_page": 10,
        "current_page": 1,
        "last_page": 1,
        "data": [
            {
                "app_id": 1,
                "app_name": "一个简单的应用名称",
                "sales_num": 0,
                "sort": 100,
                "status": 1,
                "create_time": "2022-03-01 15:32:25",
                "icon_id": 10145,
                "icon_url": "https://qywl-1308916128.cos.ap-shanghai.myqcloud.com/10001/20220228/8e89239c427dca4fecb3b5513a93aef5.jpg"
            }
        ]
    }
}
```
#### 应用详情
GET
`domain + ?s=/admin/application.application/info`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| app_id | number | Y | 应用ID | 1 |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.application | object |  |
| data.application.app_id | number | 应用ID |
| data.application.app_name | number | 应用名称 |
| data.application.summary | string | 简介 |
| data.application.detail | string | 详细描述 |
| data.application.app_status | number | 应用状态(0下架1上架2故障) |
| data.application.sales_num | string | 总销售 |
| data.application.is_suggest | number | 是否推荐(右上角的标签，0不推荐1推荐) |
| data.application.sort | number | 排序(0-100值越大越靠前) |
| data.application.icon_id | number | 图标ID |
| data.application.icon_url | string | 图标url地址 |
| data.application.del_status | number | 删除状态(0已删除1正常) |
| data.application.create_time | string | 数据创建时间 |
| data.application.update_time | string | 数据上次操作时间 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "application": {
            "app_id": 1,
            "app_name": "一个简单的应用名称",
            "summary": "这是一个短的简介",
            "detail": "应用的描述",
            "sort": 100,
            "is_suggest": 1,
            "status": 1,
            "sales_num": 0,
            "icon_id": 10145,
            "create_time": "2022-03-01 15:32:25",
            "update_time": "2022-03-01 16:21:55",
            "icon_url": "https://qywl-1308916128.cos.ap-shanghai.myqcloud.com/10001/20220228/8e89239c427dca4fecb3b5513a93aef5.jpg"
        }
    }
}
```


#### 新增应用
POST
`domain + ?s=/admin/application.application/create`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| app_name | string | Y | 应用名称(最长36个字符) | 这是一个应用名称 |
| summary | string | N | 应用简介(最长255个字符) | ​
 |
| detail | string | N | 应用描述(最长255个字符) | ​
 |
| app_status | number | N | 应用状态(0下架1上架2故障,不传默认0) | ​
 |
| sort | number | N | 排序(值越小越靠前,0-99999) |  |
| is_suggest | number | N | 推荐状态(0未推荐1推荐) |  |
| icon_id | number | Y | 应用图标 |  |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
#### 编辑应用
POST
`domain + ?s=/admin/application.application/update`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| app_id | Number | Y | 应用id |  |
| app_name | String | N | 应用名称(最长36个字符) | 这是一个应用名称 |
| summary | String | N | 应用简介(最长255个字符) | ​
 |
| detail | String | N | 应用描述(最长255个字符) | ​
 |
| app_status | number | N | 应用状态(0下架1上架2故障,不传默认0) | ​
 |
| sort | Number | N | 排序(值越小越靠前,0-99999) |  |
| is_suggest | Number | N | 推荐状态(0未推荐1推荐) |  |
| icon_id | Number | N | 应用图标 |  |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
#### 删除应用
POST
`domain + ?s=/admin/application.application/delete`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| appId | number | Y | 应用ID | 1 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
## 文章分类
#### 文章分类列表
GET
`domain + ?s=/api/article.category/list`
请求参数
   

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| page | number | N | 页码数(不传默认1) | 5 |
| num | number | N | 每页条数(不传默认10) | 15 |
| status | number | N | 展示状态(0隐藏1展示) |  |
| search_name | string | N | 查询关键字(分类名称) |  |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.list | array | 返回数据列表 |
| data.list.category_id | number | 分类ID |
| data.list.name | string | 分类名称 |
| data.list.status | number | 分类状态(1:展示0:隐藏) |
| data.list.sort | number | 排序(0-100值越大越靠前) |
| data.list.store_id | number | 商城ID |
| data.list.create_time | string | 数据创建时间 |
| data.list.update_time | string | 数据上次操作时间 |

```json
{
    "status": 200,
    "message": "success",
    "data": {
        "list": [
            {
                "category_id": 10004,
                "name": "桌子",
                "status": 1,
                "sort": 3,
                "store_id": 0,
                "create_time": "2022-02-22 18:35:50",
                "update_time": "2022-02-23 09:35:07"
            },
            {
                "category_id": 10007,
                "name": "网络",
                "status": 1,
                "sort": 3,
                "store_id": 0,
                "create_time": "2022-02-22 18:43:14",
                "update_time": "2022-02-22 18:43:14"
            }
        ]
    }
}
```
#### 文章分类详情
GET
`domain + ?s=/api/article.category/info`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| category_id | number | Y | 分类ID | 10001 |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.categoryInfo | object |  |
| data.categoryInfo.category_id | number | 分类ID |
| data.categoryInfo.name | string | 分类名称 |
| data.categoryInfo.status | number | 分类状态(1:展示0:隐藏) |
| data.categoryInfo.sort | number | 排序(0-100值越大越靠前) |
| data.categoryInfo.store_id | number | 商城ID |
| data.categoryInfo.create_time | string | 数据创建时间 |
| data.categoryInfo.update_time | string | 数据上次操作时间 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "categoryInfo": {
            "category_id": 10001,
            "name": "热卖",
            "status": 1,
            "sort": 100,
            "store_id": 10001,
            "create_time": "2022-02-12 14:30:17",
            "update_time": "2022-02-12 14:30:17"
        }
    }
}
```
#### 新增文章分类
POST
`domain + ?s=/api/article.category/create`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| name | string | Y | 分类名称 | 热卖 |
| status | number | Y | 分类状态(1:展示0:隐藏) | 1 |
| sort | number | Y | 排序(0-100值越大越靠前) | 50 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
#### 编辑文章分类
POST
`domain + ?s=/api/article.category/edit`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| category_id | number | Y | 文章分类ID | 10004 |
| name | string | Y | 分类名称 | 热卖 |
| status | number | Y | 分类状态(1:展示0:隐藏) | 1 |
| sort | number | Y | 排序(0-100值越大越靠前) | 50 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 500,
    "message": "非法请求",
    "data": []
}
```
#### 删除文章分类
POST
`domain + ?s=/api/article.category/delete`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| category_id | number | Y | 文章分类ID | 10004 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
## 文章
#### 文章列表
GET
`domain + ?s=/api/article.article/list`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| page | number | N | 页码数(不传默认1) | 5 |
| num | number | N | 每页条数(不传默认10) | 15 |
| category_id | number | N | 文章分类ID |  |
| status | number | N | 展示状态(0隐藏1展示) |  |
| search_title | string | N | 搜索关键字(标题) |  |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.total | number | 总条数 |
| data.data | object | 返回数据 |
| data.data.article_id | number | 文章ID |
| data.data.title | string | 文章标题 |
| data.data.category_id | number | 文章分类ID |
| data.data.image_id | number | 封面图ID |
| data.data.image_url | string | 封面图地址 |
| data.data.sort | number | 排序 |
| data.data.status | number | 状态 |
| data.data.virtual_views | number | 虚拟浏览量 |
| data.data.actual_views | number | 真实浏览量 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "total": 1,
        "data": [
            {
                "article_id": 10004,
                "title": "ASDGH",
                "category_id": 10002,
                "image_id": "10001/20220221/c3c702ccb804a3a76fe3d7cc020f4a71.png",
                "sort": 100,
                "status": 1,
                "virtual_views": 100,
                "actual_views": 0
            }
        ]
    }
}
```
#### 文章详情
GET
`domain + ?s=/api/article.article/info`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| articleId | number | Y | 文章ID | 10001 |

返回数据

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |
| data.articleInfo | object |  |
| data.articleInfo.article_id | number | 文章ID |
| data.articleInfo.title | string | 文章标题 |
| data.articleInfo.show_type | number | 展示类型(10:大图展示20:列表展示) |
| data.articleInfo.category_id | number | 文章分类ID |
| data.articleInfo.image_id | number | 封面图ID |
| data.articleInfo.image_url | string | 封面图地址 |
| data.articleInfo.content | string | 文章内容 |
| data.articleInfo.sort | number | 排序(值越小越靠前) |
| data.articleInfo.status | number | 展示状态 |
| data.articleInfo.virtual_views | number | 虚拟阅读量 |
| data.articleInfo.actual_views | number | 真实阅读量 |
| data.articleInfo.is_delete | number | 删除状态(0未删除1已删除) |
| data.articleInfo.store_id | number | 商城ID |
| data.articleInfo.create_time | string | 数据创建时间 |
| data.articleInfo.update_time | string | 数据上次操作时间 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "articleInfo": {
            "article_id": 10001,
            "title": "hot的香肠",
            "show_type": 10,
            "category_id": 10001,
            "image_id": 10072,
            "content": "&lt;p&gt;热卖热卖&lt;br/&gt;&lt;/p&gt;",
            "sort": 100,
            "status": 1,
            "virtual_views": 100,
            "actual_views": 0,
            "is_delete": 0,
            "store_id": 10001,
            "create_time": "2022-02-12 14:31:17",
            "update_time": "2022-02-12 14:31:17"
        }
    }
}
```
#### 新增文章
POST
`domain + ?s=/api/article.article/create`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| title | string | Y | 文章标题 | 热卖 |
| show_type | number | N | 展示类型(10:大图展示20:列表展示) | 20 |
| category_id | number | Y | 文章分类ID | 10004 |
| image_id | number | Y | 封面图片ID | 10001 |
| content | string | Y | 文章内容 |  |
| virtual_views | number | N | 虚拟浏览量 | 335 |
| status | number | Y | 展示状态(1:展示0:隐藏) | 1 |
| sort | number | Y | 排序(0-100值越大越靠前) | 50 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
#### 编辑文章
POST
`domain + ?s=/api/article.article/update`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| article_id | number | Y | 文章ID | 10001 |
| title | string | N | 文章标题 | 热卖 |
| show_type | number | N | 展示类型(10:大图展示20:列表展示) | 20 |
| category_id | number | N | 文章分类ID | 10004 |
| image_id | number | N | 封面图片ID | 10001 |
| content | string | N | 文章内容 |  |
| virtual_views | number | N | 虚拟浏览量 | 335 |
| status | number | N | 展示状态(1:展示0:隐藏) | 1 |
| sort | number | N | 排序(0-100值越大越靠前) | 50 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
#### 删除文章
POST
`domain + ?s=/api/article.article/delete`
请求参数

| 参数名 | 数据类型 | 是否必须 | 参数说明 | 示例 |
| --- | --- | --- | --- | --- |
| article_id | number | Y | 文章ID | 10004 |

返回信息

| 参数名 | 数据类型 | 参数说明 |
| --- | --- | --- |
| status | number | 请求状态 |
| message | string | 响应状态 |
| data | object | 返回数据 |

示例
```json
{
    "status": 200,
    "message": "success",
    "data": []
}
```
