#by的方法
###1.addLocator()  
###2.binding()  
###3.exactBinding()  
###4.model()  
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
###5.buttonText():获得按钮中的文本信息
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
###6.partialButtonText()  
###7.repeater()：
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
       element(by.buttonText('是')).click();
       browser.refresh();
      var delitems=element.all(by.repeater('student in students'));
      expect(delitems.count()).toEqual(startitemsCount.then(function(start){
      return start;}));
    }); 
  });
  });  
###8.exactRepeater()  
###9.cssContainingText()  
###10.options()  
###11.deepCss()  

#Inherited from webdriver.By的方法

###1.className()  
###2.css()  
###3.id()  
###4.linkText:获得文本的链接()
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
###5.js()  
###6.name()  
###7.partialLinkText()  
###8.tagName()  
###9.xpath()  
