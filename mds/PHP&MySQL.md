
# PHP语法
* `$query->num_rows`:获取数据集中某个某个数据的行数
## PHP语言格式:
    * PHP文件必须`<?php`开头
    * 每行代码必须以`;`结束,`if`等有固定格式的除外
    * `.`两个不同的字符串或者变量连在一起
    * `echo` 输出字符串
		* PHP变量定义及使用方式:
		```
        $preCure = “hanaNono”;
        echo $preCure;
		```

## 数据库建立:
* 1.基字符集:utf8
* 2.数据库排序规则:utf8_general_ci


## PHP的常用字符串函数
**字符串(或者变量是字符串)之间以小数点辅以空格连接**
`echo "<br/>";`换行
`echo strlen(美分符开头的变量名);`字符串长度计算
`echo substr($str, 0, 5);`字符串截取(开头是变量名,中间是开始位置,最后是截取长度)
`echo strpos($str, "world");`搜索字符串起始位置(变量名,所要搜索的字符串)
`$自定义变量名 = explode(" ", $str);`把字符串按分割符 分割成数组
`var_dump( explode(" ", $str) );`打印数组和字符串的内容并显示其长度和类型
`echo substr($lauguage, 0, strpos($lauguage, $search));`截取某段字符串之前的值
`$message = array();`定义空数组
`$php1 = count($php12);`数组长度
`$message = array("username" => "wasl", "age" => 18, "sexy" => "Male");`键名自定义数组
`echo $arr2["username"];`输出数组对应的键名的值
`array_push($numArray, 7);`向对应数组的末尾推入一个值
`$pop = array_pop($numArray);`把指定数组的最后一位推出并赋值于指定变量
`$mes["age"] = 20;`给数组中直接给新添加的索引赋值
`$lan = implode(" ", $lan);`把数组按指定分割符合并成字符串
```
if (!$boolean) {
    echo 1;
} else {
    echo 0;
}
```
**↑PHP的逻辑判断结构**
(**!=变量的boolean值的反义词↑**);
**`Boolean`:true&false**
```
define("NAME", "Lala");
define("FIRSTNAME", "Hagomoro");
echo NAME;
echo FIRSTNAME;
```
**↑宏定义:将一个值赋予一个变量以用于全局.**
(**宏定义中设定的变量名要全部大写,后面的值可以小写↑**)
* 面向对象编程的三大重要概念:
    * 封装性：封装是一种信息隐蔽技术，它体现于类的说明，是对象的重要特性。封装使数据和加工该数据的方法（函数）封装为一个整体，以实现独立性很强的模块，使得用户只能见到对象的外特性（对象能接受哪些消息，具有那些处理能力），而对象的内特性（保存内部状态的私有数据和实现加工能力的算法）对用户是隐蔽的。封装的目的在于把对象的设计者和对象的使用者分开，使用者不必知晓行为实现的细节，只须用设计者提供的消息来访问该对象。
    * 继承性：继承性是子类自动共享父类之间数据和方法的机制。它由类的派生功能体现。一个类直接继承其它类的全部描述，同时可修改和扩充。继承具有传递性。继承分为单继承（一个子类只有一父类）和多重继承（一个类有多个父类）。类的对象是各自封闭的，如果没继承性机制，则类对象中数据、方法就会出现大量重复。继承不仅支持系统的可重用性，而且还促进系统的可扩充性。
    * 多态性：对象根据所接收的消息而做出动作。同一消息为不同的对象接受时可产生完全不同的行动，这种现象称为多态性。利用多态性用户可发送一个通用的信息，而将所有的实现细节都留给接受消息的对象自行决定，如是，同一消息即可调用不同的方法。例如：Print消息被发送给一图或表时调用的打印方法与将同样的Print消息发送给一正文文件而调用的打印方法会完全不同。多态性的实现受到继承性的支持，利用类继承的层次关系，把具有通用功能的协议存放在类层次中尽可能高的地方，而将实现这一功能的不同方法置于较低层次，这样，在这些低层次上生成的对象就能给通用消息以不同的响应。在OOPL中可通过在派生类中重定义基类函数（定义为重载函数或虚函数）来实现多态性。

