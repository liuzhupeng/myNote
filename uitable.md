### Customlab
```
UILabel *lab = [Customlab WithCGRect:CGRectMake(10, 12, 100, 16) Name:@"热门搜索" Color:[UIColor clearColor] FontSize:16 FontColor:@"333"];

```

```
+(UILabel *)WithCGRect:(CGRect)rect Name:(NSString *)name Color:(id)color FontSize:(CGFloat)size FontColor:(NSString *)fontColor{
    
    UILabel *lab = [[UILabel alloc]initWithFrame:rect];
    lab.numberOfLines = 0;
    lab.text = name;
    lab.font = [UIFont systemFontOfSize:size];
//    lab.disableThreeCommon = YES;
    
//    lab.textAlignment = NSTextAlignmentCenter;
   lab.textColor = zCOLOR(fontColor);
   
    
    if ([color isKindOfClass:[UIColor class]]) {
        
        lab.backgroundColor = color;
    }
    
    if ([color isKindOfClass:[NSString class]]) {
        
        lab.backgroundColor = zCOLOR(color);
    }

    return lab;
}
```
