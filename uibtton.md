# UIButton的状态

#### lnormal（普通状态）

* 默认情况（Default）

* 对应的枚举常量：UIControlStateNormal


#### lhighlighted（高亮状态）

* 按钮被按下去的时候（手指还未松开）

* 对应的枚举常量：UIControlStateHighlighted


#### ldisabled（失效状态，不可用状态）

* 如果enabled属性为NO，就是处于disable状态，代表按钮不可以被点击

* 对应的枚举常量：UIControlStateDisabled


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

* \(void\)setTitle:\(NSString \*\)title forState:\(UIControlState\)state;
  设置按钮的文字

* \(void\)setTitleColor:\(UIColor \*\)color forState:\(UIControlState\)state;
  设置按钮的文字颜色

* \(void\)setImage:\(UIImage \*\)image forState:\(UIControlState\)state; 
  设置按钮内部的小图片

* \(void\)setBackgroundImage:\(UIImage \*\)image forState:\(UIControlState\)state;
  设置按钮的背景图片


## UIButton、UIImageView、UILabel的选择

* UIButton
  特点
  既能显示文字，又能显示图片（能显示2张图片，背景图片、内容图片）
  长按高亮的时候可以切换图片\文字
  直接通过addTarget...方法监听点击

* UIImageView
  能显示图片，不能直接通过addTarget...方法监听点击


* UILabel
  能显示文字，不能直接通过addTarget...方法监听点击
* 选择
     u仅仅是显示数据，不需要点击
     建议选择UIImageView、UILabel
* u不仅显示数据，还需要监听点击

  * 建议选择UIButton

  * 其实UIImageView、UILabel也可以通过手势识别器来监听（后面课程会学）


* 长按控件后，会改变显示的内容

  * 不用考虑了，选择UIButton（因为UIButton有highlighted这种状态）


* 同时显示2张图片：背景图片、内容图片

  * 不用考虑了，选择UIButton


