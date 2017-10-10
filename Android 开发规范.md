# Android 开发规范

|版本号|修订者|日期|备注|
|:---|:---:|:---:|:---:|
|0.1|宋永强|2017.2.17|正式版本|

### 编码风格

#### 命名规范

1.代码中的命名以英文字母开始，禁止用特殊字符开始或结尾。
>反例 _name / __name / $age 

2.代码中严禁采用拼音和英文混合的命名方式，更不允许直接使用中文。
>反例 tuijianNews DaZhePromotion getPingfenByName

3.类名使用 UpperCamelCase 风格，必须遵从驼峰形式。专有名词和缩写除外
>正例 MarcoPolo /UserInfo / TcpUdpDeal / BrowserActivity

4.方法名，参数名，成员变量，局部变量统一使用 lowerCamelCase 风格，必须遵从驼峰形式。
>正例 localValue / getUserName() / inputUserId

5.常量命名全部使用大写，单词之间用下划线隔开，力求表达完整清楚。
>正例 MAX_STOCK_COUNT
反例 MAX_COUNT

6.中括号是数组类型的一部分，数组定义如下: String[] args
>反例 String args[]

7.杜绝完全不规范的缩写，避免望文不知义。[Android 中常用的缩写参考参考]()，对于不知道如何缩写的，就不缩写。

8.接口类中的方法和属性不要加任何修饰符（ public 也不要添加），保持代码的简洁性，并加上有效的 Javadoc 注释。尽量不要在接口中定义变量。

9.Android中不建议使用枚举，在需要枚举的地方，使用静态常量替代，对于有关联的常量，命名保持一致性。
>正例 
public static final int DOWNLOAD_START = 0x10;
public static final int DOWNLOAD_RUNNING = 0x10>>1;
public static final int DOWNLOAD_PAUSE = 0x10>>2;
public statci final int DOWNLOAD_COMPLETED = 0x10>>3;

10.代码中禁止出现魔法值（未经定义的常量）
>反例
if (msg == 1){}

11.不推荐使用一个常量类维护所有常量，应该按功能归类，分开维护。

12.Android 中通用命名规范 Activity 命名统一使用 Activity 作为后缀，Fragment 统一使用 Fragment 作为后缀。

|类|	描述|例如|
|--|--|--|
|Activity类|	Activity为后缀标识|	欢迎页面类WelcomeActivity|
|Adapter类|	Adapter 为后缀标识|	新闻详情适配器 NewDetailAdapter|
|解析类|	Parser为后缀标识|	首页解析类HomePosterParser|
|工具方法类|	Util为后缀标识| 文件工具类 FileUtil|
|数据库类	|以DBHelper后缀标识|	新闻数据库：NewDBHelper|
|Service类|	以Service为后缀标识|	时间服务TimeService|
|Receiver类|	以Receiver为后缀标识|	推送接收JPushReceiver|
|ContentProvider|以Provider为后缀标识|DownloadProvider|
|自定义的共享基础类	|以Base开头|	BaseActivity,BaseFragment|

>注意：
如果项目采用MVP，所有Model、View、Presenter的接口都以I为前缀，不加后缀，其他的接口采用上述命名规则。

13.一行代码只声明一个变量，禁止一行代码声明多个同类型变量。
>反例
int a,b,c;

14.资源文件命名以及缩写
全部小写，采用下划线命名法。命名模块如下

用途_模块名_逻辑名
用途_模块名_颜色
用途_逻辑名
用途_颜色
例如：

btn_main_home.png 按键
divider_maket_white.png 分割线
ic_edit.png 图标
bg_main.png 背景
btn_red.png 红色按键
btn_red_big.png 红色大按键
ic_head_small.png 小头像
bg_input.png 输入框背景
divider_white.png 白色分割线

