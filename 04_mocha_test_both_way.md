# 讓 mocha 同時前後端執行

剛才已經有設定了關於前端執行項目，但是 mocha 實際上也可以在後端進行測試，我們就來改善一下設定，讓我們的程式也可以照常進行吧

```
npm init
```

輸入後過程中會有一些對話，內容可以全部留白，內容大致上會是如下描述，

```
name: (mocha-basic)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to /Users/chicaesar/workspace/mokayo/frontend-test-exercise/mocha-basic/package.json:

{
  "name": "mocha-basic",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "directories": {
    "test": "test"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this ok? (yes)
```

接著環境中就會多出一個 `pakcage.json` 針對於 node.js 後端專案的設定檔。

接下來就開始繼續安裝後端測試套件，並且設定到環境中吧

```
npm i bower chai --save-dev
```
