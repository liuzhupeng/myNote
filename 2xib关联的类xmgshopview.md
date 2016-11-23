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