##重写Button按钮类的方法
```
#import "XMGButton.h"

@implementation XMGButton

- (instancetype)initWithFrame:(CGRect)frame{

 if (self = [super initWithFrame:frame]) {

 // 文本居中

 self.titleLabel.textAlignment = NSTextAlignmentCenter;

 // 改变图片的内容模式

 self.imageView.contentMode = UIViewContentModeCenter;

 }

 return self;

}

#pragma mark - 方式一

/**

 * 重写两个方法: 不要调用super,就是要重写掉

 * contentRect: 内容的尺寸,内容包括(imageView和label)

 */

/*

- (CGRect)titleRectForContentRect:(CGRect)contentRect{

 return CGRectMake(0, 0, 100, 70);

}

- (CGRect)imageRectForContentRect:(CGRect)contentRect{

 return CGRectMake(100, 0, 70, 70);

}

 */

#pragma mark - 方式二

- (void)layoutSubviews{

 [super layoutSubviews];

 // 设置子控件的位置

 self.titleLabel.frame = CGRectMake(0, 0, 100, 70);

 self.imageView.frame = CGRectMake(100, 0, 70, 70);

}

@end
```
###Controller调用Button重写后的方法
```
#import "ViewController.h"

#import "XMGButton.h"

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {

 [super viewDidLoad];

 // 1.1 创建按钮

 UIButton *button = [UIButton buttonWithType:UIButtonTypeCustom];



 // 1.2 设置frame

 button.frame = CGRectMake(100, 100, 170, 70);



 // 1.3 设置背景颜色

 button.backgroundColor = [UIColor purpleColor];



 // 1.4 设置文字

 [button setTitle:@"普通按钮" forState:UIControlStateNormal];



 // 1.5 设置内容图片

 [button setImage:[UIImage imageNamed:@"miniplayer_btn_playlist_normal"] forState:UIControlStateNormal];



 // 1.6 改变位置

 button.imageView.backgroundColor = [UIColor yellowColor];

 button.titleLabel.backgroundColor = [UIColor blueColor];

 // 注意: 在按钮外面改的尺寸,按钮的内部都会覆盖掉

 /*

 button.titleLabel.frame = CGRectMake(0, 0, 100, 70);

 button.imageView.frame = CGRectMake(100, 0, 70, 70);

 */



 [button titleRectForContentRect:CGRectMake(0, 0, 100, 70)];

 [button imageRectForContentRect:CGRectMake(100, 0, 70, 70)];



 [self.view addSubview:button];

}

@end



```