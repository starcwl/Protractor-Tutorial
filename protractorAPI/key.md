##key

###webdriver.Key

######chord(有问题)
在一个chord里，模拟一次按很多键。
```Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    browser.driver.key.chord('登录');
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=browser.driver.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```