```
[self.manager GET:XMGCommonURL parameters:parameters progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id _Nullable responseObject) {
// 存储maxtime
 self.maxtime = responseObject[@"info"][@"maxtime"];
// 字典数组 -> 模型数据
 self.topics = [XMGTopic mj_objectArrayWithKeyValuesArray:responseObject[@"list"]];
}
```
```
// 累加到旧数组的后面
  [self.topics addObjectsFromArray:moreTopics];
```
```
// 将 "微博字典"数组 转为 "微博模型"数组
   NSArray *newStatuses = [HWStatus objectArrayWithKeyValuesArray:statuses];
   NSArray *newFrames = [self stausFramesWithStatuses:newStatuses];
// 将更多的微博数据，添加到总数组的最后面
[self.statusFrames addObjectsFromArray:newFrames];
```
####NSJONSerialization
```
NSString *path = [[NSBundle mainBundle]pathForResource:@"Notes" ofType:@"json"];
    NSData * jsonData = [[NSData alloc]initWithContentsOfFile:path];
    NSError *error;
//id -- NSDictionary
    id jsonObj = [NSJSONSerialization JSONObjectWithData:jsonData options:NSJSONReadingMutableContainers error:&error];
    if(!jsonObj || error){
        NSLog(@"JSON解码失败")；
    }
    self.objects = [jsonObj objectForKey:@"Record"];
```
```
NSDictionary *status = json[@"username"]
NSDictionary *user = status[@"user"];
NSString * username = status[@"username"];

```