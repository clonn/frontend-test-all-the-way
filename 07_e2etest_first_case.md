# github 程式體驗

透過底下描述，我們可以快速瞭解 github 頁面流程，以及透過快速進行頁面測試

```
Scenario('search', (I) => {
  I.amOnPage('https://github.com/search');
  I.fillField('Search GitHub', 'mokayo');
  I.pressKey('Enter');
  I.see('miiixr/mokayo', 'a');
});

Scenario('signin', (I) => {
  I.click('Sign in');
  I.see('Sign in to GitHub');
  I.fillField('Username or email address', 'user@user.com');
  I.fillField('Password', '123456');
  I.click('Sign in');
  I.see('Incorrect username or password.', '.flash-error');
});

Scenario('register', (I) => {
  within('.js-signup-form', function () {
    I.fillField('user[login]', 'User');
    I.fillField('user[email]', 'user@user.com');
    I.fillField('user[password]', 'user@user.com');
    I.fillField('q', 'aaa');
    I.click('button');
  });
  I.see('There were problems creating your account.');
  I.click('Explore');
  I.seeInCurrentUrl('/explore');
});
```