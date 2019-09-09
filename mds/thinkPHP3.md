# thinkPHP3.2

##控制器格式
```
namespace Home\Controller;

use Think\Controller;

class AccountController extends Controller {
    public function Index() {
        $users = session('user');
        $this->assign('user', $users);
        return $this->display();
    }
}

```

## 常用方法词

* 常用方法词:
	* `dump`:thinkPHP专有的变量调用词
	* `M`:连接已知存在的数据库中的目标表
	* `where`:查询条件
	* `save`:修改并保存修改后数据
	* `select`:查询结果为多条数据
	* `find`:查询结果为单条数据
	* `ctrl+R`:替换目标字段
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
    * 3.有条件查询数据的方法
    ```
    $whereArray = array("username" => "bugaoxing", "password" => "123456789");
    ```
    * 4.修改数据的方法
    ```
    $updateResult = $user->where(array("id" => 12))->save(array("password" => "4567"));
    ```
    **`save`:修改数据的关键方法**

## session&cookie

* cookie的原理:
当浏览器访问服务器的时候,服务器就会返回一个唯一的id给浏览器,这就是Cookie.这样,下次再访问同样服务器时就会带上这个Cookie,这样服务器就会知道这是谁了。

* Session的原理:
即浏览器通过访问服务器生成的存在于目标服务器里的缓存文件,但服务器本身可以设置需要缓存的内容,例如**uid**、**username**等基本信息.
	* Session使用方法:
		* 存储&读取:
            * 原生PHP使用的session存储以及取出方式
            ```
            session(‘name*可自定义的键名’， '可自定义的值')
            ↑存储
            dump($_SESSION*这是仅限于PHP的全局session的变量);
            $name = $_SESSION['name'];
            echo $name;
            ```

            * 仅thinkPHP专用的简化版session存储方式
            ```
            session('可自定义键名1’, array('可自定义的键名2’ => '可自定义的值' *多个))；
            $自定义变量名 = session('之前的自定义键名1');
            dump('之前的自定义键名1');
            echo '之前的自定义键名1'['指定数组中的指定键名'];
            ```

            * thinkPHP专用的session取出&传输方式:
            ```
             $自定义变量名 = session('自定义键名');
             $this->assign('如上所述的自定义键名', $如上所述的自定义变量名);
             return $this->display();
            ```
## 模板

* 1.在thinkPHP中使用`$this->assign('自定义键名', '$自定义变量')`把参数传给前台html文件
* 2.在html中使用`{$自定义变量[“已经在其变量所绑定的数组中完成自定义的键名”]}`
* 用于html模板的数据库内多数据循环输出: 
```
<foreach name="之前assign赋值的变量,起绑定之用" item="标签内自定义变量">
    {$之前于本标签内自定义的变量.id}:{$之前于本标签内自定义的变量.name}
</foreach>
```