```
@interface ConsultGuideViewController ()<UITextViewDelegate>
```
```
self.textView = [[UITextView alloc]initWithFrame:CGRectMake(10, 40, zWIDTH - 20, 85)];
 self.textView.delegate = self;
 self.textView.backgroundColor = zCOLOR(@"e8e8e8");
 [footV addSubview:self.textView];
 self.automaticallyAdjustsScrollViewInsets = NO;
 self.placeHoldLab = [Customlab WithCGRect:CGRectMake(5, 5, zWIDTH - 30, 50) Name:@"请填写订单的详细说明，如见面地点，见面时间，我们有老人和孩子，行程不能太紧；我们是学生，想浏览高校等..." Color:[UIColor clearColor] FontSize:13 FontColor:@"b3b3b3"];
 [self.textView addSubview:self.placeHoldLab];

```