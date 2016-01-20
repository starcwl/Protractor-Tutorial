###expectedConditions
代表一个canned函数库，在预期条件下对protractor是有用的，尤其在处理non-angular应用的时候。每个条件返回一个函数 ，等于一个promise，你可以混合使用and，or，and/or not多个组合条件。你也可以将这些条件和任何你写的其他的条件一起使用
######not
条件是否定一个结果。
```Protractor
describe('test login page', function(){
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
 it(' into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var EC = protractor.ExpectedConditions;
   var titleIsNotFoo = EC.not(EC.titleIs('爱航酒店地推管理'));
    browser.wait(titleIsNotFoo, 5000);
  });
 });
```
######and
用and将两个或者多个条件综合起来，作为判断条件的结果，只要有一个条件结果是false则总的结果就是fase.
```Protractor
describe('test login page', function(){
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
   it(' into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
   var EC = protractor.ExpectedConditions;
var titleContainsFoo = EC.titleContains('爱航酒店地推管理');
var titleIsNotFooBar = EC.not(EC.titleIs('FooBar'));
browser.wait(EC.and(titleContainsFoo, titleIsNotFooBar), 5000);
  });
 });
```
######or
用or将两个或者多个条件综合起来，作为判断条件的结果，只要有一个条件结果是true则总的结果就是true.
```Protractor
describe('test login page', function(){
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
   it(' into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
    var EC = protractor.ExpectedConditions;
var titleContainsFoo = EC.titleContains('爱航酒店');
var titleContainsBar = EC.titleContains('fdsf管理');
browser.wait(EC.or(titleContainsFoo, titleContainsBar), 5000);
  });
 });
```
######alertIsPresent
显示警示框
```Protractor
describe('test login page', function(){
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
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
  it('should into student',function(){
    var targetUrl3='http://www.aihangyun.com/bd/student#/';
    var text=element(by.linkText('学生'));
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl3);
    var startitems=element.all(by.repeater('student in students'));
    var startitemsCount=startitems.count();
    var create=element(by.linkText('新建'));
    create.click();
    expect(browser.getCurrentUrl()).toBe('http://www.aihangyun.com/bd/student#/new');
    element(by.model('student.firstName')).sendKeys('liling');
    element(by.model('student.lastName')).sendKeys('zhang');
    element(by.model('student.phone')).sendKeys('123');
    element(by.model('student.province')).sendKeys('shandong');
    element(by.model('student.city')).sendKeys('changle');
    element(by.model('student.county')).sendKeys('zhang');
    element(by.model('student.address')).sendKeys('china');
    element(by.model('student.age')).sendKeys('18');
    element(by.model('student.birth')).sendKeys('1970-01-01T00:00:00.000Z');
    element(by.model('student.email')).sendKeys('zhang@qq.com');
    element(by.model('student.school')).sendKeys('univisity');
    element(by.buttonText('保存')).click();
    expect(element.all(by.css('.model-dialog')).isDisplayed()).toBeTruthy();
    element(by.buttonText('Close')).click();
    var items=element.all(by.repeater('student in students'));
   expect(items.count()).toEqual(startitemsCount.then(function(start){
        return start+1;}));
       items.then(function(its){
       var del = its[0].element(by.linkText('删除'));
       del.click();
                     var EC = protractor.ExpectedConditions;
EC.alertIsPresent();
       element(by.buttonText('是')).click();
       browser.refresh();
      var delitems=element.all(by.repeater('student in students'));
      expect(delitems.count()).toEqual(startitemsCount.then(function(start){
      return start;}));
    }); 
  });
 });
```
######elementToBeClickable
检验一个元素是可见的或者说能够被利用的，例如你可以点击它。
```Protractor
describe('test login page', function(){
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
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
 it(' into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
    var EC = protractor.ExpectedConditions;
browser.wait(EC.elementToBeClickable($('.navbar-brand')), 5000);
 });
});
```
######textToBePresentInElement
检查元素的文本是否能够找到。
```Protractor
describe('test login page', function(){
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
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
  it(' into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
    var h1=element(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var EC = protractor.ExpectedConditions;
browser.wait(EC.textToBePresentInElement($('.ng-binding'), '(0)'), 5000);
    var label=element(by.tagName('label'));
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
 });
```
######textToBePresentInElementValue
一个期望用来检验在一个元素的值的文本是否显示。如果elementFinder没有找到元素返回false。
```Protractor
describe('test login page', function(){
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
     var EC = protractor.ExpectedConditions;
browser.wait(EC.textToBePresentInElementValue($('.form-control'), 'chenwulin@aihanginns.com'), 5000);
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
 });
```
######titleContains
检验标题中包含的区分大小写的子字符串
```Protractor
describe('test login page', function(){
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
    var EC = protractor.ExpectedConditions;
browser.wait(EC.titleContains('爱航市场拓展管理系统'), 5000);
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
 });
```
######titleIs
检验页面的标题
```Protractor
describe('test login page', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
     var EC = protractor.ExpectedConditions;
browser.wait(EC.titleIs('爱航市场拓展管理系统'), 5000);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
   element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
  });
 });
```
######presenceOf
一个用来检验一个元素出现在在页面的DOM上的期望，这并不意味着元素是可见的，他与“ataleneessOf”是相反的
```Protractor

```
######stalenessOf
一个用来检验一个元素没有附加到页面的DOM上的期望，他与“presenceOf”的是相反的
```Protractor

```
######visibilityOf
一个用来检验一个元素出现在页面DOM上并且是可见的期望。可见性意味着元素不仅显示出来，并且还有一个大于0的高度和宽度。他与“invisibilityOf”相反
```Protractor

```
######invisibilityOf
检验一个元素是不可见的，也没出现在页面的DOM上，他与“visibilityOf”相反
```Protractor

```
######elementToBeSelected
检验选项被选择(复选框)
```Protractor

```