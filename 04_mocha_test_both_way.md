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

# mocha 前後端共用測試

前面我們已經開始了前端的測試流程，現在我們開始可以進入到 『前後端共用』模組架構，讓開發的可以是前端端共用結構，讓測試可以透過 `mocha` 指令進行。

首先在開始之前，我們先安裝 mocha 終端機指令，

```
npm install -g mocha
npm install mocha
npm install chai
```

## 修改成前後端共用測試 scripts

我們開始修改原本已經建立好的 `test/add.spec.js` ，將整體程式碼進行 function closure 之後，再引入判斷條件，讓程式判別目前是在前端還是後端執行，而這邊主要的特徵在於 node.js 的環境中，每個獨立檔案都可以成為一個 module.exports 條件，依據這種特性我們可以進行測試，瞭解其中執行方向。

全部程式碼修改完，內容如下，

```
(function (isNode) {
    var chai, add;

    if (isNode) {
        chai = require('chai');
        add = require('../js/add.js');
    } else {
        add = window.add;
        chai = window.chai;
    }

    chai.should();
    describe('Test add function', function() {
        it('test simple add basic', function () {
            var result = add(2, 1);
            result.should.be.equal(3);
        });

        it('add with a string', function () {
            var result = add(2, 'kerker');
            result.should.be.equal(2);
        })
    });

}(typeof module !== 'undefined' && module.exports));
```

接著進行設定 `js/add.js` ，修改 add function, 這邊一樣依據 `module.exports` 這樣的特性，進行判斷，如果有 module.export 就會把 add 這個函式直接引入，如果沒有的話，就將這個 add function 視為一個前端執行函式。

`js/add.js` 修改後內容如下，

```
function add(num1, num2) {
    num1 = (typeof num1 !== 'number') ? 0 : parseInt(num1, 10);
    num2 = (typeof num2 !== 'number') ? 0 : parseInt(num2, 10);
    return num1 + num2;
}

var module = module || {};
if (module && module.exports)
    module.exports = add;
```

修改完後，目前會發現架構裡面可以直接透過 `mocha` 進行測試，終端機中測試指令如下，單獨透過 `test/add.spec.js` 進行單獨測試，指令如下，

```
mocha test/add.spec.js
```

測試後，驗證結果正確，將會是如下的畫面，

```
  Test add function
    ✓ test simple add basic
    ✓ add with a string


  2 passing (8ms)

```

看到上面描述，表示進行 add.js 函式中驗證結果正確，恭喜各位完成一個前後端共用的測試流程。

當我們這樣開始編寫後，此時測試單元已經可以從單純前端驗證，直接透過後端進行處理，當然更深一步我們可以繼續透過類似 webpack, browserify 之類的工具編譯出前後端共用函式，模組，這個部分就不再繼續深入討論。

如果各位有興趣，可以查詢關於前後端共用模組建置，及編譯方式，希望各位能夠試著打造前後端共用的環境。

