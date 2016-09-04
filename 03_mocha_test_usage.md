# Mocha 基本前端單元測試

首先我們要建立基本前端單元測試環境，因此需要透過 `bower` 進行 mocha 安裝，請輸入以下指令。

```
npm i -g bower
```

安裝完成後，我們接著就會採用 bower 進行安裝 mocha, chai 等套件，而且會將這些套件使用於前端開發測試流程中。

## 什麼是 Mocha

 * [mocha.js](https://mochajs.org/)

關於官方簡單描述如下，

```
Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser, making asynchronous testing simple and fun. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases. Hosted on GitHub.
```

Mocha 是一種基礎於 JavaScript 的測試框架，同時讓 Node.js 及前端 JavaScript 進行測試使用，使用情境並不限定於前端或者後端，是一個很方便，輕巧的測試框架。

接下來我們都會透過 mocha 進行前端測試，請跟步驟一步一步進行。

## 設定 mocha 環境

可以跟著 程式碼中的 `03_mocha-basic` 範例程式進行，當然你也可以透過複製，轉移到自己的框架流程中，讓自己方便使用。

接下來我們要透過剛才安裝好的 `bower` 進行安裝 mocha, chai 套件，請在 terminal 輸入底下指令，

```
cd 03_mocha-basic
bower i mocha
bower i chai
```

安裝完成後會看到資料夾中，會顯示結果如下，表示安裝完成

```
bower cached        https://github.com/mochajs/mocha.git#3.0.2
bower validate      3.0.2 against https://github.com/mochajs/mocha.git#*
bower cached        https://github.com/chaijs/chai.git#3.5.0
bower validate      3.5.0 against https://github.com/chaijs/chai.git#*
bower install       chai#3.5.0
bower install       mocha#3.0.2

chai#3.5.0 bower_components/chai

mocha#3.0.2 bower_components/mocha
```
並且會將安裝好的內容放置於 `bower_components` 資料夾中，也就是待會我們會使用引入到前端的測試套件。

接著建立一個檔案名稱為 `index.html` ，內容如下，

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <div id="mocha"></div>
    <script src="./bower_components/chai/chai.js"></script>
    <script src="./bower_components/mocha/mocha.js"></script>
    <script src="./js/add.js"></script>
    <script>mocha.setup('bdd')</script>
    <script src="./test/add.spec.js"></script>
    <script>
        mocha.run();
    </script>
</body>
</html>
```

主要結構載入了 mocha, chai 兩個套件，並且設定 mocha 測試條件，同時將主要程式 `js/add.js` 一個簡易加法程式直接引入到頁面中。

接著引入 `test/add.spec.js` ，這段測試程式，主要用於驗證前端邏輯測試結果。

通常命名上，我們會將測試程式放置於 `test` 資料夾中，並且測試檔案都會取名為 `xxx.spec.js` 這是一個約定的方式，當然你也可以使用自己習慣方式進行名命，名稱並不是主要的關鍵，只要日後可以進行識別都會是很棒的名稱。

最後再設定 `mocha.run()` 就會執行程式，很快的就可以把程式運行起來。

接著我們再繼續將 test/add.spec.js 的內容先補起來，再接著實做 add.js 本身的程式架構，接下來都會採用測試先行的方式將測試流程補充完畢之後，才會進行實際 function 的編寫。 

## Test first 流程

建立一個 test 資料夾，並且在資料夾中建立名為 `add.spec.js` 的檔案，裡面主要放置了 add.js 相關的測試範疇。

```
mkdir test
touch test/add.spec.js
```

`add.spec.js` 裡面測試內容如下

```
var expect = chai.expect;
var should = chai.should();
describe('Test add function', function() {
    it('test simple add basic', function () {
        var result = add(2, 1);
        result.should.be.equal(3);
    })
});
```

整體架構規範採用於 mocha 框架流程，當我們採用 mocha 之後，就直接可以使用 `describe` `it` 這兩個描述句型，主要用於描述 test 本身的用法及範圍，本身除了就是程式之外，透過友善文字性的描述，可以之後維護者更容易瞭解當初的場景，以及設定的測試情境。

在測試中，我們直接進行呼叫 `add(2, 1)` 直接進行 add 程式呼叫，透過 chai 驗證結果。

當我們設定好 add 程式中的預期輸入及預期輸出之後，準備回到 add 程式本身，我們開始進行 add.js 主要程式內容編寫，指令如下，

```
mkdir js
touch js/add.js
# then edit js/add.js
```

修改 `js/add.js` 修改內容如下，

```
function add(num1, num2) {
    return num1 + num2;
}
```

根據實做過程， add 是一個非常簡單的加法函式，直接將加入的資料進行回傳，讓我們可以看到實際的結果產出。

接著透過前端 `index.html` 結果的執行，可以看到實際產出的頁面會如下，表示為驗證結果正確。

![](https://cldup.com/jVwzESPvgn.png)


恭喜各位，完成第一個 test first 的前端開發流程。

這是一個非常簡單不過的測試流程，實際上我們在進行測試開發時都應該保持同樣的方式及節奏，讓開發流程盡量符合期待及規範，保持有一定的預期輸入及預期輸出，讓程式保持一定的簡潔度，才有辦法進行測試。


