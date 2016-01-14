##locator
###by
#####addLocator()
#####binding()
#####exactBinding()
#####model()
#####buttonText()
#####partialButtonText()
#####repeater()
#####exactRepeater()
#####cssContainingext()
#####options()
#####deepCss()
#####className()
#####css()
#####id()
#####linkText()
#####js()
#####name()
#####partialLinkText()
#####tagName()
#####xpath
###by的方法
Protractor定位器。它提供了很多在Angular应用中寻找元素的方法，例如by.binding(),by.model()等等。
######addLocator()
为实例增加一个可以通过by方法找到元素的定位。
```Protractor
// Add the custom locator.
by.addLocator('buttonTextSimple',
    function(buttonText, opt_parentElement, opt_rootSelector) {
  // This function will be serialized as a string and will execute in the
  // browser. The first argument is the text for the button. The second
  // argument is the parent element, if any.
  var using = opt_parentElement,
      buttons = using.querySelectorAll('button');

  // Return an array of buttons with the text.
  return Array.prototype.filter.call(buttons, function(button) {
    return button.textContent === buttonText;
  });
});

// Use the custom locator.
element(by.buttonTextSimple('Go!')).click();
```
######binding()  
这是AngularJs版本的方法，可以找到通过{{}｝定义的网页元素。
```Protractor
var span1 = element(by.binding('person.name'));
expect(span1.getText()).toBe('Foo');

var span2 = element(by.binding('person.email'));
expect(span2.getText()).toBe('foo@bar.com');

// You can also use a substring for a partial match
var span1alt = element(by.binding('name'));
expect(span1alt.getText()).toBe('Foo');

// This works for sites using Angular 1.2 but NOT 1.3
var deprecatedSyntax = element(by.binding('{{person.name}}'));
```
######exactBinding()  
这是AngularJs版本的方法，可以找到通过{{}｝定义的网页元素，输入全称。
```Protractor
expect(element(by.exactBinding('person.name')).isPresent()).toBe(true);
expect(element(by.exactBinding('person-email')).isPresent()).toBe(true);
expect(element(by.exactBinding('person')).isPresent()).toBe(false);
expect(element(by.exactBinding('person_phone')).isPresent()).toBe(true);
expect(element(by.exactBinding('person_phone|uppercase')).isPresent()).toBe(true);
expect(element(by.exactBinding('phone')).isPresent()).toBe(false);
```
######model()  
找到使用ng-model表达式的元素
```Protractor
describe('model', function(){  
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
  });  
  });  
```
######buttonText():
获得按钮中的文本信息
```Protractor
describe('buttonText', function(){  
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
  });  
```
######partialButtonText()
通过按钮部分文本定位按钮  
```Protractor
describe('buttonText', function(){  
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
    element(by.partialButtonText('登录')).click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl);  
  });  
  });  
```
######repeater()：
找到中继器里面的元素
```Protractor
describe('repeater', function(){  
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
    var text=element(by.linkText('学生'));  par
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
       element(by.buttonText('是')).click();  
       browser.refresh();  
      var delitems=element.all(by.repeater('student in students'));  
      expect(delitems.count()).toEqual(startitemsCount.then(function(start){  
      return start;}));  
    });  
  });  
  });  
```
######exactRepeater()  
找到具体哪一个中继器
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
it('by.exactRepeater',function(){
  expect(element(by.exactRepeater('page in pages track by $index')).isPresent()).toBe(false);

});
 });


```
######cssContainingText()  
找到想要得到的具体的那个css元素
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
it('by.cssContainingText',function(){
  browser.get('http://www.aihangyun.com/bd/#');
  var title=element(by.cssContainingText('.dropdown','我的任务'));
});
 });


```
######options()  
找到使用ng-options表达式的元素
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
    var text=element(by.linkText('我的任务'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
    var h1=element(by.tagName('h1'));  
    expect(h1.getText()).toBe('酒店列表(0)');  
    var label=element(by.tagName('label'));  
    expect(label.getText()).toBe('排序:');  
    var options=element.all(by.options('field.label for field in orderByFields'));  
    expect(options.count()).toBe(2);  
    expect(options.get(0).getText()).toBe('名称');  
    expect(options.get(1).getText()).toBe('更新时间');  
  });  
  });  
```
######deepCss()  
在shadow下使用css选择器找到元素
```Protractor
Example
<div>
  <span id="outerspan">
  <"shadow tree">
    <span id="span1"></span>
    <"shadow tree">
      <span id="span2"></span>
    </>
  </>
</div>
Code
var spans = element.all(by.deepCss('span'));
expect(spans.count()).toEqual(3);
```
###Inherited from webdriver.By的方法

######className()
通过class名定位元素  
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
    var targetUrl2='http://www.aihangyun.com/bd/';  
    var text=element(by.className('dropdown'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
  });  
  });  
```
######css():
使用css选择器定位元素  
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
  it('display analyze',function(){  
    var ul3=element.all(by.css('.dropdown-menu'));  
    var text=element(by.linkText('分析'));  
    text.click();  
    expect(ul3.isDisplayed()).toBeTruthy();  
  });  
  });  
```
######id()：
通过id名定位元素  
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
it('by.cssContainingText',function(){
  browser.get('http://www.aihangyun.com/bd/#');
  var title=element(by.id('bs-example-navbar-collapse-1'));
});
 });
######linkText():
获得文本的链接
```Protractor
describe('linkText', function(){  
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
  it('linkText',function(){  
  var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';  
    var text=element(by.linkText('我的任务'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
  });  
  });   
```
######js()：
通过一个JavaScript表达式定位一个元素。这个表达式的结果必须是一个元素或元素的列表。  
webdriver.By.js = function(script, var_args) {
  var args = goog.array.slice(arguments, 0);
  return function(driver) {
    return driver.executeScript.apply(driver, args);
  };
};
######name()
通过name定位元素  
```Protractor
describe('buttonText', function(){  
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
    element(by.partialButtonText('登录')).click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl);  
  });  
  });
```
######partialLinkText()
通过链接中的部分文本获得文本链接  
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
    var text=element(by.partialLinkText('我的任务'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
  });  
  });  
```
######tagName()
通过标签名定位元素  
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
    var text=element(by.linkText('我的任务'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
    var h1=element(by.tagName('h1'));  
    expect(h1.getText()).toBe('酒店列表(0)');  
    var label=element(by.tagName('label'));  
    expect(label.getText()).toBe('排序:');  
    var options=element.all(by.options('field.label for field in orderByFields'));  
    expect(options.count()).toBe(2);  
    expect(options.get(0).getText()).toBe('名称');  
    expect(options.get(1).getText()).toBe('更新时间');  
  });  
  });  
```
######xpath()
通过xpath选择器定位元素
