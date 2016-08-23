# 介紹 CodeceptJS

```
MODERN ERA ACCEPTANCE TESTING FOR NODEJS
```

CodeceptJS 是一個基於 WebDriver 全新的 E2E 測試框架。
以使用者角度進行使用者行為測試，進行簡單使用者操作步驟來編寫測試


[http://codecept.io/](http://codecept.io/)


## 安裝方式

```
npm install -g codeceptjs
```

透過 npm 指令就可以快速將 codeceptjs 安裝到環境中，除了安裝 codeceptjs 之外，還要安裝底層 e2e 執行環境，

例如需要優先安裝 `webdriverio`，

```
npm install webdriverio
```

## 執行方法

安裝好 coeceptjs 之後，可以開始進行設定環境，透過 `codeceptjs` 指令

```
codeceptjs init
```

開始進行設定專案，目前我們僅需要進行處理 `webdriverio` 就選擇 `webdriverio` 項目即可，以及確定資料夾路徑。

設定流程大約會如下描述，

```
Test root is assumed to be $PATH_ENV

  Welcome to CodeceptJS initialization tool
  It will prepare and configure a test environment for you

Installing to $PATH_ENV/
? Where are your tests located? ./*_test.js
? What helpers do you want to use? WebDriverIO
? Where should logs, screenshots, and reports to be stored? ./output
? Would you like to extend I object with custom steps? No
Configure helpers...
? [WebDriverIO] Base url of site to be tested http://localhost
? [WebDriverIO] Browser in which testing will be performed chrome
Config created at $PATH_ENV/codecept.json
Directory for temporaty output files created at `_output`
Almost done! Create your first test by executing `codeceptjs gt` (generate test) command
```

設定好之後，就會看到資料夾中多出了一個 `codecept.json` 檔案，這也就是 codecept.json 的執行環境。

大概描述內容如下，

```
{
  "tests": "./*_test.js",
  "timeout": 10000,
  "output": "./output",
  "helpers": {
    "WebDriverIO": {
      "url": "http://localhost",
      "browser": "chrome"
    }
  },
  "include": {},
  "bootstrap": false,
  "mocha": {},
  "name": "06_e2e_codeceptjs"
}
```

如此一來就完成 codeceptjs 環境設定，記得開始測試之前一定要先安裝 seleium 以及模擬環境。