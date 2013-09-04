# iOS编码规范

上海益生健康科技有限公司技术研发部 2013年9月3日

## 关于



## 术语


**例如：**
```objc
NSString *password;
```

**而不是**
```objc
NSString* password;
```

**或者**
```objc
NSString * password;
```

```objc
if (user.isHappy) {
    //Do something
} else {
    //Do something else
}
```

* 为避免错误，条件语句体必须使用大括号，即便语句体中的语句可以不必使用大括号（比如只有一行语句）；

**例如：**
```objc
if (!error) {
    return success;
}
```

**而不是**
```objc
if (!error)
    return success;
```

**或者**
```objc
if (!error) return success;
```

* 三元运算子：仅当使用该运算子可以让代码显得更清晰易懂时方可使用三元运算子，更多情况下应使用条件语句；

**例如：**
```objc
result = a > b ? x : y;
```

**而不是**
```objc
result = a > b ? x = c > d ? c : d : y;
```

* 在方法声明中，在(`-`/`+`)符号与返回值之间留1个空格。此外，参数与前面的冒号不留空，方法段与之间留1个空格；

**例如：**
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image;
```

* 为保证视觉上的整洁和代码组织，在方法之间应摒弃大段的空白行，提供且仅提供一行空白。

  * 优先使用全局常量而非宏，应使用`static`方式声明常量；
  
**例如：**
```objc
static NSString * const kNotificationLoggedIn;
```


**例如：**
```objc
UIButton *settingsButton;
```

**而不是**
```objc
UIButton *setBtn;
```


```objc
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

**而不是**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```
* 因为`nil`将被解析为`NO`，因此没有必要在条件语句中进行比较。永远不要将任何东西和`YES`进行直接比较，因为`YES`被定义为1，而一个`BOOL`变量可以有8个字节。

**例如：**
```objc
if (!someObject) {
}
```

**而不是**
```objc
if (someObject == nil) {
}
```

**以下是BOOL变量的恰当用法：**
```objc
if (isAwesome)
if (![someObject boolValue])
```

**而不是**
```objc
if ([someObject boolValue] == NO)
if (isAwesome == YES)
```


typedef enum {
    RequestUnload,
    RequestLoading,	
    RequestLoadedOK,
    RequestLoadedFailed
} RequestLoadState;
```

**例如：**
+ (instancetype)sharedInstance {
   static id sharedInstance = nil;
   static dispatch_once_t onceToken;
   dispatch_once(&onceToken, ^{
      sharedInstance = [[self alloc] init];
   });
   return sharedInstance;
}
```

* 在创建`NSString`，`NSDictionary`，`NSArray`和`NSNumber`等对象实例时，应使用Literals字面量。需要注意的是，不应将`nil`传给`NSArray`和`NSDictionary`字面量，否则会引起程序崩溃。

**例如：**
```objc
NSArray *names = @[@"Brian", @"Matt", @"Chris", @"Alex", @"Steve"];
NSDictionary *productManagers = @{@"iPhone" : @"Kate", @"iPad" : @"Kamal"};
NSNumber *shouldUseLiterals = @YES;
NSNumber *buildingZIPCode = @10018;
```

**而不是**
```objc
NSArray *names = [NSArray arrayWithObjects:@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", nil];
NSDictionary *productManagers = [NSDictionary dictionaryWithObjectsAndKeys:@"Kate", @"iPhone", @"Kamal", @"iPad", nil];
NSNumber *shouldUseLiterals = [NSNumber numberWithBool:YES];
NSNumber *buildingZIPCode = [NSNumber numberWithInteger:10018];
```