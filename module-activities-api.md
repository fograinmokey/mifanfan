## 最新活动
+ 2018年7月12日
    + API初始化

+ Data
    + id (Long) - ID
    + title (String) - 标题
    + description (String) - 描述
    + conPlan (String) - 封面图
    + status (int) - 活动状态 0：待开始， 1：正在进行(默认)，  2：已结束
    + startDate (Date) - 日程开始时间
    + endDate (Date) - 日程结束时间
    + activityType (int) - 活动类型 0：线上活动，1:线下活动
    + banner (String) - 横幅图
    + activityLocation (String) - 活动地点，逗号隔开的
    + isBlank (int) - 是否为外链接 0：否，1：是
    + content (String) - 内容
    + blank (String) - 来源URL(外链接)
    + enabled (int) - 启用/禁用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (Date) - 创建时间
    + modified (Date) - 修改时间

### 增加 [POST] /activities

+ Description 
     + [MUST] authenticated
     + [MUST] ROLE_ADMIN 

+ Parameters
    + title 必填
    + description 必填
    + conPlan 必填
    + startDate 必填
    + endDate 必填
    + banner 
    + activityType 
    
+ Request (application/json)

        {
        	"data":{
        	"title":"第十五届“录音艺术大师班”盛大开幕",
        	"description":"2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
        	"coverPlan":"kaimushituqq.jpa",
        	"startDate":"2018-07-09",
        	"endDate":"2018-07-11",
        	"banner":"bannerhahahaxx.jpg",
        	"content":"莫非长大就意味着一心只为自己考虑而拒绝理..",
        	"blank":"",
        	"activitiesSponsor":[
        		{
        			"logo":"mifanxinglogo.jpa",
        		 	"sponsor":"米饭星科技发展有限公司"
        		},
        		{
        			"logo":"budeelogo.jpa",
        		 	"sponsor":"宝迪科技发展有限公司"
        		}
        	 ],
        	 "locations":[
        	 		"北京市",
        	 		"天津市",
        	 		"上海市"
        	 	]
        	 }
      }

+ Response 201 (application/json)

        {
        "data": {
                "id": 1,
                "type":"activities"
            }
        }

### 修改 [PATCH] /activities/{id}

+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
    + title 必填
    + description 必填
    + conPlan 必填
    + startDate 必填
    + endDate 必填
    + banner 
    + activityType 


+ Request (application/json)

        {
    	"data":{
    	"title":"@@第十五届“录音艺术大师班”盛大开幕",
    	"description":"@@2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
    	"coverPlan":"@@kaimushituqq.jpa",
    	"startDate":"2018-07-09",
    	"endDate":"2018-07-11",
    	"banner":"@@bannerhahahaxx.jpg",
    	"activityLocation":"",
    	"content":"第十五届“录音艺术大师班",
    	"blank":"",
    	"activitiesSponsor":[
    		{
    			"logo":"mifanxinglogo.jpa",
    		 	"sponsor":"阿里巴巴发展有限公司"
    		},
    		{
    			"logo":"budeelogo.jpa",
    		 	"sponsor":"腾讯科技发展有限公司"
    		},
    		{
    			"id":111,
    			"logo":"xxxxxxxxx.jpa",
    		 	"sponsor":"百度科技发展有限公司"
    		}
    	 ],
    	 "locations":[
    	 	"青岛市",
     		"杭州市",
     		"深圳市",
     		"郑州市"
    	 	]
    	 }
      }

+ Response 200 (application/json)

### 查询活动列表详情（客户端） [GET] /activities/{id}
+ Parameters
    + id 
    
