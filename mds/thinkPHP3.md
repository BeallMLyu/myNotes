# thinkPHP3.2

## 常用方法词

* 常用方法词:
	* `dump`:thinkPHP专有的变量调用词
	* 

* 本地网页访问规则:`http://www.test.test(本地域名)/home(模块名)/test(控制器名)/index1(方法名)`
	* 1.一个本地域名,如`http://www.test.test/`
	* 2.模块名,在本地域名后,如`home`
	* 3.控制器名,如`test`
	* 4.方法名,如`index1`
	**如果方法名没有写进去或者提出来,那么方法名就是默认`index`**
* 与mySql数据库的连接:
	* 1.配置数据库信息:
	```
    'DB_TYPE'   => 'mysql', // 数据库类型
    'DB_HOST'   => '127.0.0.1', // 服务器地址
    'DB_NAME'   => 'mall', // 数据库名
    'DB_USER'   => 'root', // 用户名
    'DB_PWD'    => 'root', // 密码
    'DB_PORT'   => 3306, // 端口
    'DB_PARAMS' =>  array(), // 数据库连接参数
    'DB_CHARSET'=> 'utf8', // 字符集
    'DB_DEBUG'  =>  TRUE, // 数据库调试模式 开启后可以记录SQL日志
    ```
    * 2.使用`M方法`(**大写**)
    ```
    $自定义变量名 = M('users');
    var_dump($自定义变量名->select());
    ```
		* 2-1.单独查询的条件
	```
    dump($user->where(推荐以包含有所要查询的条件的数组变量)->select());
    ```
    **例子↓:**
    ```
    $whereArray = array("username" => "bugaoxing", "password" => "123456789");
    ```