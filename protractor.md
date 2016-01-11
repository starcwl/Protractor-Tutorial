**使用须知：Protractor编写测试的核心是查找DOM元素，与其交互，然后查看交互后的状态与你的期望是否一致。所以查找DOM元素并与之交互显的非常重要。Protractor提供了一个全局函数element，其接受一个Locator对象并返回一个ElementFinder对象。该函数会返回单个元素。如果你想返回多个元素，可以使用element.all函数，其接受一个Locator对象并返回ElementArrayFinder对象。ElementFinder对象有一组方法，用于元素交互，比如click()，getText(),sendKeys等。Locator对象的创建主要使用全局的by对象，其提供一些API来生成Locator对象以供element或element.all函数使用。**  
**1.browser,全局对象,代表当前浏览器的一个实例,常用的get方法用来实现浏览器改变地址**  
**2.element,全局对象,提供像jquery里负责查找文档元素的功能,常于by对象联合使用**  
**3.by, 全局对象,提供一个选择器类型,比如可以通过css,model,bind等特性来查找一个元素**  
##element(元素)  
  *element.all(locator)*  
###(1)clone:复制元素数组  
describe('test login module', function(){  
  var time = new Date;  
  console.log(time);  
  var testUrl = '/bd/login';  
  it('clone',function(){  
  browser.get('http://www.aihangyun.com/bd/');  
  var ul1=element.all(by.css('.dropdown-menu scrollable-menu'));  
  var ul2=ul1.clone();  
  expect(ul1.count()).toBe(ul2.count());  
  });  
   });  
###(2)count:获取元素个数  
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
  it('count',function(){  
        browser.get('http://www.aihangyun.com/bd/hotel#/my');  
        var options=element.all(by.options('field.label for field in orderByFields'));  
    expect(options.count()).toBe(2);  
    expect(options.get(0).getText()).toBe('名称');  
    expect(options.get(1).getText()).toBe('更新时间');  
  });  
});  
###(3)all:查找其一组子元素  
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
  it('all',function(){  
        browser.get('http://www.aihangyun.com/bd/');  
          var ul2=element.all(by.css('.dropdown-menu'));  
    var text=element(by.linkText('云管理'));  
    text.click();  
    expect(ul2.isDisplayed()).toBeTruthy();  
  });  
});  
###(4)get: 根据索引获取指定元素  
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
  }):  
###(5)filter:提供一个过滤器过滤其中的元素  

###(6)first:获取第一个元素
element.all(by.css('myclass')).first();  
###(7)last:获取最后一个元素  
element.all(by.css('myclass')).last();
###(8)locator:返回locator对象  
###(9)each:从0计数，依次输出元素  
###(10)map:  
###(11)reduce:让每一个元素变成单一的值  
###(12)evaluate:原语将得到解决,函数将被转换为字符串,将作为WebElement返回元素  
###(13)allowAnimations:解决是否允许动画    
*webdriver.webElement*
###(1)sendKeys:将将一个或多个按键消息发送到活动窗口，就如同用键盘进行输入一样。
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
  }):  
###(2)getTagName:
###(3)getText:获得文本信息
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
    var label=element(by.tagName('label'));  
    expect(label.getText()).toBe('排序:');  
    var options=element.all(by.options('field.label for field in orderByFields'));  
    expect(options.count()).toBe(2);  
    expect(options.get(0).getText()).toBe('名称');  
    expect(options.get(1).getText()).toBe('更新时间');  
  });  
*by*
###(1)linkText:获得文本的链接
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
  it('linkText',function(){  
  var targetUrl2='http://www.aihangyun.com/bd/hotel#/my';  
    var text=element(by.linkText('我的任务'));  
    text.click();  
    expect(browser.getCurrentUrl()).toBe(targetUrl2);  
  });  
  });    