## PHP本地根目录查询
    * 1.打开PHPStudy
    * 2.“其他选项菜单”
    * 3.“网站根目录”
    * 4.Localhost/127.0.0.1
    * 5.Phpinfo.php

##PHP事物设定/定义某类

```
class Test {
    public $age;
    private $sex;
}
```
**↑关键词class开头,其类名称必须首字母大写，然后加空格花括号**

* class下可用定义属性和方法:
`public`:公开,可外部调用和内部使用,方法`(class) public function 信息名`
`private`:仅自己使用(私有),方法同上
`protected`:仅自己使用和继承(保护),方法同上
```
public function setAge($age){
    $this->age = $age;
}
private function setSex($sex){
    $this->sex = $sex;
    return $this->sex;
}
protected function setName($name){
    $this->name = $name;
    return $this->name;
}
```
```
public function makePerson($age, $sex, $name){
    $personAge = $this->setAge($age);
    $personSex = $this->setSex($sex);
    $personName = $this->setName($name);
    $person = array("age" => "", "sex" => "", "name" => "");
    $person["age"] = $personAge;
    $person["sex"] = $personSex;
    $person["name"] = $personName;
    return $person;
}
```
`makePerson`:一个公开创造虚拟人物的办法
`$this`: 一个类在其内部调用自己的方法和属性的时候,所使用的一个变量

```
$obj->setAge(30);
echo $obj->age;
```
**↑调用公开class的办法**

```
$obj = new Test();
echo $obj->age;
```
**↑外部调用public信息的方式**
`new`:实例化一个类

`$_GET["test"];`
**↑从浏览器的GET方式所获得的字符串**
**↓使用方式**:
var_dump($_GET["test"]);
然后:
```
http://localhost/object.php(分开看)?test=任意要输入的字符串
```
`$_POST["name"];`
**↑以POST方式所获得的字符串**
使用方式是Postman
两者区别:POST提交的信息不会在浏览器的网址栏显示


`require` 要求、包括;如果要引用的文件不存在,则抛出异常程序结束
用法:
```
require "./Persona.php";
```
**↑你所要引用的文件的路径**
`./` 当前文件的相对路径


`include` 也是包括;如果要引用的文件不存在,则弹出相应警告，然后继续,一般用于框架中的公共模块
**↓用法**:
```
include "./Person.php";
```
**↑你所要引用的文件的路径**
`./` 当前文件的相对路径

其相同点是引用的文件可以直接使用.
```
require "./includeString.php";
echo $name;
```
**↑此变量name来自名为includeString的php文件**

**PHP变量名定义规范:
不能以特殊符号和非现代英文26字母以外的文字命名和不能以数字开头(一般情况下尽量不用).**

* 怎么定义函数:
* 函数名一般为自定义，以function开头，例子如下:
    ```
    function 自定义函数名($赋值形式参数, $未赋值形式参数) {
    //函数代码逻辑,此为函数逻辑的代码,注释是不会运行,用于让开发者们在开发过程中更好理解;
    }
    ```
    * 实参:实际参数调用此函数所传的参数，是一个有类型的变量参数
    * 形参:形式参数只为实参存在，接受函数参数的变量。

## Php在mySQL中获取数据的方式

### 语法解释
	    ```
    $host = "地址";
    $user = "用户名";
    $password = "密码";
    $database = "数据库名";
    try {
        $connect = mysqli_connect($host, $user, $password, $database);
        var_dump(mysqli_connect_errno());
        var_dump($connect);
    $sql = "select * from `users` where `id` > 0";
    $result = mysqli_query($connect, $sql);
    var_dump($result);
    echo "<br/>";
    while ($row = mysqli_fetch_array($result)) {
        echo $row['id'];
        echo "<br/>";
        echo $row['username'];
        echo "<br/>";
        echo $row['password'];
        echo "<br/>";
        echo $row['sex'];
        echo "<br/>";
    }
    mysqli_close($connect);
    } catch (ErrorException $e) {
        echo $e->getMessage();
    }
    ```
    * **例内语法解释↑:**
    	* Mysqli_connect_Errno(error number) 错误代码
        * Mysqli_Query 执行
        * Mysqli_Fetch_array 从结果集中获取数据并将其变成数组,通常配合while使用
