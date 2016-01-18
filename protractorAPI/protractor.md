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
找到一个定位的元素
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=browser.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####findElements
找到一组定位的元素。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=browser.findElements(by.css('.page-header'));
    console.log(h1);
   // expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####isElementPresent
测试一个元素是否在页面上呈现出来。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    var s=browser.isElementPresent(by.css('.page-header'));
    s.then(function(as){
      console.log(as);
    });
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####addMockModule
增加一个模块在用例执行前。模块注册在已存在模块所在的页面上，并且和已存在模块相同的名字。
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    browser.addMockModule('email',function(){
    angular.module('email',[]).value('name');
    });
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####clearMockModules
清理注册的MockModules列表
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    browser.clearMockModule;
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####removeMockModule
清除注册的MockModule
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    browser.removeMockModule('email');
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getRegisteredMockModules
得到当前注册的MockModules列表
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    browser.addMockModule('email',function(){
    angular.module('email',[]).value('name');
    });
    var ad =browser.getRegisteredMockModules();
    console.log(ad);
    var a=element(by.buttonText('登录'));
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####get
让页面加载到指定网址。
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
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
#####refresh
实现一个页面的刷新，实现了该页面的重新加载。
```Protractor
describe('test login module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
  browser.isElementPresent;
 it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
    browser.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    var a=element(by.buttonText('登录'));
    a.click();
    browser.refresh();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####navigate
为navigation混入一个执行方法,以至于他可以像以前的driver.navigate()那样引用。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.navigate();
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####setLocation
通过页面导航使其浏览另一个页面。
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
       browser.setLocation('login');
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####getLocationAbsUrl(得不到？)
从AngularJS中返回当前的绝对地址。
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
    expect(browser.getLocationAbsUrl()).toBe(targetUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####debugger(没有显示)
增加一个任务来实现测试的执行和暂停并且在浏览器中加入帮助方法，以便于调试可以在浏览器的控制台进行。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    var sd=browser.debugger();
    console.log(sd);
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####enterRepl
返回一个重要的调试端口。
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
    browser.enterRepl();
    browser.debugger;
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####pause
返回一个重要的调试端口。
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
    browser.pause();
    //browser.debugger;
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####attachToSession
为已存在的协议建立一个新的webDriver客户端。
```Protractor

```

#####createSession
建立一个新的webDriver协议。
#####controlFlow
返回这个实例使用的控制流。
#####schedule

#####setFileDetector
建立实例应当用到的文件检测器
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    var s=browser.driver.setFileDetector(h1);
    console.log(s);
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####getSession
得到浏览器的客户端协议
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.getSession().then(function(ad){
      console.log(ad);
    });  
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getCapabilities
得到解决这个实例的能力。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.getCapabilities().then(function(s){
      console.log(s);
    });
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####quit
停止当前协议，方法执行后实例将会无效或者说将不会向浏览器提交命令。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.quit().then(function(s){
      console.log(s);
    });
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####actions
创建一个新的动作队列。当出现.perform()时队列结束。
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
    var a=element(by.buttonText('登录'))
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.actions().
    mouseUp().perform();
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####touchActions
创建一个接触动作序列，同样以.perform()结束。
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
    var a=element(by.buttonText('登录'))
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.touchActions().
    tap(h1).doubleTap(h1).perform();
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####executeScript(有问题)
根据网页的内容执行一个javascript代码，并返回一个代表代码值的promise对象。
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
    var a=element(by.buttonText('登录'))
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.executeScript("alert('Hello');");
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####executeAsyncScript(有问题)
根据网页的上下文执行一个同步的脚本代码，同样返回一个代表代码值的一个promise对象。
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
    var start = new Date().getTime();
    browser.driver.executeAsyncScript(
    'window.setTimeout(arguments[arguments.length - 1], 500);').
    then(function() {
      console.log(
          'Elapsed time: ' + (new Date().getTime() - start) + ' ms');
    });
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    var a=element(by.buttonText('登录'))
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    browser.driver.executeScript("alert('Hello');");
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####call
执行一个常用方法，并返回一个决定方法结果的promise对象。
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
    var a=element(by.buttonText('登录'))
    a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
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
    var options=element.all(by.options('field.label for field in orderByFields'));
    browser.driver.call(options.count(),options,'a');
    expect(options.count()).toBe(2);
    expect(options.get(0).getText()).toBe('名称');
    expect(options.get(1).getText()).toBe('更新时间');
  });
});

```
#####wait
等待条件执行。参数是条件和执行条件所需要的时间，条件可以是webdriver.until.Condition，一个常用方法或者是作为一个webdriver.promise.Promise。返回值是条件方法实现的第一真实值或者是超时的拒绝值。
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
    //var a=element(by.buttonText('登录'))
    browser.driver.wait(element(by.buttonText('登录')).click(),1000);
    //a.click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####sleep
