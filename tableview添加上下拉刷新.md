```
//刷新回调
typedef void(^RefreshBlock)();
@interface BaseViewController : UIViewController
@property (nonatomic,strong) NSMutableArray *dataArray;
@property (nonatomic,strong) UITableView *tableView;
//对tableView添加下拉刷新 (1、定义Block变量)
- (void)addHeaderRefresh:(RefreshBlock)refreshBlock;
//对tableView添加上拉加载
- (void)addFooterRefresh:(RefreshBlock)refreshBlock;
@end

```
```
//

// BaseViewController.m

// Kekeyou

//

// Created by zhao on 16/11/17.

// Copyright © 2016年 zhao. All rights reserved.

//

#import "BaseViewController.h"

@interface BaseViewController ()<UITableViewDelegate,UITableViewDataSource>

@end

@implementation BaseViewController

- (void)viewDidLoad {

 [super viewDidLoad];



 self.automaticallyAdjustsScrollViewInsets=NO;



 self.tableView = [[UITableView alloc]init];

 self.tableView.frame = [UIScreen mainScreen].bounds;



 self.tableView.backgroundColor = [UIColor clearColor];

 self.tableView.delegate = self;

 self.tableView.dataSource = self;

// self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;

 [self.view addSubview:self.tableView];

}

-(NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {



 return _dataArray.count;

}

-(UITableViewCell*)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {



 UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:@"ID"];



 if (!cell) {



 cell = [[UITableViewCell alloc]initWithStyle:UITableViewCellStyleDefault reuseIdentifier:@"ID"];

 }

// cell.selectionStyle = UITableViewCellSelectionStyleNone;



 return cell;

}

//上拉、下拉

- (void)addHeaderRefresh:(RefreshBlock)refreshBlock

{

 //1、初始化

 MJRefreshGifHeader *header = [MJRefreshGifHeader headerWithRefreshingBlock:^{

 refreshBlock();

 }];



 [header setTitle:@"正在刷新。。" forState:MJRefreshStateRefreshing];



 //3、赋值

 _tableView.mj_header = header;

}

- (void)addFooterRefresh:(RefreshBlock)refreshBlock

{

 MJRefreshAutoGifFooter *footer = [MJRefreshAutoGifFooter footerWithRefreshingBlock:^{

 footer.mj_h = 0;

 //（3、调用Block）

 refreshBlock();



 }];





 // footer.stateLabel.hidden = YES;



 _tableView.mj_footer = footer;



}

- (NSMutableArray *)dataArray {



 if (_dataArray == nil) {



 _dataArray = [NSMutableArray array];

 }

 return _dataArray;

}

- (UITableView *)tableView {



 if (!_tableView) {



 _tableView = [[UITableView alloc] init];

 }

 return _tableView;

}

- (void)dealloc {

 // 删除通知对象

 [[NSNotificationCenter defaultCenter] removeObserver:self];



}

- (void)didReceiveMemoryWarning {

 [super didReceiveMemoryWarning];

 // Dispose of any resources that can be recreated.

}

/*

#pragma mark - Navigation

// In a storyboard-based application, you will often want to do a little preparation before navigation

- (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender {

 // Get the new view controller using [segue destinationViewController].

 // Pass the selected object to the new view controller.

}

*/

@end

```
```
#import "MJRefreshStateHeader.h"

@interface MJRefreshGifHeader : MJRefreshStateHeader

@property (weak, nonatomic, readonly) UIImageView *gifView;

/** 设置state状态下的动画图片images 动画持续时间duration*/

- (void)setImages:(NSArray *)images duration:(NSTimeInterval)duration forState:(MJRefreshState)state;

- (void)setImages:(NSArray *)images forState:(MJRefreshState)state;

@end

```
