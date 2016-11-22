# UIButton的状态

#### lnormal（普通状态）

* Ø默认情况（Default）

* Ø对应的枚举常量：UIControlStateNormal


#### lhighlighted（高亮状态）

* Ø按钮被按下去的时候（手指还未松开）

* Ø对应的枚举常量：UIControlStateHighlighted


#### ldisabled（失效状态，不可用状态）

* Ø如果enabled属性为NO，就是处于disable状态，代表按钮不可以被点击

* Ø对应的枚举常量：UIControlStateDisabled


## 设置按钮的背景图片

* 设置按钮在不同状态下的背景图片


（为了保证高亮状态下的图片正常显示，必须设置按钮的type为custom 

## 按钮的样式

在用代码创建按钮的同时指定按钮样式
UIButton \*btn = \[UIButton buttonWithType:UIButtonTypeCustom\]; 
UIButtonTypeCustom：无类型，按钮的内容需要自定义
UIButtonTypeDetailDisclosure： 
UIButtonTypeInfoLight： 
UIButtonTypeInfoDark： 
UIButtonTypeContactAdd： 

## UIButton的常见设置 






