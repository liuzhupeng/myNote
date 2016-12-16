- AFNetworking-cookies 的使用

```
[objc] view plain copy
</pre><p></p><pre name="code" class="objc">关于AFNetworking的 cookies的使用:  
   默认情况下AFNetWorking支持cookies.比如在调用登陆接口后,会保存cookies.在请求其他接口时,会携带cookies给服务器那边.  
   这里有个问题,如果要设置请求登陆时不保存cookies,这里可以在AFHTTPSessionManager设置 [self.requestSerializer setHTTPShouldHandleCookies:NO]来实现.  
   如果项目中要实现自己获取,删除cookies,方法如下:  
[objc] view plain copy
 1.获取登陆请求成功后保存的cookies:  
+ (NSString *)cookieValueWithKey:(NSString *)key  
{  
    NSHTTPCookieStorage *sharedHTTPCookieStorage = [NSHTTPCookieStorage sharedHTTPCookieStorage];  
  
    if ([sharedHTTPCookieStorage cookieAcceptPolicy] != NSHTTPCookieAcceptPolicyAlways) {  
        [[NSHTTPCookieStorage sharedHTTPCookieStorage] setCookieAcceptPolicy:NSHTTPCookieAcceptPolicyAlways];  
    }  
  
    NSArray         *cookies = [sharedHTTPCookieStorage cookiesForURL:[NSURL URLWithString:@"http://192...."]];  
    NSEnumerator    *enumerator = [cookies objectEnumerator];  
    NSHTTPCookie    *cookie;  
    while (cookie = [enumerator nextObject]) {  
        if ([[cookie name] isEqualToString:key]) {  
            return [NSString stringWithString:[[cookie value] stringByReplacingPercentEscapesUsingEncoding:NSUTF8StringEncoding]];  
        }  
    }  
  
    return nil;  
}  
[objc] view plain copy
2.删除cookies (key所对应的cookies) ///因为cookies保存在NSHTTPCookieStorage.cookies中.这里删除它里边的元素即可.  
+ (void)deleteCookieWithKey:(NSString *)key  
{  
    NSHTTPCookieStorage *cookieJar = [NSHTTPCookieStorage sharedHTTPCookieStorage];  
  
    NSArray *cookies = [NSArray arrayWithArray:[cookieJar cookies]];  
  
    for (NSHTTPCookie *cookie in cookies) {  
        if ([[cookie name] isEqualToString:key]) {  
            [cookieJar deleteCookie:cookie];  
        }  
    }  
}  

```