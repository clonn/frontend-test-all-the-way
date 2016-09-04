# env install

以下列表為基本環境必須要安裝項目，

 * git - [git install](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
 * node.js - https://nodejs.org/en/ (請以 LTS 版本為主)
 * bower - https://bower.io/#install-bower
 * [Web server - chrome extension](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?utm_source=chrome-ntp-icon)
 * [Java](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

安裝完成後，開始先試著透過 `node` `npm` 安裝整體接下來會用到的指令，

```
npm install -g mocha
npm install -g grunt-cli
npm install -g gulp
npm install -g codeceptjs
npm install -g webdriver-manager
```

安裝完以上指令之後，就可以透過例如 `mocha`, `gulp` 等指令直接在終端機上面執行，接下來的每個動作都會相互在編輯器，及終端機上面互相執行，所以當各位如果有看到 $ 表示指令是在終端機底下執行。