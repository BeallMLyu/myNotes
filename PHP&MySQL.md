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


# MySQL数据库