+ Response (application/json)

        {
        "data": {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2018-07-12 11:21:10",
            "modified": "2018-07-12 14:33:55",
            "title": "@@第十五届“录音艺术大师班”盛大开幕",
            "description": "@@2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
            "coverPlan": "@@kaimushituqq.jpa",
            "status": 1,
            "startDate": "2018-07-09T00:00:00.000+0000",
            "endDate": "2018-07-11T00:00:00.000+0000",
            "activityType": 0,
            "banner": "@@bannerhahahaxx.jpg",
            "activityLocation": "",
            "isBlank": 0,
            "content": "第十五届“录音艺术大师班",
            "blank": "",
            "activitiesSponsor": [
                {
                    "logo": "mifanxinglogo.jpa",
                    "sponsor": "米饭星科技发展有限公司"
                },
                {
                    "logo": "budeelogo.jpa",
                    "sponsor": "腾讯科技发展有限公司"
                },
                {
                    "logo": "shujutang.jpa",
                    "sponsor": "百度科技发展有限公司"
                }
            ]
        }
    }

### 查询活动列表 （客户端） [GET]  /activities?page[number]=1&page[size]=5&sort=-modified

+ Parameters

  + sort -modified(从新到旧) | modified(从旧到新)      
 
+ Response 200 (application/json)
    
        {
        "meta": {
            "totalPages": 1,
            "totalElements": 4,
            "size": 5,
            "number": 1,
            "numberOfElements": 4,
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
            "self": "/activities?sort=-modified&page[number]=1&page[size]=5",
            "first": "/activities?sort=-modified&page[number]=1&page[size]=5",
            "last": "/activities?sort=-modified&page[number]=1&page[size]=5"
        },
        "data": [
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-07-12 11:21:10",
                "modified": "2018-07-12 14:33:55",
                "title": "@@第十五届“录音艺术大师班”盛大开幕",
                "description": "@@2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
                "coverPlan": "@@kaimushituqq.jpa",
                "status": 1,
                "startDate": "2018-07-09T00:00:00.000+0000",
                "endDate": "2018-07-11T00:00:00.000+0000",
                "activityType": 0,
                "banner": "@@bannerhahahaxx.jpg",
                "activityLocation": "",
                "isBlank": 0,
                "content": "第十五届“录音艺术大师班",
                "blank": ""
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-07-12 11:52:40",
                "modified": "2018-07-12 11:52:40",
                "title": "!!!第十五届“录音艺术大师班”盛大开幕",
                "description": "!!2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
                "coverPlan": "!!kaimushituqq.jpa",
                "status": 1,
                "startDate": "2018-07-09T00:00:00.000+0000",
                "endDate": "2018-07-11T00:00:00.000+0000",
                "activityType": 1,
                "banner": "!!bannerhahahaxx.jpg",
                "activityLocation": "河北省, 陕西省, 浙江省, 福建省",
                "isBlank": 1,
                "content": "",
                "blank": "http://www.mifanxing.com/"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-07-12 11:39:46",
                "modified": "2018-07-12 11:39:46",
                "title": "!!!第十五届“录音艺术大师班”盛大开幕",
                "description": "!!2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
                "coverPlan": "!!kaimushituqq.jpa",
                "status": 1,
                "startDate": "2018-07-09T00:00:00.000+0000",
                "endDate": "2018-07-11T00:00:00.000+0000",
                "activityType": 0,
                "banner": "!!bannerhahahaxx.jpg",
                "activityLocation": "河北省, 陕西省, 浙江省, 福建省",
                "isBlank": 0,
                "content": "!!莫非长大就意味着一心只为自己考虑而拒绝理..",
                "blank": ""
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-07-12 11:21:54",
                "modified": "2018-07-12 11:21:54",
                "title": "第十五届“录音艺术大师班”盛大开幕",
                "description": "2018年7月9日上午9:00，第十五届“录音艺术大师班”在中国传媒大学400人报告厅隆重举行",
                "coverPlan": "kaimushituqq.jpa",
                "status": 1,
                "startDate": "2018-07-09T00:00:00.000+0000",
                "endDate": "2018-07-11T00:00:00.000+0000",
                "activityType": 0,
                "banner": "bannerhahahaxx.jpg",
                "activityLocation": "河南省, 陕西省, 浙江省, 福建省",
                "isBlank": 0,
                "content": "莫非长大就意味着一心只为自己考虑而拒绝理..",
                "blank": ""
            }
        ]
      }

### 删除 [DELETE] /activities/{id}
+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+  Response 204

