####方法调用
```
- (IBAction)loadingAction:(UIButton *)sender {
 [self showLoading];
 dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(3.0f * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
 [self dismissLoading];
 });
}
- (IBAction)normalTextAction:(UIButton *)sender {
 [self showText:sender.currentTitle];
 dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(1.0f * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
 [self dismissLoading];
 });
}

- (IBAction)failureAction:(UIButton *)sender {
 [self showErrorText:sender.currentTitle];
 dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(1.0f * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
 [self dismissLoading];
 });
}

- (IBAction)successAction:(UIButton *)sender {
 [self showSuccessText:sender.currentTitle];
 dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(1.0f * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
 [self dismissLoading];
 });
}

- (IBAction)percentAction:(UIButton *)sender {
 self.timer = [NSTimer timerWithTimeInterval:0.1 target:self selector:@selector(showPercent) userInfo:nil repeats:YES];
 [[NSRunLoop currentRunLoop] addTimer:self.timer forMode:NSRunLoopCommonModes];
}

- (IBAction)imageAction:(UIButton *)sender {
 [self showImage:[UIImage imageNamed:@"emj"] text:sender.currentTitle];
 dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(1.0f * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
 [self dismissLoading];
 });

}

- (void)showPercent
{
 self.percent += 5;
 [self showProgress:self.percent];
 if (self.percent == 100) {
 [self.timer invalidate];
 self.timer = nil;
 [self dismissLoading];
 }
}
```
#### 自定义方法
```

```