## 活动报名
+ 2018年6月10日
    + API初始化
+ 2018年6月12日
    + 添加微信登录接口

+ Data
    + ActivityRosters - 活动报名表
        + userId (long) - 用户id
        + phoneNumber (String) - 报名号码
        + fullName (long) - 姓名
        + email (String) - 邮箱
        + city (String) - 所在城市
        + position (String) - 职位
        + jobNature (String) - 工作性质
        + jobYears (String) - 工作年限
        + makingType (String) - 制作类型
        + hopeSkill (String) - 希望学到的技术
        + hopeOnsite (int) - 是否希望现场分析
        + remark (String) - 备注，不超过500个字符
        + smsCode (String) - 短信验证码
        + enabled (int) - 是否可用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (String) - 创建时间
        + modified (String) - 修改时间


### 获取图形验证码 [GET] /register/check.jpg?username=13126822398
+ Data
    + username 报名号码（即phoneNumber）
    
+ Response 200 (application/json)

### 获取短信验证码 [GET] /register/send_sms_code?username=13126822398&verifyCode=690568&description=commonly
+ Data
    + username 报名号码（即phoneNumber）
    + verifyCode 图形验证码
    + description 必填commonly
    
+ Response 204 (application/json)
+ Response 400 (application/json)

        {
          "errors": [
            {
              "code": "300",
              "detail": "图形验证码不正确，或未能获取验证码！"
            }
          ]
        }

### 提交报名信息 [POST] /activityRosters
+ Description
    + [MUST] Authenticated
+ Parameters
    + phoneNumber - 必填
    + fullName - 必填
    + email - 必填
    + city - 必填
    + position - 必填
    + jobNature - 必填
    + jobYears - 必填
    + makingType - 必填
    + hopeSkill - 必填
    + hopeOnsite - 必填
    + remark
    + smsCode

+ Request（application/json）

        {
            "data":{
                "email":"zysdsscw@126.com",
                "phoneNumber":"18611111111",
                "fullName":"张dada伟",
                "city":"北京",
                "position":"程序猿",
                "jobNature":"私企",
                "jobYears":"8年",
                "makingType":"nicai",
                "hopeSkill":"yes",
                "hopeOnsite":1,
                "smsCode":"690568"
            }
        }
+ Response 201 (application/json)

        {
          "data": {
            "id": 6,
            "type": "/activityRosters"
          }
        }
+ Response 400 (application/json)

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "该帐号已经报名了"
            }
          ]
        }
### 报名列表 [GET] /activityRosters?page[number]=1&page[size]=10
       
+ Parameters
    + page[number]=1
    + page[size]=10
      
       
+ Response 200 (application/json)  

        {
          "meta": {
            "totalPages": 1,
            "totalElements": 1,
            "size": 10,
            "number": 1,
            "numberOfElements": 1,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/activityRosters?page[number]=1&page[size]=10",
            "first": "/activityRosters?page[number]=1&page[size]=10",
            "last": "/activityRosters?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 6,
              "enabled": 1,
              "creator": 1031,
              "modifier": 1031,
              "created": "2018-06-10 15:18:27",
              "modified": "2018-06-10 15:18:27",
              "userId": 1031,
              "phoneNumber": "18611194890",
              "fullName": "张dada伟",
              "email": "zydsdw@126.com",
              "city": "北京",
              "position": "程序猿",
              "jobNature": "私企",
              "jobYears": "8年",
              "makingType": "nicai",
              "hopeSkill": "yes",
              "hopeOnsite": 1
            }
          ]
        }

### 是否报名/报名详情 [GET] /activityRosters/detail
       
+ Description
    + [MUST] Authenticated
       
+ Response 200 (application/json)  
+ 可根据alreadyRegistered字段判断是否已报名true/false:已报名/未报名

        {
          "data": {
            "alreadyRegistered": true,
            "detail": {
              "id": 6,
              "enabled": 1,
              "creator": 1031,
              "modifier": 1031,
              "created": "2018-06-10 15:18:27",
              "modified": "2018-06-10 15:18:27",
              "userId": 1031,
              "phoneNumber": "18611194890",
              "fullName": "张永伟",
              "email": "zyweicw@126.com",
              "city": "北京",
              "position": "程序猿",
              "jobNature": "私企",
              "jobYears": "四年",
              "makingType": "nicai",
              "hopeSkill": "yes",
              "hopeOnsite": 1
            }
          }
        }

### 微信登录（微信客户端） [GET] 
    https://open.weixin.qq.com/connect/oauth2/authorize?appid=wx20250f71156b4d41&redirect_uri=http://www.mifanxing.com/api/user/oauth/weChat?redirect=登录完成后想要跳转的页面&response_type=code&scope=snsapi_userinfo&state=wechatpub#wechat_redirect

+ Parameters
    + appid - 固定值wx20250f71156b4d41
    + redirect_uri - 需要urlencode编码
    + response_type - 固定值code
    + scope - 固定值snsapi_userinfo
    + state - 固定值wechatpub

### 微信登录 （非微信客户端）[GET]
    https://open.weixin.qq.com/connect/qrconnect?appid=wxd6142addd37f819a&redirect_uri=http://www.mifanxing.com/api/user/oauth/weChat?redirect=登录完成后想要跳转的页面&response_type=code&scope=snsapi_login&state=wechatweb#wechat_redirect
    
+ Parameters
    + appid - wxd6142addd37f819a
    + redirect_uri - 需要urlencode编码
    + response_type - 固定值code
    + scope - 固定值snsapi_login
    + state - wechatweb
