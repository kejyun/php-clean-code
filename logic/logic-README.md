# 邏輯

## 避免使用過度深入的條件判斷式


*錯誤示範：*

```php
class User {
    public function isUserAuthorize(User $User)
    {
        if ($User->age < 18) {
            throw new Exception("Too young");

        } else {
            if (!$User->is_email_verify) {
                return false;
            } else if (!$User->is_phone_verify) {
                return false;
            } else {
                return true;
            }
        }
    }
}
```

**正確示範：**

```php
class User {
    public function isUserAuthorize(User $User)
    {
        if ($User->age < 18) {
            throw new Exception("Too young");
        }

        if (!$User->is_email_verify) {
            return false;
        }

        if (!$User->is_phone_verify) {
            return false;
        }

        return true;
    }
}
```


## 條件式使用 AND 及 OR 當作條件判斷，不要使用 && 及 ||


*錯誤示範：*

```php
if ($age > 18 && $is_email_verify && $is_phone_verify) {
    # code...
}

if ($age > 18 || $is_email_verify || $is_phone_verify) {
    # code...
}
```

**正確示範：**

```php
if ($age > 18 AND $is_email_verify AND $is_phone_verify) {
    # code...
}

if ($age > 18 OR $is_email_verify OR $is_phone_verify) {
    # code...
}
```

> 程式若能寫給人閱讀，最好用有語意的文字取代。