|名称|	功能|
|---|---|
|btn_xx|按钮图片使用btn_整体效果（selector）|
|btn_xx_normal|	按钮图片使用btn_正常情况效果|
|btn_xx_pressed|按钮图片使用btn_点击时候效果|
|btn_xx_focused	|state_focused聚焦效果|
|btn_xx_disabled|	state_enabled (false)不可用效果|
|btn_xx_checked	|state_checked选中效果|
|btn_xx_selected|	state_selected选中效果|
|btn_xx_checkable|	state_checkable可选效果|
|btn_xx_activated|	state_activated激活的|
|btn_xx_windowfocused|	state_window_focused|
|bg_head|	背景图片使用bg_功能_说明|
|def_search_cell|	默认图片使用def_功能_说明|
|ic_more_help|	图标图片使用ic_功能_说明|
|seg_list_line|	具有分隔特征的图片使用seg_功能_说明|
|sel_ok	选择图标使用sel_功能_说明|


#### 代码格式
代码格式统一使用 **2345AndroidCodeStyle** , 在AndroidStudio中添加为通用模板，提交代码时可以选择自动格式化代码，提倡在编辑代码之后，主动格式化代码。
**2345AndroidCodeStyle** 的主要内容

1.大括号的使用约定。如果大括号内为空，使用{}，不需要换行；如果非空代码，则按照如下约定：

- 左大括号前不换行
- 左大括号后换行
- 右大括号前换行
- 右大括号后还有 else 等代码则不换行，表示终止的右大括号后必须换行

2.左括号和后一个字符之间不出现空格，同样，右括号和前一个字符之间不出现空格。

3.if/for/while/switch/do 等保留关键字与左右括号之间都必须添加空格。

4.任何运算符左右都必须有一个空格

5.缩进统一使用4个空格，禁止使用 tab 字符。如果使用 tab 缩进，必须设置1个 tab 为4个空格

>正例 (涉及1-5点)

	public static void main(String[] args) {
		// 缩进 4 个空格
		String say = "hello";
		// 运算符的左右必须有一个空格
		int flag = 0;
		// 关键词 if 与括号之间必须有一个空格，括号内的 f 与左括号，0 与右括号不需要空格 
		if (flag == 0) {
	        System.out.println(say);
	   	}

		// 左大括号前加空格且不换行;左大括号后换行 
		if (flag==1) {
	    	System.out.println("world");
		// 右大括号前换行，右大括号后有 else，不用换行
		} else { 
		    System.out.println("ok");
		// 在右大括号后直接结束，则必须换行
		} 
	}

6.单行字符数限制不超过120个，超出需要换行，换行规则如下
- 第二行对第一行缩进4个空格，从第三行开始不再继续缩进。
- 运算符与下文一起换行。
- 调用方法的点符号与下文一起换行
- 在多个参数超长，逗号后进行换行。
- 在括号前不要换行

>正例
StringBuffer sb = new StringBuffer();
//超过 120 个字符的情况下，换行缩进 4 个空格，并且方法前的点符号一起换行 
sb.append("zi").append("xin")...
          .append("huang")...
          .append("huang")...
          .append("huang");
反例
StringBuffer sb = new StringBuffer();
//超过 120 个字符的情况下，不要在括号前换行 
sb.append("zi").append("xin")...append
("huang");
//参数很多的方法调用可能超过 120 个字符，不要在逗号前换行 method(args1, args2, args3, ...
, argsX);

#### 编码规约

1.避免通过一个类的对象引用访问此类的静态变量或静态方法，无谓的增加编译器的解析成本，直接使用类名访问即可。

2.所有的覆写方法，必须加@Override注解。

3.字符串是否相等的比较，强制使用 **TextUtils.equals()** ,Object 的 equals 方法，容易造成空指针异常，应该使用常量或者确定值的对象来调用equals。
>正例
TextUtils.equals("a",user.name);

4.使用索引访问用 String 的 split 方法得到的数组时，需要做最后一个分隔符后有无内容的检查，否则会抛出 IndexOutOfBoundsException 的风险
>说明：
String str = "a,b,c,,"; 
String[] ary = str.split(","); 
//预期大于 3，结果是 3 
System.out.println(ary.length);

5.当一个类有多个构造方法，或多个同名方法，这些方法应该按顺序放在一起，便于阅读。

6.类内部的方法定义顺序依次是：共有方法或保护方法 > 私有方法 > getter/setter

7.Android 中的实体类，不推荐使用 getter/setter 。直接将成员变量设置为 public 。

