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
```
//

// MJRefreshGifHeader.m

// MJRefreshExample

//

// Created by MJ Lee on 15/4/24.

// Copyright (c) 2015年 小码哥. All rights reserved.

//

#import "MJRefreshGifHeader.h"

@interface MJRefreshGifHeader()

{

 __unsafe_unretained UIImageView *_gifView;

}

/** 所有状态对应的动画图片 */

@property (strong, nonatomic) NSMutableDictionary *stateImages;

/** 所有状态对应的动画时间 */

@property (strong, nonatomic) NSMutableDictionary *stateDurations;

@end

@implementation MJRefreshGifHeader

#pragma mark - 懒加载

- (UIImageView *)gifView

{

 if (!_gifView) {

 UIImageView *gifView = [[UIImageView alloc] init];

 [self addSubview:_gifView = gifView];

 }

 return _gifView;

}

- (NSMutableDictionary *)stateImages

{

 if (!_stateImages) {

 self.stateImages = [NSMutableDictionary dictionary];

 }

 return _stateImages;

}

- (NSMutableDictionary *)stateDurations

{

 if (!_stateDurations) {

 self.stateDurations = [NSMutableDictionary dictionary];

 }

 return _stateDurations;

}

#pragma mark - 公共方法

- (void)setImages:(NSArray *)images duration:(NSTimeInterval)duration forState:(MJRefreshState)state

{

 if (images == nil) return;



 self.stateImages[@(state)] = images;

 self.stateDurations[@(state)] = @(duration);



 /* 根据图片设置控件的高度 */

 UIImage *image = [images firstObject];

 if (image.size.height > self.mj_h) {

 self.mj_h = image.size.height;

 }

}

- (void)setImages:(NSArray *)images forState:(MJRefreshState)state

{

 [self setImages:images duration:images.count * 0.1 forState:state];

}

#pragma mark - 实现父类的方法

- (void)prepare

{

 [super prepare];



 // 初始化间距

 self.labelLeftInset = 20;

}

- (void)setPullingPercent:(CGFloat)pullingPercent

{

 [super setPullingPercent:pullingPercent];

 NSArray *images = self.stateImages[@(MJRefreshStateIdle)];

 if (self.state != MJRefreshStateIdle || images.count == 0) return;

 // 停止动画

 [self.gifView stopAnimating];

 // 设置当前需要显示的图片

 NSUInteger index = images.count * pullingPercent;

 if (index >= images.count) index = images.count - 1;

 self.gifView.image = images[index];

}

- (void)placeSubviews

{

 [super placeSubviews];



 if (self.gifView.constraints.count) return;



 self.gifView.frame = self.bounds;

 if (self.stateLabel.hidden && self.lastUpdatedTimeLabel.hidden) {

 self.gifView.contentMode = UIViewContentModeCenter;

 } else {

 self.gifView.contentMode = UIViewContentModeRight;



 CGFloat stateWidth = self.stateLabel.mj_textWith;

 CGFloat timeWidth = 0.0;

 if (!self.lastUpdatedTimeLabel.hidden) {

 timeWidth = self.lastUpdatedTimeLabel.mj_textWith;

 }

 CGFloat textWidth = MAX(stateWidth, timeWidth);

 self.gifView.mj_w = self.mj_w * 0.5 - textWidth * 0.5 - self.labelLeftInset;

 }

}

- (void)setState:(MJRefreshState)state

{

 MJRefreshCheckState



 // 根据状态做事情

 if (state == MJRefreshStatePulling || state == MJRefreshStateRefreshing) {

 NSArray *images = self.stateImages[@(state)];

 if (images.count == 0) return;



 [self.gifView stopAnimating];

 if (images.count == 1) { // 单张图片

 self.gifView.image = [images lastObject];

 } else { // 多张图片

 self.gifView.animationImages = images;

 self.gifView.animationDuration = [self.stateDurations[@(state)] doubleValue];

 [self.gifView startAnimating];

 }

 } else if (state == MJRefreshStateIdle) {

 [self.gifView stopAnimating];

 }

}

@end
```
```
#import "MJRefreshAutoStateFooter.h"

@interface MJRefreshAutoGifFooter : MJRefreshAutoStateFooter

@property (weak, nonatomic, readonly) UIImageView *gifView;

/** 设置state状态下的动画图片images 动画持续时间duration*/

- (void)setImages:(NSArray *)images duration:(NSTimeInterval)duration forState:(MJRefreshState)state;

- (void)setImages:(NSArray *)images forState:(MJRefreshState)state;

@end

```
```

```