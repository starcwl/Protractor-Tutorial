

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
调用此方法可以找到一个把当前元素作为起点的一个新的数组。方法结果返回一个包含当前数组子元素的新的数组。
view 
``` Protractor
<div id='id1' class="parent">
  <ul>
    <li class="foo">1a</li>
    <li class="baz">1b</li>
  </ul>
</div>
<div id='id2' class="parent">
  <ul>
    <li class="foo">2a</li>
    <li class="bar">2b</li>
  </ul>
</div>
```
code
```
var foo = element.all(by.css('.parent')).all(by.css('.foo'))
expect(foo.getText()).toEqual(['1a', '2a'])
var baz = element.all(by.css('.parent')).all(by.css('.baz'))
expect(baz.getText()).toEqual(['1b'])
var nonexistent = element.all(by.css('.parent')).all(by.css('.NONEXISTENT'))
expect(nonexistent.getText()).toEqual([''])
```
###### filter()
通过这个filter方法是为了找到一组符合filter方法的一组元素，因为filter（）不能检索到列表中的  所有元素，所以它一般用于一个网页对象。
view
``` Protractor
<ul class="items">
  <li class="one">First</li>
  <li class="two">Second</li>
  <li class="three">Third</li>
</ul>
```
code
```
element.all(by.css('.items li')).filter(function(elem, index) {
  return elem.getText().then(function(text) {
    return text === 'Third';
  });
}).first().click();
```
###### get()
通过索引找到数组中的一个元素，索引从０开始。
view
``` Protractor
<ul class="items">
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
code
```
var list = element.all(by.css('.items li'));
expect(list.get(0).getText()).toBe('First');
expect(list.get(1).getText()).toBe('Second');
```
######first()
找到数组中的第一个元素。
view
``` Protractor
<ul class="items">
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
code

```
var first = element.all(by.css('.items li')).first();
expect(first.getText()).toBe('First');
```
######last()
找到数组中的最后一个元素。
```Protractor
<ul class="items">
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
code
```
var last = element.all(by.css('.items li')).last();
expect(last.getText()).toBe('Third');
```
###### count()
这个数组所代表的元素的个数，结果不一定是整型。它返回的是一个Promise对象不能直接用于四则运算。
``` Protractor
<ul class="items">
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
code

```
var list = element.all(by.css('.items li'));
expect(list.count()).toBe(3);
```
###### locator()
返回最相关的定位说明。
```Protractor

  // returns by.css('#ID2')
$('#ID1').$('#ID2').locator();

```
######each()
调用数组中的每个元素执行each()中定义的方法，输出方法的结果。

View
``` view 
<ul class="items">
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
Code
```
element.all(by.css('.items li')).each(function(element, index) {
  // Will print 0 First, 1 Second, 2 Third.
  element.getText().then(function (text) {
    console.log(index, text);
  });
});
```
######map()
让ElementArrayFinder中的元素执行map方法，回调方法的结果作为第一个参数。索引作为第二个参数。
view
``` Protractor
<ul class="items">
  <li class="one">First</li>
  <li class="two">Second</li>
  <li class="three">Third</li>
</ul>
```
Code
```
var items = element.all(by.css('.items li')).map(function(elm, index) {
  return {
    index: index,
    text: elm.getText(),
    class: elm.getAttribute('class')
  };
});
expect(items).toEqual([
  {index: 0, text: 'First', class: 'one'},
  {index: 1, text: 'Second', class: 'two'},
  {index: 2, text: 'Third', class: 'three'}
]);
```
######reduce()(有问题)
实现一个累加器，通过这个累加器把所需要的参数加到一起，然后统一输出结果。
view
```Protractor
<ul class="items">
  <li class="one">First</li>
  <li class="two">Second</li>
  <li class="three">Third</li>
</ul>
```
code
```
var value = element.all(by.css('.items li')).reduce(function(acc, elem) {
  return elem.getText().then(function(text) {
    return acc + text + ' ';
  });
}, '');
expect(value).toEqual('First Second Third ');

```

###### evaluate()
评估输入是否时当前元素的范围。
view
```Protractor
<span id="foo">{{variableInScope}}</span>
```
Code
```
var value = element(by.id('foo')).evaluate('variableInScope');
```
######allowAnimation()
确定动画在当前基础元素中是否允许
code 
```Protractor
element(by.css('body')).allowAnimations(false);

```
####element的方法：
element 是ElementArrayFinder 中一个简单的单个元素的代表。你可以把ElementFinder看作是一个WebElement并对它进行一系列操作，尤其是你可以进行和一系列操作，例如点击等。　　　　　
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
确定某个元素是否在页面上存在,不管它是否在页面上呈现出来。它和isDisplayed()的区别是，isDispalyed()必须在页面上呈现出来。
view
```Protractor
<span>{{person.name}}</span>
```
Code
```
// Element exists.
expect(element(by.binding('person.name')).isPresent()).toBe(true);

// Element not present.
expect(element(by.binding('notPresent')).isPresent()).toBe(false);
```
###### isElementPresent()
方法的结果意义和isPresent()相同。但是用法有点不同。
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