* **当字符串内需要使用变量时，即用{},也就是花括号括起来,且如果是字符串,还需要单引号引起来↓**
    ```
    $sql = "update `users` set `password` = ‘{$pwd}’ where `id` > 0";
    ```

* 与前端结合后的后端资料的交互方式
     * date(“Y-m-d H:i:s”); 当前时间
     * Y:year
     * m:mouth
     * d:day
	 * **(Y,m,d用"-"接合然后位于左边,H,i,s用":"接合然后位于右边,但两边相距一个空格)**
     * H:hour
     * i:minute
     * s:second

     * **例子↓**

    ```

    $host = "127.0.0.1";
    $user = "root";
    $password = "root";
    $database = "mall";
    $connect = mysqli_connect($host, $user, $password, $database);
    $username = $_POST["username"];
    $password = $_POST["password"];
    $mobile = $_POST["mobile"];
    **//$nowTime = date("Y-m-d H:i:s");//**
    $sql = "insert into `users` (`username`, `password`, `sex`, `create_time`, `update_time`) value ('{$username}', '{$password}', 'man', '{$nowTime}', '{$nowTime}')";
    echo $sql;
    $query = mysqli_query($connect, $sql);

    echo "success";
    mysqli_close($connect);
    ```
* **`die();` 强制结束其程序↓**
    ```
    $search = "select * from `users` where `username` = '{$username}'";
    $query = mysqli_query($connect, $search);
    if ($query->num_rows > 0) {
        while ($sleACT = mysqli_fetch_array($query)) {
            if ($sleACT) {
                echo "<br/>";
                echo "username is created or used";
                die();
            }
        }
    } else {
        $sql = "insert into `users` (`username`, `password`, `sex`, `create_time`, `update_time`) value ('{$username}', '{$password}', 'man', '{$nowTime}', '{$nowTime}')";
        echo $sql;
        $query = mysqli_query($connect, $sql);
    }

    echo "<br/>";
    echo "success";
    mysqli_close($connect);
    ```


### 登录/注册的逻辑

* 一、先头准备
    ```
    $host = "本机地址";
    $user = "本地用户名-root";
    $pwd = "本地密码-root";
    $database = "目标数据库";
    $connect = mysqli_connect($host, $user, $pwd, $database);
    $username = $_POST["username"];
    $password = $_POST["password"];
    ```
    如果是注册,很大可能还要再加上:
    ```
    $mobile = $_POST["mobile"];
    $nowTime = date("Y-m-d H:i:s");
    ```
    * “热身”句子
    ```
    $search = "select * from `users` where `username` = '{$username}'";(必备的SQL搜索语句)
    $query = mysqli_query($connect, $search);(执行连接和搜索)
    ```
* 二、登录篇
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
* 三、注册篇
	* 1.判断用户名在表内是否存在
	* 2.如用户名存在则判断失败
	* 3.如注册在表内不存在则注册成功
    ```
    if ($query->num_rows > 0) { //1
        while ($sleACT = mysqli_fetch_array($query)) {
            if ($sleACT) {
                echo "<br/>";
                echo "username is created or used";//2
                die();
            }
        }
    } else {
        $sql = "insert into `users` (`username`, `password`, `sex`, `create_time`, `update_time`) value ('{$username}', '{$password}', 'man', '{$nowTime}', '{$nowTime}')";
        echo $sql;
        $query = mysqli_query($connect, $sql);//3
    }
    ```

# MySQL数据库

* 一、基本语法:
	`F9` 运行SQL代码的键位
    `CREATE DATABASE “数据库名”;` 创建并命名一个新数据库
    `DROP DATABASE “数据库名”`;卸载目标数据库
    `DROP TABLE` `表名`;删除目标表
    `Now()` 在表中表现现在的时间
    `int` 整形数字
    `varchar` 字符串
    `decimal` 浮点(小数点)数字,设置格式为(自定义数位,自定义小数点数位)
    `key` 索引
    `primary key` 主键
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
	* 最基本查询方式(如果是查询多个字段,以逗号隔开):
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

##PHP算法##
* `ceil`:向上取整(如6.1~6.9都能算成7)
* `round`:纯四舍五入

