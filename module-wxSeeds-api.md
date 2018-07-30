+ 2018年5月24日
    + API初始化

## 文件上传
### 获取上传文件验证 (GET) [/upload] (本接口是support服务提供的，所以完整url为/support/upload)
+ Data
    + code (string) - 固定值
    + isPublic (int) - 固定值
    + time (long) - 时间戳
    + userId (long) - 当前用户id
    + key (string) - 验证串
+ Description
    + [MUST] Authenticated
+ Response 200 (application/json)

        {
          "data": {
            "isPublic": 1,
            "code": "20160725001",
            "time": 1527152862645,
            "userId": 1031,
            "key": "456c1c8ae1f5223527b0478219303145"
          }
        }
### 上传文件 (POST) [http://192.168.1.248/upload/image] 
+ Request (application/form-data)

        {
          "code": "20160725001",
          "isPublic": 1,
          "time": 1491885189308,
          "userId": 12,
          "key": "afb66afa0404f92ac4670f6f4a721779"
          "file": "avatar.jpg"
        }
+ Response 200 (application/json)

        {
              "code": 100,
              "message": null,
              "data": {
                  "url":"http://static.budee.com/iyyren/image/201704/11/1234/195238888195899392.jpg"
              },
              "error": null
          }

## 公众号管理
+ Data
    + articleSeedId (Long) - seed与article的seed表id对应表 
    + title (String) - 微信号名称
    + wechatId (String) - 微信号wechat_id
    + funcIntro (String) - 功能介绍
    + biz (String) - 公众号唯一识别符（唯一）
    + logo (String) - 公众号logo
    + accountType (int) - 订阅号0   服务号1
    + accountSubject (int) - 企业和个人
    + companyName (String) - 企业全称
    + businessRegNo (String) - 工商执照注册号
    + serviceTel (String) - 客服电话
    + companyType (String) - 企业类型
    + businessScope (String) - 经营范围
    + establishDate (date) - 企业成立日期
    + operatingPeriod (date) - 企业经营期限
    + region (String) - 地区
    + classify (String) - 分类
    + description (String) - 描述
    + updateRate (int) - 更新频率
    + language (int) - 0中文  1英文
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    
### 增加 [POST] /wxSeeds
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Parameters
    + articleSeedId
    + title 必填
    + wechatId 必填
    + funcIntro
    + biz
    + logo
    + accountType
    + accountSubject
    + companyName
    + businessRegNo
    + serviceTel
    + companyType
    + businessScope
    + establishDate
    + operatingPeriod
    + region
    + classify
    + description
    + updateRate
    + language
    + enabled
+ Request（application/json）

        {
            "data":{
                "title":"未来无限可能",
                "wechatId":"feiguohai123"
            }
        }
       
+ Response 201 (application/json)  

        {
          "data": {
            "id": 74,
            "type": "wxSeeds"
          }
        }
       
### 修改 [PATCH] /wxSeeds/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Parameters
    + articleSeedId
    + title 必填
    + wechatId 必填
    + funcIntro
    + biz
    + logo
    + accountType
    + accountSubject
    + companyName
    + businessRegNo
    + serviceTel
    + companyType
    + businessScope
    + establishDate
    + operatingPeriod
    + region
    + classify
    + description
    + updateRate
    + language
    + enabled
       
+ 修改Request 200（application/json）

        {
            "data":{
                "title":"我的未来无限可能",
                "wechatId":"feiguohai123",
                "biz":"woshiweiyibiaoshifu"
            }
        }
+  Response 200       


### 列表 [GET] /wxSeeds?filter[title:like]=%25Midifan%25&page[number]=1&page[size]=5&sort=-modified      
       
+ Parameters
  + id 
  + title
     + 查询示例：filter[title]=%25助手%25 （'%25'为'%'的转义） 
  + sort -modified(从新到旧) | modified(从旧到新)       
       
