### 一、UI
- self.topView.userInteractionEnabled = YES;
- self.tableView.contentInset = UIEdgeInsetsMake(-35, 0, 0, 0);
- self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;//去掉所有下划线
- self.tableView.tableFooterView = [[UIView alloc] initWithFrame:CGRectZero];  //去掉下面多余的线
- self.headView = [[UIView alloc]initWithFrame:CGRectMake(0, 0, zWIDTH, 241)];
 - self.tableView.tableHeaderView = self.headView;
- UIView *footV = [[UIView alloc]initWithFrame:CGRectMake(0, 0, zWIDTH, 160)];
-  //尾部视图------------------
 - UIView *footV = [[UIView alloc]initWithFrame:CGRectMake(0, 0, zWIDTH, 160)];
 - self.tableView.tableFooterView = footV;
- cell.accessoryType = UITableViewCellAccessoryDisclosureIndicator; //cell右侧箭头
-  //移除之前子视图
   - [_dateBgView.subviews enumerateObjectsUsingBlock:^(id obj, NSUInteger idx, BOOL *stop) {
        [obj removeFromSuperview];
    }];


#### 二、OC

- _titleLab.text = [NSString stringWithFormat:@"%@年,%@月",@(self.year),@(self.month)];
- 获取数组第i个值
 -  NSArray *tmparr =  @[@"日",@"一",@"二",@"三",@"四",@"五",@"六"];
 - lab.text = [tmparr objectAtIndex:i];