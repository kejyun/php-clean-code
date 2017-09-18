# 類別


## 使用大駝峰式命名法（upper camel case）定義類別名稱


*錯誤示範：*

```php
class user {

}

class userRememberToken {

}
```

**正確示範：**

```php
class User {

}

class UserRememberToken {

}
```

## 函數方法使用小駝峰式命名法（lower camel case）

*錯誤示範：*

```php
// 使用者物件
class User {
    public function finduserbyid()
    {
        # code...
    }

    public function get_user_collections()
    {
        # code...
    }
}
```

**正確示範：**

```php
// 使用者物件
class User {
    public function findUserById()
    {
        # code...
    }

    public function getUserCollections()
    {

    }
}
```

## 函式名稱必須寫清楚做的事情是什麼


*錯誤示範：*

```php
// 使用者物件
class User {
    public function getUserCollections()
    {
        # code...
    }
}

// Email 物件
class Email {
    public function handle()
    {
        # code...
    }
}
```

**正確示範：**

```php
// 使用者物件
class User {
    // 取得已啟用會員資料
    public function getActiveUserCollections()
    {
        # code...
    }
}

// Email 物件
class Email {
    public function send()
    {
        # code...
    }
}
```

## 類別變數屬性不需要加入額外的贅字

*錯誤示範：*

```php
// 使用者物件
class User {
    public $user_name;
    public $user_gender;
}
```

**正確示範：**

```php
// 使用者物件
class User {
    public $name;
    public $gender;
}
```

變數屬性已經在類別裡面，一定要為使用者的屬性資料

## 每個方法只專心做一件事


*錯誤示範：*

```php
public function activeUserAccount(User $User)
{
    $User->status = UserConstant::STATUS_ACTIVE;
    $User->save();

    Mail::send(
        'email.activeUserAccountNotification',
        $mail_binding,
        function($mail) use ($mail_binding)
    {
        $mail->to($mail_binding['email']['to']);
        $mail->from($mail_binding['email']['from']);
        $mail->subject('恭喜啟用帳號成功');
    });
}
```

**正確示範：**

```php
public function activeUserAccount(User $User)
{
    $User->status = UserConstant::STATUS_ACTIVE;
    $User->save();
}

public function sendActiveUserAccountEmail($mail_binding)
{
    Mail::send(
        'email.activeUserAccountNotification',
        $mail_binding,
        function($mail) use ($mail_binding)
    {
        $mail->to($mail_binding['email']['to']);
        $mail->from($mail_binding['email']['from']);
        $mail->subject('恭喜啟用帳號成功');
    });
}
```

## 避免檢查傳入資料格式


*錯誤示範：*

```php
public function activeUserAccount($User)
{
    if (!($User instanceof User)) {
        throw new Exception("非使用者物件");
    }
    ## code
}

public function add($value1, $value2)
{
    if (!is_numeric($value1) OR !is_numeric($value1)) {
        throw new Exception("傳入資料非數字");
    }
    return $value1 + $value2;
}
```

**正確示範：**

```php
public function activeUserAccount(User $User)
{
    ## code
}

public function add(int $value1, int $value2)
{
    return $value1 + $value2;
}
```
