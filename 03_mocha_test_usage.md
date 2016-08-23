# mocha run test

```
npm i -g bower
```

## About mocha

 * [mocha.js](https://mochajs.org/)

```
Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser, making asynchronous testing simple and fun. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases. Hosted on GitHub.
```

## start  mocha env

install by script below, and `mocha-basic` is your project name, you can change whatever you want.
install mocha and chai

```
mkdir mocha-basic && mocha-basic
bower i mocha
bower i chai
```

create a `index.html` file, content is below,

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
    <script src="./js/functions.js"></script>
    <script>mocha.setup('bdd')</script>
    <script src="test.js"></script>
    <script>
        mocha.run();
    </script>
</body>
</html>
```

## test first

create a test folder, and create a new `add.spec.js` file, as a test file for run test add function.

```
mkdir test
touch test/add.spec.js
```

## edit test content

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

Prepare about `add.js`

```
mkdir js
touch js/add.js
# then edit js/add.js
```

edit js/add.js

```
function add(num1, num2) {
    return num1 + num2;
}
```
then run `index.html`, you will see test reslut is correct.

![](https://cldup.com/jVwzESPvgn.png)




