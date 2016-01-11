# Protractor API

标签（空格分隔）： Protractor

---

## element(元素)：
 element也可以称为ElementFinder，它是ElementArrayFinder（element.all)里的一个单个元素，因此用ElementFinder可以做的用ElementArrayFinder也可以做。 element可以看作是实际网页中的元素，任何你对网页元素的操作都可以通过对它的操作实现，每个动作的操作结果都可以通过element中的方法获取。
element中的方法分为element（ElementFinder）和element.all（ElementArrayFinder）的方法。
#### element.all的方法：
1.clone():实现对一个元素数组的简单复制。
``` Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  it('clone',function(){
  browser.get('http://www.aihangyun.com/bd/#');
  var ul1=element.all(by.css('.dropdown-menu scrollable-menu'));
  var ul2=ul1.clone();
  //console.log(ul2);
  expect(ul1.count()).toBe(ul2.count());
  });
   });
```
2.all():调用此方法可以找到一个把当前元素作为起点的一个新的数组。方法结果返回一个包含当前数组子元素的新的数组。
``` Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  it('clone',function(){
  browser.get('http://www.aihangyun.com/bd/#');
  var ul1=element.all(by.css('nav navbar-nav')).all(by.linkText('我的任务'));
  var ul2=element.all(by.css('nav navbar-nav'));
  expect(ul1.count()).toBe(ul2.count());
  });
   });
```
3.filter():通过这个filter方法是为了找到一组符合filter方法的一组元素，因为filter（）不能检索到列表中的所有元素，所以它一般用于一个网页对象。
``` Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  it('clone',function(){
  browser.get('http://www.aihangyun.com/bd/#');
  var ul1=element.all(by.css('nav navbar-nav')).filter(function(elem,index){
      return elem.getTagName().then(function(tagname){
  		return tagname='li';
  	});
  });
  });
   });
```
4.get():通过索引找到数组中的一个元素，索引从０开始。
``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
 	var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
 
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});
```
5.first():找到数组中的第一个元素。
``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
 	var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl2);
 
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.first().getText()).toBe('名称');
    expect(options.last().getText()).toBe('更新时间');
  });
});
```
6.last():找到数组中的最后一个元素。
7.count():这个数组所代表的元素的个数，结果不一定是整型。它返回的是一个Promise对象不能直接用于四则运算。
``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
 	var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
  var targetUrl3='http://www.aihangyun.com/bd/student#/';
    var text=element(by.linkText('学生'));
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl3);
    var startitems=element.all(by.repeater('student in students'));
    var startitemsCount=startitems.count();
    //console.log( 'startitemsCount'+startitemsCount);
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
    expect(element.all(by.css('.modal-dialog')).isDisplayed()).toBeTruthy();
    element(by.buttonText('Close')).click();
    var items=element.all(by.repeater('student in students'));
    expect(items.count()).toEqual(startitemsCount.then(function(start){
        return start+1;}));
  });
});
```
8.locator():返回最相关的定位说明。
```Protractor
  // returns by.css('#ID2')
$('#ID1').$('#ID2').locator()

```
9.each():通过each中定义的方法调用数组中的每个元素，然后输出方法的结果。
``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
 	var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
   var ul1=element.all(by.css('.dropdown-menu scrollable-menu'));
    var text=element(by.linkText('BDHotel'));
    text.click();
    expect(ul1.isDisplayed()).toBeTruthy();
    ul1.each(function(elem,index){
    	  elem.getText().then(function(text){
    	  	console.log('***********************');
    	  	console.log(index,text);
    	  	console.log('***********************');
    	  });
   });
  });
});
```
10.map(): 对ElementArrayFinder的每个元素执行map中的方法，方法中ElementArrayFinder中的元素
作为第一个变量，元素索引作为第二个变量。

``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
   var ul1=element.all(by.css('.dropdown-menu scrollable-menu'));
   var text=element(by.linkText('BDHotel'));
    text.click();
    expect(ul1.isDisplayed()).toBeTruthy();
    var a=ul1.map(function(elem,index){
    	return{
    		index
    	};
    });
    expect(a).toEqual([0]);
  });
});

```
11.reduce():通过

12.evaluate():评估输入是否时当前元素的范围。

```Protractor
<span id="foo">{{variableInScope}}</span>

var value = element(by.id('foo')).evaluate('variableInScope');
```
13.allowAnimation():确定动画在当前基础元素中是否允许

```Protractor
element(by.css('body')).allowAnimations(false);

```
####element的方法：
1.then():访问地层的actionResult ElementFinder。

``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
     var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
  var targetUrl3='http://www.aihangyun.com/bd/student#/';
    var text=element(by.linkText('学生'));
    text.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl3);
    var startitems=element.all(by.repeater('student in students'));
    var startitemsCount=startitems.count();
    //console.log( 'startitemsCount'+startitemsCount);
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
    expect(element.all(by.css('.modal-dialog')).isDisplayed()).toBeTruthy();
    element(by.buttonText('Close')).click();
    var items=element.all(by.repeater('student in students'));
    expect(items.count()).toEqual(startitemsCount.then(function(start){
        return start+1;}));
  });
});
```
2.getWebElement():返回ElementFinder所代表的web元素，如果不存在将会向WebDriver抛出错误。

``` Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
   var a =element(by.linkText('学生')).getWebElement();
   console.log(a);
  });
});

```
3.$$和$; $$是找到一组元素，$是找到一个元素

```Protractor
var items = element(by.css('.parent')).$$('li')
var child = element(by.css('.parent')).$('.child');

```
４.isPresent():确定某个元素是否在页面上存在。

```Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
     var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);

    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();

    //expect(browser.getLocationAbsUrl()).toBe(targetUrl);
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
    browser.get('http://www.aihangyun.com/bd/#');
  });
  it('should into my work',function(){
   var a =element(by.linkText('学生'));
   expect(a.isPresent()).toBe(true);
  });
});

```
5.isElementPresent():和ElementFinder.isPresent()相同
