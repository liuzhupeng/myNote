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
