```
//1.1创建UIImageView对象
UIImageView  *imageView = [[UIImageView alloc] init];
//1.2设置frame
imageView.frame = CGRectMake(100,100,200,200);
//imageView.frame = (CGRect){{100,100},{200,200}};
/*##方式二
imageView.frame = CGRectMake(100,100,image.size.width,image.size.height);
  imageView.image = image;
####方式三
UIImage *image = [UIImage imageNamed:@"1"]
UIImageView *imageView = [[UIImageView alloc] initWithFrame:CGRectMake(100,10,image.size.width,image.size.height)];
####方式四
//创一个UIImageview对象
//注意：InitWIthImage默认就有尺寸-->图片尺寸
UIImageView *imageView = [[UIImageView alloc]initWithImage:[UIImage imageNamed:@"1"]]
[self.view addSubView:imageView]
//改变位置--中心点位置
imageView.center = CGPointMake(200,150)
imageView.center = CGPointMake(self.view.frame.size.width*0.5,self.view.frame.size.height*0.5);
*/


//1.3设置背景颜色
imageView.backgroundColor = [UIColor greenColor]
//1.4设置图片
imageView.image = [UIImage imageNamed:@"1"]
/////////
UIViewContentModeRedraw //重新绘制（核心绘图）drawRact
//带有Scale，标明图片可能被拉伸或压缩
UIViewContentModeScaleToFill,//完全的压缩或拉伸
//Aspect比例，素芳是带有比例的
UIViewContentModeScaleAosectFit,//宽度比不变Fit适应
UIViewContentModeScaleAosectFill, //宽高比不变Fill填充
//不带有Scale,标明图片不可能被拉伸或压缩
UIViewContentModeCenter,
UIViewContentModeTop,
UIViewContentModeBottom
UIViewContentModeLeft,
UIViewContentModeRight,
UIViewContentModeTopLeft,
UIViewContentModeTopRight,
UIViewContentModeBottomLeft,
UIViewContentModeBottomRight,
//1.5设置图片的内容
imageView.contentMode = UIViewContentModeCenter;
//1.6添加到控制器View中
[self.view addSubView:imageView]
#设置毛玻璃
//1.1创建UIImageView对象
UIImageView  *imageView = [[UIImageView alloc] init]
//1.2设置frame
//imageView.frame = CGRectMake(0,0,self.view.frame.size.width,self.view.frame.size.height);
imageView.frame = self.view.bounds;
//1.3设置背景颜色
imageView.backgroundColor = [UIColor greenColor]
//1.4设置图片
imageView.image = [UIImage imageNamed:@"1"]
//1.5设置图片的内容
imageView.contentMode = UIViewContentModeCenter;
//1.6加毛玻璃
//1.6.1创建UIToolBar对象
UIToolbar *toolBar = [[UIToolbar alloc] init];
//1.6.2设置toolBar的frame
toolBar.frame = imageView.bounds;
//1.6.3设置毛玻璃的样式
toolBar.barStyle = UIBarStyleBlack;
toolBar.alpha = 0.9
//1.6添加到imageView中
[imageView addSubView:toolBar]
```

## 加载图片的方式：

* 1.imageNamed:
* 2.imageWithContentsOfFile:

* 1.加载Assets.xcassets这里面的图片

  * 1&gt; 打包后变成Assets.car
  * 2&gt; 拿不到路径
  * 3&gt; 只能通过imageNamed：来加载图片
  * 4&gt; 不能通过imageWithContentsOfFile:来加载图片

* 2.放到项目中的图片
  * 1&gt; 可以拿到路径
  * 2&gt; 能通过imageNamed:来加载图片
  * 3&gt; 也能通过imageWithContentsOfFile:来加载图片
    ```
    //图片设置方式
    //方式一
    self.imageView.image = [Image imageNamed:@"1"]
    //方式二
    //路径
    NNstring *path = [[NSBundle mainBundle] pathForResource:@"1" ofType:@"png"];
    self.imageView.image = [UIImage imageWithContentsOfFile:path]
    ```

    \#\#\#\#图片动画 
    多张图片形成动画
    \`\`\`
    - \(IBAction\)stand{
        \/\/1.加载所有的图片
        NSMutableArray&lt;UIImage \*&gt; \*standImages = \[NSMutableArray array\]
        for\(int i=0;i&lt;10;i++\){
            \/\/获取所有图片的名称
            NSString \*imageName = \[NSString stringWithFormat:@"stand\_%d",i+1\];
            \/\/创建UIImage
            UIImage \*image = \[UIImage imageNamed:imageName\];
            \/\/装入数组
            \[standImages addObject:image\]
        }
        \/\/2.设置动画图片
        self.imageView.animationImages = standImages;
        \/\/3.设置播放次数
        self.imageView.animationRepeatCount = 0;
        \/\/4.设置播放的时长
        self.imageView.animationDurantion = 0.6
        \/\/5.播放
        \[self.imageView.startAnimating\];
    }
    \`\`\`


