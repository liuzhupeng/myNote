```
#pragma mark - 加载数据
- (void)setUpData
{
    //查看接口文档:请求方式:GET 请求地址:http://api.budejie.com/api/api_open.php
    //请求参数:a = square ; c = topic
    //模型参数:icon;name;url
    //创建会话管理者
    AFHTTPSessionManager *manager = [AFHTTPSessionManager manager];
    //设置请求参数
    NSMutableDictionary *dict = [NSMutableDictionary dictionary];
    //包装请求参数
    dict[@"a"] = @"square";
    dict[@"c"] = @"topic";
    //发送请求
    [manager GET:@"http://api.budejie.com/api/api_open.php" parameters:dict progress:nil success:^(NSURLSessionDataTask * _Nonnull task, id  _Nullable responseObject) {
        //由于是字典数组.那么取出数组来转
        NSArray *array = responseObject[@"square_list"];
        //运用mj框架字典转模型
        self.meItems = [XFJMeItem mj_objectArrayWithKeyValuesArray:array];
        //写入plist文件,方便阅读
        [responseObject writeToFile:@"/Users/xiaofeng/Desktop/BuDeJie/Me.plist" atomically:YES];
        //调用处理数据的方法
        [self sloveData];
        //刷新表格
        [self.collectionView reloadData];
        //计算collectionView的高度
        //取出模型数组中的元素
        NSInteger count = self.meItems.count;
        //计算行数
        NSInteger rows = (count - margin) / cols + margin;
        //计算collectionView的总高度
        CGFloat cellH = XFJ_itemsWH * rows + (rows - margin) * margin;
        //collectionView的总高度
        self.collectionView.XFJ_Height = cellH;
        //根据内容自适应
        self.tableView.tableFooterView = self.collectionView;
    } failure:^(NSURLSessionDataTask * _Nullable task, NSError * _Nonnull error) {
        NSLog(@"error");
    }];
}
```