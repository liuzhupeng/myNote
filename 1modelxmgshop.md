###头文件
```
#import <Foundation/Foundation.h>

@interface XMGShop : NSObject

/** 图片的名称 */

@property (nonatomic, copy) NSString *icon;

/** 商品的名称 */

@property (nonatomic, copy) NSString *name;

// 提供构造方法

/*

- (instancetype)initWithIcon: (NSString *)icon name: (NSString *)name;

+ (instancetype)shopWithIcon: (NSString *)icon name: (NSString *)name;

 */

- (instancetype)initWithDict:(NSDictionary *)dict;

+ (instancetype)shopWithDict:(NSDictionary *)dict;

@end
```

---

###实现
```
#import "XMGShop.h"

@implementation XMGShop

/*

- (instancetype)initWithIcon:(NSString *)icon name:(NSString *)name{

 if (self = [super init]) {

 self.icon = icon;

 self.name = name;

 }

 return self;

}

+ (instancetype)shopWithIcon:(NSString *)icon name:(NSString *)name{

 return [[self alloc] initWithIcon:icon name:name];

}

 */

- (instancetype)initWithDict:(NSDictionary *)dict{

 if (self = [super init]) {

 self.icon = dict[@"icon"];

 self.name = dict[@"name"];

 }

 return self;

}

+ (instancetype)shopWithDict:(NSDictionary *)dict{

 return [[self alloc] initWithDict:dict];

}

@end
```