8.循环体内避免创建对象，字符串拼接，使用 StringBuilder 的 append 方法进行扩展。
>反例
String str = "start"
for (int i = 0; i<100; i++){
	str = str+"hello";
}
说明：
反编译出的字节码文件显示每次循环都会 new 出一个 StringBuilder 对象，然后进行 append 操作，最后通过 toString 方法返回 String 对象，造成内存资源浪费。

9.类成员与方法访问控制从严

- 如果不允许外部直接通过 new 创建对象，那么构造方法必须是 private。
- 工具类不允许有 public 或 default 构造方法
- 类非 static 成员变量并且与子类共享 ，必须是 protected。
- 类非 static 成员变量并且只在本类使用，必须是 private。
- 类 static 成员变量，必须考虑是否为 final。

>说明
任何类、方法、参数、变量，严控访问范围。过宽泛的访问范围，不利于模块解耦。

#### 集合相关

1.ArrayList 的 SubList 结果不可以强转成 ArrayList，否则会抛出 ClassCastException 异常：java.util.RandomAccessSubList cannot be cast to java.util.ArrayList;
>说明
subList 返回的是 ArrayList 的内部类 SubList，并不是 ArrayList，而是 ArrayList 的一个视图，对于 SubList 子列表的任何操作最终会反映到原列表上。

2.在 SubList 的场景中，要高度注意对原集合元素个数的修改，会导致子列表的遍历，增加，删除均产生ConcurrentModificationException 异常。

3.使用集合转数组的方法，必须使用集合的 toArray(T[] array) ,传入的是类型完全一样的数组，大小是 list.size()。

>反例
直接使用 toArray 无参方法存在问题，此方法返回值只能是 Object[] 类，若强转其他类型数组将出现 ClassCastException 异常。

>正例
List<String> list = new ArrayList<String>(2);
list.add("guan");
list.add("fang");
String[] array = new String[list.size()];
array = list.toArray(array);

>说明
使用 toArray 带参数方法，入参分配的数组控件不够大时，toArray 方法内部将重新分配内存空间，并返回新的数组地址，如果数组元素大于实际需要，下标为 [list.size()] 的数组元素将被置为 null，其他数组元素保持原值。因此最好将方法入参数组大小定义与集合元素个数一致。

4.使用工具类 Arrays.asList 把数组转换成集合时，不能使用其修改集合相关的方法，它的 add/remove/clear 方法会抛出 UnsupportedOperationException 异常。

>说明
asList 的返回对象是一个Arrays内部类，并没有实现集合的修改方法。Arrays.asList体现的是适配器模式，只是转换接口，后台的数据仍是数组。
String[] strs = new String[]{"a","b","c"};
List list = Arrays.asList(strs);
第一种情况：list.add("c");运行时异常
第二种情况：strs[0] = "java";那么list.get(0)也会随之改变。

5.不要在 foreach 循环里进行元素的 remove/add 操作。remove 元素操作请使用 Iterator 方式，如果并发操作，要对 Iterator 对象加锁。

>反例
List<String> a = new ArrayList<String>();
a.add("1");
a.add("2");
for(String temp :a){
	if("1".equals(temp)){
		a.remove(temp);
	}
}
正例
Iterator<String> it = a.iterator();
while(it.hasNext()){
	String temp = it.next();
	if("1".equals(temp)){
		it.remove();
	}
}

6.泛型通配符 < ?extends T> 来接收返回的数据，此写法的泛型集合不能使用 add 方法。

7.集合初始化时，尽量指定集合初始值大小。
>ArrayList 尽量使用 ArrayList（int initialCapacity）初始化

8.遍历 Map 时，推荐使用 entrySet 而不是 keySet 方式。
> keySet 其实遍历了两次，一次转为Iterator对象，另一次从hashMap中取出key 对应的value。而 entry 只需要遍历一次就把 key 和 value 都放在了 entry 中，效率更高。
> values() 返回的是V值集合，是一个list 集合对象；keySet()返回的是 k 值集合，是一个Set集合对象；entrySet返回的是K-V值组合集合。

9.高度注意，Map 类集合不能存储能否 null 值的情况，如下表格；

