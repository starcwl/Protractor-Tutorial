##webdriver

###webdriver.WebElementPromise

######cancel
撤销
```Protractor
  this.cancel = goog.bind(el.cancel, el);
```
######isPending
未解决的
```Protractor
 this.isPending = goog.bind(el.isPending, el);
```
######then
```Protractor
this.then = goog.bind(el.then, el);
```
######thenCatch
```Protractor
  this.thenCatch = goog.bind(el.thenCatch, el);
```
######thenFinally
```Protractor
this.thenFinally = goog.bind(el.thenFinally, el);
```
######getId
推迟返回元素的id，直到被包装的WebElement已解决
```Protractor

```
###webdriver.AlertPromise

######cancel
```Protractor
 this.cancel = goog.bind(alert.cancel, alert);
```
######visPending
```Protractor
  this.isPending = goog.bind(alert.isPending, alert);
```
######then
```Protractor
this.then = goog.bind(alert.then, alert);
```
######thenCatch
```Protractor
  this.thenCatch = goog.bind(alert.thenCatch, alert);
```
######thenFinally
```Protractor
 this.thenFinally = goog.bind(alert.thenFinally, alert);
```
######getText
推迟返回文本直到promise警示框已经被解决
```Protractor

```
######accept
推迟动作，直到找到警示框
```Protractor

```
######dismiss
推迟动作，直到找到警示框
```Protractor

```
######sendKeys
推迟动作，直到找到警示框
```Protractor

```
###Inherited from webdriver.Alert

######getText
检索信息文本，通过警示框显示
```Protractor

```
######accept
接受这个警示框
```Protractor

```
######dismiss
解除这个警示框
```Protractor

```
######sendKeys
在这个警示框中设置响应文本
```Protractor

```
###webdriver.UnhandledAlertError

######getAlertText
文本显示未处理的警报
```Protractor

```
###webdriver.FileDetector