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