|集合类|Key|Value|Super|说明|
|---|---|---|---|---|
|HashTable|不允许为null|不允许为null|Dictionary|线程安全|
|ConcurrentHashMap|不允许为null|不允许为null|AbstractMap|分段锁技术|
|TreeMap|不允许为null|允许为null|AbstractMap|线程不安全|
|HashMap|允许为null|允许为null|AbstractMap|线程不安全|


#### 控制语句

1.字一个 switch 块内，每个 case 要么通过 break/return 等来终止，要么注释说明程序将继续执行到哪一个 case 为止；在一个 switch 块内，都必须包含一个 default 语句并且放在最后，即使 default 中没有任何代码。

2.if/else/for/while/do 语句中必须使用大括号，即使只有一行代码，避免使用下面的形式
>反例
if(condition) statements;

3.嵌套不要超过3层。

4.循环体重的语句要考虑性能，下面的操纵尽量移植到循环体外进行，对象定义，变量，数据库连接，try-catch。

#### 注释规范

1.代码中禁止出现超过5行的注释代码，对于当前版本不使用的代码，应及时删除，保持代码简洁。

2.类，类属性，类方法的注释要符合Javadoc规范，使用 /** 内容 **/格式注释，不能使用 //xxx方式。

3.方法内单行注释在被注释的语句上方，另起一行，使用 //xxx 注释。多行注释使用 /* */。

4.修改代码的同时，注释也要进行相应的修改，尤其是参数，返回值，异常，核心逻辑等的修改。

#### 日志异常

1.日志打印使用统一工具类，日志打印级别设置合理，普通日志不要使用 error 级别。

2.不要捕获 Java 类库中自定义的集成自 RuntimeException的运行时异常类，如 NullPointException/IndexOutOfBundsException ,这类异常由程序员通过预检查来规避，保证程序的健壮性。

3.对打断代码进行 try-catch ，这是不负责任的表现。catch 时要分清稳定代码和非稳定代码，稳定代码是之无论在什么场景下都不会出错的代码。对于非稳定代码的 catch，要尽可能区分异常类型，再做对应的异常处理。

4.finally 块必须对资源对象，流对象进行关闭，有异常也要 try-catch。

5.不要在 finally 块中使用 return 语句，finally 块中的 return 返回后方法结束执行，不会再执行try块中的 return 语句。

6.程序员对常见错误要时刻保持警惕，NullPointException，IndexOutOfBundsException。防止常见错误重复出现，是程序员的基本修养之一。






### 开发工具

- 团队统一使用 **[AndroidStudio](http://tools.android.com/)**，最新的Stable版本。
- 编码统一使用 UTF-8 
- 缩进统一使用 **4个空格**，如果使用Tab缩进，请将1个Tab设置为4个空格。

-------

**UI控件缩写表**

|控件|	缩写|例子|
|--|---|---|
|LinearLayout|	ll	| llFriend或者mFriendLL|
|RelativeLayout|	rl |	rlMessage或mMessageRL|
|FrameLayout|	fl	|flCart或mCartFL|
|TableLayout|	tl	|tlTab或mTabTL|
|Button	btn	|btnHome或mHomeBtn|
|ImageButton|	ibtn|	btnPlay或mPlayIBtn|
|TextView	|tv	|tvName或mNameTV|
|EditText	|et	|etName或mNameET|
|ListView	|lv	|lvCart或mCartLV|
|ImageView|	iv	|ivHead或mHeadIV|
|GridView	|gv	|gvPhoto或mPhotoGV|

**常见的英文单词缩写:**

|名称	|缩写|
|---|----|
|icon	|ic （主要用在app的图标）|
|color	|cl（主要用于颜色值）|
|divider|	di（主要用于分隔线）|
|average|	avg|
|background|	bg（主要用于布局和子布局的背景）|
|buffer	|buf|
|control|	ctrl|
|delete	|del|
|document|	doc|
|error	|err|
|escape	|esc|
|increment|	inc|
|infomation	|info|
|initial	|init|
|image	|img|
|length	|len|
|library|	lib|
|message|	msg|
|password|	pwd|
|position|	pos|
|string	|str|
|temp	tmp|
