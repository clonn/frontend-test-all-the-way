## 開始進行 codeceptjs

在環境完成安裝設定之後，我們就可以開始編寫第一個 e2e 測試腳本。

透過 codeceptjs 指令進行新增腳本，

```
codeceptjs gt
```

透過 gt 參數，代表 generater test 的意思，開始進行測試的編輯，並且同時設定檔案名稱為 `first_test.js` ，因為我們前面已經設定 test 執行路徑將會讀取 `*_test.js` ，所以命名規則必須要符合才有辦法進如執行環境中。

```
Test root is assumed to be $PATH_ENV
Creating a new test...
----------------------
? Filename of a test first_test.js
? Feature which is being tested First test.js
Test for first_test.js was created in $PATH_ENV/first_test.js
```

如上述設定完成後，就會看到新增一個基本的測試環境可以提供使用，

## 第一個測試腳本

完成上述描述後，我們就可以開始進行第一個測試腳本，

```
Feature('First test.js');

Scenario('test something', (I) => {
	I.amOnPage('https://www.google.com.tw/');
	I.see('Google');
});
```

`I.amOnPage` 表示瀏覽器即將前往的網址。

`I.see` 為最後確認 assertion ，確定驗證資訊是否與預測相同，目前會直接找到 page title 進行驗證。

我們可以透過底下指令，就會看到立即開啟一個 google page ，並且進行驗證的動作。

```
codeceptjs run --steps
```