设定一个driver的休眠时间。返回一个决定什么时候休眠结束的promise的对象。
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
    var a=element(by.buttonText('登录'))
    a.click();
    browser.driver.sleep(1000);
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getWindowHandle
检索当前窗口的处理，返回值为通过当前窗口处理解决的promise对象。
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
    var a=element(by.buttonText('登录'))
    a.click();
    browser.driver.getWindowHandle().then(function(a){
      console.log(a);
    });
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getAllWindowHandles
检索当前可获得的窗口处理列表。返回值将会是解决一组窗口处理的promise值。
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
    var a=element(by.buttonText('登录'))
    a.click();
    browser.driver.getAllWindowHandles().then(function(a){
      console.log(a);
    });
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getPageSource
检索当前页面资源。返回的页面资源是一个不被格式化或者不会逃一样的从浏览器作出相应的资源。
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
    var a=element(by.buttonText('登录'))
    a.click();
    browser.driver.getPageSource().then(function(a){
      console.log(a);
    });
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####close(有问题)
关闭当前窗口的命令。返回值是一个决定什么时候命令完成的promise值。
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
    var a=element(by.buttonText('登录'))
    a.click();
    browser.driver.close();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####get(有问题)
导航到给的URL地址。返回值是一个决定什么时候文件加载结束的promise的值。
```Protractor
describe('test zhuye module', function(){
  var time = new Date;
  console.log(time);
  var testUrl = '/bd/login';
it('should login with correct account name & password', function(){
    var name = 'chenwulin@aihanginns.com';
    var pwd = 'helloworld';
    var targetUrl = 'http://www.aihangyun.com/bd/';
     browser.driver.get(testUrl);
    element(by.name('email')).sendKeys(name);
    element(by.name('password')).sendKeys(pwd);
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####getCurrentUrl
检索URL的当前页面。
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
    element(by.buttonText('登录')).click();
    //expect(browser.getLocationAbsUrl()).toBe(targetUrl);
    expect(browser.driver.getCurrentUrl()).toBe(targetUrl);
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####getTitle
检索当前页面的标题。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    browser.driver.getTitle().then(function(a){
      console.log(a);
    });
    var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####findElement
找到页面的一个元素，如果元素不能够被找到将会返回一个bot.ErrorCode.NO_SUCH_ELEMENT结果。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=browser.driver.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});

```
#####isElementPresent
检查一个页面元素是否存在
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
     browser.driver.isElementPresent(by.css('.page-header')).then(function(a){
      console.log(a);
    });
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####findElements
寻找页面的多个元素。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var h1=browser.driver.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
 it('should display a manager',function(){
    var ul1=browser.driver.findElements(by.css('.dropdown-menu'));
    var text=element(by.linkText('云管理'));
    text.click();
   });
});
```
#####takeScreenshot
得到一个屏幕截图。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    browser.driver.takeScreenshot().then(function(a){
      console.log(a);
    });
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
 it('should display a manager',function(){
    var ul1=browser.driver.findElements(by.css('.dropdown-menu'));
    var text=element(by.linkText('云管理'));
    text.click();
   });
});
```
#####manage
返回一个界面选项。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    browser.driver.manager();
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
 it('should display a manager',function(){
    var ul1=browser.driver.findElements(by.css('.dropdown-menu'));
    var text=element(by.linkText('云管理'));
    text.click();
   });
});
```
#####navigate(有时候出现超时现象)
返回实例的导航界面。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.navigate();
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####switch To
返回这个实例的目标定位界面。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.switchTo();
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####Navigation
在浏览器历史中的导航界面。

######to
导航到新的URL的值（有问题）
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.Navigation(browser.driver).to(testUrl);
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
######back(有问题)
导航到浏览器历史中的上一个网页。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.Navigation.back();
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
######forward（有问题）
向前移动浏览器历史中的网页地址。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.Navigation.forward();
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
######refresh(有问题)
刷新当前的网页。
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
    element(by.buttonText('登录')).click();
    expect(browser.getCurrentUrl()).toBe(targetUrl);
    var a =browser.driver.Navigation.refresh();
    console.log(a);
    var h1=browser.driver.findElement(by.css('.page-header'));
    //var h1=element(by.css('.page-header'));
    expect(h1.getText()).toBe('AiHang Business Development Management Console');
  });
});
```
#####Options（有问题）
提供管理浏览器和驱动状态的方法。
######addCookie
增加一个网页cookie。
```Protractor

```
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