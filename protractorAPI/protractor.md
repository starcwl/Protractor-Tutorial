##protractor
###brower
浏览器对象，可以理解成在测试网页中的网页浏览器。
#####getProcessedConfig
得到当前正在运行的线程配置对象，他将包含当前运行实例的规格和性能。
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
    browser.getProcessedConfig().then(function(s){
      console.log(s)});
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
     var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    //expect(element.equals(a,h1))toBe(false);
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####forNewDriverInstance
在交互测试中复刻一个实例来使用。
```protractor
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
    //expect(element.equals(a,h1))toBe(false);
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
        browser.forkNewDriverInstance();
  });
});
```
#####restart
重启浏览器实例。
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.restart();
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
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####useAllAngular2AppRoots
在定位元素的或者等待稳定的时候代替使用单一的根元素，而是寻找所有可用的angular程序。仅在Angular２中兼容。
#####waitForAngular
等待一段时间，让程序结束上一个页面的操作再进入下一个页面实例。
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
    //expect(element.equals(a,h1))toBe(false);
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
 it('should into my work',function(){
      browser.waitForAngular();
    var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';
    var text=element(by.linkText('我的任务'))  ;
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
#####findElement

#####findElements
#####isElementPresent
#####addMockModule
#####clearMockModules
#####removeMockModule
#####getRegisteredMockModules
#####get
#####refresh
#####navigate
#####setLocation
#####getLocationAbsUrl
#####debugger
#####enterRepl
#####pause
#####attachToSession
#####createSession
#####controlFlow
#####schedule
#####setFileDetector
#####getSession
#####getCapabilities
#####quit
#####actions
#####touchActions
#####executeAsyncScript
#####call
#####wait
#####sleep
#####getWindowHandle
#####getAllWindowHandles
#####getPageSource
#####close
#####get
#####getCurrentUrl
#####getTitle
#####findElement
#####isElementPresent
#####findElements
#####takeScreenshot
#####manage
#####navigate
#####switch To
#####Navigation
######to
######back
######forward
######refresh
#####Options
######addCookie
######deleteAllCookies
######deleteCookie
######logs
######timeouts
######window
#####Timeouts
######implicitlyWait
######setScriptTimeout
######pageLoadTimeout
#####Window
######getPosition
######setPosition
######getSize
######setSize
######maximize
#####Logs
######get
######getAvailableLogTypes
#####TargetLocator
######activeElement
######defaultContent
######frame
######window
######alert