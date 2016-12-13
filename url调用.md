```
NSDictionary *dic = @{@"username":@"3256",@"password":@"2356"};
[SFHttpTool post:@"http://192.168.10.109:8080/kkyou/login" params:dic success:^(id json) {
        MYLog(@",,,%@",json);
    } failure:^(NSError *error) {
      MYLog(@"err==%@",error);
    }];
```