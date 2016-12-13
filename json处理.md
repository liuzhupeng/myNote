```
[self.manager GET:XMGCommonURL parameters:parameters progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id _Nullable responseObject) {
// 存储maxtime
 self.maxtime = responseObject[@"info"][@"maxtime"];
// 字典数组 -> 模型数据
 self.topics = [XMGTopic mj_objectArrayWithKeyValuesArray:responseObject[@"list"]];
}
```