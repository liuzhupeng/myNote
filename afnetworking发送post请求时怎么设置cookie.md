- AFNetworking发送post请求时怎么设置cookie
```
//发送post请求的同时传入cookie
+ (void)requestCookieWithPath:(NSString *)path
                 Params:(NSDictionary *)params
                 Method:(NSString *)method
                Success:(HttpSuccessBlock)success{
    
    //创建post请求
    
    //创建AFHTTPClient对象
    AFHTTPClient *client = [AFHTTPClient clientWithBaseURL:[NSURL URLWithString:kBaseUrl]];
    
    NSMutableURLRequest *post = [client requestWithMethod:method path:path parameters:params];
    
    NSData *cookiesData = [[NSUserDefaults standardUserDefaults]objectForKey:@"Set-Cookie"];
    if ([cookiesData length]) {
        NSArray *cookies = [NSKeyedUnarchiver unarchiveObjectWithData:cookiesData];
        NSHTTPCookie *cookie;
        for (cookie in cookies) {
            [[NSHTTPCookieStorage sharedHTTPCookieStorage]setCookie:cookie];
        }
    }
    
    //创建AFJSONRequestOperation对象
    NSOperation *operation = [AFJSONRequestOperation JSONRequestOperationWithRequest:post success:^(NSURLRequest *request, NSHTTPURLResponse *response, id JSON) {
        
        success(JSON);
        
    } failure:^(NSURLRequest *request, NSHTTPURLResponse *response, NSError *error, id JSON) {
        
        NSLog(@"error = %@",error);
        //请求超时提示
        NSString *errorStr = [[NSString alloc]initWithFormat:@"%@",error];
        NSString *theError = @"The request timed out.";
        if ([errorStr rangeOfString:theError].length > 0) {
            UIAlertView *alert = [[UIAlertView alloc]initWithTitle:@"提示" message:@"请求超时" delegate:self cancelButtonTitle:@"确定" otherButtonTitles: nil];
            [alert show];
        }

}];
    //开始请求
    [operation start];

}
```