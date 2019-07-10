
# PHP语法
* `$query->num_rows`:获取数据集中某个某个数据的行数
#### 登录/注册的逻辑
* 一,登录篇
	* 1.判断用户名是否存在
	* 2.如用户名存在则开始判断其密码是否正确
		* 2-1.如不存在则登陆失败
	* 3.判断密码是否正确,如密码和数据库里的不匹配,则登陆失败
		* 3-1.如匹配则登录成功

```
if ($query->num_rows == 0) { //1
    echo "the username wasn't exist"; //2-1
    return;
} else {
    while ($check = mysqli_fetch_array($query)) { //2
        if ($check) {
            if ($password == $check["password"]) { //3-1
                echo "login success";
                return;
            } else { //3
                echo "pwd error";
                return;
            }
        }
    }
}
```
* 二、注册篇


# MySQL数据库

* 一、基本语法:
	`F9` 运行SQL代码的键位
    `CREATE DATABASE “数据库名”;` 创建并命名一个新数据库
    `DROP DATABASE “数据库名”`;卸载目标数据库
    `DROP TABLE` `表名`;删除目标表
    `Now()` 在表中表现现在的时间
* 二、建立表格:
    ```
    CREATE TABLE `表名` (
      `id` INT(11) NOT NULL AUTO_INCREMENT,
      `username` VARCHAR(20) NOT NULL COMMENT '用户名',
      `password` VARCHAR(32) NOT NULL COMMENT '密码',
      `creat_time` DATETIME DEFAULT NULL COMMENT '创建时间',
      `update_time` DATETIME DEFAULT NULL COMMENT '更新时间',
      PRIMARY KEY (`id`)
    ) ENGINE=INNODB DEFAULT CHARSET=utf8;
    ```
* 三、表格中插入数据:
    ```
    INSERT INTO `数据库中已存在表名` (
    `若干字段-以逗号隔开`,) VALUE ('字段对应的值-也以逗号隔开');
    ```
    **↓如果是多人则`value`改成`values`**
    ```
    INSERT INTO `users` (
    `username`,`password`,`create_time`,`update_time`
    ) VALUES ('cxk123','cxknmsl','2019-06-03 10:20:35','2019-06-03 10:21:16'),
    ('nikki','nikki1206','2019-06-03 10:20:35','2019-06-03 10:21:16'),
    ('cxkFans','cxkF2019y01m01d','2019-06-03 10:20:35','2019-06-03 10:21:16'),
    ('sjfosjoejcie','asdfghjkl123456789','2019-06-03 10:20:35','2019-06-03 10:21:16'),
    ('howlongmybaby','15kilimetersss','2019-06-03 10:20:35','2019-06-03 10:21:16');
    ```
* 四、对已存在数据的处理方式:
	* 最基本查询方式:
    ```
    SELECT *(星号仅用于表内所有字段)或者`表内指定类名`  FROM `表名` WHERE `id` = 3;
    ```
    * 表内数据删除方式:
    ```
    DELETE FROM `users` WHERE `id` <> 2;
    ```
    * 修改数据的方法:
    ```
    UPDATE `表名` SET `字段名` = '值' WHERE 条件(`id` = 1),如果是多条件必须被同时满足,使用and与其相连;
    ```
    * 模糊搜索的方法:
    ```
    SELECT * FROM `users` WHERE `username` LIKE '%caixukun%';
    ```
    **↑模糊搜索的目标对象应该头尾都是百分符（%）**
    * And(和、与)和like的组合使用:
    ```
    SELECT * FROM `users` WHERE `id` > 1 AND `username` LIKE '%cai%';
    ```
    * Or(或者)的使用方式:
    ```
    SELECT * FROM `users` WHERE `id` = 1 OR `id` = 3;
    ```
    * where加括号在面对多种条件时的应用方式
    ```
    SELECT * FROM `users` WHERE (`id` >= 2 AND `username` LIKE '%cai%') OR `id` = 1 ;
    ```
    * 升/降序排序:
    ```
    SELECT * FROM `users` WHERE `id` > 0 ORDER BY `sort` ASC/DESC;
    ```
    **ORDER BY `字段名` ASC/DESC 表内排序**
    * 数据数量查询:
    ```
    SELECT COUNT(*) FROM `表名` WHERE `id` > 1;
    ```
    **COUNT:统计总条数,但是也可以加入任何条件**
    * 统计字段累加的总和
    ```
    SELECT SUM(`字段`) FROM `表名` WHERE `id` > 1;
    ```
    **SUM(`字段名`) 统计已存在目标字段的总和**
    * 分组统计
    ```
    SELECT COUNT(*),`字段` FROM `表名` WHERE `id` <> 0 GROUP BY `同第一字段`;
    ```
    **`Group by` 分组**
    * 关联查询
    ```
    SELECT * FROM `主表(存有用户最基本主句)` INNER JOIN `次表` ON `主表`.`id` = `次表`.`次表的关联ID`;
	```
    **`Inner join` 交集**
    * 关联查询-重心向左(右)
    ```
    SELECT * FROM `users` LEFT(RIGHT) JOIN `users_info` ON `主表`.`id` = `次表`.`此表的关联id`(位置调换);
    ```
    
    **(“=” 等于
    “>” 大于
    “<” 小于
    “>=” 大于等于
    “<=” 小于等于
    “<>” 不等于
    )**

