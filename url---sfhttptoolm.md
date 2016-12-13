```

#import "SFHttpTool.h"
#import <AFNetworking.h>
#import "LoginViewController.h"

@implementation SFHttpTool

/**
 *  发送get请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)get:(NSString *)url params:(NSDictionary *)params success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure
{
    
    AFHTTPSessionManager *session=[AFHTTPSessionManager manager];
     
    [session GET:url parameters:params progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
         if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
        
             if ([responseObject[@"code"]intValue] == 401) {
                 [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
             }else if([responseObject[@"code"]intValue] == 403) {
                 [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
             }
             dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                 
                 [SVProgressHUD dismiss];
                 LoginViewController *login = [[LoginViewController alloc]init];
                 UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                 [UIApplication sharedApplication].keyWindow.rootViewController = nav;
             });

         }else {
        
             success (responseObject);
             
         }
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
        if (failure) {
            failure(error);
        }
    }];

}

/**
 *  带进度条的get请求
 *
 *  @param url      <#url description#>
 *  @param params   <#params description#>
 *  @param progress <#progress description#>
 *  @param success  <#success description#>
 *  @param failure  <#failure description#>
 */

+(void)get:(NSString *)url params:(NSDictionary *)params progress:(void (^)(NSProgress *  downloadProgress))progress  success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure
{
    AFHTTPSessionManager *session = [AFHTTPSessionManager manager];
    [session GET:url parameters:params progress:^(NSProgress * _Nonnull downloadProgress) {
        if (progress) {
            progress(downloadProgress);
        }
        
    } success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
//        if (success) {
//            success(responseObject);
//        }
        if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
            
            if ([responseObject[@"code"]intValue] == 401) {
                [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
            }else if([responseObject[@"code"]intValue] == 403) {
                [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
            }
            dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                
                [SVProgressHUD dismiss];
                LoginViewController *login = [[LoginViewController alloc]init];
                UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                [UIApplication sharedApplication].keyWindow.rootViewController = nav;
            });
            
        }else {
            
            success (responseObject);
            
        }
        
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
       
        if (failure)
        {
            failure(error);
            
        }
        
    }];
}

/**
 *  post上传带进度条
 *
 *  @param url      <#url description#>
 *  @param params   <#params description#>
 *  @param progress <#progress description#>
 *  @param success  <#success description#>
 *  @param failure  <#failure description#>
 */
+(void)post:(NSString *)url params:(NSDictionary *)params progress:(void (^)(NSProgress *  downloadProgress))progress  success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure
{
    AFHTTPSessionManager *session = [AFHTTPSessionManager manager];
    
    [session POST:url parameters:params progress:^(NSProgress * _Nonnull uploadProgress) {
       
        if (progress)
        {
            progress(uploadProgress);
        }
        
    } success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
       
       //        if (success)
//        {
//            success(responseObject);
//        }
        if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
            
            if ([responseObject[@"code"]intValue] == 401) {
                [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
            }else if([responseObject[@"code"]intValue] == 403) {
                [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
            }
            dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                
                [SVProgressHUD dismiss];
                LoginViewController *login = [[LoginViewController alloc]init];
                UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                [UIApplication sharedApplication].keyWindow.rootViewController = nav;
            });
            
        }else {
            
            success (responseObject);
            
        }

        
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
       
        if (failure)
        {
            failure(error);
        }
    }];
    
}

/**
 *  发送post 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)post:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure
{

    AFHTTPSessionManager *session=[AFHTTPSessionManager manager];
    
// [session.requestSerializer setValue:@"application/html" forHTTPHeaderField:@"Content-Type"];
//    
    
    [session POST:url parameters:params progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
         
        if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
            
            if ([responseObject[@"code"]intValue] == 401) {
                [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
            }else if([responseObject[@"code"]intValue] == 403) {
                [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
            }
            dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                
                [SVProgressHUD dismiss];
                LoginViewController *login = [[LoginViewController alloc]init];
                UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                [UIApplication sharedApplication].keyWindow.rootViewController = nav;
            });
            
        }else {
            
            success (responseObject);
            
        }
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
        if (error) {
            failure(error);
        }
    }];
    
}

/**
 *  发送put 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)put:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure {
     
     AFHTTPSessionManager *session=[AFHTTPSessionManager manager];
     
     [session PUT:url parameters:params success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
          
         if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
             
             if ([responseObject[@"code"]intValue] == 401) {
                 [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
             }else if([responseObject[@"code"]intValue] == 403) {
                 [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
             }
             dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                 
                 [SVProgressHUD dismiss];
                 LoginViewController *login = [[LoginViewController alloc]init];
                 UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                 [UIApplication sharedApplication].keyWindow.rootViewController = nav;
             });
             
         }else {
             
             success (responseObject);
             
         }
     } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
          
          if (error) {
               
               failure(error);
              
          }
     }];
}

/**
 *  发送put 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)del:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure {
     
     AFHTTPSessionManager *session = [AFHTTPSessionManager manager];
     
     [session DELETE:url parameters:params success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
          
         if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
             
             if ([responseObject[@"code"]intValue] == 401) {
                 [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
             }else if([responseObject[@"code"]intValue] == 403) {
                 [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
             }
             dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                 
                 [SVProgressHUD dismiss];
                 LoginViewController *login = [[LoginViewController alloc]init];
                 UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                 [UIApplication sharedApplication].keyWindow.rootViewController = nav;
             });
             
         }else {
             
             success (responseObject);
             
         }
         
     } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
          
          
          if (error) {
               
               failure(error);
               
          }
     }];
}


+(void)startMultiPartUploadTaskWithURL:(NSString *)url
                           imagesArray:(NSArray *)images
                     parameterOfimages:(NSString *)parameter
                        parametersDict:(NSDictionary *)parameters
                      compressionRatio:(float)ratio
                          succeedBlock:(void (^)(id, id))succeedBlock
                           failedBlock:(void (^)(id, NSError *))failedBlock
                   uploadProgressBlock:(void (^)(float, long long, long long))uploadProgressBlock{
     
//     if (images.count == 0) {
//          NSLog(@"上传内容没有包含图片");
//          return;
//     }
     for (int i = 0; i < images.count; i++) {
          if (![images[i] isKindOfClass:[UIImage class]]) {
               NSLog(@"images中第%d个元素不是UIImage对象",i+1);
               return;
          }
     }
        AFHTTPSessionManager *session = [AFHTTPSessionManager manager];
       session.responseSerializer=[AFJSONResponseSerializer serializer];
     
     [session POST:url parameters:parameters constructingBodyWithBlock:^(id<AFMultipartFormData>  _Nonnull formData) {
          int i = 0;
          //根据当前系统时间生成图片名称
          NSDate *date = [NSDate date];
          NSDateFormatter *formatter = [[NSDateFormatter alloc]init];
          [formatter setDateFormat:@"yyyy年MM月dd日"];
          NSString *dateString = [formatter stringFromDate:date];
          
          for (UIImage *image in images) {
               NSString *fileName = [NSString stringWithFormat:@"%@%d.png",dateString,i];

               NSData *imageData;
               if (UIImagePNGRepresentation(image)) {
                   
//                  imageData =  [myImage imageData:image];
//                   SFLog(@"%ld kb",imageData.length/1024);
               }
              
               [formData appendPartWithFileData:imageData name:parameter fileName:fileName mimeType:@"image/jpeg"];
               
          }

          
     } progress:^(NSProgress * _Nonnull uploadProgress) {
          
     } success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
        
//          succeedBlock(session,responseObject);
         if ([responseObject[@"code"]intValue] == 401 || [responseObject[@"code"]intValue] == 403) {
             
             if ([responseObject[@"code"]intValue] == 401) {
                 [SVProgressHUD showErrorWithStatus:@"您的身份信息已过期,请重新登录"];
             }else if([responseObject[@"code"]intValue] == 403) {
                 [SVProgressHUD showErrorWithStatus:responseObject[@"msg"]];
             }
             dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
                 
                 [SVProgressHUD dismiss];
                 LoginViewController *login = [[LoginViewController alloc]init];
                 UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:login];
                 [UIApplication sharedApplication].keyWindow.rootViewController = nav;
             });
             
         }else {
             
             succeedBlock(session,responseObject);
             
         }

         
     } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
//          NSLog(@"%@",error);
          failedBlock(session,error);
          
     }];
     

}

#pragma mark --保存cookie---
-(void)saveCookie {
    
    //cookie存储
    NSData * cookiesData = [NSKeyedArchiver archivedDataWithRootObject: [[NSHTTPCookieStorage sharedHTTPCookieStorage] cookies]];
    
    USERDEFULT_ADD(cookiesData, @"zCookies");
    
    

}

#pragma mark --读取cookie---
-(void)readCookie {
    
    //cookie读取
    NSArray * cookies = [NSKeyedUnarchiver unarchiveObjectWithData: [[NSUserDefaults standardUserDefaults] objectForKey:@"zCookies"]];
    
    NSHTTPCookieStorage * cookieStorage = [NSHTTPCookieStorage sharedHTTPCookieStorage];
    for (NSHTTPCookie * cookie in cookies){
        [cookieStorage setCookie: cookie];
    }
}
@end

```