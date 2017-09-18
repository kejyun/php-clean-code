# 變數

## 變數名稱必須要有意義

*錯誤示範：*

```php
// 目前日期
$ymdstr = Carbon::now()->format('Y-m-d');

// 年份
for($i = 2000; $i <= 2018, $i++) {

}
```

**正確示範：**

```php
// 目前日期
$current_date = Carbon::now()->format('Y-m-d');

// 年份
for($year = 2000; $year <= 2018, $year++) {

}
```


## 一般變數須用小寫及底線，用底線隔開有意義的文字

*錯誤示範：*

```php
// 字串
$userName = 'KJ';

// 整數
$AGE = 18;
```

**正確示範：**

```php
// 字串
$user_name = 'KJ';

// 整數
$age = 18;
```

## 陣列後方加入 `list` 特殊字，表示為陣列清單資料

*錯誤示範：*

```php
// 陣列
$Interest = [
    'Basketball',
    'Long board',
    'Cooking',
];
```

**正確示範：**

```php
// 陣列
$interest_list = [
    'Basketball',
    'Long board',
    'Cooking',
];
```

## 布林值前方加入 `is` 特殊字，表示為布林資料

*錯誤示範：*

```php
// 布林值
$EmailVerify = true;
```

**正確示範：**

```php
// 布林值
$is_email_verify = true;
```

## 物件使用大駝峰式命名法（upper camel case），表示有可以呼叫的方法

*錯誤示範：*

```php
// 使用者物件
$user = User::find(1);

// 使用者物件資料集
$userCollections = User::all();
```

**正確示範：**

```php
// 使用者物件
$User = User::find(1);

// 使用者物件資料集
$UserCollections = User::all();
```




## 使用有意義且可以被搜尋的名稱

*錯誤示範：*

```php
// 設定使用者狀態
$User->status = 'A';
$User->status = 'I';

// 例外錯誤
throw new Exception("使用者權限不足", 100010001);
```

**正確示範：**

```php
// 定義類別整理常數
class UserConstant {
    const STATUS_ACTIVE = 'A';
    const STATUS_INACTIVE = 'I';
}

// 設定使用者狀態
$User->status = UserConstant::STATUS_ACTIVE;
$User->status = UserConstant::STATUS_INACTIVE;


// 例外錯誤
class UserExceptionCode {
    const INSUFFICIENT_PERMISSIONS = 100010001;
}


throw new Exception(
    "使用者權限不足",
    UserExceptionCode::INSUFFICIENT_PERMISSIONS
);
```
