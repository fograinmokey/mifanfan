## 海报集锦
+ 2018年7月6日
     + API初始化
+ Data
    + id (Long) - ID
    + title (String) - 标题
    + author (String) - 作者
    + coverPlan (String) - 封面图
    + postTime (Date) - 发布时间
    + enabled (int) - 是否可用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (Date) - 创建时间
    + modified (Date) - 修改时间    

### 增加 [POST] /posters
+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
    + title 必填  
    + author 
    + coverPlan 必填
    + postTime 
    + enabled
    + image
    + description

+ Request (application/json)

        {
        	"data":{
        	"title":"足球海报",
        	"author":"c罗",
        	"coverPlan":"CCCCCCCCCCCC.jpa",
        	"postTime":"2018-07-06",
    		"posterImages":[
    			{
    			"image":"clclclclclclclcl.jpa",
    		 	"description":"足球先生描述"
    			},
    			{
    			"image":"CLCLCLCLCLCLCLCLCL.jpa",
    		 	"description":"世界顶级球星描述"
    			}
    			]
        	 }
        }
+ Response 201 (application/json)

      {
        "data": {
            "id":8,
            "type":"posters"
        }
      }


### 修改 [PATCH] /posters/{id}

+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
    + title 必填  
    + author 
    + coverPlan  
    + postTime  
    + enabled 
    + image 
    + description 

+ Request (application/json)

      {
        	"data":{
        	"title":"测试",
        	"author":"cc罗",
        	"coverPlan":"nbCCCCCCCCCCCC.jpa",
        	"postTime":"2018-07-06",
    		"posterImages":[
    			{
    			"id":99,
    			"image":"111",
    		 	"description":"111"
    			},{
    			"id":101,
    			"image":"3333",
    			"description":"333"
    			},{
    			"image":"444",
    			"description":"444"
    			}
    			]
        	  }
        }    

+ Response (application/json)


### 查询海报集锦详情（客户端）[GET] /posters/{id}
+ Parameters
    + id 
    
+ Response 200 (application/json)
       
        {
            "data": {
                "id": 8,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-07-06 19:46:52",
                "modified": "2018-07-06 19:46:52",
                "title": "足球海报",
                "author": "c罗",
                "coverPlan": "CCCCCCCCCCCC.jpa",
                "postTime": "2018-07-06T00:00:00.000+0000",
                "posterImages": [
                    {
                        "id": 25,
                        "enabled": 1,
                        "creator": 0,
                        "modifier": 0,
                        "created": "2018-07-06 19:46:52",
                        "modified": "2018-07-06 19:46:52",
                        "type": 0,
                        "posterActivityId": 8,
                        "image": "clclclclclclclcl.jpa",
                        "description": "足球先生描述"
                    },
                    {
                        "id": 26,
                        "enabled": 1,
                        "creator": 0,
                        "modifier": 0,
                        "created": "2018-07-06 19:46:52",
                        "modified": "2018-07-06 19:46:52",
                        "type": 0,
                        "posterActivityId": 8,
                        "image": "CLCLCLCLCLCLCLCLCL.jpa",
                        "description": "世界顶级球星描述"
                    }
                ]
            }
        }


### 查询海报集锦列表 （客户端）[GET]  /posters?page[number]=1&page[size]=10 
    
+ Response 200 (application/json)

        {
            "meta": {
                "totalPages": 1,
                "totalElements": 8,
                "size": 10,
                "number": 1,
                "numberOfElements": 8,
                "first": true,
                "last": true,
                "sort": null
            },
            "links": {
                "self": "/posters?page[number]=1&page[size]=10",
                "first": "/posters?page[number]=1&page[size]=10",
                "last": "/posters?page[number]=1&page[size]=10"
            },
            "data": [
                {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-05 15:31:05",
                    "modified": "2018-07-05 15:31:05",
                    "title": "海报哈",
                    "author": "某某",
                    "coverPlan": "xxxxxxx.jpa"
                },
                {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-05 15:32:33",
                    "modified": "2018-07-05 15:33:31",
                    "title": "海报XX哈",
                    "author": "某X某",
                    "coverPlan": "xxxxxxx.jpa",
                    "postTime": "2018-07-05T00:00:00.000+0000"
                },
                {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 15:32:54",
                    "modified": "2018-07-06 15:32:54",
                    "title": "米饭星海报",
                    "author": "某某作者",
                    "coverPlan": "*********.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                },
                {
                    "id": 4,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 15:34:41",
                    "modified": "2018-07-06 15:34:41",
                    "title": "米饭星海报",
                    "author": "某某作者",
                    "coverPlan": "*********.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                },
                {
                    "id": 5,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 15:37:42",
                    "modified": "2018-07-06 15:37:42",
                    "title": "米饭星海报",
                    "author": "某某作者",
                    "coverPlan": "*********.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                },
                {
                    "id": 6,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 15:48:04",
                    "modified": "2018-07-06 16:38:36",
                    "title": "米饭星海报哈哈",
                    "author": "某某xx作者",
                    "coverPlan": "***||******.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                },
                {
                    "id": 7,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 16:46:09",
                    "modified": "2018-07-06 20:02:03",
                    "title": "足球海报",
                    "author": "c罗",
                    "coverPlan": "CCCCCCCCCCCC.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                },
                {
                    "id": 8,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2018-07-06 19:46:52",
                    "modified": "2018-07-06 19:46:52",
                    "title": "足球海报",
                    "author": "c罗",
                    "coverPlan": "CCCCCCCCCCCC.jpa",
                    "postTime": "2018-07-06T00:00:00.000+0000"
                }
            ]
        }


### 删除 [DELETE] /posters/{id}
+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+  Response 204























