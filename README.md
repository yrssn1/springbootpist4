# springboot069视频网站系统的设计与实现

## 简介

本代码仅供学习参考使用

加QQ(**3055269939**)免费获取项目和论文

## 主要内容

### ***\*数据库\*******\*表\*******\*结构设计\****

本次程序开发选用的数据库管理工具是MySQL数据管理工具，使用它存放数据也需要创建程序对应的数据库文件，并命名刚创建的数据库文件，有了数据库也需要创建各种数据表来充实数据库，在数据表的创建中，不仅需要对数据表命名，也需要对数据表的字段进行设计，包括每个数据表里面需要设置的字段名称，字段对应的数据类型信息，字段的主键设置这个也是不可缺少的，因为每个数据表里面的主键就是标记着这个数据表跟其他数据表相区分的唯一标志。就相当于生活中的每个人都有姓名，但是上网搜索自己的名字，会发现全国上下有很多人的名字跟自己的名字一模一样，包括姓氏以及名字，区分每个人的唯一信息就是每个人的身份证号信息，主键在数据表里面也是起着这样的重要作用。下面就介绍本次开发的程序视频网站系统的数据表结构信息。

表4.1 视频分享评论表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| refid     | bigint(20)   | 否   |                   | 关联表id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| nickname  | varchar(200) | 是   | NULL              | 用户名   |
| content   | longtext     | 否   |                   | 评论内容 |
| reply     | longtext     | 是   | NULL              | 回复内容 |

表4.2 视频排名评论表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| refid     | bigint(20)   | 否   |                   | 关联表id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| nickname  | varchar(200) | 是   | NULL              | 用户名   |
| content   | longtext     | 否   |                   | 评论内容 |
| reply     | longtext     | 是   | NULL              | 回复内容 |

表4.3 交流论坛

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| title     | varchar(200) | 是   | NULL              | 帖子标题 |
| content   | longtext     | 否   |                   | 帖子内容 |
| parentid  | bigint(20)   | 是   | NULL              | 父节点id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| username  | varchar(200) | 是   | NULL              | 用户名   |
| isdone    | varchar(200) | 是   | NULL              | 状态     |

表4.4 留言板

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| userid    | bigint(20)   | 否   |                   | 留言人id |
| username  | varchar(200) | 是   | NULL              | 用户名   |
| content   | longtext     | 否   |                   | 留言内容 |
| reply     | longtext     | 是   | NULL              | 回复内容 |

表4.5 平台公告

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| biaoti    | varchar(200) | 是   | NULL              | 标题     |
| neirong   | longtext     | 是   | NULL              | 内容     |
| faburen   | varchar(200) | 是   | NULL              | 发布人   |
| faburiqi  | date         | 是   | NULL              | 发布日期 |
| tupian    | varchar(200) | 是   | NULL              | 图片     |

表4.6 视频分享

| 字段            | 类型         | 空   | 默认              | 注释         |
| --------------- | ------------ | ---- | ----------------- | ------------ |
| id (主键)       | bigint(20)   | 否   |                   | 主键         |
| addtime         | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间     |
| shipinmingcheng | varchar(200) | 是   | NULL              | 视频名称     |
| leixing         | varchar(200) | 是   | NULL              | 类型         |
| shipinjianjie   | longtext     | 是   | NULL              | 视频简介     |
| shipinneirong   | longtext     | 是   | NULL              | 视频内容     |
| bofangshizhang  | varchar(200) | 是   | NULL              | 播放时长     |
| zaixianshipin   | varchar(200) | 是   | NULL              | 在线视频     |
| faburiqi        | date         | 是   | NULL              | 发布日期     |
| fengmian        | varchar(200) | 是   | NULL              | 封面         |
| zhanghao        | varchar(200) | 是   | NULL              | 账号         |
| xingming        | varchar(200) | 是   | NULL              | 姓名         |
| sfsh            | varchar(200) | 是   | 否                | 是否审核     |
| shhf            | longtext     | 是   | NULL              | 审核回复     |
| thumbsupnum     | int(11)      | 是   | 0                 | 赞           |
| crazilynum      | int(11)      | 是   | 0                 | 踩           |
| clicktime       | datetime     | 是   | NULL              | 最近点击时间 |
| clicknum        | int(11)      | 是   | 0                 | 点击次数     |

表4.7 视频类型

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| leixing   | varchar(200) | 是   | NULL              | 类型     |

表4.8 视频排名

| 字段            | 类型         | 空   | 默认              | 注释     |
| --------------- | ------------ | ---- | ----------------- | -------- |
| id (主键)       | bigint(20)   | 否   |                   | 主键     |
| addtime         | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| shipinmingcheng | varchar(200) | 是   | NULL              | 视频名称 |
| leixing         | varchar(200) | 是   | NULL              | 类型     |
| shipinjianjie   | longtext     | 是   | NULL              | 视频简介 |
| bofangliang     | int(11)      | 是   | NULL              | 播放量   |
| bofangshizhang  | varchar(200) | 是   | NULL              | 播放时长 |
| zaixianshipin   | varchar(200) | 是   | NULL              | 在线视频 |
| fabuzhe         | varchar(200) | 是   | NULL              | 发布者   |
| faburiqi        | date         | 是   | NULL              | 发布日期 |
| fengmian        | varchar(200) | 是   | NULL              | 封面     |
| thumbsupnum     | int(11)      | 是   | 0                 | 赞       |
| crazilynum      | int(11)      | 是   | 0                 | 踩       |

表4.9 收藏表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| refid     | bigint(20)   | 是   | NULL              | 收藏id   |
| tablename | varchar(200) | 是   | NULL              | 表名     |
| name      | varchar(200) | 否   |                   | 收藏名称 |
| picture   | varchar(200) | 否   |                   | 收藏图片 |

表4.10 管理员表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| username  | varchar(100) | 否   |                   | 用户名   |
| password  | varchar(100) | 否   |                   | 密码     |
| role      | varchar(100) | 是   | 管理员            | 角色     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 新增时间 |

表4.11 用户

| 字段         | 类型         | 空   | 默认              | 注释     |
| ------------ | ------------ | ---- | ----------------- | -------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键     |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| zhanghao     | varchar(200) | 否   |                   | 账号     |
| mima         | varchar(200) | 否   |                   | 密码     |
| xingming     | varchar(200) | 否   |                   | 姓名     |
| xingbie      | varchar(200) | 是   | NULL              | 性别     |
| shouji       | varchar(200) | 是   | NULL              | 手机     |
| youxiang     | varchar(200) | 是   | NULL              | 邮箱     |
| shenfenzheng | varchar(200) | 是   | NULL              | 身份证   |