+ Response 200 (application/json)       

        {
          "meta": {
            "totalPages": 1,
            "totalElements": 1,
            "size": 5,
            "number": 1,
            "numberOfElements": 1,
            "first": true,
            "last": true,
            "sort": [
              {
                "direction": "DESC",
                "property": "modified",
                "ignoreCase": false,
                "nullHandling": "NATIVE",
                "descending": true,
                "ascending": false
              }
            ]
          },
          "links": {
            "self": "/wxSeeds?filter[title:like]=%Midifa%&sort=-modified&page[number]=1&page[size]=5",
            "first": "/wxSeeds?filter[title:like]=%Midifa%&sort=-modified&page[number]=1&page[size]=5",
            "last": "/wxSeeds?filter[title:like]=%Midifa%&sort=-modified&page[number]=1&page[size]=5"
          },
          "data": [
            {
              "id": 32,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "articleSeedId": 157,
              "title": "Midifan",
              "wechatId": "",
              "biz": "MjM5MTA1NjMwMA=="
            }
          ]
        }

### 删除 [DELETE] /wxSeeds/{id}
+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+  Response 204

## 微信文章管理
+ Data
   +  articleTopicId (long) - 与 article topics 表中对应的id
   +  seedId (long) 
   +  type (int) - 主题类型 0:图文，1：视频，2：音视频混合
   +  title (String) - 标题
   +  content (String) - 内容
   +  author (String) - 作者
   +  postDate (date) - 发布时间
   +  top (int) - 是否头条 0:是，1：否
   +  original (int) - 是否原创 0:否，1：是
   +  enabled (int) - 启用/禁用
   +  reviews (int) - 浏览量
   +  thumbsUp (int) - 点赞数
   +  seedTitle (String) - 公众号名
   +  creator (long) - 创建人
   +  modifier (long) - 修改人
   +  created (date) - 创建时间
   +  modified (date) - 修改时间

### 列表[GET]/topics?filter[seedId]=1&fields[Topics]=id,title,seedId,original,postDate,modified,created
+ Parameters
  + id 
  + seedId
  + title
     + 模糊查询示例：filter[title]=%25助手%25 （'%25'为'%'的转义） 
  + sort -modified(从新到旧) | modified(从旧到新)   
+ fields （必须返回的字段，不填则返回全部）
    + id 必须
    + title 必须
    + seedId 必须
    + original 必须
    + postDate 必须
    + modified 必须
    + created 必须
+ Response 200 (application/json)

        {
          "meta": {
            "totalPages": 6,
            "totalElements": 11,
            "size": 2,
            "number": 1,
            "numberOfElements": 2,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/topics?fields[Topics]=id,title,seedId,original,postDate,modified,created&filter[seedId]=1&page[number]=1&page[size]=2",
            "first": "/topics?fields[Topics]=id,title,seedId,original,postDate,modified,created&filter[seedId]=1&page[number]=1&page[size]=2",
            "next": "/topics?fields[Topics]=id,title,seedId,original,postDate,modified,created&filter[seedId]=1&page[number]=2&page[size]=2",
            "last": "/topics?fields[Topics]=id,title,seedId,original,postDate,modified,created&filter[seedId]=1&page[number]=6&page[size]=2"
          },
          "data": [
            {
              "id": 3812,
              "created": "2018-05-03 16:17:15",
              "modified": "2018-05-14 14:34:37",
              "seedId": 1,
              "title": "Tokyo热不热我不知道，我只知道最近黑胶热！",
              "postDate": "2018-04-20T14:48:43.000+0000",
              "original": 0,
              "reviews": 184,
              "thumbsUp": 0,
              "seedTitle": "AKAI雅佳乐园"
            },
            {
              "id": 3813,
              "created": "2018-05-03 16:17:16",
              "modified": "2018-05-22 18:49:34",
              "seedId": 1,
              "title": "贾老板用MPC在演唱会上帅了一把！",
              "postDate": "2018-04-18T07:23:07.000+0000",
              "original": 0,
              "reviews": 236,
              "thumbsUp": 1,
              "seedTitle": "AKAI雅佳乐园"
            }
          ]
        }

### 删除 [DELETE] /topics/{id}

+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+ Response 200

### 文章详情[GET] /topics/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Response 200 (application/json)

        {
        "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2018-04-27 16:37:11",
            "modified": "2018-05-23 14:31:11",
            "articleTopicId": 997312,
            "seedId": 2,
            "type": 0,
            "title": "知名无线音箱秘密提交上市申请 估值最高30亿美元",
            "titleHash": 5636961133973108502,
            "content": "内容",
            "author": "艾维音响网",
            "postDate": "2018-04-27T05:05:18.000+0000",
            "top": 0,
            "original": 0,
            "groupSign": 1527056915994,
            "reviews": 272,
            "thumbsUp": 2,
            "seedTitle": "艾维音响网"
        }
    }
