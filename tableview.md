### tableHeaderView 
```
self.headView = [[UIView alloc]initWithFrame:CGRectMake(0, 0, zWIDTH, 241)]; self.headView.userInteractionEnabled = YES; self.headView.backgroundColor = zCOLOR(@"f9f9f9"); self.tableView.tableHeaderView = self.headView;
```
```
#pragma mark ---tableView代理-----
//索引
- (NSArray *)sectionIndexTitlesForTableView:(UITableView *)tableView
{
 tableView.sectionIndexBackgroundColor = [UIColor clearColor];
 return _indexArray;
}

- (CGFloat)tableView:(UITableView *)tableView heightForFooterInSection:(NSInteger)section {
 return 0.1;
}
- (CGFloat)tableView:(UITableView *)tableView heightForHeaderInSection:(NSInteger)section{
 if ([self.dataArray[section] count] == 0) {
 return 0;
 }else {
 return 20;
 }
}

- (nullable UIView *)tableView:(UITableView *)tableView viewForHeaderInSection:(NSInteger)section{
 if ([self.dataArray[section] count] == 0) {
 return nil;
 }else{
 UIView *titV = [[UIView alloc]initWithFrame:CGRectMake(0, 0, zWIDTH, 20)];
 titV.backgroundColor = zCOLOR(@"efefef");
 UILabel *titL = [[UILabel alloc]initWithFrame:CGRectMake(20, 0, zWIDTH - 20, 20)];
 if (section <self.dataArray.count) {
 titL.text = [NSString stringWithFormat:@"%C", (unichar)(section + 'A')];
 }
// titL.textColor = BKCOLOR(@"c5c5c5");
 titL.font = [UIFont systemFontOfSize:15];
 [titV addSubview:titL];
 return titV;
 }
}
-(NSInteger)numberOfSectionsInTableView:(UITableView *)tableView {
 return self.dataArray.count;
}
-(NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {
 return [self.dataArray[section] count];
}
-(UITableViewCell*)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
 CityListTableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:@"ID"];
 if (!cell) {
 cell = [[CityListTableViewCell alloc]initWithStyle:UITableViewCellStyleDefault reuseIdentifier:@"ID"];
 }
// CityLIstModel *model = self.dataArray[indexPath.section][indexPath.row];
 cell.textLabel.text = self.dataArray[indexPath.section][indexPath.row];
// [cell configWithModel:model];
 return cell;
}
- (CGFloat)tableView:(UITableView *)tableView heightForRowAtIndexPath:(NSIndexPath *)indexPath{
 return 44;
}

-(void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath {

// [self.tableView deselectRowAtIndexPath:indexPath animated:YES];

// FriendModel *fmodel = self.dataArray[indexPath.section][indexPath.row];

// PepRegViewController *pep = [[PepRegViewController alloc]init];

// pep.accId = fmodel.accId;

//

// [self.navigationController pushViewController:pep animated:YES];

}

- (void)didReceiveMemoryWarning {

 [super didReceiveMemoryWarning];

 // Dispose of any resources that can be recreated.

}

```