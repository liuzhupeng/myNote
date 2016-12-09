```
@interface HomeViewController ()<CLLocationManagerDelegate,ZLScrollViewDelegate,UICollectionViewDelegateFlowLayout,UICollectionViewDataSource,UITableViewDelegate,UITableViewDataSource>
{
 CLLocationManager *locationManager;
}
```
```
#pragma mark --定位---

-(void)location {
 locationManager = [[CLLocationManager alloc] init];
 locationManager.delegate = self;
 [locationManager startUpdatingLocation];
 if (![CLLocationManager locationServicesEnabled]) {
 NSLog(@"定位服务当前可能尚未打开，请设置打开！");
 return;
 }
 //如果没有授权则请求用户授权
 if ([CLLocationManager authorizationStatus]==kCLAuthorizationStatusNotDetermined){
 [locationManager requestWhenInUseAuthorization];
 }else if([CLLocationManager authorizationStatus]==kCLAuthorizationStatusAuthorizedWhenInUse){
 //设置代理
 locationManager.delegate=self;
//设置定位精度
 locationManager.desiredAccuracy=kCLLocationAccuracyBest;
 //定位频率,每隔多少米定位一次
 CLLocationDistance distance=10.0;//十米定位一次
 locationManager.distanceFilter=distance;
 //启动跟踪定位
 [locationManager startUpdatingLocation];
 }
}

-(void)locationManager:(CLLocationManager *)manager didUpdateLocations:(NSArray *)locations{
 CLLocation *location=[locations firstObject];//取出第一个位置
 CLLocationCoordinate2D coordinate=location.coordinate;//位置坐标
 NSLog(@"经度：%f,纬度：%f,海拔：%f,航向：%f,行走速度：%f",coordinate.longitude,coordinate.latitude,location.altitude,location.course,location.speed);
 //如果不需要实时定位，使用完即使关闭定位服务
 // [locationManager stopUpdatingLocation];
}
- (void)locationManager:(CLLocationManager *)manager didFailWithError:(NSError *)error {
 NSLog(@"locError:%@", error);
}



```



