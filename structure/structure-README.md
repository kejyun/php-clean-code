# 架構

## 同一個檔案盡量避免超過 2000 行

*錯誤示範：*

```php
// 使用者服務
class UserService {

    # 全部使用者的 code 都寫在這裡
    # 全部使用者的 code 都寫在這裡
    # 全部使用者的 code 都寫在這裡
    # 全部使用者的 code 都寫在這裡
    # 全部使用者的 code 都寫在這裡

}
```

**正確示範：**

```php
// 使用者驗證服務
class UserAuthService {

}

// 使用者個人資料服務
class UserProfileService {

}

// 使用者郵件寄送服務
class UserMailService {

}

// 使用者統計資料服務
class UserStatisticService {

}
```

> 程式可以依照資料邏輯分不同的類別，同一個類別程式行數不要過長，這樣會比較容易除錯及維護，找 Code 會比較快。
