@interface ViewController\(\)

@property \(weak,nonatomic\) IBOutlet UITextFiled \*num1TextField;

@property \(weak,nonatomic\) IBOutlet UITextFiled \*num2TextField;

@property \(weak,nonatomic\) IBOutlet UILabel \*resultLabel;

@end

@implementation ViewController

- \(void\) viewDidLoad{

 \[super viewDidLoad\];

}

- \(IBAction\)sum\(\){

 \/\/1.拿到字符串

 NNstring \*sum1String = self.num1TextField.text;

 NNstring \*sum1String = self.num1TextField.text;

 \/\/判断

 if\(sum1String.length==0\){

 \/\/NSLog\(@"请输入第一个数"\);

 \[self showInfo:@"请输入第二个数"\]

 return;

 }

 \/\/2.把字符串转成数值

 NSInteger sum1 = \[sum1String integerValue\];

 NSInteger sum2 = \[sum2String integerValue\];

 \/\/2.相加

 NSInteger result = sum1+sum2;

 \/\/4.显示结果

 self.resultLabel.text = \[NSString stringWithFormat:@"%zd",result\];

}

- \(void\)showInfo:\(NSString \*\)info{

 \/\/创建对象

 UIAlertView \*alertView = \[\[UIAlertView alloc\] initWithTitle:@"输入有误" message:@"请输入第一个数" delegate:nil cancelButtonTitle:@"我知道了" otherButtoonTitles:nil,nil\]

 \/\/显示

 \[alertView show\]

}

@end



