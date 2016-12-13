```
#import <Foundation/Foundation.h>
#import "MJExtension.h"
#import "HWStatus.h"
#import "HWUser.h"

#import "HWPerson.h"
#import "HWBook.h"

int main(int argc, const char * argv[])
{
    @autoreleasepool {
        NSDictionary *dict = @{
                               @"name" : @"张三",
                               @"books" : @[
                                       @{
                                           @"name" : @"葵花1",
                                           @"price" : @"10.6"
                                           },
                                       @{
                                           @"name" : @"葵花2",
                                           @"price" : @"10.9"
                                           },
                                       @{
                                           @"name" : @"葵花3",
                                           @"price" : @"17.6"
                                           },
                                       @{
                                           @"name" : @"葵花4",
                                           @"price" : @"14.4"
                                           }
                                       ]
                               
                               };
        
        HWPerson *person = [HWPerson objectWithKeyValues:dict];
        
        NSLog(@"-----");
    }
    return 0;
}

void test2()
{
    HWUser *user = [[HWUser alloc] init];
    user.profile_image_url = @"abc.png";
    user.idstr = @"4435435";
    user.name = @"旺财";
    
    HWStatus *status = [[HWStatus alloc] init];
    status.mytext = @"哈哈哈哈";
    status.user = user;
    
    NSDictionary *dict = [status keyValues];
    NSLog(@"%@", dict);
}

/**
 *  简单的字典转模型
 */
void test()
{
    NSDictionary *dict = @{
                           @"id" : @"123424324",
                           @"text" : @"哈哈哈哈哈，天气真好",
                           @"user" : @{
                                   @"idstr" : @"987766",
                                   @"name" : @"搞笑排行榜",
                                   @"profile_image_url" : @"http://abc.png"
                                   }
                           
                           };
    
    HWStatus *status = [HWStatus objectWithKeyValues:dict];
    
    NSLog(@"------");
}
```
- HWPerson.h

```
#import <Foundation/Foundation.h>

@interface HWPerson : NSObject
@property (nonatomic, copy) NSString *name;
@property (nonatomic, strong) NSArray *books;
@end
```
- HWPerson.m

```
#import "HWPerson.h"
#import "MJExtension.h"
#import "HWBook.h"

@implementation HWPerson

- (NSDictionary *)objectClassInArray
{
    return @{@"books" : [HWBook class]};
}

@end
```