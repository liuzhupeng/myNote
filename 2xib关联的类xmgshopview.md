##头文件
```
#import <UIKit/UIKit.h>

@class XMGShop;

@interface XMGShopView : UIView

/** 数据模型 */

@property (nonatomic, strong) XMGShop *shop;

// 快速构造方法

+ (instancetype)shopView;

@end

```
###
```
#import "XMGShopView.h"

#import "XMGShop.h"

@interface XMGShopView ()

@property (weak, nonatomic) IBOutlet UIImageView *iconView;

@property (weak, nonatomic) IBOutlet UILabel *titlelabel;

@end

@implementation XMGShopView

+ (instancetype)shopView{

 return [[[NSBundle mainBundle] loadNibNamed:NSStringFromClass(self) owner:nil options:nil] firstObject];

}

//- (void)awakeFromNib

- (void)setShop:(XMGShop *)shop{
 _shop = shop;
 // 设置子控件的数据
 self.iconView.image = [UIImage imageNamed:shop.icon];
 self.titlelabel.text = shop.name;
}

@end



```