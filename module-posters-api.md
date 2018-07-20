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
        	"author":"c
