

标签（空格分隔）： Protractor

---
###element 中的方法:
####element.all(locator)
######clone()
######all()
######filter()
######get()
######first()
######last()
######count()
######locator()
######each()
######map()
######reduce()
######evaluate()
######allAnimations()
####element(locator)
######then
######clone()
######locator()
######getWebElement()
######all()
######element
######$$
######$
######isPresent()
######isElementPresent()
######evaluate()
######allowAnimations()
######equals()
######getDriver()
######serialize()
######findElement()
######isElementPresent()
######findElements()
######click()
######sendKeys()
######getTagName()
######getCssValue()
######getAttribute()
######getText()
######getSize()
######getLocation()
######isEnabled()
######isSelected()
######submit()
######clear()
######isDisplayed()
######takeScreenshot()
######getOuterHtml()
######getInnerHtml()
## element(元素)：
 element也可以称为ElementFinder，它是ElementArrayFinder（element.all)里的一个单个元素，因此用ElementFinder可以做的用ElementArrayFinder也可以做。 element可以看作是实际网页中的元素，任何你对网页元素的操作都可以通过对它的操作实现，每个动作的操作结果都可以通过element中的方法获取。
element中的方法分为element（ElementFinder）和element.all（ElementArrayFinder）的方法。
#### element.all的方法：
###### clone()
实现对一个元素数组的简单复制。
``` Protractor  
describe('test login module', function(){  
     var time = new Date;  
     console.log(time);  
     var testUrl = '/bd/login';  
     it('clone',function(){  
     browser.get('http://www.aihangyun.com/bd/#');  
     var ul1=element.all(by.css('.dropdown-menu scrollable-menu'));  
     var ul2=ul1.clone();  
    expect(ul1.count()).toBe(ul2.count());  
                                         });  
              });                                                      
```
 
###### all()
调用此方法可以找到一个把当前元素作为起点的一个新的数组。方法结果返回一个包含当前数组子         元素的新的数组。
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
###### filter()
通过这个filter方法是为了找到一组符合filter方法的一组元素，因为filter（）不能检索到列表中的  所有元素，所以它一般用于一个网页对象。
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
###### get()
通过索引找到数组中的一个元素，索引从０开始。
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
######first()
找到数组中的第一个元素。
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
######last()
```Protractor
找到数组中的最后一个元素。
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
###### count()
这个数组所代表的元素的个数，结果不一定是整型。它返回的是一个Promise对象不能直接用于四则运算。
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
###### locator()
返回最相关的定位说明。
```Protractor

  // returns by.css('#ID2')
$('#ID1').$('#ID2').locator();

```
######each()
通过each中定义的方法调用数组中的每个元素，然后输出方法的结果。
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
######map()
对ElementArrayFinder的每个元素执行map中的方法，方法中ElementArrayFinder中的元素
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
######reduce()(有问题)
实现一个累加器，通过这个累加器把所需要的参数加到一起，然后统一输出结果。
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
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    //browser.driver.WebElement.equals(h1,label);
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields')).reduce(function(acc,elem){
      return elem.getText().then(function(text){
        return acc + ' ';
      });
    }, '');
    expect(options).toEqual('dsjf');
    
  });
});

```

###### evaluate()
评估输入是否时当前元素的范围。

```Protractor
<span id="foo">{{variableInScope}}</span>

var value = element(by.id('foo')).evaluate('variableInScope');
```
######allowAnimation()
确定动画在当前基础元素中是否允许

```Protractor
element(by.css('body')).allowAnimations(false);

```
####element的方法：
######then()
访问地层的actionResult ElementFinder。

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
######getWebElement()
返回ElementFinder所代表的web元素，如果不存在将会向WebDriver抛出错误。

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
###### cssSelector
$$是找到一组元素，$是找到一个元素

```Protractor
var items = element(by.css('.parent')).$$('li')
var child = element(by.css('.parent')).$('.child');

```
######isPresent()
确定某个元素是否在页面上存在。

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
###### isElementPresent()
和ElementFinder.isPresent()相同
######  equals()（有问题）
比较两个网页元素是否相同。
``` Prortractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    browser.driver.WebElement.equals(h1,label);
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});

```
###### getDriver()
返回这个实例的父驱动。
``` Prortractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 beforeEach(function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    var s=label.getDriver();
    console.log(s);
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});

```
###### getId()
承诺解决这个元素的JSON表示WebDriver线定义的协议
``` Prortractor
describe('test login module', function(){
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
     var a=element(by.buttonText('登录'));
    a.getId().then(function(location){
       console.log(location);
    });
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getRawId()
返回该元素的原始ID字符串ID.
``` Prortractor
describe('test login module', function(){
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
     var a=element(by.buttonText('登录'));
    a.getRawId().then(function(location){
       console.log(location);
    });
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
###### serialize()
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
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    //browser.driver.WebElement.equals(h1,label);
    label.serialize().then(function(location){
        console.log(location);
    });
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});

```
###### findElement()(有问题)
找到一个元素并在这个元素上发布命令，如果这个元素没有找到，那么此方法无效，在这个元素上发布的命令终止。
``` Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.get(testUrl);
    browser.WebElement.findElement(by.name('email')).sendKeys(name);
    browser.WebElement.findElement(by.name('password')).sendKeys(pwd);
     var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### isElementPresent()（不理解）
返回一个布尔类型的值，确定一个元素是否位于页面上。
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
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.isElementPresent(by.tagName('h1'))).toBe(true);
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});

```
###### findElements()
用来寻找一组满足这个定位要求的元素，然后让他们执行命令。
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
    var a=element(by.name('email')).sendKeys(name);
    var b=element(by.name('password')).sendKeys(pwd);
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
    var h1=browser.findElement(by.tagName('h1'));
    expect(h1.getText()).toBe('酒店列表(0)');
    var label=browser.findElement(by.tagName('label'));
    var s=label.findElements(by.tagName('option'));
    s.then(function(ad){
      console.log(ad);
    });
    expect(label.getText()).toBe('排序:');
    var options=element.all(by.options('field.label for field in orderByFields'));
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});
```
###### click()
用于点击命令完成时对事件的处理。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    })
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### sendKeys()
用于对文本输入框输入数值
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    })
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getTagName()
得到元素的标签名。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    expect(a.getTagName()).toBe('button');
    a.getTagName().then(function(location){
       console.log(location);

    })
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    })
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
######< getCssValue()>
寻CSS样式的属性名称
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    a.getCssValue().then(function(location){
       console.log(location);
    })
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
     h1.getCssValue().then(function(location){
       console.log(location);
    })
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getAttribute()
属性名称的查询，返回值要么是字符串要么是空。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    expect(a.getText()).toBe('登录');
    a.getAttribute().then(function(location){
       console.log(location);
    })
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getText()
得到元素的可见的innerText。返回值是可见的文本。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    expect(a.getText()).toBe('登录');
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getSize()
用像素为单位表示的元素的边界数值。返回一个{width:number, height:number} 对像。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    a.getSize().then(function(location){
       console.log(location);
    })
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### getLocation()
计算元素在页面空间的位置，返回一个{x:number, y:number} 对象
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    a.getLocation().then(function(location){
       console.log(location);
    })
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
###### isEnabled()
确定这个空间元素是否可以进行操作，结果是布尔类型。
```Protractor
describe('test login module', function(){
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
    var a=element(by.buttonText('登录'));
    expect(a.isEnabled()).toBe(true);
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```

