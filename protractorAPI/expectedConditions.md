###expectedConditions
代表一个canned函数库，在预期条件下对protractor是有用的，尤其在处理non-angular应用的时候。每个条件返回一个函数 ，等于一个promise，你可以混合使用and，or，and/or not多个组合条件。你也可以将这些条件和任何你写的其他的条件一起使用
######not
不显示not方法里面的内容
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
var titleIsNotFoo = EC.not(EC.titleIs('Foo'));
console.log ('***');
// Waits for title to become something besides 'foo'.
browser.wait(titleIsNotFoo, 5000);
  });
 });

```
######and
显示所有的内容
```Protractor

```
######or
显示or方法中任意一个内容
```Protractor

```
######alertIsPresent
显示警示框
```Protractor

```
######elementToBeClickable
检验一个元素是可见的和能够被点击
```Protractor

```
######textToBePresentInElement
检验一个元素中的文本是否显示
```Protractor

```
######textToBePresentInElementValue
检验一个元素值中的文本是否显示
```Protractor

```
######titleContains
检验标题中包含的区分大小写的子字符串
```Protractor

```
######titleIs
检验页面的标题
```Protractor

```
######presenceOf
检验一个元素出现在在页面DOM上
```Protractor

```
######stalenessOf
检验一个元素没有附加到页面的DOM上
```Protractor

```
######visibilityOf
检验一个元素出现在页面DOM上并且是可见的
```Protractor

```
######invisibilityOf
检验一个元素是不可见的，也没出现在页面的DOM上
```Protractor

```
######elementToBeSelected
检验选项被选择
```Protractor

```