\/\/1.1创建UILable对象

UILabel \*label = \[\[UILabel alloc\] init\];

\/\/1.2设置frame

label.frame = CGRectMake\(100,100,200,75\);

\/\/1.3设置背景颜色

label.backgroundColor = \[UIColor redColor\];

\/\/1.4设置文字

label.text = @"da shen";

\/\/1.5居中

label.textAlignment = NSTextAlignmentCenter;

\/\/1.6设置字体大小

label.font = \[UIFont systemFontOfSize:20.f\];

label.font = \[UIFont boldSystemFontOfSize:25.f\];

label.font = \[UIFont italicSystemFontOfSize:20.f\];

\/\/1.7设置文字的颜色

label.textColor = \[UIColor purpleColor\];

\/\/1.8设置阴影（默认有值）

label.shadowColor = \[UIColor blackColor\];

label.shadowOffset = CGSizeMake\(-2,1\)

\/\/1.9显示模式

label.lineBreakMode = NSLineBreakByWordWrapping;

\/\/2.0添加到控制器的View中



