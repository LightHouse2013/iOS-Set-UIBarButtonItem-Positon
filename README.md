# iOS-Set-UIBarButtonItem-Positon
## iOS 修改导航栏按钮的位置

* UINavigationItem可以理解为Navigation Bar中的内容，通过编辑UINavigationItem，我们可以使得在Navigation Bar中显示想要的东西，比如设置标题、添加按钮等。

* 当我们使用系统原生控件时，有时候不能满足需求，因此需要自定义重写，最近在项目中需要用导航栏的右侧按钮，先是直接用系统原生的控件。

* 代码如下：
``` Objective-C
	UIButton *settingButton = [UIButton buttonWithType:UIButtonTypeCustom];
	[settingButton setFrame:CGRectMake(0.0, 0.0, 44.0, 44.0)];
	[settingButton addTarget:self action:@selector(settingButtonOnClicked:) forControlEvents:UIControlEventTouchUpInside];
	[settingButton setImage:[UIImage imageNamed:@"ic_main_setting"] forState:UIControlStateNormal];
	
	UIBarButtonItem *rightItem = [[UIBarButtonItem alloc] initWithCustomView:settingButton];
```
* 效果如图：       
  ![系统原生按钮位置效果](https://github.com/zhang33121/iOS-Set-UIBarButtonItem-Positon/blob/master/systemdefultRightBarButtonPositon.png)

*  按钮右侧与屏幕右侧有20 point的间距，按钮图标居中显示，需求来讲该按钮是偏左了。当然你可以修改图标的位置也可以。
*  代码来修改是不是更灵活？当然是了，如果再需求变更也不用重新切图了。

* 修改后代码如下:
```Objective-C
	UIButton *settingButton = [UIButton buttonWithType:UIButtonTypeCustom];
	
	//修改按钮向右偏移10 point
	[settingButton setFrame:CGRectMake(10.0, 0.0, 44.0, 44.0)];
	[settingButton addTarget:self action:@selector(settingButtonOnClicked:) forControlEvents:UIControlEventTouchUpInside];
	[settingButton setImage:[UIImage imageNamed:@"ic_main_setting"] forState:UIControlStateNormal];
	
	//修改方法
	UIView *view = [[UIView alloc] initWithFrame:CGRectMake(0.0, 0.0, 44.0, 44.0)];
	[view addSubview:settingButton];
	
	UIBarButtonItem *rightItem = [[UIBarButtonItem alloc] initWithCustomView:view];
```
* 效果如图:       
  ![修改后按钮位置效果](https://github.com/zhang33121/iOS-Set-UIBarButtonItem-Positon/blob/master/motifyAfterPositon.png)

* 希望你对有所帮助，简书(http://www.jianshu.com/u/67d60ad73d4a)


