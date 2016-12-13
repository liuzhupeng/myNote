#post 
```


```
```
#import <Foundation/Foundation.h>

@interface SFHttpTool : NSObject

/**
 *  发送post 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)post:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure;
/**
 *  发送get请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)get:(NSString *)url params:(NSDictionary *)params success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure;



/**
 *  post上传带进度条
 *
 *  @param url      <#url description#>
 *  @param params   <#params description#>
 *  @param progress <#progress description#>
 *  @param success  <#success description#>
 *  @param failure  <#failure description#>
 */
+(void)post:(NSString *)url params:(NSDictionary *)params progress:(void (^)(NSProgress *  downloadProgress))progress  success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure;



/**
 *  带进度条的get请求
 *
 *  @param url      <#url description#>
 *  @param params   <#params description#>
 *  @param progress <#progress description#>
 *  @param success  <#success description#>
 *  @param failure  <#failure description#>
 */

+(void)get:(NSString *)url params:(NSDictionary *)params progress:(void (^)(NSProgress *  downloadProgress))progress  success:(void (^)(id json)) success failure:(void(^)(NSError *error))failure;

/**
 *  发送put 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)put:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure;

/**
 *  发送put 请求
 *
 *  @param url     请求地址
 *  @param params  请求参数
 *  @param success 成功
 *  @param failure 失败
 */
+(void)del:(NSString *)url params:(NSDictionary *)params success:(void(^)(id json))success failure:(void(^)(NSError *error ))failure;


/**
 *  上传带图片的内容，允许多张图片上传（URL）POST
 *
 *  @param url                 网络请求地址
 *  @param images              要上传的图片数组（注意数组内容需是图片）
 *  @param parameter           图片数组对应的参数
 *  @param parameters          其他参数字典
 *  @param ratio               图片的压缩比例（0.0~1.0之间）
 *  @param succeedBlock        成功的回调
 *  @param failedBlock         失败的回调
 *  @param uploadProgressBlock 上传进度的回调
 */
+(void)startMultiPartUploadTaskWithURL:(NSString *)url
                           imagesArray:(NSArray *)images
                     parameterOfimages:(NSString *)parameter
                        parametersDict:(NSDictionary *)parameters
                      compressionRatio:(float)ratio
                          succeedBlock:(void(^)(id operation, id responseObject))succeedBlock
                           failedBlock:(void(^)(id operation, NSError *error))failedBlock
                   uploadProgressBlock:(void(^)(float uploadPercent,long long totalBytesWritten,long long totalBytesExpectedToWrite))uploadProgressBlock;





@end
```

