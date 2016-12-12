```
 self.timer = [NSTimer timerWithTimeInterval:0.1 target:self selector:@selector(showPercent) userInfo:nil repeats:YES];
 [[NSRunLoop currentRunLoop] addTimer:self.timer forMode:NSRunLoopCommonModes];
```
```
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