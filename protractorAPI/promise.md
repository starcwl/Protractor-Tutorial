##promise

###promise

######captureStackTrace
生成一个错误捕捉当前的堆栈跟踪。
```Protractor

```
######CancellationError
当一个promise计算取消了时候，使用错误
```Protractor

```
######MultipleUnhandledRejectionError
当有多个未处理的promise，在一个任务或回调中拒绝检测，使用错误
```Protractor

```
######Thenable
thenble是一个使用then方法的promise-like对象，可能被用来在promise值上安排回调，
```Protractor

```
######Promise
代表完成操作的最终值
```Protractor

```
######Deferred
代表一个值在将来的某个时间点被解决
```Protractor

```
######isPromise
判断一个值是否应该被视为一个承诺。
```Protractor

```
######delayed
创建一个promise,将在未来设定的时间解决。
```Protractor

```
######defer
创建一个新的延迟对象。
```Protractor

```
######fulfilled
创建一个使用给出的值已经解决的promise
```Protractor

```
######rejected
创建一个已经被给出的原因拒绝的promise
```Protractor

```
######checkedNodeCall
包装一个node-style作为最终参数回调的函数
```Protractor

```
######when
在一个promise值上注册一个观测器,返回一个新的将会被解决的promise，当给出这个值
```Protractor

```
######asap
一旦promise的值解决了，就调用相应的回调函数
```Protractor

```
######all
给出一个promise的数组，将会返回一个promise，将输入数组的值的实现价值将会被实现。
```Protractor

```
######map
数组的每一个元素调用一个函数，并将结果插入到一个新的数组，他是用来通过这个函数返回promise的实现价值
```Protractor

```
######filter
在一个数组中，每个元素调用一个函数，如果函数返回值为真，把这个元素添加到新的数组中
```Protractor

```
######fullyResolved
返回一个promise，它在一个完全解决状态下使用输入的值被解决
```Protractor

```
######ControlFlow
处理执行任务的计划，每一个都可能是异步操作
```Protractor

```
######EventType
事件可能会通过一个webdriver.promise.ControlFlow.被发出
```Protractor

```
######setDefaultFlow
当没有其他动作时，更改默认流
```Protractor

```
######controlFlow
当前活跃的控制流
```Protractor

```
######createFlow
创建一个新的控制流
```Protractor

```
######isGenerator
测试是一个函数，是一个发电机
```Protractor

```
######consume
消耗一个GeneratorFunction
```Protractor

```