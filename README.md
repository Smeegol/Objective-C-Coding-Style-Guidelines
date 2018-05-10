# Objective-C 编码规范

## 目录
* [关于](#关于)
* [参考资料](#参考资料)
* [术语](#术语)
* [Xcode设置](#Xcode设置)
* [语言](#语言)
* [空格与换行](#空格与换行)
* [工程组织](#工程组织)
* [命名方式](#命名方式)
* [编程实践](#编程实践)

## 关于为了统一团队协作下代码的规范性、风格的统一性以及编程的注意点，制定本规范。本规范仅作为建议推广使用，原则上只要代码风格保持自身的规范性、风格的统一性，也是允许的，但是为了团队开发的确定性，遂希望 iOS 开发人员强制遵守。很多规范是语言通用的，有些是 Objective-C 特有的，本规范基于 Apple 编码规范、Xcode 代码示例、Objective-C 语言规范以及 Java 语言官方规范等文档，适用于使用 Objective-C 语言相关的工程。## 参考资料
* [Coding Guidelines for Cocoa](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)* [The official raywenderlich.com Objective-C style guide](https://github.com/raywenderlich/objective-c-style-guide)

## 术语* 大写驼峰式命名法——每个词首字符大写，其余字符均小写，如`AppDelegate`、`Global`、`DataService`等；* 小写驼峰式命名法——除第一个词首字符小写外，其余词首字符大写，其他字符均小写，如`fileName`、`tempArray`、`titleLabel`等。

## Xcode设置* 使用等宽字体（如 Xcode 默认的 SF Menlo Regular）而不是非等宽字体，利于视觉上的上下对齐；* 每行不超过 120 个字符：Preferences->Text Editing->Editing->Page guide at column 输入 120；* 使用空格缩进而非 Tab 缩进，且缩进宽度为 4 个字符：Preferences->Text Editing->Indentation->Prefer indent using 选择 Spaces，Tab width 输入 4，Indent width 输入 4；
* 自动剔除行尾空白字符：Preferences->Text Editing->Automatically trim trailing whitespace 勾选。

## 语言* 使用美式英语；

**例如：**
```objc
UIColor *myColor = [UIColor whiteColor];
```

**而不是**
```objc
UIColor *myColour = [UIColor whiteColor];
```
## 空格与换行* 普通代码行之间最多留 1 个空白行；
* 语义、功能不同的代码行之间最多留 2 个空白行；
* 同一行代码只包含一条语句；* 单目运算符与操作数之间不留空，如 `&`、`!`、`^`；
* 双目运算符与操作数之间留 1 个空格；
* 逗号和分号紧跟前面的语句，与后面的语句之间留 1 个空格；* 指针符号 `*` 与前面的数据类型之间留 1 个空格，紧贴后面的变量名；

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

* 小括号与被它包含的内容之间不留空；
* 中括号与被它包含的内容之间留 1 个空格；
* 大括号与被它包含的内容之间留 1 个空格；* 大括号在语句的行尾开始，而在新的行首关闭；**例如：**
```objc
if (user.isHappy) {
    //Do something
} else {
    //Do something else
}
```

* 条件语句体必须使用大括号，即使只有一行语句；

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

* 三元运算符仅当使用该运算符让代码更清晰易懂时才使用，更多情况下使用条件语句；

**例如：**
```objc
result = a > b ? x : y;
```

**而不是**
```objc
result = a > b ? x = c > d ? c : d : y;
```

* 方法声明中，在 `-` / `+` 与返回值之间留 1 个空格。参数与前面的冒号之间不留空，方法段之间留 1 个空格；

**例如：**
```objc
- (void)setupWithText:(NSString *)text image:(UIImage *)image;
```
## 工程组织* 工程Group组织尽量跟本地磁盘实际路径相一致，利于定位；* 工程Group名尽量跟相关功能名或模块名相一致。不推荐按照类型来组织，比如有些将视图控制器类放到一个Group，视图类放到另外的Group的做法；* 工程Group尽量使用中文名，利于辨识；* 工程Group组织可按照约定俗成的来，比如第三方框架放在`Libs`、`Utils`、`公共`等Group中，Bean类放在`Bean` Group中，公共的自定义类及其他放到专门的Group中，命名为`Global`或`XxxUtils`、`XxxTools`等；* 资源文件的组织应跟上面的文件一样，文件应使用有意义的英文命名，应能表达它的用法；应避免使用中文或汉语拼音，除非表达更清晰、更利于辨识。## 命名方式* 常量：  * 应避免在代码中出现字面常数或常字符串，使用超过一次的应以宏或全局常量来替代；
  * 优先使用全局常量而非宏，应使用`static`方式声明常量；
  
**例如：**
```objc
static NSString * const kNotificationLoggedIn;
```
  * 宏有两种方式命名，一是全部大写，并使用下划线连接各个部分，如`SCREEN_WIDTH`；或者以`k`开头，后面每个词首字符大写，其余小写，如`kAppKey`；  * 其他约定俗成的命名方式，字典数据的键使用形如`kXxxKey`的方式命名，通知名称使用形如`kNotificationXxx`的方式命名。* 变量：  * 变量采用小写驼峰式命名法；  * 对于特殊类型的变量，命名时可带上属性，如`NSArray`的变量命名为`xxxArray`，其他的如`xxxDictionary`，`xxxSize`，`xxxRect`等；  * 对于UI相关的变量，命名时要后缀以特定的控件名，如`UILabel`的变量命名为`xxxLabel`，其他的如`xxxButton`，`xxxTableView`，`xxxImageView`等；  * 除了循环控制内的变量可以使用约定俗成的`i`、`j`、`k`等之外，变量应使用非缩写的英文单词。

**例如：**
```objc
UIButton *settingsButton;
```

**而不是**
```objc
UIButton *setBtn;
```
* 方法：  * 方法采用小写驼峰式命名法；  * 方法的参数个数不宜超过4个，过多则考虑封装或重构，比如封装成`NSDictionary`格式；* 类、协议、分类等：  * 采用大写驼峰式命名法；  * 其他可参照Xcode默认生成文件。* 文件：  * 文件采用大写驼峰式命名法；  * 视图控制器相关的按照`XxxViewController`的方式命名；  * 分类使用父类+分类名来命名，如`UIImageView+AFNetworking.h`。* 杂项：  * 上面所有应使用有意义的英文命名，应能表达它的用法，避免使用汉语拼音；  * 推荐使用约定俗成的缩写，比如`app`（application）, `bg`（background）, `func`（function）, `info`（information）, `init`（initialize）, `max`（maximum）, `min`（minimum）, `msg`（message）, `rect`（rectangle）, `temp`（temporary）等；  * 专有名词保持通用的大小写格式，要么全部大写，要么全部小写，比如`XML`、`HTML`、`URL`、`HTTP`、`FTP`、`JPG`、`PNG`、`GIF`、`RGB`等。## 编程实践* 点表示法仅用于获取和改变属性，获取和改变属性同样仅用点表示法，括号表示法用于其他情况。
**例如：**
```objc
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

**而不是**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```* 警告应该尽量解决掉，但也不必开启Treat Warnings as Errors，因为有些警告还是无法解决的。* 不推荐处处都是注释，好的代码应该自解释。关键的逻辑、跳转、判断，以及复杂的算法，非常有必要使用注释。多个注释应尽量左对齐。
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
* 方法的参数有效性检查；* 成员变量在初始化方法中不必设置为`0`或`nil`；* 使用`ARC`，并且要注意内存管理规范；
* 禁用不利于团队开发的`Storyboard`；* 分类明显的推荐使用`enum`来代替，而不是0、1、2……这样的字面数字；
**例如：**```objc
typedef enum {
    RequestUnload,
    RequestLoading,	
    RequestLoadedOK,
    RequestLoadedFailed
} RequestLoadState;
```
* 使用MVC模式，减少层与层之间的耦合；
* 优先使用 auto-synthesis。但如果有必要，@synthesize 和 @dynamic应该在实现中每个都声明新的一行；* 回调的最佳方式是使用代理模式，而不是使用Notification；* `delegate`属性使用`weak`，防止循环引用；* 所有自定义的`Notification`名应统一在公共文件中命名，便于甄别重复；* 本地存储：单一对象可用归档，简单属性可用`NSUserDefaults`，多个相同类型的数据可用`SQLite`；使用`FMDB`框架；
* 数据库表名使用复数而不是单数，采用大写驼峰式命名法；各个字段使用下划线连接，采用小写写法；SQL语句中关键字使用大写，其他不变；
* 使用通用的、约定俗成的`alloc`和`init`的方式创建实例，而不是使用`new`方法；* 使用`#pragma mark – XXX`来区别不同的区块；* 在创建单例对象的共享实例时，应使用线程安全模式；
**例如：**```objc
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
