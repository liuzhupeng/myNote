####  UICollectionViewDelegate,UICollectionViewDataSource,UICollectionViewDelegateFlowLayout
```
@interface CityListViewController ()<UICollectionViewDelegate,UICollectionViewDataSource,UICollectionViewDelegateFlowLayout>
```
```
self.collectionView = [[UICollectionView alloc]initWithFrame:CGRectMake(10, 15, zWIDTH - 20, 170) collectionViewLayout:flow];
    self.collectionView.backgroundColor = [UIColor whiteColor];
    self.collectionView.delegate = self;
    self.collectionView.dataSource = self;
    [self.collectionView registerNib:[UINib nibWithNibName:NSStringFromClass([CityListCollectionViewCell class]) bundle:nil] forCellWithReuseIdentifier:colID];
```
```
#pragma mark--collectionV 代理---
- (NSInteger)collectionView:(UICollectionView *)collectionView numberOfItemsInSection:(NSInteger)section
{
    return 6;
}


- (UICollectionViewCell *)collectionView:(UICollectionView *)collectionView cellForItemAtIndexPath:(NSIndexPath *)indexPath
{
    
    CityListCollectionViewCell *cell = [collectionView dequeueReusableCellWithReuseIdentifier:colID forIndexPath:indexPath];
    
    cell.nameLab.text = @"北京";
    cell.pinYinLab.text = @"beijing";
    cell.backImageV.image = [UIImage imageNamed:@"22.jpg"];
    return cell;
}

#pragma mark ---- UICollectionViewDelegate

// 选中某item
- (void)collectionView:(UICollectionView *)collectionView didSelectItemAtIndexPath:(NSIndexPath *)indexPath
{
    MYLog(@"item");
}
#pragma mark- FlowDelegate

//设置每个item的大小
-(CGSize)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout *)collectionViewLayout sizeForItemAtIndexPath:(NSIndexPath *)indexPath{
    
    return  CGSizeMake((zWIDTH - 30)/3, 80);
}

- (CGFloat)collectionView:(UICollectionView *)collectionView layout:(UICollectionViewLayout*)collectionViewLayout minimumInteritemSpacingForSectionAtIndex:(NSInteger)section {
    
    return 5;
}


```
- cell 实现
```
#import <UIKit/UIKit.h>
@interface CityListCollectionViewCell : UICollectionViewCell
@property (weak, nonatomic) IBOutlet UIImageView *backImageV;
@property (weak, nonatomic) IBOutlet UILabel *nameLab;
@property (weak, nonatomic) IBOutlet UILabel *pinYinLab;
@property (weak, nonatomic) IBOutlet UIView *mengBanView;
@end

```