#### 开发环境
IDEA

#### 主要内容

chart：存放生成的图表
img：存放系统图标
src：存放具体代码
Text.txt:存放数据

#### src内容

##### Frame.java 
绘制界面内容，与事件的监听处理，详细可clone后查看
![](https://img2020.cnblogs.com/blog/1474762/202003/1474762-20200328152846590-666742195.png)

![](https://img2020.cnblogs.com/blog/1474762/202003/1474762-20200328152808109-1515449448.png)

##### MenuTnput.java 
其中有initializeGragh方法，主要用于初始化内容，包括数据计数和生成graph

##### ProduceChart.java 

生成数据统计图，借用了插件JFreeChart Java图表库，它是一个免费的开源项目，向创造者们表示感谢。
里面有ProduceChart，ProduceChartC2，生成柱状图和扇形图的方法，生成的在chart文件中。
![](https://img2020.cnblogs.com/blog/1474762/202003/1474762-20200328160117197-930729053.png)

##### Search.java 
增加方法BuildGragh()，生成图表的包装函数，一次执行完生成图表。
其他可阅读源码，或一个博客：[链接](https://www.cnblogs.com/2017xinghui/p/12452438.html)
部分旧方法未删除。
##### SthFunction.java 
其中有采集数据的方法：Insert_Message，会在action事件中被调用
##### listMain.java 
主函数，运行入口，其中实例化了MenuTnput，ReadFile进行初始化工作，再通过frame生成swing界面
##### writetxt.java
生成Text.txt中数据信息






#### 代码规范

命名风格：

 1. 代码命名不能以下划线或者美元符号开头或者结尾
 2. 代码命名不能以中文拼音或者中文拼音与英文混合方式
 3. 类名使用UpperCamCamelCase风格，但DO、PO、DTO、VO、BO等除外
 4. 方法名、参数名、变量名统一使用lowerCamelCase，必须遵守驼峰命名
 5. 常量名全部大写，单词间用下划线隔开
 6. 抽象类必须以Abstract或者Base开头，异常类必须以Exception结尾，测试类以测试的类的名称开头Test结尾
 7. 类型与中括号紧挨相连标示数组
 8. POJO类中布尔类型变量不要加is前缀
 9. 包名统一小写，点分隔符有且有一个自然语义单词
 10. 避免在父子类和不同代码块中采用相同变量名
 11. 避免不规范的缩写命名
 12. 在对元素命名时用完整单词组合表达其意
 13. 常量和变量命名时，表示类型放在词尾，如：idList、TERMINATED_TREAD_COUNT
 14. 接口、类、方法、模块使用设计模式，命名时要体现具体模式
 15. 接口类中的方法和属性不要加任何修饰符，并加上有效的javadoc。
 16. 接口和实现类的命名规则：
     1）对于service和dao类，实现类必须用Impl结尾；
     2）如果是形容能力的接口名称，取对应的形容词为接口名 AbstractTranslator实现 Translatable接口
 17. 枚举类名加Enum后缀，枚举成员名称全大写，单词间用下划线隔开
 18. 各层命名规范：
     A) Service/DAO层命名规约
        1.获取单个对象的方法用get做前缀
        2.获取多个对象的方法用list做前缀，如：listObjects
        3.获取统计值的方法用count做前缀
        4.插入方法用save/insert做前缀
        5.删除方法用delete/remove做前缀
        6.修改方法用update做前缀
     B）领域模型命名规范
        1.数据对象：xxxDO, xxx为数据库表名
        2.数据传输对象：xxxDTO,xxx为业务模型相关名称
        3.展示对象：xxxVO，xxx一般为网页名称
        4.POJO是对DO、DTO、VO、BO的统称，禁止xxxPOJO


常量定义：

 1. 代码中禁止出现魔法值
 2. 在Long类型中赋值，数值后使用大写L
 3. 不要在一个常量类中维护所有常量，要根据功能分开维护
 4. 常量的复用层次：
* 跨应用：放在二方库中，通常在constant目录下
* 应用内：放在一方库中，通常在constant目录下
* 子工程内：放在当前子工程constant目录下
* 包内共享常量：当前包下单独的constant目录下
* 类内共享常量：直接在类内部private static final定义
 5. 如果变量值只在固定的范围内变化，用enum类型定义

代码格式：

 1. 不用一个类型的对象引用来访问静态方法和静态属性，直接类名访问即可
 2. 所有覆写方法，必须加@Override注解
 3. 相同业务含义，相同参数类型才能使用java可变参数
 4. 外部依赖或者二方库依赖的接口，不能修改方法签名。接口过时必须用@Deprecated 注解，并说明新接口或者新服务是什么
 5. 不能使用过时的类或者方法
 6.  Object的equals方法容易抛出空指针，应使用常量或者确定值的对象来调用equals
 7. 所有整型包装类之间的值比较都用equals 方法比较
 8. 浮点数之间的等值判断，基本类型不能用==，包装类不能用equals。
    解决方案：
(1) 指定一个误差范围，两个浮点数的差值在此范围之内，则认为是相等的。
(2) 使用BigDecimal来定义值，再进行浮点数的运算操作。
 9. 定义DO类时，属性类型要数据库字段类型相匹配
 10. 防止精度丢失，禁止使用BigDecimal(double)方式将double对象转换成BigDecimal。建议使用BigDecimal的valueOf方法
 11. 基本类型和包装类型的使用标准
     1.所有POJO的属性必须用包装类型
     2.RPC方法的参数和返回值必须使用包装类型
     3.所有局部变量使用基本变量
 12. 所有POJO 不要对其属性设置默认值
 13. 序列化类新增时不要修改其serialVersionUID字段
 14. 构造方法里禁止加任何业务处理逻辑，有要加在init()
 15. POJO类必须要写toString方法
 16. 禁止在POJO类中对属性xxx 同时存在isXxx()和getXxx()
 17. 使用索引访问用String的split方法得到数组时，需要对最后一个分隔符有无内容做检查
 18.   一个类有多个构造方法或者多个同名方法，要按照顺序来。
 19. 类中的方法顺序 ：共有方法-> 私有方法 -> get/set
 20. setter方法中参数名称和成员变量名称一致，不要在getter和setter方法中加业务逻辑
 21. 循环体内用StringBuilder的append方法进行扩展
 22. final可以修饰类，方法，变量。
 23. 慎用Object的clone方法
 24. 类成员与方法访问控制从严
    1） 如果不允许外部直接通过new来创建对象，那么构造方法必须是private。     
    2） 工具类不允许有public或default构造方法。
    3） 类非static成员变量并且与子类共享，必须是protected。
    4） 类非static成员变量并且仅在本类使用，必须是private。
    5） 类static成员变量如果仅在本类使用，必须是private。 
    6） 若是static成员变量，考虑是否为final。
    7） 类成员方法只供类内部调用，必须是private。 
    8） 类成员方法只对继承类公开，那么限制为protected。










































































