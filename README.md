# iOS编码规范

上海益生健康科技有限公司技术研发部 2013年9月3日

## 关于为了统一团队协作下代码的规范性、风格的统一性以及编程的注意点，而制定本规范。本规范仅作为建议推广使用，只要代码风格保持自身的规范性、风格的统一性，也是允许的。很多规范是语言通用的，有些是Objective-C特有的，本规范基于Apple编码规范、Xcode代码示例、Objective-C语言规范以及Java语言官方规范等文档，适用于使用Objective-C语言相关的工程。

## 术语* 大写驼峰式命名法——每个词首字符大写，其余字符均小写，如AppDelegate、Global、DataTransfer等；* 小写驼峰式命名法——除第一个词首字符小写外，其余词首字符大写，其他字符均小写，如fileName、tempArray、titleLabel等；
##编码规范### 一、编码排版格式* 使用等宽字体（如Xcode默认的Menlo Regular）而不是非等宽字体，利于视觉上的上下对齐；* 每行不超过100个字符，Xcode通过Preferences->Text Editing->Editing-> Page guide at column输入100来设置宽度提醒线；* 使用Tab缩进而非空格缩进，并且缩进以4个字符为单位，Xcode通过Preferences->Text Editing->Indentation，Prefer indent using选择Tabs，Tab width输入4，Indent width输入4来进行设置。* 空格的使用：  * 关键字与后面的表达式之间留1个空格，如for、if、while等条件判断句；  * 单目运算符与操作数之间不留空，如&、!、^；  * 双目运算符应与它们的操作数用1个空格分开；  * 逗号和分号紧跟前面的语句，与后面的语句用1个空格分开；  * .h文件协议<>前面有一个空格；  * @property与后面的()之间留1个空格，()里面的属性特性跟4）一致，然后再是属性声明；  * 指针*与前面的数据类型留1个空格，紧贴后面的变量名，如NSString *str；  * 方法中，-或+号与返回值之间留1个空格，参数与前面的冒号不留空，参数与参数之间留1个空格，如- (NSString *)geTel；  * 类的对齐方式可参照Xcode默认生成文件。* 大括号的对齐有两种，单独起一行且对齐或顶上一行然后换行，Xcode采用的后一种对齐方式，如if/for/while/switch以及类、方法等声明莫不如是。### 二、工程组织* 工程Group组织尽量跟本地磁盘实际路径相一致，利于定位；* 工程Group名尽量跟相关功能名或模块名相一致。不推荐按照类型来组织，比如有些将视图控制器类放到一个Group，视图类放到另外的Group；* 工程Group尽量使用中文名，利于辨识；* 工程Group组织可按照约定俗成的来，比如第三方框架放在Libs、Utils、公共等Group中，Bean类放在Bean Group中，公共的自定义类及其他放到专门的Group中，命名为Global或XxxUtils、XxxTools等；* 资源文件的组织应跟上面的文件一样，文件应使用有意义的英文命名，应能表达它的用法；应避免使用中文或汉语拼音，除非表达更清晰、更利于辨识。### 三、命名* 常量：  * 应避免在代码中出现常数或常字符串，使用超过一次的应以宏或全局常量来替代；  * 宏有两种方式命名，一是全部大写，并使用下划线连接，如SCREEN_WIDTH；或者以k开头，后面每个词首字符大写，其余小写，如kAppKey；  * 其他约定俗成的命名方式，字典数据的键使用形如kXxxKey的方式命名，通知名称使用形如kNotificationXxx的方式命名。* 变量：  * 变量采用小写驼峰式命名法；  * 对于特殊类型的变量，命名时可带上属性，如NSArray的变量命名为xxxArray，其他的如xxxDictionary，xxxSize，xxxRect等；  * 对于UI相关的变量，命名时要后缀以特定的控件名，如UILabel的变量命名为xxxLabel，其他的如xxxButton，xxxTableView，xxxImageView等；  * 循环控制内的变量可以使用约定俗成的i、j、k等。* 方法：  * 方法采用小写驼峰式命名法；  * 方法每个参数冒号前的描述均不留空；  * -或+号与返回值之间留1个空格，参数与前面的冒号不留空，参数与参数之间留1个空格；  * 方法的参数个数不宜超过4个，过多则考虑封装或重构，比如封装成NSDictionary格式；* 类、协议、分类等：  * 采用大写驼峰式命名法；  * 其他可参照Xcode默认生成文件。* 文件：  * 文件采用大写驼峰式命名法；  * 视图控制器相关的按照XxxViewController的方式命名；  * 分类使用父类+分类名来命名，如UIImageView+AFNetworking.h。* 杂项：  * 上面所有应使用有意义的英文命名，应能表达它的用法，避免使用汉语拼音；  * 推荐使用约定俗成的缩写，比如app（application），bg（background），func（function），info（information），init（initialize），max（maximum），min（minimum），msg（message），rect（rectangle），temp（temporary）等；  * 专有名词保持通用的大小写格式，要么全部大写，要么全部小写，比如XML、HTML、URL、HTTP、FTP、JPG、PNG、GIF、RGB等。### 四、注释* 不推荐处处都是注释，好的代码应该自解释；* 关键的逻辑、跳转、判断，以及复杂的算法，非常有必要使用注释；* 多个注释应尽量左对齐### 五、其他* 点表示法仅用于获取和改变属性，获取和改变属性同样仅用点表示法，括号表示法用于其他情况。
**例如：**
```objc
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

**而不是：**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```## 编码实践* 方法的参数检查；* 成员变量在初始化方法中不必设置为0或nil；* 使用ARC；* 分类明显的推荐使用enum来代替，而不是0、1、2……* 使用MVC模式，减少层与层之间的耦合；* 回调的最佳方式是使用代理模式，而不是使用Notification；* delegate属性使用weak，防止循环引用；* 所有自定义的Notification名应统一在公共文件中命名，便于甄别重复；* 本地存储：单一对象可用归档，简单属性可用NSUserDefaults，多个相同类型的数据可用SQLite；使用FMDB框架；* 使用alloc和init的方式创建实例，而不是使用new方法；* 使用#pragma mark – XXX来区别不同的区块。
