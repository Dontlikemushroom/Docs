 [Java学习攻略详解.pdf](E:\WeChat Files\wxid_t6z19ziwk6se12\FileStorage\File\2024-10\Java学习攻略详解.pdf) 

# JavaSE

**IDEA**中的快捷键：sout——>System.out.println()；ctrl+alt+v——>快速生成对应的返回值；alt+enter——>显示意向动作；alt+insert——>快速生成一些内容；ctrl+H——>检查子类型；

**VsCode**中的快捷键：alt+shift+f——>快速整理；ctrl+shif+L快速编辑相同的数据变量

**VSCode**中要进行Java编程的话，首先需要下载jdk文件，然后配置系统环境变量的配置，之后就可以进行编写Java代码了。**注意**：**如果出现无法加载主类**但是java文件的编译是成功的而运行时出错，一般是Java项目文件中package所导致的，这个时候建议在扩展中安装**Debugger for Java**然后在文件中右击选择Run Java即可运行成功。

## Java入门

### 基础

#### 运算符

**定义**：Java 中的运算符可以分为多个类型，包括**算数运算符**、**关系运算符**、**位运算符**、和**逻辑运算符**。其中算数运算符有+、-、*、/（加减乘除）等，关系运算符有>、<、==、!=（大于小于等于和非等于）等，位运算符有&、|、^、~（按位取与、按位取或、按位异或、按位取反）等，逻辑运算符有&&、||、！（逻辑取与、逻辑取或、逻辑取反）等。

**运算符计算顺序**：Java 语言中大部分运算符也是从左向右结合的，只有单目运算符、赋值运算符和三目运算符例外，其中，单目运算符、赋值运算符和三目运算符是从右向左结合的，也就是从右向左运算。

#### 控制流程语句

**for-each**：是在一定范围之内进行循环，没有判断部分

```java
// 示例：遍历数组
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);  // 输出数组中的每个元素
}
// 示例：遍历 List 集合
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
for (String name : names) {
    System.out.println(name);  // 输出集合中的每个元素
}
```

#### static静态关键字

**定义**：指的是其内部的细节全部静态不变，这样的话就可以在类外面直接调用，而不是需要定义一个对象将其动态变化的细节固定住才可以访问，被static关键字修饰的方法或者变量不需要依赖于对象来进行访问，只要类被加载了，就可以通过类名去进行访问。

#### Java中的包

**定义**：在 Java 中，包（package） 是一种用于组织和管理类（classes）、接口（interfaces）及其他类型的机制。它可以理解为一个 命名空间（namespace），用于分类和管理代码，使代码结构更加清晰，同时避免命名冲突。实际上就是一个个的文件夹，调用包的类时，需要将包引入才可以。

#### java中的各种常见的变量

**集合类：**在Java中，Map和List是两种不同的集合类型，它们分别属于java.util包，并且它们各自有不同的用途和特点。Map是一种存储键值对（key-value pairs）的集合，它不允许重复的键，但可以有多个值与不同的键相关联。每个键最多只能映射到一个值。Map接口的主要实现类包括HashMap、TreeMap和LinkedHashMap等。List是一种有序集合，可以包含重复的元素。List接口的主要实现类包括ArrayList、LinkedList和Vector等。总得来说，Map适合于需要根据键快速查找、更新、删除值的场景。List适合于需要保持元素插入顺序或者需要快速随机访问元素的场景。这两种集合类型各有优势，选择使用哪种类型取决于你的具体需求。

```java
Map<String, Object> params;
List<CategoryBrandRelationEntity data;
```



### 重点

#### 覆写和重载

**覆写（override）**是指可以重新写一个和父类中方法名参数都一样的方法，在子类中调用该方法时将会调用子类里重写的这个方法，要想再调用父类中的方法只能用super关键字才可以。
**重载（overload）**和覆写（override）相同的地方是方法名都是一样的。区别是覆写是重新写父类中的方法，重载是一个类里面的方法参数不一样。

#### 接口

**定义**：接口（interface）定义了一系列的抽象方法和常量，形成一个属性集合。接口定义完后，任何类都可以实现这个接口，而且一个类可以实现多个接口。实现接口的类必须实现接口中定义的抽象方法，具体实现细节由类自己定义。可以说接口定义了类的框架，可以把它理解成一种完全的抽象类一没有实现任何方法。接口的定义跟类的定义十分相似，只是使用的关键字不同，类的定义使用的关键字是class，接口用interface。

```java
public interface Animal{
    //接口中的常量
    public static final int CHANGLANG = 1;
    //接口中的方法
    public void eat();
    public String getName();
}
```

**抽象类和接口之间的比较**：（1）一个类可以实现多个接口，但只能继承一个抽象类（2）抽象类可以有非抽象方法，接口中定义的方法必须全部为抽象方法（3）在抽象类中定义的方法，可以是public、private、protected或默认值，但在接口中全部是public的（4）抽象类可以有构造函数，接口不能。两者都不能实例化，但是都能通过它们来存放子类对象，具体为抽象类不可以实例化但可以声明对象，通常会通过动态绑定的方式来声明父类。**注意**：这里的实例化就是分配内存，声明对象就是声明。

```java
public class tiger implements Animal{
    public void eat(){
        System.out.println("老虎吃肉");
    }
    public String getName(){
        return "老虎"；
    }
}
//implements和extend的区别是前者限定了子类必须要定义父类的具体方法，而后者可以不用，同时还可以添加其他成员方法
public class Main{
    public static void main(String[] args){
        Animal tiger = new Tiger();
        tiger.eat();
        System.out.println(tiger.getName());
    }
}
```

#### 内部类

**定义**：内部类定义在其它类的内部，内部类所在的类被称为宿主类。内部类种类很多，有静态内部类、非静态内部类、定义在方法内的局部内部类，还有连名字都没有的匿名内部类。

#### 进程和线程

**线程**：在Java编程语言中，**线程**（Thread）是程序调度的最小单位，进程是计算机资源分配的最小单位。线程允许程序在并发（concurrent）或并行（parallel）执行任务，这对于提高性能、响应速度等方面具有重要作用。Java中的线程是通过 `java.lang.Thread` 类或实现 `java.lang.Runnable` 接口来创建和管理的。Java中线程的执行机制是基于 **JVM（Java虚拟机）** 的，底层依赖于操作系统的线程模型。

```java
package threads;

public class ThreadDemo1 extends Thread{
    private String name;
    public ThreadDemo1(String name){
        this.name = name;
    }
    public void run(){
        for (int i = 0; i < 100; i++){
            System.out.println(name);
        }
    }
    public static void main(String[] args){
        ThreadDemo1 td1 = new ThreadDemo1("第一个线程");
        ThreadDemo1 td2 = new ThreadDemo1("第二个线程");
        ThreadDemo1 td3 = new ThreadDemo1("第三个线程");
        td1.start();
        td2.start();
        td3.start();
    }
}
```

这里还可以使用匿名类来创建一个新线程并重写它的run（）方法

```java
package test01;

public class Test {
    public static void main(String[] args) {
        // 创建并启动一个匿名线程
        new Thread() {
            // 重写 run 方法，定义线程的执行内容
            public void run() {
                int i = 5; // 初始化变量 i 为 5
                // 当 i 大于 0 时，循环执行
                while(i > 0) {
                    // 打印 i 的当前值
                    System.out.println("i=" + i);
                    try {
                        // 线程休眠 1 秒（1000 毫秒）
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        // 捕获并处理可能出现的 InterruptedException 异常
                        e.printStackTrace();
                    }
                    i--; // 每次循环后，i 减 1
                }
                // 当 i 减到 0 时，循环结束，打印 "done"
                System.out.println("done");
            }
        }.start(); // 启动线程，开始执行 run 方法
        
        // 主线程继续执行，打印 "线程外"
        System.out.println("线程外");
    }
}
```



**File类**：File 类对象可封装要操作的文件，可通过File类的对象对文件进行操作，如查看文件的大小、判断文件是否隐藏、判断文件是否可读等。**局限：**File类的相关操作，并不涉及文件内容相关的操作，这是单独依靠File类对象无法实现的操作，此时需要借助I/O流完成。

**流（Stream）** ：是一个用于顺序处理数据的抽象概念，指的是**数据在源（输入）或目标（输出）之间的连续传输**。

**I/O流**：**I/O 流（Input/Output Stream）** 是用于在程序与外部设备（如文件、网络、控制台等）之间进行 输入（Input） 和 输出（Output） 数据的机制。I/O 流 是 Java 中处理 数据读写 的核心概念，能够处理字节和字符的数据流动。将I/O流理解为一根“管子”，I为Input，O为Output，即输入输出流，可以理解为两个流向的“管子”。

## Java核心

### 封装（OOP语言的特性）

### 继承（OOP语言的特性）

**拓展**：子类对象的创建是由最顶层的父类的构造函数依次往下层进行调用

```java
class Animal {
    public Animal() {
        System.out.println("Animal 构造函数被调用");
    }
}
class Mammal extends Animal {
    public Mammal() {
        System.out.println("Mammal 构造函数被调用");
    }
}
class Dog extends Mammal {
    public Dog() {
        System.out.println("Dog 构造函数被调用");
    }
}
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();  // 创建 Dog 类的对象
    }
}
```

**注意**：在Java中继承一般是单继承，也就是一个类只有一个父类。这不同与其他oop语言，比如c++、c#或者python，但是在Java中为接口interface提供了一对多的继承关系。

### 多态（OOP语言的特性）

**定义：**多态是面向对象语言的又一重要特性。多态是指同一个方法根据上下文使用不同的定义的能力。从这一点上看，前面讲的方法覆写和方法重载都可被看作是多态。但是Java的多态更多的是跟动态绑定放在一起理解的。**动态绑定**是一种机制，通过这种机制，对一个已经被重写的方法的调用将会发生在运行时，而不是在编译时解析。通常会通过子类的对象赋值给父类的指针，只有当调用父类中被覆写的方法时才会根据映射，对应的子类使用子类中的方法。



**拓展**：除此之外，子类还可以反过来调用父类的方法或者成员变量，在动态规划的时候想直接用父类的函数可以通过强制类型转换实现，在override的时候想直接用父类的成员可以通过super.成员进行实现

```java
class Parent {
    protected String value = "Parent value";

    public void display() {
        System.out.println("Parent display");
    }
}

class Child extends Parent {
    protected String value = "Child value";

    @Override
    public void display() {
        super.display(); // 调用父类的 display 方法
    }
}

public class Test {
    public static void main(String[] args) {
        Child child = new Child();
        child.display();//通过super.调用父类的display方法
        ((Parent)child).display(); // 强制转换调用父类的 display 方法
    }
}
```

### 反射

背景：Java程序中，所有的对象都有两种类型:编译时类型和运行时类型 ，而很多时候对象的编译时类型和运行时类型不一致。 

`Object obj=new String("hello"); `

`obj.getClass()`
例如:某些变量或形参的声明类型是Obiect类型，但是程序却需要调用该对象运行时类型的方法，该方法不是Object中的方法，那么如何解决呢?方案1:在编译和运行时都完全知道类型的具体信息，在这种情况下，我们可以直接先使用instanceof运算符进行判断，再利用强制类型转换符将其转换成运行时类型的变量即可。方案2:编译时根本无法预知该对象和类的真实信息，程序只能依靠运行时信息来发现该对象和类的真实信息，这就必须使用反射。

概述：**Reflection(反射)**是被视为动态语言的关键，反射机制允许程序在运行期间借助于Reflection API取得任何类的内部信息，并能直接操作任意对象的内部属性及方法。加载完类之后，在堆内存的方法区中就产生了一个class类型的对象(一个类只有一个class对象)，这个对象就包含了完整的类的结构信息。我们可以通过这个对象看到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，我们形象的称之为：反射。

## Java基本框架和工具

框架 = 注解+反射+设计模式

### 注解

**@Para：**在Java中，`@Param`注解主要用于MyBatis框架中，其作用是给方法参数命名，以便在对应的XML映射文件中引用这些参数。

**@Transactional：**在Web项目中使用`@Transactional`注解来表明事务的原因是为了保证业务操作的原子性、一致性、隔离性和持久性，特别是在涉及到多个数据库操作时。

**@RequestMapping：**在Spring框架中，`@RequestMapping`、`@RequestParam` 和 `@RequestBody` 是用于处理HTTP请求的常用注解。它们在Spring MVC中扮演着不同的角色，用于不同的场景。`@RequestMapping`是一个用于处理HTTP请求的注解，可以用于类或方法上。当用于类上时，表示类中的所有响应方法都是以该路径为父路径。当用于方法上时，表示该方法可以处理特定的HTTP请求。

**@RequestParam：**其用于绑定请求参数到方法的参数上。它通常用于处理GET请求的查询参数或POST请求的表单参数。一般会放在控制类函数中的参数中，使用这个注解会将前端传过来的json文件放入Map对象中进行保存。

**@RequestBody：**其用于绑定请求体（通常是JSON或XML格式的数据）到方法的参数上。它通常用于处理POST或PUT请求，这些请求通常包含复杂的对象数据。一般会放在控制类函数中的参数中，使用这个注解会将前端传过来的json文件放入编写复杂lei对象中进行保存。

### Maven框架

**依赖：**运行时开发时都需要用到的包，比如项目中需要一个包，就要添加一个依赖，这个依赖在项目运行时也需要，因此在[项目打包](https://so.csdn.net/so/search?q=项目打包&spm=1001.2101.3001.7020)时需要把这些依赖也打包进项目里；

**插件：**在项目开的发时需要，但是在项目运行时不需要，因此在项目开发完成后不需要把插件打包进项目中。

**坐标：**和数学一样，在一个空间有三个坐标，这三个坐标可以确定空间中的一个点。在 Maven 当中，同样也是由这三个标量，去确定一个 "jar 包"所在的位置。我们之前了解到 Maven 不会像本地项目一样，直接把 "jar 包"下载本地，再通过项目去绑定 "jar 包"。也就是 Maven 项目想要依赖一个 "jar 包" ，就是通过上面三个。首先会去本地仓库寻找(也就是之前在 settings.xml 设置的一个自己的仓库地址)，如果本地仓库没有，就会去我们配置的 " 镜像 "，去远程通过镜像地址通过网络进行下载。（阿里云->华为云->Maven 中央本地仓库，依次把需要的下载到本地仓库）而我们举的这个例子的三个，这个其实是本项目的一个坐标信息。因为我们本项目这个 hello 也可以打包成一个 "jar 包"。当别的 Maven 项目想要引用这个 hello 的某个类，就直接通过当前这个项目的坐标信息来引用的。所以每个 Maven 项目都会有一个唯一的坐标。保证能够确认到唯一的"jar 包"了。

### Spring框架

**定义**：**Spring**，**SpringIOC/DI**

**使用**：首先选择版本，目前学习的最新版本为6.1.13（日期为2024/10/15）学习视频版本为5.3.23。第一步为创建maven项目，第二部添加Spring依赖到pom文件中，第三步创建Spring配置文件，最后进行测试，再测试中通过**ApplicationContext** context = new **ClassPathXmlApplicationContext**("applicationContext.xml");进行创建容器，这样Spring的基本框架就构造成功了。注意：当出现类文件具有错误的版本61.0应为52.0的报错时，是因为jdk8只能支持Spring6.x.x以下的版本。

```java
//Spring通过加载配置文件，创建Spring容器
ApplicationContext ac = new ClassPathXmlApplicationContext("applicationContext.xml");//事实上创建容器时对象已生成
//从容器中取出叫做p的bean
Person p2 = (Person)ac.getBean("p");//这种方式需要强制转换
```

**Spring的属性注入**：在上述代码中知识简单的配置了Spring的配置文件，所以创建容器的时候对象的生成只是通过默认构造器生成，所以成员变量也是默认的数值，在原来没有引入Spring容器的概念之前，创建对象对其进行属性注入（赋值操作）一共有两种分别为**属性注入-设值注入**和**属性注入-构造注入**

```java
//设值注入
Book b = new Book();
b.setID(1);
b.setName("活着")；
//构造注入
Book b = new Book(1,"活着")；
```

所以同样的在Spring的配置文件中也有相似的属性注入的方式即**设置注入和构造注入**

```xml
<bean id="b1" class="com.msb.pojo.Book">
	<!-- collaborators and configuration for this bean go here -->
	<property name="id" value="1"></property>
	<property name="name" value="活着"></property>
</bean>
<bean id="b2" class="com.msb.pojo.Book">
	<constructor-arg name="id" value="2"></constructor-arg>
	<constructor-arg name="name" value="三体"></constructor-arg>
</bean>
```

**Spring的属性注入方式**：一般的属性注入方式有**简单数据类型的直接设置和类类型的引用注入**，其关键字分别为value（即简单数据类型包括基本数据类型和String的直接设置）和ref（即需要引用另一个bean的id。也就是说这个参数是一个类类型，且这个类的对象也被Spring容器所管理）

**注解的引用**：注解其实就是代码里的**特殊标记**，这些标记可以在编译、类加载、运行时被读取，并执行相应的处理通过使用注解，程序员可以在不改变原有逻辑的情况下，在源文件中嵌入一些补充信息。代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证或者进行部署。**使用注解时**要在其前面增加@符号，并把该注解当成一个修饰符使用。用于修饰它支持的程序元素(包、类、构造器、方法、成员变量、参数、局部变量的声明)。**注解的重要性**——在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE/Arldroid中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗代码和XML配置等。未来的开发模式都是基于注解的，一定程度上可以说:框架=注解+反射+设计模式。

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component                     //实例化Bean，默认名称为类名首字母变小写。无需指定setter方法
public class Girl {
    @Value("19")               //给普通数据类型属性赋值
    private int age;
    @Value("小刚")              
    private String name;
    @Autowired                 //自动注入。默认byType，如果多个同类型bean，使用byName
    private Boy boyfriend;
}

```

### Mysql数据库

**定义**：MySQL是一个流行的关系型数据库管理系统（RDBMS），它使用SQL（Structured Query Language）进行数据库管理。MySQL是开源的，并且广泛用于各种应用程序，特别是在Web应用程序中。

**JDBC**：JDBC（Java Database Connectivity）是一个Java API，它提供了一种标准的方法，允许Java程序连接到数据库并执行SQL语句。JDBC是一个独立的接口，它由一组用Java语言编写的类和接口组成，它们为不同类型的数据库提供了统一的访问方式。

**两者之间的关系**：在Java项目中，JDBC和MySQL的关系可以这样理解：（1）连接接口：JDBC作为Java应用程序与MySQL数据库之间的桥梁。Java程序可以通过JDBC接口与MySQL数据库进行交互。（2）驱动程序：为了使用JDBC连接到MySQL数据库，需要一个JDBC驱动程序。这个驱动程序充当Java应用程序和MySQL数据库之间的中介，负责将JDBC API的调用转换为MySQL数据库能理解的原生SQL语句。（3）数据库操作：通过JDBC，Java程序可以执行各种数据库操作，如查询数据（SELECT）、插入数据（INSERT）、更新数据（UPDATE）和删除数据（DELETE）等。（4）数据访问对象（DAO）模式：在Java项目中，通常会使用数据访问对象（DAO）模式来封装数据库访问逻辑。在这种模式中，JDBC用于实现DAO类，这些类提供了与MySQL数据库交互的方法。（5）框架集成：许多现代Java框架（如Spring）提供了对JDBC的抽象，使得数据库操作更加简单和安全。例如，Spring的JdbcTemplate可以简化JDBC代码，而MyBatis或Hibernate等ORM（对象关系映射）框架可以进一步抽象数据库操作，使得开发者可以用面向对象的方式处理数据库交互。**总结来说，在Java项目中，JDBC提供了与MySQL数据库进行交互的机制，而MySQL是实际存储数据的数据库系统。开发者通过JDBC编写代码来执行数据库操作，而JDBC驱动程序则负责将这些操作转换为MySQL可以理解的SQL语句。**

**基本语法：**

事务，在计算机科学中，特别是在数据库管理系统（DBMS）中，事务（Transaction）是一个操作序列，这些操作要么全部成功执行，要么全部不执行，它是一个不可分割的工作单位。事务是数据库操作的逻辑单元，用于保证数据库状态的完整性和一致性。于是在Web项目中使用`@Transactional`注解来表明事务的原因是为了保证业务操作的原子性、一致性、隔离性和持久性，特别是在涉及到多个数据库操作时。

### git工具的使用

**定义**：git是一个免费开源的分布式版本控制系统，版本控制系统主要负责文件的版本变化以及在线文件编辑等功能，其分为两个版本即**集中式（SVM）**和**分布式（git）**，其主要区别是前者使用一个主机进行存储和上传数据，而后者每个用户负责一个主机，在自己的主机中进行更新最后统一到主服务器上。

**安装**：

**使用方式**：命令行、图形化界面（GUI）和IDE插件/扩展。

**初始化配置**：初始化配置需要配置用户名、邮箱以及密码等（省略为本地配置Local、--global为全局配置以及--system为系统配置）

```shell
git config --global user.name "Zhao Wei"			#姓名
git config --global user.email 15155635016@163.com  #邮箱
git config --global credential.helper store			#设置存储方式
git config --global --list							#查看配置情况
```

**创建仓库**：git中有两种创建方式分别为git init（即将以一个文件夹交给git管理）和git clone（即将远程文件下载下来交给git管理）

```shell
>md learn-git				#生成文件夹
>rd /s learn-git			#删除文件
>cd learn_git
/learn-git>git init			#会直接生成.git文件
/learn-git>git init	my-repo #会先生成一个my-repo文件再生成.git文件
/learn-git/my-repo>ls		#阅读文件
/learn-git/my-repo>ls -a	#阅读含.git文件
/learn-git/my-repo>ls -alter#阅读全部信息文件
```

**工作区域和文件状态**：工作区域分为工作区（.git所在的目录）、暂存区（.git下面的index目录）和本地仓库（.git下面的objects目录），文件专态又分为未跟踪、未修改、已修改和已暂存

**添加和提交文件**：

```shell
D:>cd learn-git/my-repo
D:/learn-git/my-repo>git status										#查看仓库状态
D:/learn-git/my-repo>echo "这是第一个文件">file1.txt				    #创建文件以及内容
D:/learn-git/my-repo>cat file1.txt									 #查看文件内容
D:/learn-git/my-repo>git add file1.txt								 #提交到暂存区
D:/learn-git/my-repo>git commit file1.txt	#进入vim编辑器，esc退出编辑，w保存，q退出,注意esc结束后若无输入还需要shift+：进入命令输入模式
D:/learn-git/my-repo>git commit file1.txt -m "第一次提交"			#提交
D:/learn-git/my-repo>git add *.txt									#提交所有txt文件到暂存区
D:/learn-git/my-repo>git add .										#提交所有文件
D:/learn-git/my-repo>git log										#查看提交记录
D:/learn-git/my-repo>git log --online								#查看简洁的提交记录
```

**回退版本**：

```shell
D:/learn-git/my-repo>git reset --soft								#工作区和暂存区出现过的均保存
D:/learn-git/my-repo>git reset --hard								#工作区和暂存区出现过的均不保存
D:/learn-git/my-repo>git reset --mixed								#工作区出现过的保存，暂存区出现过的不保存
D:/learn-git/my-repo>ls												#阅读所有保存的文件
D:/learn-git/my-repo>git ls-files									#只阅读已经提交到暂存区的文件
```

**查看差异**：

```shell
D:/learn-git/my-repo>git diff										#默认比较工作区和暂存区的差异
D:/learn-git/my-repo>git diff HEAD									#比较工作区和最新版本区之间的差异
D:/learn-git/my-repo>git diff --cached								#比较暂存区和最新版本区之间的差异
D:/learn-git/my-repo>git 版本号1 版本号2								#比较特定版本区之间的差异
D:/learn-git/my-repo>git diff HEAD^ HEAD							#比较上一个版本和最新版本的差异
D:/learn-git/my-repo>git diff HEAD^2 HEAD file3.txt					#比较上上个版本和最新版本中file3.txt的差异
```

**删除文件**：由于工作区、暂存区和本地仓库是三个相互独立的文件夹，所以所有在工作区的删除都需要向上更新，但是git提供了git rm file.txt可以直接删除暂存区的文件，这个和工作区是实时更新的而对于本地仓库并不是。

```shell
D:/learn-git/my-repo>git rm <file>
D:/learn-git/my-repo>git rm --cached <file>					#只删除暂存区文件
D:/learn-git/my-repo>git rm -r*								#递归删除某个目录下的所有子文件和子目录
```

**gitignore忽略文件**：一般在git中会忽略以下文件包含系统或者软件自动生成的文件、编译产生的中间文件和结果文件、运行时生成日志文件、缓存文件、临时文件以及涉及身份、密码、口令、秘钥等敏感信息文件。也就是说git中提供了一个.gitignore文件夹将所有需要忽略的文件放入进去，这样提交的时候只会看到.gitignore文件而没有大量的不必要文件。

```shell
D:/learn-git/my-repo>echo "111.log">111.log					
D:/learn-git/my-repo>echo "222.log">222.log
D:/learn-git/my-repo>echo 111.log>.gitignore				#覆盖写
D:/learn-git/my-repo>echo 111.log>>.gitignore				#增加写
```

**远程仓库**：在GitHub上可以自己配置远程仓库也可以下载别人的仓库，一般提供了两种仓库的下载地址分别为**https**和**ssh**，前者需要验证用户名和密码而后者不需要只用在GitHub上添加SSH公钥即可。通过SSH建立远程仓库需要在本地文件中的.ssh文件中新建私钥和公钥文件，一般可以在git.Bash中输入ssh-keygen查看到.ssh文件位置进行创建。

```shell
D:/learn-git/remote_repo>git push						#推送仓库
D:/learn-git/remote_repo>git pull						#拉取仓库
D:/learn-git/my-repo>git remote add origin git@github.com:Dontlikemushroom/first-repo.git		#关联本地仓库
D:/learn-git/my-repo>git remote -v						#查看远程仓库
D:/learn-git/my-repo>git branch							#查看分支名称
D:/learn-git/my-repo>git branch -M main					#设置分支名称
D:/learn-git/my-repo>git push -u origin master:main		#将本地分支名称对应到远程仓库origin中的master分支名称
D:/learn-git/remote_repo>git pull origin main:master	#将远程仓库中的main分支同步到本地仓库中的master文件
```

### Web项目

**定义**：什么是Java项目（jar项目）什么是Web项目（war项目），Java项目是由main()方法来开始的，直接依赖JVM就能被编译执行。Java项目不需要服务器。Web项目中的Java文件是tomcat服务器来触发的，脱离了web服务器就无法启动。Web项目需要服务器。Web项目部署到服务器上，任何用户都可以通过浏览器来访问。将本地资源共享给外部访问。
**服务器**：Tomcat服务器对Servlet，Jsp，JNDl，JavaMail有很好的的支持，并且这个Web容器是开源免费的(Apache 开源免费)，在开发的过程中，需要将服务器引入，如何将本地java文件在服务器上部署，通常需要服务器插件。在maven项目框架中可以通过配置pom文件引入，但需要注意的是，在一个服务器中不能同时出现两个相同接口的web.xml。**端口** 指两个不同应用进程之间的接口，这两个程序可以在网络中的不同主机上，也可以是一台，类似于路由器和交换机通过IP地址和mac地址来标识，而进程之间的标识是端口号，注意，在同一台主机上不同的应用进程不会有相同的端口号。

### SpringMvC框架

**定义：**在开发项目过程中，面临着前端，后端和数据库，而maven框架实现了对插件和包的使用，mybratis框架实现了后端和数据库之间的信息交互，spring框架实现了在后端的业务层和数据库连接层的对象处理（不包含控制层），那么springmvc框架就是来处理后端中对象的处理，除此之外，使用springmvc的重要原因是用来实现前端和后端的数据信息交互。（包括：目前项目是否可以获取前端传过来的数据、目前项目是否可以相映内容到前端等等）

**运行过程：**由于springmvc是负责前端和后端的数据交互和控制层的调动，所以一般需要在前端传递信息给后端控制层，然后再由后端返回操作给前端，一般通过类的方式进行，**这是因为在war项目中项目的入口是web.xml**（而在Jar项目中则是java文件即xx.java）,一般传递分为两种即**控制**和**参数**，其中参数又分为**获取普通参数**和**使用类对象作为控制单元参数**进行接收；获取普通参数，只需要在控制单元中提供与请求参数同名的方法参数即可，Spring MVC会自动进行类型转换。使用类对象作为控制单元参数时，在控制单元中放置一个类型对象，对象名称没有要求，只需要保证请求参数名和类的属性名相同就可以了。

**SpringMVC中的类：**

Java Bean、POJO、 Entity、 VO ， 其实都是java 对象，只不过用于不同场合罢了。按照 Spring MVC 分层结构：JavaBean: 表示层 （Presentation Layer）、Entity： 业务层 （Service layer）、Dao： 数据访问层 （data access layer）。

Entity接近原始数据，是专用于EF的对数据库表的操作，Model接近业务对象，是为页面提供数据和数据校验的，所以两者可以并存；POJO是Plain OrdinaryJava Object的缩写不错，但是它通指没有使用Entity Beans的普通java对象，可以把POJO作为支持业务逻辑的协助类。domain：domain这个包国外很多项目经常用到，字面意思是域的意思。

POJO实质上可以理解为简单的实体类，顾名思义POJO类的作用是方便程序员使用数据库中的数据表，对于广大的程序员，可以很方便的将POJO类当做对象来进行使用，当然也是可以方便的调用其get,set方法。JavaBean，JavaBean更多的是一种规范，也即包含一组set和get方法的Java对象。也就是一个包含私有属性，qetter/setter方法和无参构造方法的Java类。是不是感觉和实体类特别像。其实写法上和实体类相同。唯一区别是实体类是数据库层面的概念，类型中属性要和数据库字段对应。而JavaBean的属性是灵活的，不是必须和哪里对应的。JavaBean是一个专业概念，可以简单点理解:使用类对象做为控制单元参数，接收请求参数。如果不是特别较真，狭义上可以认为JavaBean就是项目中的实体类。


# JavaWeb

## SSM框架

**定义：**

**区别：**日志是mybatis特有的配置方式，spring没有提供那样的配置，所以日志部分没法替代。所以你可以把mybatis.xml保留，里面留下这个log4j的配置。

### 项目的引用和整合

### 项目分层

### 响应数据

一般当我们想将后端的数据返回给前端让用户所使用，通常需要在控制层的类中加上特殊的注解即@ResponseBody，同时希望返回的结果是用户可读的结果，那就需要在类中的@RequestMapping加入一些参数例如@RequestMapping(value = "/findAllBooks",produces = "text/html;charset=utf-8")，这样就可以将后端的数据响应给用户。

**注意：**但是一般的tomcat7的插件中并不支持，就需要更换版本tomcat8进行运行，而在maven的中央库中并没有这个tomcat8的插件，在mvn的库中存在tomcat8的插件，所以会通过给出插件的下载地址。然后根据这个地址进行引用下载，从而可以使用tomcat8进行数据的响应，最后注意的是在tomcat8中并不是运行run插件而是war-run插件。

```xml
<pluginRepositories>
    <pluginRepository>
      <id>mvnrepository</id>
      <url>https://artifacts.alfresco.com/nexus/content/repositories/public</url>
    </pluginRepository>
  </pluginRepositories>
  <build>
    <plugins>
      <plugin>
      <groupId>org.apache.tomcat.maven</groupId>
      <artifactId>tomcat8-maven-plugin</artifactId>
      <version>3.0-r1756463</version>
      <configuration>
        <path>/testssm</path>
        <port>8082</port>
      </configuration>
    </plugin>
    </plugins>
  </build>
```



## SpringBoot的引入

**概念简介：**Spring Boot是Spring公司的一个顶级项目，和Spring Framework是一个级别的。Spring Boot实际上是利用Spring Framework4 自动配置特性完成。编写项目时不需要编写xml文件。发展到现在，Spring Boot已经具有很很大的生态圈，各种主流技术已经都提供了Spring Boot的启动器。
**引入原因：**核心思想——约定大于配置

**启动器&启动类**：Spring框架在项目中作用是Spring整合各种其他技术，让其他技术使用更加方便。Spring Boot的启动器实际上就是一个依赖。这个依赖中包含了整个这个技术的相关jar包，还包含了这个技术的自动配置，以前绝大多数XML配置都不需要配置了。以后每次使用Spring Boot整合其他技术时首先需要考虑导入启动器。Spring Boot的启动类的作用是启动Spring Boot项目，是基于Main方法来运行的。**两者的区别**：启动类表示项目的启动入口启动器表示jar包的坐标。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.msb</groupId>
    <artifactId>TestSpringBoot02</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!-- 注意在这里的引用依赖不同与普通的依赖，其在<dependencyManagement></dependencyManagement>标签下运行 -->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <!-- 注意在这里的引用依赖不是<artifactId>spring-boot-devtools</artifactId> -->
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.7.6</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>2.7.6</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>2.1.3</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.21</version>
        </dependency>
    </dependencies>
</project>
```

**yml配置文件：**springboot官方推荐的配置文件是yml文件，yml是用层级来表示关系的一种配置文件。yml中没有标签，而是通过两个空格的缩进来表示层级结构。

```xml
<!-- properties中的写法规范 -->
server.port = 8080
<!-- yml文件中的写法规范 -->
server:
  port: 8080
```

层级结构怎么找(SpringBoot常见配置，查看官网文档):
https://docs.spring.io/spring-boot/docs/2.7.6/reference/html/application-properties.html#appendix.application-properties
注意:文件名字为:application.yml，文件名字application开头，不能随意动。注意冒号后空格。

**springboot中的bean文件配置：**

通常一个项目中分为mapper、业务（service）、控制（control）三个部分，每个部分都有相应的接口和具体实现类，而这个类一般由最开始的mapper开始实现，也就是mybatis中的Mapper接口的配置方式。其分为三种——（1）在java代码中声明定义相应的具体对象；（2）Mybatis支持与spring结合使用，使得mybatis中的mapper接口可以作为spring容器中的bean被应用代码中相关类，如Service类，通过@Autowired自动注入进来。（3）如果应用是使用Java配置方式而不是XML，则在@Configuration配置类使用@MapperScan或者@MapperScans注解。

```java
@Configuration
@MapperScan("org.xyz.jblog.dao")
public class AppConfig {
    @Bean
    public DataSource dataSource() {
        return new PooledDataSource("com.mysql.jdbc.Driver", "jdbc:mysql://localhost:3306/test", "root", "root");
    }
    @Bean
    public SqlSessionFactory sqlSessionFactory() throws Exception {
        SqlSessionFactoryBeansessionFactory = new SqlSessionFactoryBean();
        sessionFactory.setDataSource(dataSource());
        return sessionFactory.getObject();
    }
}
```



# 分布式微服务架构

# 项目

## 谷粒商城（分布式基础—全栈开发篇）

**注意信息：**

- 在后端中的实体类中加上来自lombok的@Data的注解指得是为我们当前类自动写入每个变量的get和set方法。
- 在本项目中我们将主要使用到的数据进行这样的划分，即商品分类信息（一级信息）—>商品分组信息（二级信息）—>商品规格参数信息或者商品属性信息（三级信息），其对应的变量名分别为Category、Group、Attr

重点内容：

- 环境配置
- 三级树形结构
- 数据校验
- 父子组件信息交互

### 项目介绍

**背景：**市面上的电商模式有常见的5种模式分别为B2B,B2C,C2B,C2C,O2O等等，本项目也就是谷粒商城属于B2C模式，也就是我们经常看到的供应商直接把商品卖给用户，即“商对客模式，也就是通常说的商业零售，直接面向消费者销售产品和服务。如:苏宁易购、京东、天猫、小米商城。

**技术栈特色：**前后分离开发，并开发基于vue的后台管理系统
SpringCloud 全新的解决方案
应用监控、限流、网关、熔断降级等分布式方案 全方位涉及
透彻讲解分布式事务、分布式锁等分布式系统的难点
分析高并发场景的编码方式，线程池，异步编排等使用
压力测试与性能优化
各种集群技术的区别以及使用
CI/CD 使用

**项目前置要求：**
熟悉 SpringBoot 以及常见整合方案
了解 SpringCloud
熟悉 git，maven
熟悉 linux，redis，docker 基本操作
了解html,css,js,vue
熟练使用 idea 开发项目

### 分布式基础概念

**微服务：**微服务架构风格，就像是把一个单独的应用程序开发为一套小服务，每个小服务运行在自己的进程中，并使用轻量级机制通信，通常是HTTP API。这些服务围绕着业务能力来构建，并通过完全自动化部署机制来独立部署。这些服务使用不同的编程语言书写，以及不同数据存储技术，并保持最低限度的集中式管理。简而言之：拒绝大型单体应用，基于业务边界进行服务微化拆分，各个服务独立部署运行。

**集群&分布式&节点：**集群是个**物理形态**，只要是一堆机器，就可以叫集群，他们是不是一起协作着干活，这个谁也不知道；
《分布式系统原理与范型》定义：“分布式系统是若干独立计算机的集合，这些计算机对于用户来说就像单个相关系统”分布式系统(distributedsystem)是建立在网络之上的软件系统。分布式是个**工作方式**。分布式是指将不同的业务分布在不同的地声 + 集群指的是将几台服务器集中在一起，实现同一业务。例如:京东是一个分布式系统，众多业务运行在不同的机器，所有业务构成一个大型的业务集群。每一个小的业务，比如用户系统，访问压力大的时候一台服务器是不够的。我们就应该将用户系统部署到多个服务器，也就是每一个业务系统也可以做集群化；节点：集群中的一个**服务器**，分布式中的每一个节点，都可以做集群。而集群并不一定就是分布式的。
**远程调用：**在分布式系统中，各个服务可能处于不同主机，但是服务之间不可避免的需要互相调用，我们称为远程调用。**SpringCloud** 中使用 HTTP+JSON 的方式完成远程调用。

**负载均衡：**分布式系统中，A服务需要调用B服务，B服务在多台机器中都存在，A调用任意一个服务器均可完成功能。为了使每一个服务器都不要太忙或者太闲，我们可以负载均衡的调用每一个服务器，提升网站的健壮性。常见的负载均衡算法：**轮询**、**最小连接**、**散列**等等。

**服务注册/发现&注册中心：**A服务调用B服务，A服务并不知道B服务当前在哪几台服务器有，哪些正常的，哪些服务已经下线。解决这个问题可以引入注册中心；
如果某些服务下线，我们其他人可以实时的感知到其他服务的状态，从而避免调用不可用的服务。

**配置中心：**每一个服务最终都有大量的配置，并且每个服务都可能部署在多台机器上。我们经常需要变更配置，我们可以让每个服务在配置中心获取自己的配置。配置中心用来集中管理微服务的配置信息。

**服务熔断&服务降级：**在微服务架构中，微服务之间通过网络进行通信,存在相互依赖,当其中一个服务不可用时，有可能会造成雪崩效应。要防止这样的情况，必须要有容错机制来保护服务。（1）**服务熔断**，设置服务的超时，当被调用的服务经常失败到达某个值，我们可以开a.启断路保护机制，后来的请求不再去调用这个服务。本地直接返回默认的数据（2）**服务降级**，在运维期间，当系统处于高峰期，系统资源紧张，我们可以让非核心业a.务降级运行。降级:某些服务不处理，或者简单处理【抛异常、返回 NULL、调用 Mock 数据、调用 Fallback 处理逻辑】

**API网关：**在微服务架构中，APIGateway作为整体架构的重要组，它抽象了微服务中都需要的公共功能，同时提供了客户端负载均衡，服务自动熔断，灰度发布，统一认证，限流控，日志统计等丰富的功能，帮助我们解决很多 API管理难题。

### 环境搭建

**安装Linux虚拟机：**一般虚拟机的使用通常需要第三方软件进行运行，市面上的虚拟机运行软件有两款分别为VMware和VirtualBox，这个项目使用后者进行安装虚拟机。在官网下载好virtualbox软件之后，主机电脑需要进行开启cpu虚拟化才可以正常运行，可以在任务管理器中查看是否开启，开启之后一般需要下载Linux镜像然后交给virtualbox进行管理，但是在这里我们使用vagrant进行下载linux的镜像，在官网下载好vagrant之后在命令行中输入指令进行安装Linux虚拟机。

```shell
vagrant								#验证是否安装好了vagrant
vagrant init centos/7				#进行安装linux虚拟机的镜像
vagrant up							#启动虚拟机
vagrant ssh							#连接linux虚拟机
```

由于虚拟机安装在本机之上，但又与本机独立所以称之为虚拟机，而当网络接入的时候就涉及到了网络地址的转换，一般会按照端口进行转发，也就是将主机的端口与虚拟机端口进行映射，从而在接入网络的时候通过这种方式使虚拟机接入网络。不过由于每个软件进程都有属于自己的端口号，这就是得这种映射十分的繁琐，所以我们需要对虚拟机进行设置一个独立的IP地址，从而在接入网络的时候就可以跳过这些繁琐的过程。

```shell
ipconfig						#查询主机的网络连接状态
ipconfig/all					#查询主机所有接口（包括虚拟机）的网络连接状态
ping 121.194.58.22				#查询IP地址的网络连接状态
```

首先需要在cmd中查找主机IP和虚拟机IP，然后在:c/用户/用户名/Vagrantfile的文件中修改config.vm.network "private_network", ip: "192.168.56.10"中的IP地址（该行前面没有#号，注意删除），并且确保与主机的IP地址在同一子网下面（一般在最后一个4位二进制数上修改），修改之后分别在主机上ping虚拟机的IP地址和在虚拟机上ping主机的IP地址。

```shell
$ whoami							#查询用户名
$ ls/								#查询根目录
$ ip addr							#查询网络连接状态
$ ping 192.168.56.10				#测试IP地址的连接状态
```

**安装docker：**

Doker：虚拟化容器技术。Docker基于镜像，可以秒级启动各种容器。每一种容器都是一个完整的运行环境，容器之间互相隔离。

```shell
sudo yum remove docker \							#清除之前下载过的docker文件
				docker-clientdocker-client-latest \
				docker-common \
				docker-latest \
				docker-latest-logrotate \
				docker-logrotate \
				docker.engine
```

```shell
sudo yum install -y yum-utils \						#下载一些docker相关依赖的包
				device-mapper-persistent-data \
				lvm2
```

注意：在这个步骤的时候会报错

```shell
Could not retrieve mirrorlist http://mirrorlist.centos.org/?release=7&arch=x86_64&repo=os&infra=stock error was
14: curl#6 - "Could not resolve host: mirrorlist.centos.org; 未知的错误"
```

出现这个错误是因为使用的 CentOS 7 仓库已经被归档，当前的镜像地址无法找到所需的文件。CentOS 7 的官方支持已经结束，部分仓库已被移至归档库。这导致了你的 yum 命令无法找到所需的元数据文件。CentOS 7 的官方仓库在 2024 年 6 月 30 日之后已经停止维护。因此，使用最新的 CentOS 7 官方仓库可能会遇到问题，所以更换阿里云的镜像文件。

```shell
cd /etc/yum.repos.d								#进入/etc/yum.repos.d目录下找到 CentOS-Base.repo
cp  CentOS-Base.repo   CentOS-Base.repo.backup  #保存副本
vi CentOS-Base.repo								#修改仓库文件
sudo su root 									#这里肯会由于权限无法修改，所以需要提高权限，再去修改
```

```vim
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#
#
 
[base]
name=CentOS-$releasever - Base
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra
#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/
#baseurl=http://vault.centos.org/7.9.2009/x86_64/os/
baseurl=http://vault.centos.org/7.9.2009/os/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
 
#released updates 
[updates]
name=CentOS-$releasever - Updates
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates&infra=$infra
#baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/
#baseurl=http://vault.centos.org/7.9.2009/x86_64/os/
baseurl=http://vault.centos.org/7.9.2009/updates/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
 
#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras&infra=$infra
#$baseurl=http://mirror.centos.org/centos/$releasever/extras/$basearch/
#baseurl=http://vault.centos.org/7.9.2009/x86_64/os/
baseurl=http://vault.centos.org/7.9.2009/extras/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
 
#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus&infra=$infra
#baseurl=http://mirror.centos.org/centos/$releasever/centosplus/$basearch/
#baseurl=http://vault.centos.org/7.9.2009/x86_64/os/
baseurl=http://vault.centos.org/7.9.2009/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

```

修改成上面的内容之后保存退出，然后准备导入阿里云镜像文件

```shell
sudo yum clean all								#清除
sudo yum makecache								#加载
curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo			#这两个任意一个都可以
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
cat CentOS-Base.repo							#查看文件情况，看是否出现aliyuan，否则就是创建失败
```

```shell
#再次导入所依赖的相关包
sudo yum-config-manager \				#设置docker仓库的下载地址，由于官网的链接过慢，这里使用的是阿里云提供的地址
	--add-repo \
	https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo to file /etc/yum.repos.d/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io		#安装docker
sudo systemctl start docker				#启动docker
docker -v								#查看版本
docker images							#检查虚拟机相关软件的镜像
```

配置docker阿里云镜像加速：为了下载相关的镜像的时候可以快速下载（当你设置了官方的下载地址的时候），可以为虚拟机配置镜像加速器

```shell
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://7utf8e6p.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

**docker安装mysql：**

通过官网的方式进行安装mysql的镜像，但是通常这个时候会出现Error response from daemon的报错，无论后面接上什么解释都是由于网络的问题无法下载，一般3中方式进行解决。

```shell
 vi /etc/docker/daemon.json			#更换下载源
 cat /etc/resolv.conf				#修改DNS的服务配置
 									#vpn进行翻墙
 ping www.baidu.com					#查看网络是否可以正常的连接
 df -h								#查看磁盘的使用情况
 systemctl status docker			#查看镜像源shi'you
 									#当上述都没有问题的时候选择vpn来解决
```

```shell
docker run -p 3306:3306 --name mysql \
-v /mydata/mysql/log:/var/log/mysql \
-v /mydata/mysql/data:/var/lib/mysql \
-v /mydata/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5.7
docker exec -it mysql /bin/bash				#进入mysql容器的linux系统中
ls											#可以查看所有文件与一个独立的Linux系统相似，所以这就是虚拟化容器是实现的效果
```

**参数说明：**
-p3306:3306：将容器的 3306 端口映射到主机的3306 端口

-v/mydata/mysq//conf:/etc/mysgl：将配置文件夹挂载到主机

-v/mydata/mysq!/log:/var/log/mysql：将日志文件夹挂载到主机

-v/mydata/mysq!/data:/var/ib/mysg!/：将配置文件夹挂载到主机

-e MYSQL ROOT PASSWORD=root：初始化root用户的密码

-d mysql:5.7：安装容器的对应镜像的版本

```shell
cd /mydata/mysql/conf		#由于引进了文件挂载的功能，所以在虚拟机上就可以改变镜像中的文件内容
vi my.cnf					#为我们mysql容器进行基本配置
[client]
default-character-set=utf8
[mysql]
default-character-set=utf8
[mysqld]
init_connect='SET collation_connection = utf8_unicode_ci'
init_connect='SET NAMES utf8'
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
skip-name-resolve
```

![image-20241114232728348](C:\Users\hdk\AppData\Roaming\Typora\typora-user-images\image-20241114232728348.png)

文件挂载指的就是将设备文件中的顶级目录连接到 Linux 根目录下的某一目录（最好是空目录），访问此目录就等同于访问设备文件。端口映射就是将内网中的主机的一个端口映射到外网主机的一个端口，提供相应的服务。当用户访问外网IP的这个端口时，服务器自动将请求映射到对应局域网内部的机器上。



**docker安装redis：**

```shell
docker run -p 6379:6379 --name redis \
-v /mydata/redis/data:/data \
-v /mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf
```

同理安装redis按照mysql相似的初始化，需要注意的是在虚拟机linux的redis/conf文件目录下没有redis.conf文件，所以需要自行新建文件

```shell
mkdir -p /mydata/redis/conf
touch /mydata/redis/conf/redis.conf
docker exec -it redis redis-cli						#进入redis容器的redis软件中进行试验
exit
pwd
sudo tee /etc/docker/daemon.json <<-'EOF'
appendonly yes
EOF													#将redis实现AOF数据持久化
```

由于redis默认的数据在容器重启的时候是不会进行保存的，这个时候就需要进行配置redis.conf文件，结束之后就可以在容器重启的时候保存数据了，同时这里可以在redis可视化工具中进行查看——RedisDesktopManager，下载之后可以通过连接相关的服务器和账户进行查看。

最后我们希望在每次启动虚拟机的时候，免去其他冗余繁琐的操作，需要为docker以及docker中所有镜像的容器进行设置自启动，这样每当启动虚拟机就可以直接进行开发：

```shell
sudo systemctl enable docker			#设置docker开机自启动
docker update mysql --restart=always	#容器mysql开机自启动
docker update redis --restart=always	#容器redis开机自启动
```

**开发环境统一：**

首先需要安装好java和maven软件，安装完成之后可以在命令行中输入java --version和mvn -version进行查看是否成功，注意maven同样需要进行配置setting文件中的镜像和jdk版本。为了方便后期后端开发项目使用的是idea的ide，并且在idea中设置好下载的maven版本、setting文件以及本地库的位置，并且安装好Lombok和MyBatisX这两个插件，同时为了方便后期前端的开发项目使用vscode进行开发，并安装好Auto Close Tag、Auto Rename Tag、Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code、ESLint、HTML CSS Support、HTML Snippets、JavaScript (ES6) code snippets、Live Server、open in browser和Vetur等插件。

为了方便开发项目使用git进行开发，需要下载之后在GitBash中配置用户名和邮件并报错ssh密钥，这样就可以与远程仓库进行连接方便开发。

```shell
git config --global user.name "Zhao Wei"			#姓名
git config --global user.email 15155635016@163.com  #邮箱
git config user.name
git config user.email
ssh-keygen -t rsa -C "15155635016@163.com"			#设置ssh密钥
cat ~/.ssh/id_rsa.pub								#查看密钥内容
ssh -T git@gitee.com								#查看远程仓库是否连接成功
```

**创建项目微服务：**

从gitee中初始化一个项目，然后复制其网址在IDEA中打开这个项目，为我们的项目创建一些相关的微服务包括商品服务、仓储服务、订单服务、优惠劵服务和用户服务，并均创建spring initialr项目设置相同的包名（com.atguigu.gulimall.xxxx）、java版本（推荐1.8）、Maven模板以及选择web、openfeign模块。这里注意设置spring-boot-starter-parent的时候版本最好选择2.1.8.RELEASE否则会报错，并且在sringinitialr的时候由于maven的设置也可以在pom文件中设置低版本的java。没有问题之后再将gulimall文件设置为总文件，在其文件夹下新建.pom文件，初始化后加入<models><model>将所有的微服务项目加入进去，这样就可以在root根目录中管理所有的微服务了，同时在.gitignore文件中加入无需更新的文件内容，这样在提交项目的时候就不会将垃圾文件上传，最后在plugin中下载gitee插件可以快速上传，在version control中将修改的数据加入到vs中并commit and push，成功之后在云端的gitee中就可以看到项目的更新。

### 快速开发

**搭建后台管理系统：**

为了快速建立项目，我们使用gitee网址上的人人开源的项目模板进行快速建立，登陆官网之后分别下载renren-fast和renren-fast-vue，这对应着后台管理系统的后端和前端。

将renren-fast文件通过git克隆下来，导入到gulimall的文件夹中，导入完成相应的依赖之后在文件夹下的mysql.sql文件内容复制到数据库中创建数据库gulimall-admin并按照文件内容生成相对应的表，然后再application.yml中修改数据库的连接相关信息，结束之后在启动类中运行查看是否可以正常启动。**注意**：安装的mysql版本与mysql的驱动器版本有着严格的要求，MySQL驱动器8.0.x以上的版本在配置文件中使用spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver，而驱动器为5.x.x则使用spring.datasource.driver-class-name=com.mysql.jdbc.Driver，一般什么版本的mysql对应着什么样版本的驱动器，如果在5.7.27版本的mysql中使用8.0.x的驱动器需要注意的是MySQL在高版本需要指明是否进行SSL连接，MySQL5是不需要这个参数的。解决方案是：在url中的serverTimezone后面加上useSSL=false。

同理将renren-vue-fast文件通过git克隆下来并导入到vscode项目文件夹中，前端开发，少不了 Node.js；**Node.js**是一个基于 chrome v8 引擎的 JavaScript 运行环境http://nodejs.cn/api/，这里我们只需要关注与 node.js 的 npm 功能就行；NPM 是随同 NodeJs，一起安装的包管理工具，JavaScript-NPM就类似于Java-Maven。首先在官网下载安装node.js，并使用 node -v 检查版本，然后配置npm 使用淘宝镜像npm config set registry http://registry.npm.taobao.org/，然后再在vscode中运行npm init为项目安装对应的依赖包，最后通过npm run dev进行启动项目，这里需要和IDEA中的后端项目同时运行，启动成功后就可以正常使用后台管理系统了。

```cmd
node -v														#查看下载node.js的版本
npm config set registry http://registry.npm.taobao.org/		#设置node的下载源镜像
npm config get registry										#查看已经设置的镜像
#具体运行项目的方式可以在giee中查看相应文档，这是其提供的一种启动方式
npm init													#安装相应的依赖
npm run dev													#运行项目
#这是另一种启动方式
npm install -g cnpm --registry=https://registry.npm.taobao.org		#通过指定的镜像源下载cnpm包管理工具
cnpm install														#通过cnpm安装相关的依赖
npm run dev															#运行项目
```

在做这个过程中经常会报错，而具体报错原因大概是版本兼容和对应、运行时有的包未被下载以及安装相应的依赖时无法找到合理的python、c++或者是vscode等等，这个时候就需要下载nvm进行管理node和npm的版本使用工具

```cmd
nvm -v						#查看nvm版本
node -v						#查看node版本
npm -v						#查看npm版本
nvm ls						#显示所有已经下载的node版本
nvm install 16.20.2			#安装所需要的版本
nvm use 16.20.2				#运行使用确切的版本
#一般处理报错的方法
npm install babel-runtime							#使用npm安装相对应的包
npm install -g yarn									#安装yarn工具下载包
yarn add core-js									#使用yarn安装相对应的包
yarn global add core-js								#全局安装相对应的包
npm install --g --production windows-build-tools	#下载安装依赖时所缺少的工具
npm cache clean --force								#清除npm缓存 
```

**逆向工程的搭建&使用：**

逆向工程又被称为反求工程(Reverse Engineering)，是一种再现产品设计技术的过程，通过对给定的产品进行逆向研究与分析，从而得出该产品的相关参数及特性，以制造出结构相近、性能更优秀的产品模型。利用三维扫描仪获取被测产品或者模型的数字化信息(点云数据)，在通过逆向软件进行编辑、修改、优化得出CAD模型图，最后通过CAD/CAM技术传送至数控加工机床，生产制造出对应所需模具的技术过程。

在本次项目中指得是通过模块renren-generator进行快速建立每个微服务的Dao层、服务层和控制层，并为每个微服务提供启动类。逆向工程指得就是通过对生成项目进行调整和编写配置文件，从而在下一次生成项目时可以逆向的调整用已有的项目去生成新的项目，具体实现一般表现为修改renren-generator中resource的template文件或者修改不同文件的相关import等等。注意：在本次项目中当出现java里面没有longblobQ类型，这个用renren-fast-generator自动生成的类型没有自动转换，所以需要将错误位置将Longblob改为byte[]

```java
	private byte[] rollbackInfo;
```

**配置&测试微服务基本CRUD功能：**

**微服务**（Microservices）是一种软件架构风格，它将一个应用程序构建为一系列小型服务的集合，每个服务运行在其独立的进程中，并通常围绕特定的业务功能构建。这些服务可以通过定义良好的API（通常是HTTP RESTful API）进行通信，并且可以被独立部署、扩展和更新。

**CRUD**是“创建（Create）、读取（Read）、更新（Update）和删除（Delete）”的缩写，它代表了应用程序中数据管理的基本操作。在微服务架构中，每个服务通常都会实现CRUD操作来处理其特定的业务逻辑和数据。



### 分布式组件

![image-20241118215505128](C:\Users\hdk\AppData\Roaming\Typora\typora-user-images\image-20241118215505128.png)





SpringCloud 的几大痛点：

SpringCoud 部分组件停止维护和更新，给开发带来不便;Springcloud,部分环境搭建复杂，没有完善的可视化界面，我们需要大量的二次开发和定制SpringCloud配置复杂，难以上手，部分配置差别难以区分和合理应用

SpringCloud Alibaba 的优势：

阿里使用过的组件经历了考验，性能强悍，设计合理，现在开源出来大家用成套的产品搭配完善的可视化界面给开发运维带来极大的便利搭建简单，学习曲线低。

**结合 SpringcloudAlibaba我们最终的技术搭配方案：**

Springcloud Alibaba-Nacos：注册中心(服务发现/注册)

Springcloud Alibaba-Nacos：配置中心(动态配置管理)

SpringCloud-Ribbon：负载均衡

Springcloud-OpenFeign：声明式HTTP 客户端(调用远程服务)

Springcloud Alibaba-sentinel：服务容错(限流、降级、熔断)

SpringCloud-Gateway：API网关(webflux编程模式)

SpringCloud-sleuth：调用链监控

SpringCloud Alibaba-seata：原 Fescar，即分布式事务解决方案

**SpringCloud Alibaba-Nacos注册中心：**

注意下载好的nacos如果是发现闪退可以在命令行窗口移动到nacos文件bin文件夹下，手动启动查看无法启动的原因——cd /**/nacos/bin

start startup.cmd  如果发现报错是java的变量环境问题，那么需要在系统环境中配置JAVA_HOME变量，然后再添加到path中就可以正常的启动了，如果nacos一直处于startuping可能是nacos保持在用户状态，在项目初期可以先设置为本地运行的nacos版本，具体操作为用记事本打开startup.cmd，在set MODE处修改为"standalone"，这样就可以运行nacos了。

```xml
<!--        导入nacos作为服务注册/发现-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
```

**SpringCloud-OpenFeign测试远程调用：**

启动gulimall-member进行调用gulimall-coupon的时候发现注入失败**Unexpected exception during bean creation； nested exception is java.lang.IllegalStateE **这是因为SpringCloud Feign在Hoxton.M2 RELEASED版本之后不再使用ribbon，而是使用spring-cloud-loadbalancer，所以在不引入spring-cloud-loadbalancer情况下会报错，那么就需要手动的引入依赖loadbalancer并且去除掉依赖ribbon。

```xml
        <!-- 负载均衡-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-loadbalancer</artifactId>
            <version>3.0.3</version>
        </dependency>
        <!-- 导入nacos作为服务注册/发现-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
            <exclusions>
                <exclusion>
                    <artifactId>spring-cloud-netflix-ribbon</artifactId>
                    <groupId>org.springframework.cloud</groupId>
                </exclusion>
            </exclusions>
        </dependency>
```



**SpringCloud Alibaba-Nacos配置中心：**

当运行的时候出现报错create config service error!properties=NacosConfigProperties**，这是由spring boot的加载属性文件的优先级决定的，想要在加载属性之前去config server上取配置文件，那NacosConfig或SpringCloudConfig相关配置就是需要最先加载的，而bootstrap.properties的加载是先于application.properties的，所以config client要配置config的相关配置就只能写到bootstrap.properties里了。

```xml
<!--        导入nacos作为配置中心-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
        </dependency>
<!--        导入依赖使得可以用bootstrap.properties作为配置文件-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-bootstrap</artifactId>
            <version>3.1.0</version>
        </dependency>
```

**命名空间和配置分组：**

命名空间：就是用来配置隔离的，默认命名空间是public(保留空间)，也就是默认新增的所有配置都在public空间。这样就有利于在开发，测试，生产中利用命名空间来做环境隔离。注意：在bootstrap.properties配置上，需要使用哪个命名空间下的配置需要在文件中说明。例如spring.cloud.nacos.config.namespace=9c32e24d-0d4a-4751-8406-41a288144fb7

同时每一个微服务之间互相隔离配置，每一个微服务都创建自己的命名空间，只加载自己命名空间下的所有配置，其中配置集就是所有的配置的集合，而配置集ID就类似文件名，同理Data ID也是文件名，最后使用配置分组可以进一步进行配置隔离，默认所有的配置集都属于DEFAULT_GROUP，在这个项目中每个微服务创建自己的命名空间，使用配置分组区分环境，dev，test，prod。同时spring-cloud-starter-alibaba-nacos-config还为开发人员提供了加载多配置集的功能，从而使得在每一个微服务中可以通过使用nacos只需要配置一个bootstrap.properties文件就可以运行项目。

```properties
spring.application.name=gulimall-coupon
spring.cloud.nacos.config.server-addr=127.0.0.1:8848
spring.cloud.nacos.config.namespace=452d0b17-2e15-4353-8441-989b5b442ee1

spring.cloud.nacos.config.ext-config[0].data-id=datasource.yml
spring.cloud.nacos.config.ext-config[0].group=dev
spring.cloud.nacos.config.ext-config[0].refresh=true

spring.cloud.nacos.config.ext-config[1].data-id=mybatis.yml
spring.cloud.nacos.config.ext-config[1].group=dev
spring.cloud.nacos.config.ext-config[1].refresh=true

spring.cloud.nacos.config.ext-config[2].data-id=other.yml
spring.cloud.nacos.config.ext-config[2].group=dev
spring.cloud.nacos.config.ext-config[2].refresh=true
```

**SpringCloud-Gateway的创建以及测试网关：**

本项目可以通过创建API网关项目进行对各个微服务的网络数据的控制，在项目gulimall文件下创建spring initializr项目并命名为gulimall_gateway，在创建的时候查询插件依赖GateWay并添加进来，同时由于该项目也使用nacos作为配置中心和服务注册发现中心，所以需要引入gulimall_common项目的依赖。注意：新版本的依赖会选择gateway-web，这里我们需要选择spring-cloud-starter-gateway即可。

由于不用使用数据库的依赖，所以直接运行会报错，这里可以直接去依赖中exclude掉mysql的依赖，也可以在启动类中过滤掉数据源的相关操作。

```java
@EnableDiscoveryClient
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})
```

基本部署完成之后，gateway的项目就可以启动了，但是根据官网的说明我们还需要为其配置相关的配置文件。一般就是为其配置网关的路由以及路由相对应的断言条件，这样就可以在路由部分对用户的网络使用进行控制。**注意：**同样的yml文件依然可以写成properties文件，那么就可以在nacos中为项目进行配置从而去掉了一些冗余的操作。

```xml
spring:
  cloud:
    gateway:
      routes:
        - id: test_route
          uri: https://www.baidu.com
          predicates:
            - Query=url,baidu

        - id: qq_route
          uri: https://www.qq.com
          predicates:
            - Query=url,qq
```

### 前端基础

**技术栈简介：**

前端的技术栈大致有VScode、ES6、Node.js、Vue、Babel、Webpack六个部分，其基本解释为前端开发IDE、JavaScript的版本特性、类似于Maven的包管理工具、在前端开发中类似与后端开发的SpringSVC框架、前端代码兼容浏览器工具以及前端代码打包工具。本项目主要集中学习ES6和Vue这两个技术栈。

**ES6中的let以及const：**

**ES6中的解构表达式：**

**ES6中的字符串扩展：**

**ES6中的箭头函数：**



**Vue的介绍：**

MVVM思想——M:即 Model，模型，包括数据和一些基本操作，V:即 View，视图，页面渲染结果，VM:即 View-Model，模型与视图间的双向操作(无需开发人员干涉)。在 MWM 之前，开发人员从后端获取需要的数据模型，然后要通过 DOM 操作 Model 渲染到 View 中。而后当用户操作视图，我们还需要通过 DOM 获取 View 中的数据，然后同步到Model 中。而 MVVM 中的 VM 要做的事情就是把 DOM 操作完全封装起来，开发人员不用再关心 Model和 View 之间是如何互相影响的：

只要我们 Model发生了改变，View 上自然就会表现出来。当用户修改了 View，Model中的数据也会跟着改变。把开发人员从繁琐的 DOM 操作中解放出来，把关注点放在如何操作 Model 上。

注意在安装vue的依赖包的时候，如果安装vue后无法识别到vue.js文件，是因为官方指令是下载最新版，而最新版中没有这个文件，可以下载2.6.10版本这个是与我们项目兼容的Vue版本。

```cmd
npm init -y					#初始化npm工具
npm init vue				#安装vue依赖默认最新版本
npm init vue@2.6.10			#安装vue依赖的指定版本
```



**Vue-使用Vue脚手架进行模块化开发：**

在开发之前需要进行全局安装webpack，这里注意在命令行之中如果被打断则需要在cmd属性里面把快速开发关闭，这样在进行下载或者加载的过程中点击窗口就可以不被打断。前端项目和后端开发相似，都有一套相似的框架进行开发，比如在后端开发中我们经常使用的框架是ssm框架（spring，springboot，mybatis），那么在前端中常用的框架就有JQuery、Vue、React等等，而进行项目构建的方式通常也是使用第三方工具进行构建，比如后端中使用maven进行构建，而在前端中就是通过webpack进行构建。那么怎么进行构建呢，通常我们需要通过包管理工具进行安装相关的依赖，然后就可以进行项目构建了。

```cmd
npm install webpack -g				#全局安装webpack
npm install -g @vue/cli				#快速管理项目工具
npm install -g @vue/cli-init		#全局安装vue手脚架
vue init webpack appname			#初始化vue项目
```

如果命令行中出现了Command vue init requires a global addon to be installed.Please run undefined @vue/cli-init and try again.这是因为在最新的cli-init的版本中已经不再使用webpack进行构建项目了，而是选择vue create appname进行构建项目

```cmd
npm install -g @vue/cli-init@4.0.3		#安装指定版本
vue init webpack appname				#旧版启动
vue create appname						#新版启动
npm list -g								#显示安装的依赖包
npm uninstall -g @vue/cli-init			#卸载包
```

**Vue-整合ElenmentUI快速开发：**

在进行前端开发的过程中，一般会使用vue文件作为组件，快速的形成前端页面，而一般的vue文件是由三部分组成，分别是<template><script>和<style>。所以为了方便开发我们需要为自己配置一个代码片段，这个选项在文件/首选项/配置代码片段/新建全局代码片段文件，新建之后输入以下内容https://www.cnblogs.com/songjilong/p/12635448.html，这样在以后的vue文件输入vue关键字就可以直接快速进行开发。

### 商品服务

**三级分类-查询、递归树形结构数据获取：**

API

箭头函数

```java
 	@Override
    public List<CategoryEntity> listWithTree() {
        //1、查出所有分类
        List<CategoryEntity> categoryEntities = baseMapper.selectList(null);
        /**2、组装成父子的树形结构
         *      1）、找到所有的一级分类
         *      2）、递归查找所有的子菜单
         */
        List<CategoryEntity> collect = categoryEntities.stream().filter((CategoryEntity) -> {
            return CategoryEntity.getParentCid() == 0;
        }).map((menu)->{
            menu.setChildren(getChildrens(menu,categoryEntities));
            return menu;
        }).sorted((menu1,menu2)->{
            return (menu1.getSort()==null?0:menu1.getSort())-(menu2.getSort()==null?0:menu2.getSort());
        }).collect(Collectors.toList());
        return collect;
    }

    //获取菜单的子菜单函数
    private List<CategoryEntity> getChildrens(CategoryEntity root, List<CategoryEntity> all) {
        List<CategoryEntity> children = all.stream().filter(categoryEntity -> {
            return categoryEntity.getParentCid() == root.getCatId();
            //a.找到子菜单
        }).map((menu)->{
            menu.setChildren(getChildrens(menu,all));
            return menu;
            //b.菜单的排序
        }).sorted((menu1,menu2)->{
            return (menu1.getSort()==null?0:menu1.getSort())-(menu2.getSort()==null?0:menu2.getSort());
        }).collect(Collectors.toList());

        return children;
    }
```

**三级分类-配置网关路由与路径重写：**

当我们在renren-fast项目的菜单管理中创建商品系统下的分类维护，我们可以发现其访问的是http://localhost:8001/#/product-category，而其url路劲则是product/category这说明在这个项目中将“/”转换为了“-”，我们可以在renren-fast-vue前端项目中观察到，在文件夹src/models/views/sys中就有menu.vue文件，这说明在models文件下文件夹和vue文件就组成了前面所说的转换形式，所以当我们要设计分类维护(product/category)的界面的时候就需要在models下新建product文件夹以及category.vue文件。

输入vue可以快速生成vue模板，然后在elementui中可以找到相关的界面设计，在 Tree 树形控件中从而可以快速的进行形成我们想要的树形结构数据模板。不过，在这个项目中我们需要将后端从数据库中的数据调入到前端中进行显示，所以需要通过发送请求的方式进行获取数据，一般发送请求的方式获取数据可以从其他vue文件中获取也可以写入以下的函数

```javascript
getDataList () {
        this.dataListLoading = true
        this.$http({
          url: this.$http.adornUrl('/sys/role/list'),
          method: 'get',
          params: this.$http.adornParams({
            'page': this.pageIndex,
            'limit': this.pageSize,
            'roleName': this.dataForm.roleName
          })
        }).then(({data}) => {
          if (data && data.code === 0) {
            this.dataList = data.page.list
            this.totalPage = data.page.totalCount
          } else {
            this.dataList = []
            this.totalPage = 0
          }
          this.dataListLoading = false
        })
      }

//生命周期 - 创建完成（可以访问当前this实例）
created() {
   this.getDataList();
},
```

在这里我们可以通过函数去请求对应的数据返回并在then中做后续的处理，结束后在生命周期中调用测试，但是当我们刷新界面的时候却在控制台中发现tree的请求报错404，细心的我们可以发现这个时候我们请求的url是在本项目的协议、地址和接口下访问而不是在特定的协议、地址和接口，那么我们这个时候就开始需要网关的出现了，因为网关最大的作用就是协助进行API的调用。

首先，我们可以在renren-fast项目中找到根api请求地址，一般出现在static/config/index.js中，修改接口的请求地址为网关的协议、地址和接口，这样我们去请求数据的时候就可以先请求网关，然后再**由网关去转换地址为目标地址从而请求成功数据**。但再设置完api请求接口的时候，renren-fast的网址退出了主界面要求重新登陆，这个时候发现验证码却显示不出来了，这是因为验证码的数据应该请求到renren-fast的项目，而刚刚的操作却直接发送给了网关项目，所以为了能够将发往网关的请求发送给响应的项目就需要将网关项目添加到nacos中，并为其配置相应的配置文件。

```xml
spring:
  cloud:
    gateway:
      routes:
        - id: test_route
          uri: https://www.baidu.com
          predicates:
            - Query=url,baidu

        - id: qq_route
          uri: https://www.qq.com
          predicates:
            - Query=url,qq

        - id: admin_route
          uri: lb://renren-fast
          predicates:
            - Path=/api/**
          filters:
            - RewritePath=/api/(?<segment>.*),/renren-fast/$\{segment}
```

其中lb选择目标项目的协议、地址和接口，predicates筛选哪些请求通过这个路由规则，filters将访问路径修改成开发人员想要的对应路径。如果再网关项目中的debuglog中出现RoundRobinLoadBalancer      : No servers available for service: renren-fast，由于springcloud2020弃用了Ribbon，因此Alibaba在2021版本nacos中删除了Ribbon的jar包，因此无法通过lb路由到指定微服务，出现了503情况，所以只需要引入springcloud loadbalancer包即可。输入信息和验证码之后却在登陆过程中发现了403的报错，这是由于在网址访问的过程中出现了跨域的现象；

**三级分类-网关统一配置跨域：**

跨域：指的是浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对javascript施加的安全限制。而同源策略是指协议，域名，端口都要相同，其中有一个不同都会产生跨域。解决方法有：（1）使用nginx部署为同一域；（2）配置当次请求允许跨域；

我们这里准备通过第二种方式处理，首先我们需要了解跨域资源共享是如何进行的，跨域资源共享标准新增了一组 HTTP 首部字段，允许服务器声明哪些源站通过浏览器有权限访问哪些资源。另外，规范要求，对那些可能对服务器数据产生副作用的 HTTP请求方法(特别是 GET 以外的 HTTP 请求，或者搭配某些 MIME 类型的 POST 请求)，浏览器必须首先使用OPTIONS 方法发起一个预检请求(preflghtrequest)，从而获知服务端是否允许该跨域请求，服务器确认允许之后，才发起实际的 HTTP 请求。在预检请求的返回中，服务器端也可以通知客户端，是否需要携带身份凭证(包括 Cookies 和 HTTP 认证相关数据)。
CORS请求失败会产生错误，但是为了安全，在JavaScrpt代码层面是无法获知到底具体是哪里出了问题。你只能查看浏览器的控制台以得知具体是哪里出现了错误。

简单来说，跨域只有简单请求的时候会直接发送http文件，而非简单请求的时候一般会先发送预检请求头，我就只需要在这里将预检信息设置为允许跨域即可，查看官网知道，在网关项目中配置控制类这样就可以在跨界的时候允许直接访问了。

```java
import org.springframework.web.cors.reactive.UrlBasedCorsConfigurationSource;

@Configuration
public class GulimallCorsConfiguration{

    @Bean
    public CorsWebFilter corsWebFilter(){
        //注意这里引用的是响应式的urlbasecorsconfiguration
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        CorsConfiguration corsConfiguration = new CorsConfiguration();

        //配置跨域信息
        corsConfiguration.addAllowedHeader("*");
        corsConfiguration.addAllowedMethod("*");
        corsConfiguration.addAllowedOrigin("*");
        corsConfiguration.setAllowCredentials(true);

        source.registerCorsConfiguration("/**",corsConfiguration);
        return new CorsWebFilter(source);
    }
}
```

**三级分类-查询在后台管理系统中显示：**

实际上前端是如何获取数据的呢，首先一般是需要进行请求访问的，然后在上面的vue文件中的get函数实际上就是请求访问，不过请求内容是访问路径真正的请求路径是再加上他的默认地址，由于在项目中设置了网关去访问所以又由网关将路径请求到实际的项目中，这样请求内容就返回过来了，**注意返回内容是一个整体在这个地方我们请求的树形结构还需要打开data中的data属性才是我们可以直接观察到的所有一级菜单。**

**三级分类-删除：**

首先删除数据库的数据有两种方式，一种是直接删除数据而另一种是逻辑删除，后者的意思是通过一个字段来说明该数据是否显示，而在删除的时候将其的数值调成不显示即可。首先需要在控制类中找到对应菜单控制的类为其加上删除的操作，这里需要注意删除即对数据库的内容进行删除， @RequestBody:获取请求体，必须发送POST请求，SpringMVC自动将请求体的数据(json)，转为对应的对象。一般renren-fast为我们设置了简单删除，但是我们需要手动的自己写一个，这是因为业务不同可能考虑的东西也不同，所以调用service类的api进行删除，再为这个api写出实现方式

```java
    @RequestMapping("/delete")
    public R delete(@RequestBody Long[] catIds){
        //1、检查当前删除的菜单，是否被别的地方引用，所以不能简单的进行直接删除
		//categoryService.removeByIds(Arrays.asList(catIds));

        categoryService.removeMenuByIds(Arrays.asList(catIds));
        return R.ok();
    }
    
    public interface CategoryService extends IService<CategoryEntity> {
    PageUtils queryPage(Map<String, Object> params);
    List<CategoryEntity> listWithTree();
    void removeMenuByIds(List<Long> asList);

	}

    @Override
    public void removeMenuByIds(List<Long> asList) {
        //TODO 1、检查当前删除的菜单，是否被别的地方引用，所以不能简单的进行直接删除

        //逻辑删除
        baseMapper.deleteBatchIds(asList);
    }
```

实现了后端的删除操作，我们也需要再前端的控制台中实现页面的删除操作，后端操作是结果而前端就是用户的操作了，我们在前面为界面设置了两个按钮，删除按钮会调用remove（）函数。而我们就需要通过这个函数去访问后端的delete操作，然后再在界面上去除掉那个菜单

```javascript
	  remove(node, data) {
      var ids = [data.catId];
      this.$confirm(`是否删除【${data.name}】菜单?`, "提示", {
        confirmButtonText: "确定",
        cancelButtonText: "取消",
        type: "warning",
      })
        .then(() => {
          this.$http({
            url: this.$http.adornUrl("/product/category/delete"),
            method: "post",
            data: this.$http.adornData(ids, false),
          }).then(({ data }) => {
            this.$message({
              message: "菜单删除成功",
              type: "success",
            });
            //刷新菜单
            this.getMenus();
            //设置需要默认展开的菜单
            this.expandKeys = [node.parent.data.catId];
            console.log(this.expandKeys);
          });
        })
        .catch(() => {});
```

**三级分类-新增：**

```javascript
	//添加菜单
    append(data) {
      console.log("append", data);
      this.dialogVisible = true;
      //
      this.category.parentCid = data.catId;
      this.category.catLevel = data.catLevel * 1 + 1;
      this.category.catId = null;
      this.category.name = "";
      this.category.sort = 0;
      this.category.showStatus = 1;
    },
    //添加三级分类
    addCategory() {
      console.log("提交的三级分类", this.category);
      this.$http({
        url: this.$http.adornUrl("/product/category/save"),
        method: "post",
        data: this.$http.adornData(this.category, false),
      }).then(({ data }) => {
        this.$message({
          message: "菜单保存成功",
          type: "success",
        });
        //关闭对话框
        this.dialogVisible = false;
        //刷新菜单
        this.getMenus();
        //设置需要默认展开的菜单
        this.expandKeys = [this.category.parentCid];
        // console.log(this.expandKeys);
      });
    },
```

**三级分类-修改：**



**三级分类-批量删除：**



**品牌管理-效果优化和快速显示：**



**品牌管理-文件上传：**

后端

前端

**品牌管理-数据校验：**

前端自定义校验





类似postman可以跳过前端校验，乱发数据，前端防用户误操作，后端防黑客搞攻击，而黑客使用bp发的，不是postman。

后端的JSR303校验规则，其基本使用分为以下几步

 * 1）、给Bean添加校验注解，其所有的解释来自于包：javax.validation.constrains，并定义自己的message提示
 * 2）、在控制类中的方法前开启校验功能@Valid，其实现的效果为校验错误之后会有默认的的响应
 * 3）、但是有的时候默认的响应并不满足我们的业务要求所以错误响应也可以由我们进行自定义，即给校验的bean后紧跟一个BindingResult，就可以获取到校验的结果，通过校验的结果我们可以为报错进行分析并显示具体报错原因给用户

```java
    /**
     * 保存
     */
    @RequestMapping("/save")
    public R save(@Valid @RequestBody BrandEntity brand, BindingResult result){
        if(result.hasErrors()){
            //存储校验分析结果
            Map<String,String> map = new HashMap<>();
            //获取校验的错误结果
            result.getFieldErrors().forEach((item)->{
                //获取到错误的默认提示
                String message = item.getDefaultMessage();
                //获取到错误的属性名称
                String filed = item.getField();
                map.put(message,filed);
            });
            return R.error(400,"提交的数据不合法").put("data",map);
        }else{
            brandService.save(brand);
            return R.ok();
        }
    }
```

但是如果在开发的过程中为每一个微服务的每一个实现功能都配置响应的错误响应，开发的过程将相当冗余，所以我们就可以用到@ControllerAdvice来进行统一的异常处理

 * 1）、编写异常处理类，使用@ControllerAdvice
 * 2）、使用@ExceptionHandler标注方法可以处理的异常

```java
@Slf4j
@RestControllerAdvice(basePackages = "com.atguigu.gulimall.product.controller")
public class GulimallExceptionControllerAdvice {

    @ExceptionHandler(value = MethodArgumentNotValidException.class)
    public R handleValidException(MethodArgumentNotValidException e){
        log.error("数据校验出现问题{}，异常类型{}",e.getMessage(),e.getClass());
        BindingResult bindingResult = e.getBindingResult();

        Map<String,String> map = new HashMap<>();
        bindingResult.getFieldErrors().forEach((item)->{
            String message = item.getDefaultMessage();
            String filed = item.getField();
            map.put(message,filed);
        });
        return R.error(400,"数据校验出现错误").put("data",map);
    }

    //我们不清楚每一种的错误属于什么类型的错误，所以在开发的初期进行统一的输出，再在后期为每一种错误进行特定的数据处理，这里需要注意
    // throwable和exception的区别：
    //1、throwable是父类，exception是子类。
    //2、throwable是根基，exception是从throwable派生出来的。
    //3、throwable中包括exception（异常）和error（错误）。
    //所以使用包含Throwable将会更加合适
    @ExceptionHandler(value = Throwable.class)
    public R handleValidException(Throwable throwable){
        log.error("数据校验出现问题{}，异常类型{}",throwable.getMessage(),throwable.getClass());
        return R.error();
    }

}
```

同时为了统一在开发过程中面对报错的数字代码有统一的要求，并且降低项目的冗余性，所以可以为一些相同的错误设置同样的code：

```java
/**
 * @ControllerAcHandler
 * 系统错误码
 * ЖЖ
 * 错误码和错误信息定义类
 * *1.错误码定义规则为5为数字
 * *2.前两位表示业务场景，最后三位表示错误码。例如:100001。10:通用001:系统未知异常
 * *3.维护错误码后需要维护错误描述，将他们定义为枚举形式错误码列表:
 * 10:通用
 * 参数格式校验001:
 * 11:商品
 * 12: 订单
 * 13:购物车
 * 14: 物流
 * */

public enum BizCodeEnum {
    UNKNOW_EXCEPTION( 10000,"系统未知异常"),
    VALID_EXCEPTION( 10001,"参数格式校验失败");

    private int code;
    private String msg;
    BizCodeEnum(int code,String msg){
        this.code =code;
        this.msg = msg;
    }

    public int getCode() {
        return code;
    }

    public String getMsg() {
        return msg;
    }

```

除了基本的的校验方法，为了给不同情况的输入进行不同的校验规则，那么就还需要进行分组校验(即多场景的分组校验)，也分为以下步骤：

 * 1）、@NotBlank(message = ""品牌必须提交",group = {AddGroup.class,UpDateGroup.class})，即给校验注解标注什么情况需要进行校验，但是我们仔细观察就可以发现这里的group放入的是java类，而且还是没有任何jar包所提供的类，这就说明我们要为我们的操作功能提供封装的类，这样就可以实现分类校验，同时这些功能和错误编码是一样为每一个微服务都要提供的，所以建议写在gulimall-commom项目里面。
 * 2）、@Validated({AddGroup.class})
 * 3）、默认没有指定分组的校验注解@NotBlank，在分组校验@Validated({AddGroup.class})情况下不生效，只会在@Validated生效；也就是@validated 如果指定了分组，那么Bean中只校验属于该分组注解标注的值是否合法，如果@validated没有标注group，就会校验bean中所有注解group没有赋值的所有字段的值

在有些时候我们要进行特定的检验方法，而提供的注解不包含这些的实现，那么就需要进行自定义校验

 * 1）、编写一个自定义的校验注解
 * 2）、编写一个自定义的校验器  ConstrainValidator
 * 3）、关联自定义的校验器和自定义的校验注解
    * @Documented
    * @Constraint(validateBy = { ListValueConstrainValidator.class【可以指定多个不同的校验器，适配不同类型的校验】 })
    * @Target({ METHOD, FIELD, ANNOTATION_TYPE, CONSTRUCTOR, PARAMETER, TYPE_USE })
    * @Retention(RUNTIME)
    * public @interfaceListValue {}



**SPU和SKU：**

SPU（Standard Product Unit）和SKU（Stock Keeping Unit）是电商和库存管理中常用的两个术语：

SPU（Standard Product Unit）：标准产品单元，指的是商品信息聚合的最小单位，是一组可复用、易检索的标准化信息的集合，该集合描述了一个产品的特性。通常来说，SPU是商品的基本信息，包括品牌、型号、配置等，对于同一SPU的商品，它们在功能和外观上是相同的。例如，对于手机来说，同一型号的不同颜色和存储容量可以视为同一个SPU。
SKU（Stock Keeping Unit）：库存量单位，指的是库存进出计量的基本单元，可以唯一地标识商品。SKU是库存管理中的最小单位，每个SKU都对应着一个唯一的库存商品。例如，对于手机来说，不同颜色和存储容量的组合会有不同的SKU，因为它们在库存中被视为不同的商品。简单来说，SPU是商品的标准化信息，而SKU是商品的具体库存单位。一个SPU可以对应多个SKU，因为不同的颜色、尺寸、配置等可以形成不同的SKU。

简单一点就是sku是具体的商品单位，相互独立，而spu是在描述商品的过程中的某一个属性，彼此之间还可以相互组合。

在本项目中我们将主要使用到的数据进行这样的划分，即商品分类信息（一级信息）—>商品分组信息（二级信息）—>商品规格参数信息或者商品属性信息（三级信息）



**属性分类-父子组件交互：**

在后台管理系统中，我们需要提供SPU和SKU的相互关联的关系，这就这涉及到了平台属性的属性分组。首先在这个页面中我们要提供左侧为SPU的商品右侧需要提供SKU的具体属性，细心的你可以发现在未来多个页面中我们都需要提供SPU的三级分类，所以我们将其包装成一个组件并export出来，在属性分组的界面中import同时为了将界面分成多个模块，我们使用elementUI中的Layout布局。

```javascript
<el-row :gutter="20">
  <el-col :span="6"><div class="grid-content bg-purple"></div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple"></div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple"></div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple"></div></el-col>
</el-row>
```

而右侧我们将其作为主体，在快速生成的逆向工程中的attrgroup.vue中的界面复制进去，可以发现他还引用了另外一个组件，其主要实现的是添加的时候的弹窗信息。这样基本信息功能就实现了，但是在这个界面最主要的功能却还没有实现，那就是将左侧的SPU的信息和右侧的SKU的信息进行关联，也就是实现在左侧进行点击可以在右侧进行展示，那如何进行实现呢这就涉及到父子组件的交互了其中更加能体现出前端各种代码的基本实现过程。

```javascript
/**
 * 父子组件传递数据：
 * 1）、子组件给父组件传递数据，事件机制
 *      子组件给父组件发送一个事件，携带上数据
 *      父组件监听这个事件，获取数据
 *      即this.$emit("事件名",携带的数据...)
 * */ 
     nodeclick(data, node, component) {
        console.log("子组件category的节点被点击",data,node,component);
        this.$emit("tree-node-click",data,node,component);
    }
```

通过以上的方法就可以将子组件的数据和父节点的数据进行交互了，这里面可以发现原来之前的所有的elementUI中的组件虽然只有一句标签但是其中也是父子组件的调用从而使得我们在父组件中可以直接调用子组件传过来的数值。完成前端就要进行完成后端的数据实现了：

```java
@Service("attrGroupService")
public class AttrGroupServiceImpl extends ServiceImpl<AttrGroupDao, AttrGroupEntity> implements AttrGroupService {

    //这个是默认的生成方法，只有一个参数并显示所有的list
    @Override
    public PageUtils queryPage(Map<String, Object> params) {
        IPage<AttrGroupEntity> page = this.page(
                //Query类这是由逆向工程生成的类型转换器，其中的getPage就可以将params对象转换成一个分页的Page对象
                new Query<AttrGroupEntity>().getPage(params),
                //QueryWrapper类的主要功能就是按字段进行查询，如果输入为空那么就是查询所有
                new QueryWrapper<AttrGroupEntity>()
        );
        //而PageUtils也是封装好的分页对象Page转换为总分页展示对象pageutils
        return new PageUtils(page);
    }

    //在前端规定了只有确定了catelogId才显示具体的SPU对应的所有SKU的商品，而当没有进行点击具体的SPU的时候catelogId默认为0，这个时候将显示所有的SKU
    //这个部分的逻辑就是当未点击商品类，通过分辨默认值为零显示所有的商品也就是第一部分。当点击了商品类就一定会有catelogid，
    //但是在商品类中还可以进行搜索来进一步进行分类显示，所以需要进行判断key是否为空，
    // 若不为空按照key中可能存在于组名或者组id中，最后按照筛选后的结果进行显示这就是第二部分
    @Override
    public PageUtils queryPage(Map<String, Object> params, Long catelogId) {
        if( catelogId==0 ){
            IPage<AttrGroupEntity> page = this.page(new Query<AttrGroupEntity>().getPage(params),
                    new QueryWrapper<AttrGroupEntity>());
            return new PageUtils(page);
        }else{
            String key = (String) params.get("key");
            QueryWrapper<AttrGroupEntity> wrapper = new QueryWrapper<AttrGroupEntity>().eq("catelog_id",catelogId);
            if(!StringUtils.isEmpty(key)){
                wrapper.and((object)->{
                   object.eq("attr_group_id",key).or().like("attr_group_name",key);
                });
            }
            IPage<AttrGroupEntity> page = this.page(new Query<AttrGroupEntity>().getPage(params),
                    wrapper);
            return new PageUtils(page);
        }
    }
}
```

实现了前后端的操作之后，在前端的父组件中绑定点击函数，并在点击函数中将点击的数据传给父组件Vue实例中的ID参数，最后在显示列表中增加该访问路径，这样父子组件的关联就简单地实现了。

**属性分类-分组新增&分组修改：**

在新增按钮中可以发现其所属分类是一串数字，这与我们的业务不满足，所以需要将这种形式改成用户可以选择的形式。打开elementUI中在“Cascader 级联选择器”中可以实现我们所需要的业务。注意在这个组件中需要我们配置params变量才可以正确的显示，但是在我们的这个项目中可以发现，在第三级菜单中还可以打开这就要追溯到当初我们进行生成树形结构的时候的问题，那个时候我们仅仅是在第三级的孩子变量中放入了空集合，所以这里需要将这个空集合去掉

```java
	/**
	 * 菜单的子菜单
	 * */
	//该属性在数据表里面不存在
	@JsonInclude(JsonInclude.Include.NON_EMPTY)
	@TableField(exist = false)
	private List<CategoryEntity> children;
```

同时我们在修改按钮中打开之后也能看到像级联选择器那样的新式，这就需要我们在点击修改的时候向后端发送请求的时候后端可以向我们返回一个带有路劲的三级菜单，这样“Cascader 级联选择器”中的组件就可以按照返回的数据为我们显示达到我们需要的业务需求了。

```java
    @Override
    public Long[] findCatelogPath(Long catelogId) {
        List<Long> paths = new ArrayList<>();
        List<Long> ParentPath = findParentPath(catelogId,paths);
        Collections.reverse(ParentPath);

        return (Long[]) paths.toArray(new Long[ParentPath.size()]);
    }

    private List<Long> findParentPath(Long catelogId, List<Long> paths) {
        //收集当当前节点的id
        paths.add(catelogId);
        CategoryEntity byId = this.getById(catelogId);
        if(byId.getParentCid()!=0){
            findParentPath(byId.getParentCid(),paths);
        }
        return paths;
    }
```

完成上述功能之后，我们发现消除当关闭弹窗时，会发生表单数据残留的bug，所以需要按照elementUI中的文档要求使用@close="closeDialog"这样当界面框发生关闭的时候就会调用这个函数，而这个函数会重置界面框组件Vue实例中的catelogPath变量，从而在下一次打开的时候就不会发生数据残留。并且我们想要给这个界面的所属分类增加搜索功能，只需要按照elementUI的文档要求，加入`filterable placeholder="试试搜索：手机"`这样就实现了界面的搜索功能，还可以修改指定的提示语。

```javascript
      <el-form-item label="所属分类" prop="catelogId">
        <!-- <el-input v-model="dataForm.catelogId" placeholder="所属分类id"></el-input> -->
        <el-cascader
          filterable placeholder="试试搜索：手机"
          v-model="dataForm.catelogIds"
          :options="categorys"
          :props="props"
        ></el-cascader>
      </el-form-item>
```

**品牌管理-分类与品牌的关联和联级更新：**

首先我们可以发现现在搭建的项目无法实现分页功能，所以需要按照maybatis-plus的规则进行配置。可以在项目中生成一个专门进行配置的文件夹，在其中新建类MybatisConfig然后写入专门的代码从而实现分页的效果。

```java
@Configuration
@MapperScan("com.atguigu.gulimall.product.dao")
@EnableTransactionManagement  //开启事务模式
public class MybatisConfig {

    /**
     * 添加分页插件
     * 上面的是最新版，下面的是旧版
     */
//    @Bean
//    public MybatisPlusInterceptor mybatisPlusInterceptor() {
//        MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
//        interceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL)); // 如果配置多个插件, 切记分页最后添加
//        // 如果有多数据源可以不配具体类型, 否则都建议配上具体的 DbType
//        return interceptor;
//    }
    @Bean
    public PaginationInterceptor paginationInterceptor(){
        PaginationInterceptor paginationInterceptor = new PaginationInterceptor();
        // 设置请浗的页面大于最大页后操作， true调回到首页，false 继续请求 默认false
         paginationInterceptor.setOverflow(false);
        // 设置最大单页限制数量，默认 500 条，-1 不受限制
         paginationInterceptor.setLimit(1000);
         return paginationInterceptor;
    }
}
```

然后进行设置模糊搜索的功能，首先由逆向工程实现的搜索功能只是简单的根据前端发送请求的时候携带的数据，将所有的集合进行展示，所以我们这里需要手动的进行更改使其可以为我进行展示我们所想要的内容，默认的api为这样

```java
    @RequestMapping("/list")
    public R list(@RequestParam Map<String, Object> params){
        PageUtils page = brandService.queryPage(params);

        return R.ok().put("page", page);
    }
```

其中@RequestParam的作用是就是把请求中的指定名称的参数传递给控制器中的形参赋值，这样我们就简单的获取了前端的所有数据，所以在函数中我们通过服务层的功能实现了页面搜索并将搜索的结果返回形成PageUtils返回，这样我们具体修改的地方就是服务层实现类的特定函数，在这个函数中我们这样写

```java
@Service("brandService")
public class BrandServiceImpl extends ServiceImpl<BrandDao, BrandEntity> implements BrandService {

    @Override
    public PageUtils queryPage(Map<String, Object> params) {
        //获取key的值
        String key = (String) params.get("key");
        QueryWrapper<BrandEntity> wrapper = new QueryWrapper<BrandEntity>();
        if(!StringUtils.isEmpty(key)){
            wrapper.and((object)->{
                object.eq("brand_id",key).or().like("name",key);
            });
        }
        IPage<BrandEntity> page = this.page(
                new Query<BrandEntity>().getPage(params),
                wrapper
        );

        return new PageUtils(page);
    }
```

其中我们的最终目的是生成pageutils对象，而其需要通过IPage接口类进行封装，这个项目中的ServiceImpl类含有page函数，该函数通过传入IPage和Wrapper变量生成IPage接口对象，所以我们重点在如何生成Wrapper变量。首先我们需要保存搜索数据中的内容通过String进行保存，然后判断是否为空如果为空就全展示，如果不为空就生成特定的Wrapper变量，最后调用page函数按照上述过程生成分页数据并返回。注意这里和属性分组页面的模糊搜索不同，在那个页面中点击搜索会传入分类id先根据分类id进行初步筛选，然后才是模糊搜索。

在java后端中我们会为每一个微服务中的每个单体设置好对应的实体层、DAO层、服务层和控制层，但是除了每个名词的单体，我们还会处理到不同单体之间的联系，而每个单体和相互之间的联系对应的域值不同，所以仅仅由单体的层进行api的实现就十分的困难和容易出错，于是乎我们就会将这些相互之间的联系也看作为一个单体提炼出来，为其设置数据库中的表、实体层、DAO层、服务层以及控制层。就比如在微服务中的商品服务中，有菜单（categories）也有品牌（brand）为了方便处理我们就生成一个菜单和品牌的关联（CategoryBrandRelation）这样就清晰的进行处理了。

```vue
<el-popover placement="right-end" v-model="popCatelogSelectVisible">
        <category-cascader :catelogPath.sync="catelogPath"></category-cascader>
        <div style="text-align: right; margin: 0">
          <el-button
            size="mini"
            type="text"
            @click="popCatelogSelectVisible = false"
            >取消</el-button
          >
          <el-button type="primary" size="mini" @click="addCatelogSelect"
            >确定</el-button
          >
        </div>
        <el-button slot="reference">新增关联</el-button>
      </el-popover>
      <el-table :data="cateRelationTableData" style="width: 100%">
        <el-table-column prop="id" label="#"></el-table-column>
        <el-table-column prop="brandName" label="品牌名"></el-table-column>
        <el-table-column prop="catelogName" label="分类名"></el-table-column>
        <el-table-column
          fixed="right"
          header-align="center"
          align="center"
          label="操作"
        >
          <template slot-scope="scope">
            <el-button
              type="text"
              size="small"
              @click="deleteCateRelationHandle(scope.row.id, scope.row.brandId)"
              >移除</el-button
            >
          </template>
        </el-table-column>
      </el-table>
      <span slot="footer" class="dialog-footer">
        <el-button @click="cateRelationDialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="cateRelationDialogVisible = false"
          >确 定</el-button
        >
      </span>
    </el-dialog>


// 分类关联
    updateCatelogHandle(id) {
      this.cateRelationDialogVisible = true;
      this.brandId = id;
      this.getCateRelation();
    },
    getCateRelation() {
      this.$http({
        url: this.$http.adornUrl("/product/categorybrandrelation/catelog/list"),
        method: "get",
        params: this.$http.adornParams({
          brandId: this.brandId,
        }),
      }).then(({ data }) => {
        this.cateRelationTableData = data.data;
      });
    },
```

所以我们在brand.vue文件中进行显示关联品牌的视图，其中cateRelationDialogVisible变量用于展示界面，category-cascader组件由子组件CategoryCascader在公共的文件夹中引入，同时获取数据也从专门的关联类型中的控制层进行响应。

然后我们还需要实现保存功能，这里需要声明在一个web项目中的后端分为三个部分分别是控制层、业务层和数据库连接层，其中代表的命名为XXController、XXService以及XXServiceimpl、XXMapper，但是在本项目中数据库连接层通过DAO层进行实现。在Java项目中，DAO（Data Access Object）层是一个设计模式，用于抽象和封装数据访问层，使得应用的业务逻辑层（Service层）与数据访问逻辑分离。DAO层的主要作用是提供与数据库交互的接口和实现，包括CRUD操作（创建、读取、更新、删除），同理按照上述思路再实现删除功能。

```java
 /**
     * 保存
     * 由于默认逆向工程生成的保存功能只能保存品牌id和分类id，而在数据库中的名称并没有保存，
     * 但是数据库中的数据是一定要进行保存的，所以我们需要将默认的功能进行修改
     */
    @RequestMapping("/save")
    public R saveDetail(@RequestBody CategoryBrandRelationEntity categoryBrandRelation){
        //保存id
        Long brandId = categoryBrandRelation.getBrandId();
        Long categoryId = categoryBrandRelation.getCatelogId();
        //找到对应的类
        BrandEntity brandEntity = brandDao.selectById(brandId);
        CategoryEntity categoryEntity = categoryDao.selectById(categoryId);
        //保存相应的name
        categoryBrandRelation.setBrandName(brandEntity.getName());
        categoryBrandRelation.setCatelogName(categoryEntity.getName());
        //在数据库中新建并返回响应
		categoryBrandRelationService.save(categoryBrandRelation);
        return R.ok();
    }
```

重点来了，正是由于不同基础表中的之间关联我们用一张新表进行保存，同时没有在数据库中进行关联，所以当基础表中的数据进行变换的时候我们也需要及时更新冗余表中的数据。我们可以在服务层中调用默认的函数进行使用也可以直接去DAO层新建sql语句进行使用。

```java
@Mapper
public interface CategoryBrandRelationDao extends BaseMapper<CategoryBrandRelationEntity> {

    void updateCategory(@Param("catId")Long catId, @Param("name")String name);

}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.atguigu.gulimall.product.dao.CategoryBrandRelationDao">

	<!-- 可根据自己的需求，是否要使用 -->
    <resultMap type="com.atguigu.gulimall.product.entity.CategoryBrandRelationEntity" id="categoryBrandRelationMap">
        <result property="id" column="id"/>
        <result property="brandId" column="brand_id"/>
        <result property="catelogId" column="catelog_id"/>
        <result property="brandName" column="brand_name"/>
        <result property="catelogName" column="catelog_name"/>
    </resultMap>
    <update id="updateCategory">
        UPDATE `pms_category_brand_relation` SET catelog_name=#{name} WHERE catelog_id=#{catId}
    </update>


</mapper>
```

**平台属性-规格参数新增和VO：**

说完了分类、品牌、分组，下面就要开始说明属性的变量了，在提供的代码里面，我们的业务要求是直接保存该属性对应的分类和分组，但是在逆向工程提供的代码里面只提供了类型和属性的保存，虽然在用户界面中我们可以实现可视化的选择，但实际保存到数据库中的时候并没有显示分组信息。那传统的方式肯定不是去修改数据库的内容，而是在显示的实体类中加入关联的分组变量同时说明其不是数据库中的域，在用户保存之后通过这种方式去展示在界面中；但是这样的操作太过繁琐，于是乎我们选择去新建一个VO类在这个类中进行专门处理这样的数据。

在Java中有这样的划分，**PO**(persistant object)持久对象，PO 就是对应数据库中某个表中的一条记录,多个记录可以用 P0 的集合。 PO 中应该不包含任何对数据库的操作。**DO**(Domain object)领域对象，就是从现实世界中抽象出来的有形或无形的业务实体。**TO**(Transfer Object)，数据传输对象，不同的应用程序之间传输的对象。**DTO**(DataTransfer object)这个概念来源于 J2EE的设计模式，原来的目的是为了 E8 的分布式应用提供粗粒度的数据实体，以减少分布式调用的次数，从而提高分布式调用的性能和降低网络负载，但在这里，泛指用于展示层与服务层之间的数据传输对象。**BO**(business object)业务对象，从业务模型的角度看，见 UML元件领域模型中的领域对象。封装业务逻辑的 java 对象，通过调用 DAO 方法，结合 POVO 进行业务操作。businessobject: 业务对象 主要作用是把业务逻辑封装为一个对象。这个对象可以包括一个或多个其它的对象。 比如一个简历，有教育经历、工作经历、社会关系等等。 我们可以把教育经历对应一个 PO ，工作经历对应一个 PO ，社会关系对应一个 PO 。 建立一个对应简历的 B0 对象处理简历，每个 BO 包含这些PO。这样处理业务逻辑时，我们就可以针对 BO 去处理。**POJO**(plain ordinary java object)简单无规则 java 对象，传统意义的 java 对象。就是说在一些 0bject/RelationMapping 工具中，能够做到维护数据库表记录的 persisentobject 完全是一个符合 Java Bean 规范的纯 Java 对象，没有增加别的属性和方法。我的理解就是最基本的javaBean ，只有属性字段及 setter 和 gette!方法！POJO 是 DO/DTO/BO/VO 的统称。
**DAO**(data access object)是一个 sun 的一个标准 j2ee 设计模式， 这个模式中有个接口就是 DAO ，它负持久层的操作。为业务层提供接口。此对象用于访问数据库。通常和PO 结合使用， DAO 中包含了各种数据库的操作方法。通过它的方法，结合 PO 对数据库进行相关的操作。夹在业务逻辑与数据库资源中间。配合 VO,提供数据库的 CRUD 操作。

**VO**(value object)值对象或者为视图对象（view object），通常用于业务层之间的数据传递，和 PO 一样也是仅仅包含数据而已。但应是抽象出的业务对象，可以和表对应，也可以不，这根据业务的需要 。用 new 关键字创建，由GC 回收的。总的来说即接受页面传递来的数据，封装对象。将业务处理完成的对象，封装成页面要用的数据。

```java
    @Override
    public void saveAttr(AttrVo attr) {
        AttrEntity attrEntity = new AttrEntity();
        //attrEntity.setAttrName(attr.getAttrName());
        BeanUtils.copyProperties(attr,attrEntity);
        //1、保存基本数据，通过默认的保存函数保存到attr的表中
        //这里注意每次生成的新的数据进行保存的时候都是在默认的save函数中实现了id主键赋值
        this.save(attrEntity);
        //2、保存关联关系，通过relationDao保存在两者的关联表中
        AttrAttrgroupRelationEntity relationEntity = new AttrAttrgroupRelationEntity();
        relationEntity.setAttrGroupId(attr.getAttrGroupId());
        relationEntity.setAttrId(attrEntity.getAttrId());
        relationDao.insert(relationEntity);
    }
```

实现保存功能之后，我们还需要面临逆向工程最重要的展示列表功能没有实现，在控制台中可以发现前端访问的响应的网址，按照网址可以找到对应的函数，但是默认的函数没有提供AttrId的信息，我们可以手动生成一个，在id为0的时候展示全部在不为0的时候展示具体信息。同时我们可以注意到，在Attr数据库表中没有对应的类名和组名之间的信息，但是在前端处理的时候却需要用到，所以就又用到我们的VO对象，在VO文件夹中创建新的类用来存储这个功能中的数据。

```java
@Override
    public PageUtils querybaseAttrPage(Map<String, Object> params, Long catelogId) {
        QueryWrapper<AttrEntity> queryWrapper = new QueryWrapper<AttrEntity>();
        if (catelogId != 0) {
            queryWrapper.eq("catelogId", catelogId);
        }
        String key = (String) params.get("key");
        if (!StringUtils.isEmpty(key)) {
            //
            queryWrapper.and((wrapper) -> {
                wrapper.eq("attr_id", key).or().like("attr_name", key);
            });
        }
        IPage<AttrEntity> page = this.page(
                new Query<AttrEntity>().getPage(params),
                queryWrapper
        );

        PageUtils pageUtils = new PageUtils(page);
        List<AttrEntity> records = page.getRecords();
        List<AttrRespVo> respVos = records.stream().map((attrEntity) -> {
            AttrRespVo attrRespVo = new AttrRespVo();
            BeanUtils.copyProperties(attrEntity, attrRespVo);

            AttrAttrgroupRelationEntity attrId = relationDao.selectOne(new QueryWrapper<AttrAttrgroupRelationEntity>().eq("attr_id", attrEntity.getAttrId()));
            if (attrId != null) {
                AttrGroupEntity attrGroupEntity = attrGroupDao.selectById(attrId.getAttrGroupId());
                attrRespVo.setGroupName(attrGroupEntity.getAttrGroupName());
            }

            CategoryEntity categoryEntity = categoryDao.selectById(attrEntity.getCatelogId());
            if (categoryEntity != null) {
                attrRespVo.setCatelogName(categoryEntity.getName());
            }
            return attrRespVo;
        }).collect(Collectors.toList());

        pageUtils.setList(respVos);
        return pageUtils;
    }
```

**平台属性-查询未关联的数组：**

在这个部分我们需要实现在分组界面查询关联窗口下，实现新增关联时可以正确实现展示还未关联的属性，首先我们需要在该分组下进行实现，所以查询数据库中的分组表，然后查出该分组所属分类并找到其包含的其他分类的所以已经关联的属性，最后将该分类下还未关联的属性进行返回即可。

```java
@Override
    public PageUtils getNoRelationAttr(Map<String, Object> params, Long attrgroupId) {
        //1、同分类中的所有属性
        // AttrGroup是专门用来存储分组信息的数据库中的表，存放着分组和分类的信息
        AttrGroupEntity attrGroupEntity = attrGroupDao.selectById(attrgroupId);
        Long catelogId = attrGroupEntity.getCatelogId();
        //2、还没有关联过的属性
        //          a、当前分类下的其他分组
        // 在分组存放信息的表中查找所有属于同一个分类的组
        List<AttrGroupEntity> group = attrGroupDao.selectList(new QueryWrapper<AttrGroupEntity>().eq("catelog_id",catelogId));
        List<Long> collect = group.stream().map((item) -> {
            return item.getAttrGroupId();
        }).collect(Collectors.toList());
        //          b、获取这些分组关联的属性
        // 虽然attr是专门存放属性信息的表，但是这里我们没有设计分组信息而是存放在attr_group_relation的表中，所以在这个表中查找到所有的属性信息
        List<AttrAttrgroupRelationEntity> groupId =  relationDao.selectList(new QueryWrapper<AttrAttrgroupRelationEntity>().in("attr_group_id",collect));
        List<Long> attrIds = groupId.stream().map((item) -> {
            return item.getAttrId();
        }).collect(Collectors.toList());

        //          c、从当前分类的所有属性中移除上面的属性信息
        // 设置基本的过滤信息，同时当该分类下没有关联属性时如何处理
        QueryWrapper<AttrEntity> wrapper = new QueryWrapper<AttrEntity>().eq("catelog_id", catelogId).eq("attr_type", ProductConstant.AttrEnum.ATTR_TYPE_BASE.getCode());
        if(attrIds!=null && attrIds.size()>0){
            wrapper.notIn("attr_id", attrIds);
        }
        //  实现模糊搜索
        String key = (String) params.get("key");
        if(!StringUtils.isEmpty(key)){
            wrapper.and((w)->{
                w.eq("attr_id",key).or().like("attr_name",key);
            });
        }
        IPage<AttrEntity> page = attrService.page(new Query<AttrEntity>().getPage(params),wrapper);
        PageUtils pageUtils = new PageUtils(page);
        return pageUtils;
    }
```

**平台属性-批量新增分组与属性的关联**

实际上逆向工程实现了一个批量新建的功能但是他保存的是attr_group_relation的数据，而前端返回的数据只包含了分组id和属性id，所以需要我们进行处理，而刚刚好之前实现其他功能的时候保存过这两个变量的VO类，所以将前端数据传给VO实体，再将VO实体复制到上面的类中进行实现该功能。

```java
    @Override
    public void saveBatch(List<AttrGroupRelationVo> vos) {
        List<AttrAttrgroupRelationEntity> collect = vos.stream().map(item->{
            AttrAttrgroupRelationEntity relationEntity = new AttrAttrgroupRelationEntity();
            BeanUtils.copyProperties(item,relationEntity);
            return relationEntity;
        }).collect(Collectors.toList());
        this.saveBatch(collect);
    }

```

**新增商品-获取分类关联的品牌：**

首先，在后台管理系统中我们可以进行商品维护，这个时候我们就可以新增一些商品，在我们填写基本属性的时候会填写相关的分类，这个时候应该会显示和分类进行关联的品牌，也就是需要自动调用。实现的原理是通过`pubsub-js`库实现监听三级分类消息的变化，当分类进行变化的时候，自动调用品牌关联模块的函数，从而实现显示品牌的功能。**这里注意：**当前端返回请求url的时候就返回了参数我们使用@PathVariable的注解来保存数据，当前端返回的是json数据的时候我们使用@RequestParam的注解来保存数据，当我们想将前端的数据封装为一个对象的时候我们使用@RequestBody的注解来保存数据。

```java
    /**
     * 显示特定分类下的所有品牌列表
     * 1、Controller:处理请求，接受和校验数据
     * 2、Service接受controller传来的数据，进行业务处理
     * 3、Controller接受Service处理完的数据，封装页面指定的vo
     */
    @GetMapping("/brands/list")
    public R listbrands(@RequestParam(value = "cateid",required = true)Long cateid){
        List<BrandEntity> vos = categoryBrandRelationService.getBrandsByCatId(cateid);

        List<BrandVo> collect = vos.stream().map(item->{
            BrandVo brandVo = new BrandVo();
            brandVo.setBrandId(item.getBrandId());
            brandVo.setBrandName(item.getName());
            return brandVo;
        }).collect(Collectors.toList());

        return R.ok().put("data",collect);
    }
```

```java
    @Override
    public List<BrandEntity> getBrandsByCatId(Long cateid) {
        List<CategoryBrandRelationEntity> catelogId = relationDao.selectList(new QueryWrapper<CategoryBrandRelationEntity>().eq("catelog_id",cateid));
        List<BrandEntity> collect = catelogId.stream().map(item->{
            Long brandId = item.getBrandId();
            BrandEntity byId = brandService.getById(brandId);
            return byId;
        }).collect(Collectors.toList());
        return collect;
    }

```

**新增商品-查询当前分类下的所有分组的所有属性：**

首先在这个业务中，我们根据前端传来的数据可以知道有哪些数据需要封装，然后再在数据库中寻找是否有变量匹配的类，如果没有的话建议生成VO类来专门存储这类数据。在本业务中其需要响应的数据和AttrGroupEntity相似但是多了一个属性的集合，所以需要新建VO，然后按照要求先查询分类下的所有分组，再查询分组的所有属性最后返回一个VO变量即可。

```java
    /**
     * 实现在提交商品功能中写入基本信息后可以展示该分类下的所有属性
     * */
    @GetMapping("{catelogId}/withattr")
    public R getAttrGroupWithAttrs(@PathVariable("catelogId") Long catelogId){
        //1、查出当前分类下的所有属性分组
        //2、查出每个分组下的所有属性
        List<AttrGroupWithAttrsVo> attrGroupWithAttrsVos = attrGroupService.getGroupWithAttrs(catelogId);
        return R.ok().put("data",attrGroupWithAttrsVos);
    }
```

```java
    @Override
    public List<AttrGroupWithAttrsVo> getGroupWithAttrs(Long catelogId) {
        //1、查出当前分类下的所有属性分组
        List<AttrGroupEntity> attrGroupEntities = this.list(new QueryWrapper<AttrGroupEntity>().eq("catelog_id",catelogId));
        //2、查出每个分组下的所有属性
        List<AttrGroupWithAttrsVo> attrGroupWithAttrsVos = attrGroupEntities.stream().map(group->{
            AttrGroupWithAttrsVo attrsVo = new AttrGroupWithAttrsVo();
            BeanUtils.copyProperties(group,attrsVo);
            List<AttrEntity> attr = attrService.getRelationAttr(attrsVo.getAttrGroupId());
            attrsVo.setAttrs(attr);
            return attrsVo;
        }).collect(Collectors.toList());
        return attrGroupWithAttrsVos;
    }
```

**新增商品：**

在完成商品发布的前几个部分，也就是基本信息、规格参数、销售属性以及SKU信息之后就可以进行新增商品信息了。由于新增功能设计大量数据库中的表，同时前端页面响应的数据也是对数据库进行了修改的数据，所以我们需要在后端中增加对应着jason文件的VO类，然后在后端中传入数据给这些对象，再根据这些对象进行保存到相应的数据库中。依次需要保存的数据分别为

1）、保存spu基本信息 pms_spu_info

2）、保存spu的描述图片 pms_spu_info_desc

3）、保存spu的图片集 pms_spu_images

4）、保存spu的规格参数 pms_product_attr_value

5）、保存spu的积分信息：gulimall_sms->sms_spu_bounds

当进行远程调用的时候我们需要设置feign文件夹，同时在启动类中添加@EnableFeignClients的注解，这个注解可以找到对应的远程调用类，其中可以配置basepackages的信息，这样springboot就可以按照路径进行寻找，当然如果我们没有配置也无妨，springboot会在启动类的父类文件夹下的所有文件中进行自动寻找，但是如果启动类和远程调用的文件不在同一个文件下的话，就不可以自动寻找到了。

6）、保存当前spu对应的所有sku信息

​            6.1、sku的基本信息：pms_sku_info

​            6.2、sku的图片信息：pms_sku_images

​            6.3、sku的销售属性信息：pms_sku_sale_attr_value

​            6.4、sku的优惠、满减等信息：gulimall_sms->sms_ladder\sms_sku_full_reduction\sms_member_price

由于这个部分的后端代码是一个事务，所以在编写完成之后需要对其进行调试运行，也就是将该微服务模块进行调试运行之后在每个保存处设置断点，依次进行运行，查看所有的错误和不对的地方，如果报错，由于是事务数据库的数据会进行回滚，这样就可以在运行成功之前尽可能的不对数据库的数据进行操作。

同时，这里会发送org.springframework.cloud.netflix.ribbon.RibbonLoadBalancerClient.choose的错误，原因是spring.cloud中在最新的版本中也提供了riddon的包，这与nacos中提供的riddon发生了冲突，但是该项目需要由nacos中的riddon实现负载均衡的效果，所以就需要将spring.cloud的版本降低，这样报错就会消除了。

**商品管理-SPU检索：**

```java
    @Override
    public PageUtils queryPageBycondition(Map<String, Object> params) {
        //设置好查询对象
        QueryWrapper<SpuInfoEntity> wrapper = new QueryWrapper<>();
        /**
         * 模糊搜索会传入多个查询条件，检查这些条件是否为空
         * 以及在这里的and()的使用是类似与另类的函数的表达形式
         * 还有注意在get("catalogId")和在eq("catelog_id")里面字符型的输入区别，一个是对应着前端传入的json文件中的元素变量
         * 一个是对应着数据库中的列的元素变量
         */
        String key = (String)params.get("key");
        if(!StringUtils.isEmpty(key)){
            wrapper.and((w)->{
                w.eq("id",key).or().like("spu_name",key);
            });
        }
        String status = (String)params.get("status");
        if(!StringUtils.isEmpty(status)){
            wrapper.eq("publish_status",status);
        }
        String brandId = (String)params.get("brandId");
        if(!StringUtils.isEmpty(brandId)){
            wrapper.eq("brand_id",brandId);
        }
        String catalogId = (String)params.get("catalogId");
        if(!StringUtils.isEmpty(catalogId)){
            wrapper.eq("catalog_id",catalogId);
        }
        IPage<SpuInfoEntity> page = this.page(
                new Query<SpuInfoEntity>().getPage(params),
                wrapper
        );
         return new PageUtils(page);
    }
```

**商品管理-SKU检索：**

```java
    @Override
    public PageUtils queryPageBycondition(Map<String, Object> params) {
        QueryWrapper<SkuInfoEntity> wrapper = new QueryWrapper<>();

        String key = (String) params.get("key");
        if(!StringUtils.isEmpty(key)){
            wrapper.and((w)->{
                w.eq("sku_id",key).or().like("sku_name",key);
            });
        }
        String catalogId = (String)params.get("catalogId");
        if(!StringUtils.isEmpty(catalogId)){
            wrapper.eq("catalog_id",catalogId);
        }
        String brandId = (String)params.get("brandId");
        if(!StringUtils.isEmpty(brandId)){
            wrapper.eq("brand_id",brandId);
        }
        //同样的最小值也这样处理，但是我们处理的前端代码使得默认值为null而不是0从而为其他部分省略了这部分内容
        String min = (String)params.get("min");
        if(!StringUtils.isEmpty(min) && !"0".equalsIgnoreCase(min)){
            wrapper.ge("price",min);
        }
        //这里多出来的处理主要是当发生最小值和最大值为0的时候会查询价格为0的sku，但是系统默认的查询为0也就是最初应该是全部查询
        String max = (String)params.get("max");
        if(!StringUtils.isEmpty(max)){
            try{
                BigDecimal bigDecimal = new BigDecimal(max);
                if(bigDecimal.compareTo(new BigDecimal("0"))==1){
                    wrapper.le("price",max);
                }
            }catch (Exception e){}
        }
        IPage<SkuInfoEntity> page = this.page(
                new Query<SkuInfoEntity>().getPage(params),
                wrapper
        );

        return new PageUtils(page);
    }
```

**商品管理-SPU规格维护：**

在前端页面中的spu管理中，点击规格会弹出页面进行修改销售属性，所以前端会发送geting请求和posting请求，即先进行查询当前的spu的规格信息并返回以及将前端数据发送到后端保存到spu的数据库中。这两部分的核心思想就是前者为调用selectlist函数查找并返回对应spu_id的对象，后者为将数据保存在对象中最后调用save函数修改数据库中的数据。注意当修改sku的销售属性的时候，由于可能存在修改后为空的值，所以需要进行先删除再进行保存这样就可以将取消的销售属性设置为空。

### 仓储服务

**仓库管理-整合ware服务&获取仓库列表**

注意在idea中的ssm框架下，包括了数据库操作层、服务层以及控制层，这些最好都需要进行加上对应的注解。一般会给数据库操作层配置上@Map的注解，这样就可以正确的引入dao层的对象，如果忘记或者加入麻烦，可以在启动类前加上@MapperScan的注解并写上对应的文件夹，这样就省去了数据库操作层的添加注解的操作，同理如果没有就需要在每一个类前加上注解。

如果我们希望在测试代码的时候可以看到有哪些mysql语句对数据库进行操作，那么我们需要修改项目的log日志文件的等级。在配置文件中加入logging：level：com.atguigu（项目中对应的包）：debug，这样当我们运行项目的时候，在控制台中就可以看到运行了哪些mysql语句。

**仓库管理-查询库存&创建采购需求**

这一部分的核心思想就是通过前端传递过来的数据，在库存数据库中将对应的类进行选择查询，使用对应的服务类提供的selectlist并设置好相关条件，最后返回并进行分页处理，在前端显示；同理创建采购需求，是将前端输入的采购需求信息传递给后端，并在后端中生成对应类的对象，并将这些信息进行set，最后使用服务类包含的DAO类提供的save方法进行创建保存。

**仓库管理-合并采购需求**

注意这里的合并采购需求并不是直接将所选的采购需求进行合并成一个新的采购需求，而是根据所选择的采购需求进行合并为采购单，这个时候会发现，前端传递过来的是采购需求id的数组。那么就需要进行第一步的判断，首先查看是否在采购单中存在采购单的id，如果有那么就是直接在这个上面进行加法并修改采购需求的状态status，否则就新建一个采购单并把采购需求添加进去，同样需要进行修改状态staus。

**仓库管理-领取采购单**

这一部分并不是由前端页面发送请求，而是由第三方的软件进行发送请求。这个时候就需要通过postman进行模拟请求，那么领取采购单就是通过发送请求的请求体中的数据，修改这些采购单的状态，需要注意的就是当领取采购单的时候，我们不仅仅需要修改采购单的状态同时也需要去修改采购需求的状态为正在采购BUYING。

**仓库管理-完成采购**

同样的这一部分也不是由前端页面发送请求，而是由第三方的软件进行发送请求。那么postman会发送json数据即请求体给后端，在后端中通过发送的数据进行修改，注意这里我们同样不仅需要修改采购单的状态，同样的需要将采购单下的采购需求进行删除，这里一般会直接使用到对应服务类中的DAO类提供的方法。

### 分布式基础篇总结

**分布式基础概念**

微服务、注册中心、配置中心、远程调用、Fegin、网关

**基础开发**

SpringBoot2.0、SpringCloud、Mybatis-Plus、Vue组件化、阿里云对象存储

**环境**

Vagrant、Linux、Docker、MySQL、Redis、逆向工程&人人开源

**开发规范**

数据校验JSR303、全局异常处理、全局统一返回、全局跨域处理

枚举状态、业务状态码、VO与TO与PO划分、逻辑删除

Lombok：@Data、@SIf4j

**如何在同局域网中进行访问全栈谷粒商城**

首先知道一般的项目怎么上线，是需要一个公网的IP服务器进行启动，这样才能被用户进行访问。但是在局域网中可以由另一个用户电脑端进行访问，因为同一个局域网中设备在相同IP下，可以直接访问，只有公网IP才可以不在同一个局域网中访问。

先介绍如何进行访问后端项目，首先需要设备均连接相同的局域网，然后作为服务器的终端电脑需要将防火墙进行关闭。后端项目进行开发主要是依靠tomcat作为web服务器进行，而当前大多数项目都是由springboot进行开发，在这里其集成了tomact服务器，springboot项目需要在application.yml中进行配置其中就包含了项目的端口，一般tomat默认是8080为端口，这里可以由开发人员进行配置，然后搜索服务器的IP地址，这样在**用户端口电脑就可以通过IP：端口号/项目名称进行访问后端项目**了。

然而一般的成型的项目都是前后端同时展现，也就是用户从前端进行访问，然后由前端进行访问后端，后端进行访问数据库，最后在前端进行展示，那么前端用户怎么进行访问呢，首先前端项目也是需要进行构建web服务器的，这个一般由vue架构进行提供。在vue手脚架项目中，package.json中解释项目如何进行启动，在src中解释项目中的具体设计和请求访问，在config中解释项目中的基本配置，在static中解释项目中的全局变量（固定变量），而用户想要访问vue项目不是简单的进行访问ip加接口就行，前端和后端不同，前端需要将config/index.js中的**localhost进行修改成服务器ip**这样才可以进行访问，同时需要将static/config/index.js中的**baseUrl进行修改成电脑IP**，这样前端才可以正常进行调用后端api，最后启动前端项目并在用户电脑上访问就可以了。

**如何使用nacos**

首先需要下载nacos的项目包，可以直接去官网下载也可以在GitHub上面下载，完成之后，需要在本地运行运行成功过后，如果微服务需要进行配置那么则需要在springboot的配置文件中加入nacos的服务地址，同时在bootstrap.properties文件中写入相关的文件信息。**注意：**其实大部分的中间件的使用都是通过配置文件的地址加上端口号来进行配置访问，而中间件则需要在业务服务器启动之前在非核心业务服务器上进行运行，这样业务服务器就可以进行使用了。

**为什么可以在本地计算机上访问docker或者虚拟机的应用进程**

这是因为电脑在访问web网站的时候需要先进行**域名解析**然后进行**IP寻找**，一般使用docker或者虚拟机都不需要进行域名解析，那么核心就在怎么进行寻找IP，由于计算机中每一个网卡对应着一个IP地址，也就是计算机可以连接到每个网卡上的计算机，所以实现docker或者虚拟机就是在网卡驱动中添加上了一个IP地址从而可以由本地计算机去进行访问。同理为什么有的大型网页可以进行访问，这是因为大型网页使用的公网IP，只要电脑可以接入InterNet那么就可以访问查找到公网IP，不过往往需要进行域名解析。同理实际上如果不是公网IP或者没有使用虚拟机也可进行访问其他电脑上的web服务，只需要其均在一个局域网下即可，不过我感觉其实在用户计算机上可以添加服务器的网卡驱动一样可以进行访问，可能没办法路由额没有尝试过。

## 谷粒商城（分布式高级—微服务架构篇）

### 全文检索ES和ES可视化软件Kibana

Elasticsearch（ES）是一款开源的分布式搜索和分析引擎，基于倒排索引技术实现高效全文检索，支持海量数据的实时存储与复杂查询；Kibana则是与之配套的数据可视化平台，提供图表、仪表盘和交互式界面，帮助用户直观分析ES中的数据。

**框架**：在ES中和mysql一样不同库等价于索引（Index），不同表等价于类型（Type），不同数据等价于文档（document），不同列等价于属性。同时通过倒排索引机制实现检索功能，将检索到的关键字与存在该关键字的Type用一个额外的索引保存起来，从而实现检索的功能。在Kibana中会在安装的时候进行指定相关 的服务器，然后在内置的软件中可以进行数据可视化以及调试的功能。同时为了能和Java进行结合，需要在后端准备好全文检索的功能，通过使用ES官方提供的api从而实现新的微服务gulimall-search服务。

### 商城业务-首页

**商品上架** 众所周知上架商品的第一步就是需要将商品的信息进行上传，那么就需要进行考虑到商城页面中的全文检索，由于ES实现全文检索，同时还是利用内存的方式进行设计，虽然后期可以通过集群或者分布式的方式进行提高性能，但是在设计的时候是需要进行考虑到高并发的问题。一般有以下两种上传商品数据信息的方式。

```java
(1)、方便检索{
    skuId:1
    spuId:11
    skuTitle:华为xx
    price:998
	saleCount:99
	attrs:[
        {尺寸:5寸}
        {CPU:高通945}
        {分辨率:全高清}
    ]
}
冗余:100万*20=1000000*2KB=2000MB=2G
(2)、节约空间
	sku索引{
    skuId:1
	spuId:11
	XXXX
}
	  
	attr索引{
        spuId:11,
        attrs:[
            {尺寸:5寸}，
            {CPU:高通945}
            {分辨率:全高清}
        ]
    }
搜索 小米; 粮食，手机，电器
	10000个，4000个spu
    分步，4000个spu对应的所有可能属性;
	esClient:spuId:[4000个spuid]
	4000*8=32000byte=32kb

32kb*10000=32000mb;=32GB
```

根据以上的分析，若选择第二种会使得一次多个用户的简单查询导致大量的数据需要在网络中传送，时间会非常长。所以我们使用第二种方式从而利用空间换取时间来获得相关的优化效果。

**Fegin进行远程调用的问题** 当使用远程调用的时候经常出现调用接口实现的数据并不是我们想要的数据类型，这个时候我们往往需要进行在自己的业务代码里面进行类型转换，这种情况使得代码非常的冗余，所有有以下三种方法。第一种是通过使用相同的类进行传递数据，在这个类中进行设置泛型，然后当我们在自己的业务代码中进行调用远程服务并返回数据的时候，通过泛型就可以直接进行强制类型转换，第二种就是在远程调用的api中自己将结果进行转换，然后进行返回，第三种就是在通用传输数据类型中自己定义一个数据转换函数，然后通过这个函数进行处理数据类型，这几种方式都可解决业务代码中的冗余问题。

**商城首页** 该部分使用的是前后端不分离，在后端管理架构中我们使用的是前后端分离的框架，而在这里我们使用前后端不分离也就是说，在这里我们的商城网站是通过后端项目直接启动，一般是使用gulimall-product微服务，在这个项目中使用index保存相关网页信息，再通过web项目进行启动访问到商城首页，在商城首页我们需要进行实现三级分类功能，这个就可以通过调用相关类在启动类中进行准备数据，然后再在前端文件中进行动态展示。

**注意：**辨别项目是不是前后端分离，主要是看后端的项目中是否参与前端渲染，如果后端仅仅处理数据不进行渲染那就是前后端分离项目，而后端不仅处理数据，而且在服务层或者控制层中进行前端渲染，那就是前后端不分离，与是不是用一个服务器端口无关，例如在本项目中使用Thymeleaf进行后端渲染前端页面从而进行显示商城网站就是一个前后端不分离的项目。

### Nginx实现反向代理和负载均衡

在前面的时候我们实现ES存储数据时，为了能全文检索需要进行配置相关倒排索引，但是有的时候并不合适所以我们可以进行查看用户上传的字典，而这个字典在哪里进行保存和访问呢，一般项目会使用Nginx进行反向代理从而将内网的服务地址接口与客户端进行隔离，而访问ES就可以在Nginx中进行访问字典，我们就可以将这样的字典存放在Nginx中。

**反向代理** 首先什么是代理，代理也就是用其他服务器进行互联网的通信而不是真实的主机，而代理又分为正向代理和反向代理，在正向代理中用户可以通过正向代理服务器进行访问互联网，比如像VPN等软件实现的就是正向代理，用户终端无法访问网络那就由可以访问网络的代理进行访问然后将访问结果返回给用户。而反向代理就和正向代理是相反的，前者是保护用户，隐藏用户的IP信息，那么后者就是保护服务器端，用来保护服务器IP信息。当项目上线我们就需要进行公网IP进行访问，但是我们只想用户访问官网地址，而不能访问其他url，就可以通过Nginx实现反向代理，所有的请求信息由公网IP进行发送到Nginx但是由Nginx在内网中进行操作，并将信息数据返回给Nginx最后给用户，用户无法进行访问内网数据。

**负载均衡** 我们进行反向代理的时候其实并不是指定哪些服务器和端口，往往是进行动态调整的所以我们可以将访问负载均衡地发送到网关服务器，然后由网关实现对服务器进行操作，这样就实现了动态调整从而增加了系统的灵活性。

![图片描述](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746487380863.jpg)

### 性能测压

本质上就是通过JVM调优工具进行调整jvm从而将项目的性能进行提升，使用Apache下的JMeter进行模拟数据压力进行测试，通过选择不同的项目块进行测压并在JVM调优插件Java visualVM中进行观察调节，将项目的性能调整到最合适的情况。

**JVM调优** 通过调整jvm中的共享内存数据大小等方式从而提高项目中的响应能力。

**Nginx动静分离** 在这个商城项目中由于使用的是前后端不分离，而且静态数据是放在后端保存的，每次访问都需要进行分配静态空间项目十分冗余，所以我们将静态数据放在Nginx中保存，在前端页面进行渲染的时候通过访问nginx就可以达到效果，而不用再次去访问后端服务器了。

**SQL优化** 在本项目的商城项目中调用三层分类的时候会出现性能极差的时候，原因主要是由于调用接口的时候频繁进行与数据库进行交互从而导致缓慢，这里的sql优化主要是根据业务进行优化，将多次查询改为一次查询然后再在Java中进行整合数据从而进行提高性能。

### 缓存中间件-Redis

**Redis是什么**  Redis（Remote Dictionary Server）是一个基于内存、支持持久化的高性能键值对数据库，通常被用作缓存、消息队列、分布式锁等。它的数据以键值对形式存储，支持丰富的数据结构，如字符串（String）、哈希（Hash）、列表（List）、集合（Set）、有序集合（Sorted Set）等，Redis 具有高性能、持久化、高并发、支持集群以及支持丰富的数据结构的特点。

- 高性能：基于内存操作，读写速度极快，QPS（每秒查询率）可达数万甚至更高。
- 丰富的数据结构：除基本类型外，还支持复杂数据模型，满足不同场景需求。
- 持久化：提供RDB（快照）和AOF（日志追加）两种持久化方式，保障数据可靠性。
- 高并发：单线程模型结合非阻塞I/O，有效避免多线程切换开销，支持高并发访问。
- 集群模式：通过主从复制、哨兵模式、Cluster集群实现高可用和水平扩展。
- ![图片描述](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746486842728.jpg)

**如何实现中间件缓存的效果** 通过在代码中进行预先访问redis中是否存在，存在直接读取，反之才去访问数据库从而达到缓存的效果

**如何实现高性能** redis通过内存的方式实现，尽可能地使得在单位时间内可以响应大量的数据请求

**如何实现高并发** redis通过单线程模式以及NIO的通信方式，并且结合I/O多路复用的技术一起来实现高并发的效果

**如何实现分布式锁** redis通过setnx提供的事务函数来保存一个键值对来实现锁，当多个分布式的服务器进行访问的时候通过分布式锁从而实现读取数据的一致性和原子性，其中redis提供了获取锁和删除锁的原子性操作从而保证不出现死锁的情况

**什么是Redission**  Redission是在Redis中实现所有分布式锁的一种工具，更具体点就是redission是一个java的客户端，为java的原生锁添加了分布式的效果从而方便开发人员的使用。最简单的就是通过getlock()进行获取自定义名称的锁，再通过lock()函数进行占锁，用unlock()来进行释放锁，并且在这期间通过**Lua 脚本**保证了操作的原子性。

**什么是可重入锁** 这是一种在代码中如果代码块A包含代码块B，并且都进行加锁的操作，根据设计思路，如果A占到锁那么B应该可以顺延着使用A的锁而不用去占锁从而发生死锁现象的锁就叫可重入锁，在redission中他通过检查**客户端唯一标识**在后边进行占锁的时候进行查看当前进程是否持有锁以及**重入次数**来进行确保什么时候进行释放锁，每当有一个子代码块进行占锁就++，反之就减一从而保证了代码的正确运行，这样就在redission中实现了。

**什么是看门狗机制** 当我们使用默认的lock()时，如果占锁成功之后业务代码没有执行结束之前看门狗机制都会为我们进行续期从而避免了当业务量时间大于过期时间时发生的错误，同理业务结束后就不再为其进行续期直到进行释放锁，而用户手动输入过期时间时则不会使用看门狗的机制。

**在redis中怎么解决死锁问题** 通过设置锁的等待时间和自动续期来进行实现，在redis中所有的并发操作都放在锁代码块内部，同时设置过期时间和等待时间确保占锁情况，以及自动续期机制实现业务的正常的运行从而解决死锁问题。

**缓存中的数据一致性问题** 由于redis毕竟保存的是缓存也即是并不是实时数据库中的数据，那么就可能会出现数据不一致的问题，那么需要怎么进行处理数据一致性问题呢，一般通过写入方式以及应对策略来进行解决，有以下几种方式

- 双写模式  **核心原理**：读操作由缓存系统自动加载未命中的数据；写操作同步更新缓存和数据库，保证强一致。
- 旁路缓存模式  **核心原理**：读请求优先查缓存，未命中则读数据库并回填；写请求先更新数据库，再删除缓存。**优缺点**：优点是实现简单、灵活控制缓存，适用于读多写少场景；缺点是数据库更新后到缓存删除前可能存在短暂不一致，高并发下可能因操作顺序导致脏数据。**优化与场景**：可通过消息队列异步重试删除缓存，或结合版本号校验数据新旧。典型应用如商品详情页，通过缓存减轻数据库压力。
- 读写穿透模式 **核心原理**：读穿透由缓存系统自动加载未命中的数据；写穿透同步更新缓存和数据库，保证强一致。**优缺点**：优点是数据实时一致，自动化管理降低代码侵入性；缺点是每次写操作需同步更新两端，性能较低，且需依赖分布式事务保障原子性。**优化与场景**：适用于强一致性要求高的场景（如账户余额），可通过降级为异步回写（Write-Behind）或本地消息表优化性能。
- 异步缓存写入模式  **核心原理**：写操作先更新缓存，异步批量持久化到数据库。**优缺点**：优点是写入性能高，适合高并发场景；缺点是缓存未持久化时宕机可能导致数据丢失，仅支持最终一致性。**优化与场景**：结合WAL日志（如Redis AOF）确保数据安全，限制异步队列长度避免积压。适用于秒杀库存等高吞吐写入场景。
- 延迟双删策略  **核心原理**：更新数据库前后各删除一次缓存，第二次延迟执行以减少并发不一致窗口。**优缺点**：优点是降低脏数据概率；缺点是延迟时间难以精准设定，且无法完全消除不一致。**优化与场景**：通过监听数据库Binlog（如Canal）触发二次删除，或结合消息队列实现延迟。适用于用户信息更新后高频读取的场景。
- 删除缓存重试机制  **核心原理**：缓存删除失败时按策略（如指数退避）重试，确保最终一致性。**优缺点**：提高删除可靠性，但重试可能阻塞其他操作，增加系统复杂度。**优化与场景**：结合消息队列异步处理重试，设置最大重试次数和超时机制。适用于网络不稳定或缓存服务短暂不可用的情况。
- 监听并读取biglog异步删除缓存  **核心原理**：订阅数据库Binlog变更事件（如Canal），异步触发缓存删除或更新。**优缺点**：优点是解耦业务与缓存逻辑，可靠性高；缺点是实现复杂，需维护监听组件，且存在异步延迟。**优化与场景**：通过消息持久化和消费端幂等处理保障数据最终一致，结合CDC工具（如Debezium）简化实现。适用于订单状态同步等需解耦的场景。
- ![image-20250508133900302](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/image-20250508133900302.png)

**SpringCache的使用**  Spring Cache是一个对缓存使用的抽象，它提供了多种存储集成。 要使用它们，需要简单地声明一个适当的 CacheManager - 一个控制和管理 Cache 的实体。如何进行使用呢，再IDEA中进行导入相关的依赖，然后进行配置文件设置由于cache是为每一个类型的缓存都进行便利性准备，所以只需要在resource中设置配置文件并标明使用哪种缓存，然后在启动类前加上@EnableCaching，基本步骤就准备好了，当我们需要进行使用缓存的时候只需要在需要缓存的方法前加上注解@Cacheable（“A”，“B”），这就说明将该函数的返回值放入叫做A和B的redis缓存中进行保存，当再次访问这个函数的时候就不会进行调用该代码块而是去redis中进行寻找（默认情况下会由系统生成对应的键值对并按照这个默认的键进行查找redis）。

**优缺点** SpringCache的优点就是方便我们进行开发并且使用缓存，包括进行不同的读写操作双写模式、旁路缓存模式、读写穿透模式等等，但是缺点一样很明显，SpringCache是一个在单机环境中使用缓存的工具，其默认操作缓存不使用锁，而且就算开启锁也只能开启本地锁进行操作，没有办法进行分布式锁的操作。（其实SpringCache的优先选择ConcurrentMap作为缓存，而这种数据结构本质上就是在单机环境中进行并发操作）。

### 商城业务-核心

**检索服务** 通过构造页面信息VO类，然后在检索url里面提取json文件通过ES全文检索并生成VO类的实体，再通过一定方法将信息在检索页面中进行展示。

**异步操作** 通过线程池TreadPoolExecutor()函数进行生成和管理线程从而避免大量额外时间的开销，通过CompletableFuture进行异步编排。什么是JUC其就是Java并发编程的概念，以上的概念大多数来自于JUC，除了线程的创建管理还有一系列锁的认识和使用。

**商品详细页面** 这个页面主要是通过检索服务页面中的商品链接的url进行跳转，当用户点击url将会携带该sku信息，并且商品详细页面还需要提供sku的组合切换，那么这个地方就需要进行大量的并发操作，这种并发操作可以通过异步编程的方式进行提高效率，通过线程池进行分配线程实现异步操作，同时按照业务逻辑将部分业务进程按照回调函数的顺序进行，这样就实现了既高效又便利地控制多线程实现并发操作从而完成异步操作实现性能提高。

```java
@Override
    public SkuItemVo item(Long skuId) throws ExecutionException, InterruptedException {

        SkuItemVo vo = new SkuItemVo();
        CompletableFuture<SkuInfoEntity> infoFuture = CompletableFuture.supplyAsync(() -> {
            //1.sku基本信息获取
            SkuInfoEntity skuInfoEntity = getById(skuId);
//            Long catalogId = skuInfoEntity.getCatalogId();
            vo.setInfo(skuInfoEntity);

            return skuInfoEntity;
        }, executor);

        CompletableFuture<Void> saleAttrFuture = infoFuture.thenAcceptAsync((res) -> {
            //3.spu的销售属性
            List<SkuItemSaleAttrVo> skuSaleAttrValueEntities =
                    skuSaleAttrValueService.getSkuSaleAttrBySpuId(res.getSpuId());
            vo.setSaleAttr(skuSaleAttrValueEntities);
        }, executor);

        CompletableFuture<Void> descFuture = infoFuture.thenAcceptAsync((res) -> {
            //4.spu介绍
            SpuInfoDescEntity spuDesc = spuInfoDescService.getById(res.getSpuId());
            vo.setDesc(spuDesc);
        }, executor);

        CompletableFuture<Void> groupAttrsFuture = infoFuture.thenAcceptAsync((res) -> {
            //5.规则参数信息
            List<SpuItemAttrGroupAttrVo> groupAttrs = attrGroupService.getAttrGroupBySpuId(res.getSpuId(), res.getCatalogId());
            vo.setGroupAttrs(groupAttrs);
        }, executor);

        CompletableFuture<Void> imagesFuture = CompletableFuture.runAsync(() -> {
            //2.sku图片信息
            List<SkuImagesEntity> images = skuImagesService.getImagesById(skuId);
            vo.setImages(images);
        }, executor);

        CompletableFuture.allOf(saleAttrFuture,descFuture,groupAttrsFuture,imagesFuture).get();

        return vo;
    }
```

**认证服务** 和首页、检索以及商品详细页面一样，通过静态代码保存在nginx，使用前后端不分离技术将认证相关的登录和注册服务创建新的微服务，同时创建跳转页面的控制层、服务层以及服务实现层。注册页面的核心就是如何进行注册，其中需要为每一个用户提供唯一辨识，这里使用手机号进行注册，再前端中进行设置验证码的倒计时再通过阿里云提供的短信服务api简单实现通过验证码的手机唯一辨识进行注册账号。

**如何进行验证码防刷校验** 基本上就两个问题，问题一由于网页可以重刷所以保存的信息重刷就消失了，那么就又可能用户会恶意用同一个手机号码进行不断发送验证码，这种情况在服务器页面中进行保存变量就不可以了，我们可以在redis这样的中间层缓存中进行保存手机号码和验证码以及发送验证码时间，当短时间内进行重新发送的时候进行查看redis进行校验就可以避免，而且带有时间戳所以可以在固定时间内进行设置校验什么时候可以重新发送验证码。问题二就是在前端的控制面板可以看到接口代码，有可能被用户进行恶意地接口重刷TODO

**如何保存用户信息到member微服务** 用户注册成功之后就需要将数据保存到数据库中，通过在注册页面进行保存用户信息VO调用第三方服务进行在member的微服务中进行保存数据信息。

**如何进行保存用户的密码** 

- MD5加密，Message Digest algorithm 5，apache提供的信息摘要算法，压缩性可以满足任意长度的数据，算出的MD5值长度都是固定的。同时容易计算，可以从原数据计算出MD5值很容易。并且抗修改性高，对原数据进行任何改动，哪怕只修改1个字节，所得到的MD5值都有很大区别。而且强抗碰撞强，想找到两个不同的数据，使它们具有相同的MD5值，是非常困难的。
- 加盐，通过生成随机数与MD5生成字符串进行组合，需要数据库同时存储MD5值与salt值。验证正确性时使用salt进行MD5即可。
- BCryptPasswordEncoder进行实现，通过使用Spring Security的BCryptPasswordEncoder进行加密存储用户密码，然后当用户输入密码的时候将其明文密码和数据库中存储的密文进行matches操作得出布尔变量结果进行判断是否存在进行登录，注意BCryptPasswordEncoder使用的也是加盐的操作概率。

**社交登录**

通过OAuth2.0实现社交登录，用户除了通过上面的账户密码进行登录，也可以通过第三方的社交软件进行登录，比如csdn作为第三方软件应用向QQ、微信或者微博进行申请授权进行登录，通过以下的流程进行登录。

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746869131864.jpg)

详细步骤就是用户点击社会认证链接，而该链接是由开发人员在第三方开发平台中进行申请得到的，用户在链接中进行认证并且通过认证之后开发平台会将带有访问令牌的url进行重定向到开发服务器，这个也是由开发人员在开发平台定义，这个时候开发人员就可以在后端进行处理该请求并且将带有的访问令牌和一些相关信息包装起来去访问开发平台的相关api，成功之后会将用户的相关信息进行返回这个时候我们就可以进行处理用户的社会登录了。**注意：**这个时候一般需要进行判断用户是否为第一次进行登录，用一个社会登录的变量进行存储，登录成功之后进行查看如果是第一次登录就进行注册操作，而不是第一次登录那就取出用户信息进行正常登录。

**会话以及相关的操作问题**  首先**会话Session**指得是会话是用户与系统（如网站、软件）交互过程中，用于存储和共享跨请求 / 页面状态信息（如登录凭证、操作数据）的上下文记录，确保交互的连续性和状态一致性。但是原生的session是由Servlet 容器（如 Tomcat）进行提供，这种session会将信息保存在当前服务器的内存中，然后后续再次访问服务器的时候就会携带该会话的唯一id，服务器就会根据id进行数据读取从而保证数据的一致性。但是原生session有以下的问题

- 数据一致性问题 由于保存在服务器内存中，当项目部署了负载均衡的中间件以及出现单点失效的情况时都会丢失会话信息
- 跨域/子域问题 当项目中的一个子域名跳转到另外一个子域名，实现跨域操作的时候也会找不到会话信息

**SpringSession** 是 Spring 生态系统中的一个项目，旨在简化分布式会话管理。它为 web 应用提供了跨多个服务或实例的会话一致性解决方案，使得在微服务架构或集群环境中管理用户会话变得更加容易。其提供了三种方式进行处理会话，从而解决了三个问题，其一为在SpringSession中使用了redis来进行保存cookies信息也就是会话信息，这样就可以允许实现负载均衡的时候也能处理用户发来带有会话信息的请求，其二就是在Springsession中可以为session进行设置配置信息，将cookies的数据信息的区域设置成父域名，这样即使是子域名的跨域问题也可以进行处理而不会出错，第三点就是在session中进行传输数据是通过jdk的序列化和反序列化进行的，在springsession中通过设置配置类就可以通过json的方式进行传递参数而免去了进行序列化等复杂操作。
**SpringSession核心原理**  @EnableRedisHttpSession导入RedisHttpSessionConfiguration配置

- 1、给容器中添加了一个组件SessionRepository =>>>[RedisOperationsSessionRepository]==>redis操作session。 session的增删改查封装类

- 2、SessionRepositoryFilter==>Filter: session存储过滤器;每个请求过来都必须经过filter

​		a、创建的时候，就自动从容器中获取到了SessionRepository;

​		b、原始的request,response都被包装。SessionRepositoryRequestWrapper,SessionRepositoryResponseWrapper

​		c、以后获取session。request.getSession();

​		//SessionRepositoryRequestWrapper

​		d、wrappedRequest.getSession();===>SessionRepository 中获取到的。



![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746884058281.jpg)

**单点登录**

能实现单点登录的方式就三种分别是分布式session、CAS中央认证服务器（通过cookie实现）、JWT，但是分布式session无法实现不同父级域名进行免登录，所以这里讲讲第二中方式。

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746931559571.jpg)

还有一种就是通过JWT进行实现，**JWT（JSON Web Token）** 是一种由头部（算法信息）、载荷（用户数据）和签名（防篡改）三部分组成的无状态令牌，通过签名确保数据安全。在单点登录（SSO）中，用户首次登录认证中心后，服务器生成包含用户身份和有效期的 JWT 并返回给客户端；后续访问其他系统时，客户端在请求头（如 `Authorization: Bearer <token>`）中携带该令牌，各系统独立验证签名及有效期后直接授权，无需依赖中心化会话存储。JWT 的跨域传递能力使其天然支持不同域名系统的无缝跳转，而无需重复登录。其无状态特性简化了分布式架构的复杂度，但需配合 HTTPS 传输和短有效期设置，以防范令牌泄露风险，从而在便捷与安全间实现高效平衡。

**购物车功能** 实现购物车主要通过前后端不分离进行页面环境搭建，在将实际情况进行创建VO类，最后将每个页面信息和购物车进行结合即可实现该部分的基本功能。

**Threadload应用-在购物车功能中保存用户信息** 在该部分首先我们需要知道线程创建除了显示创建（new thread）以外还会有隐性创建，比如**HTTP 请求处理**（Tomcat/Jetty 线程池）**数据库连接池维护**（HikariCP 后台线程）**异步任务与定时任务**（`@Async`、`@Scheduled`）**消息队列监听**（RabbitMQ/Kafka 消费者线程）**缓存异步刷新**（Caffeine 线程池）**分布式锁管理**（Redisson Watchdog 线程）等，这里我们需要从第一种进行展开。由于使用VO进行保存用户信息类这就导致，每个不同的https请求处理都又可能会操作这个类的静态变量，由于请求处理是多线程的并发处理，这样就有可能会导致信息的错误。这个时候就需要通过Threadlocal进行保存用户信息类了，Threadlocal是一种map每个线程自己保存一个与其他的线程是互不打扰的，而这种业务中的用户信息一般会使用拦截器进行避免冗余的操作，我们就会拦截器中进行使用Threadlocal进行保存用户信息，这样就实现了和其他请求相互隔离，并且为线程后面使用用户信息提供了正确的信息。**注意：**有的时候我们会在这个地方使用双拦截器进行拦截，可以应用到比如权限认证等。

**购物车的小bug** 这里主要是在添加购物车的时候，正常逻辑是进行访问请求在一个controller中进行处理业务，并且将信息返回同时进行跳转到添加成功页面，但是有一个问题就是当用户仅仅刷新该页面的时候就会直接将之前的业务请求进行重新加入购物车，这是肯定不对的购物车肯定不是刷新页面就可以直接进行添加。所以进行修改用两个请求进行解决，用户点击添加按钮，我们为用户进行业务逻辑处理并且处理结束之后仅仅将信息进行页面跳转而不进行业务处理，这样的话用户单单刷新页面就不会直接改变数据了，而只有点击添加购物车才会进行业务处理。**注意：**这里使用到了**RedirectAttribute**，RedirectAttribute 是 Spring MVC 框架提供的一种工具，用于在重定向（Redirect）时传递数据，而普通的重定向是 HTTP 协议的基础功能，仅实现页面跳转。两者的核心区别在于 数据传递的方式和安全性，在这个部分就可以每次重定向的时候进行使用而不用通过其他方式。

### 消息队列-RabbitMQ

**消息队列中间件**（Message Queue Middleware）是一种用于在分布式系统中实现异步通信的软件基础设施，其核心功能是**解耦服务之间的直接依赖**，**缓冲通信压力**，并**确保消息的可靠传输**。它通过提供消息的存储、路由、传递及管理能力，帮助不同服务或组件高效、安全地交换数据，从而提升系统的可扩展性、容错性和灵活性。

- 削峰添谷
- 异步处理
- 应用解耦

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746968873481.jpg)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746969026557.jpg?Expires=1746969355&OSSAccessKeyId=TMP.3KqCgXJFPLSGTD1pxyoDbP8KLcoYdTRPofCLRoc9QCY1TK7fAgwe94j3pKdH5oV4DPcMgcMgAWyxkscVq8Vkmp8H8kLnbp&Signature=iDdghNijw%2BtWSghTWcQjZ3ZgFYA%3D)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746969392596.jpg)

**RabbitMQ**  是一款基于 AMQP 协议的开源消息中间件，充当消息代理（Broker），实现应用程序或服务间的异步通信与解耦。生产者（Publisher）创建带有路由键（Route - Key）的消息，经长连接和通道（Channel）发送至交换机（Exchange）；交换机依据绑定（Binding）规则，通过路由键将消息路由到对应队列（Queue）存储；消费者（Consumer）借助连接从队列获取并处理消息。虚拟主机（VHost，如 `/java`、`/php`）则提供逻辑隔离，区分不同应用资源。通过这些组件协作，RabbitMQ 确保消息可靠传输、精准路由与高效管理，提升系统灵活性、可扩展性，使应用间无需直接耦合，实现松耦合的异步处理。

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746970606949.jpg)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1747050592365.jpg)

**注意：**这里的fanout扇出就差不多和广播相似，而topic主题就是按照发送数据的路由键是否匹配队列的路由键规则进行部分发送数据，而direct直接就是最经典的点对点的发送方式。

**如何使用RabbitMQ操作** 首先需要在springboot中进行整合amqp驱动器，当你引入`spring-boot-starter-amqp`依赖时，它会自动包含 RabbitMQ 客户端库（`com.rabbitmq:amqp-client`），然后再在application.yml中进行配置相关接口和主机信息，这样后端就和中间件进行连接了。依赖中提供了rabbitmq的admin的组件操作，可以进行配置相关的交换机以及队列信息，使用template就可以进行简化我们发送消息的方式，通过上面的操作后端就可以进行使用rabbitmq了，同时我们还需要进行接收消息，利用提供的RabbitListener和RabbitHandler进行编辑接收消息的方式，从而可以进行在队列中进行接收消息，这里需要知道发送消息是讲数据进行发送到交换机上，而接收则是从队列中进行接收。**注意：**RabbitListener和RabbitHandler注解的区别就是前者是直接绑定接收消息的队列，后者是通过重写函数从而绑定接收消息类型，并且接受消息的时候所有消息之间是需要进行争夺资源的，并不是只要发送消息都一定会接受消息，如果一个队列有多个接受者，那么他们对于消息的接收就是资源争夺。

**RabbitMQ是如何实现可靠性传输的** **RabbitMQ的可靠传输**是指通过生产者确认（Publisher Confirm）、消息持久化（持久化队列和消息）、消费者手动应答（Manual Acknowledgement）等机制，确保消息从生产者发送到Broker（中间件）再到消费者的全链路不丢失。生产者发送消息后需等待Broker确认写入磁盘，消费者处理完成后手动发送ACK告知Broker删除消息，若处理失败则触发重试或死信队列，从而在系统故障、网络波动等场景下保障数据一致性。

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1747099241782.png)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1747099364349.jpg)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1747099400643.jpg)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1747099437819.jpg)

### 订单服务

整个商城中比较重要的地方就差不多为订单服务以及秒杀服务，这些微服务会牵扯到较多的业务流程，同时也会涉及到高并发的概念，这个部分主要来写怎么实现一个电商服务中的订单效果。下面是订单服务的大致流程图：

![image-20250513101905920](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/image-20250513101905920.png)

**提交订单的幂等性操作** 也就是如何实现用户在提交订单的时候实现防重复提交的效果，因为当用户由于各种原因去点击修改数据库操作的时候可能会发送各种各样的重复修改，这个时候就需要进行设计从而防止对数据库的灾难性修改。**接口幂等性**就是用户对于同一操作发起的一次请求或者多次请求的结果是一致的，不会因为多次点击而产生了副作用;比如说支付场景，用户购买了商品支付扣款成功，但是返回结果的时候网络异常，此时钱已经扣了，用户再次点击按钮，此时会进行第二次扣款，返回结果成功，用户查询余额返发现多扣钱了，流水记录也变成了两条.。.,这就没有保证接口的幂等性。**哪些情况需要防止**用户多次点击按钮、用户页面回退再次提交、微服务互相调用，由于网络问题，导致请求失败。feign触发重试机制其他业务情况等。**什么情况下不需要幂等**以 SQL为例，有些操作是天然幂等的。**查询操作**无论执行多少次都不会改变状态，是天然的幂等。**更新操作**无论执行成功多少次状态都是一致的,也是幂等操作。**删除目标数据**，多次操作，结果一样，具备幂等性工，**如果是插入操作就需要进行按情况分析**，如 userid 为唯一主键，即重复操作上面的业务，只会插入一条用户数据，具备幂等性。
但是**如果在更新操作的时候进行+1-1这样的函数运算就又不太一样了**，每次执行的结果都会发生变化，不是幂等的。**插入操作也有这样的现象**，如 userid 不是主键，可以重复，那上面业务多次操作，数据都会新增多条，不具备幂等性。

- token机制（令牌机制）
- 各种锁的机制，包括数据库悲观锁、数据库乐观锁、业务层分布式锁等
- 各种唯一性约束，包括数据库唯一约束、redis set防重等
- 防重表 唯一性约束是在关联的表中加入唯一性约束的列，而防重表是在数据库中新加一张表当进行操作的时候进行查询验证之后再操作
- 全局请求唯一id，即在nginx这样的中间件中进行存储全局唯一id进行区分

### 分布式事务

### 秒杀服务

### 高并发

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746487530925.jpg)

![](https://md-file-zhaowei.oss-cn-beijing.aliyuncs.com/Java%E5%AD%A6%E4%B9%A0/1746487530944.jpg)

### 熔断降级和限流

**熔断**
A服务调用B服务的某个功能，由于网络不稳定问题，或者B服务卡机，导致功能时间超长。如果这样子的次数太多。我们就可以直接将B断路了(A不再请求B接口)，凡是调用 B的直接返回降级数据，不必等待B的超长执行。这样B的故障问题，就不会级联影响到 A。
**降级**
整个网站处于流量高峰期，服务器压力剧增，根据当前业务情况及流量，对一些服务和页面进行有策略的降级[停止服务，所有的调用直接返回降级数据]。以此缓解服务器资源的的压力，以保证核心业务的正常运行，同时也保持了客户和大部分客户的得到正确的相应。
**熔断和降级的异同:**
相同点:
1、为了保证集群大部分服务的可用性和可靠性，防止崩溃，牺牲小我
2、用户最终都是体验到某个功能不可用

不同点:
1、熔断是被调用方故障，触发的系统主动规则
2、降级是基于全局考虑，停止一些正常服务，释放资源
**限流**
对打入服务的请求流量进行控制，使服务能够承担不超过自己能力的流量压力

**Sentinel 是什么**

随着[微服务](https://so.csdn.net/so/search?q=微服务&spm=1001.2101.3001.7020)的流行，服务和服务之间的稳定性变得越来越重要。Sentinel 是面向分布式服务架构的**轻量级**流量控制产品，主要以流量为切入点，从流量控制、熔断降级、系统负载保护等多个维度来帮助您保护服务的稳定性。

## 谷粒商城（高可用集群—框架师提升篇）

# 算法

## 力扣hot100

### 两数之和

**穷举算法：**

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] array = new int[2];
        int size = nums.length;
        for (int i = 0;i<size;i++){
            int j = target-nums[i];
            for(int k = i+1;k<size;k++){
                if(nums[k]==j){
                    array[0] = i;
                    array[1] = k;
                    return array;
                }
            }
        }
        return array;
    }
}
```

这样也是实现了，不过需要进行简化使其更加简洁和清楚

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[0];
    }
}
```

**哈希算法：**

我们可以发现上面的做法其根本就是遍历两遍数组，所以无论如何其复杂度都是O（n^2）所以有没有只用遍历一遍就可以实现的算法呢，我们可以注意到必须遍历两遍的原因主要是由于当我们选定一个元素的时候，另外一个元素就必须进行二次遍历所以才会是n^2，那么如果有一种方法当我们知道我们所需要的数值当不用去遍历数组的时候这样计算量就小了很多，于是乎我们就有了哈希表的诞生。哈希表是一种查询算法，由于我们在选定第一个元素的时候，我们就可以知道我们所需要的元素，那么我们就可以通过空间换时间的方式进行优化，将每次遍历过的元素放入哈希表中，当在后面遍历的时候去搜索哈希表这样就可以仅仅只有搜索一次数组就可以知道所需要的结果了。

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> hashtable = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; ++i) {
            if (hashtable.containsKey(target - nums[i])) {
                return new int[]{hashtable.get(target - nums[i]), i};
            }
            hashtable.put(nums[i], i);
        }
        return new int[0];
    }
}
```

### 字母异位词分组

**穷举算法：**

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> twoDimensionalArrayList = new ArrayList<>();
        int length = strs.length;
        int [] index = new int[length];
        Arrays.fill(index, 0);
        for(int i = 0;i<length;i++){
            if(index[i] == 1){
                continue;
            }
            List<String> row1 = new ArrayList<>();
            row1.add(strs[i]);
            for(int j = i+1;j<length;j++){
                if(areAnagrams(strs[i],strs[j])){
                    row1.add(strs[j]);
                    index[j] = 1;
                }
            }
            twoDimensionalArrayList.add(row1);
        }
        return twoDimensionalArrayList;
    }

    public boolean function(String a,String b){
        if(a.equals(b)){
            return true;
        }
        int length = a.length();
        int count = 0;
        for(int i = 0;i<length;i++){
            if(a.isEmpty()){
                return false;
            }
            char c = a.charAt(i);
            for(int j = 0;j<length;j++){
                if(b.isEmpty()){
                    return false;
                }
                char d = b.charAt(j);
                if(c==d){
                    count++;
                    break;
                }
            }
        }
        System.out.println(count);
        if(count!=length){
            return false;
        }
        return true;
    }
    public static boolean areAnagrams(String str1, String str2) {
        // 检查两个字符串长度是否相等，如果不相等，则不可能是变位词
        if (str1.length() != str2.length()) {
            return false;
        }
        
        // 将两个字符串的字符数组进行排序
        char[] charArray1 = str1.toCharArray();
        char[] charArray2 = str2.toCharArray();
        Arrays.sort(charArray1);
        Arrays.sort(charArray2);
        
        // 比较排序后的字符数组是否相等
        return Arrays.equals(charArray1, charArray2);
    }
}
```

**哈希算法：**

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<String, List<String>>();
        for (String str : strs) {
            char[] array = str.toCharArray();
            Arrays.sort(array);
            String key = new String(array);
            //Map接口的getOrDefault方法是Java 8中引入的，它结合了get和put方法的功能。这个方法接受两个参数：一个键（key）和一个默认值（defaultValue）。当你尝试从Map中获取与指定键关联的值时，如果该键存在，getOrDefault方法会返回与该键关联的值；如果该键不存在，则会返回你提供的默认值。
            List<String> list = map.getOrDefault(key, new ArrayList<String>());
            list.add(str);
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

Java中的`Map`接口是一个存储键值对（Key-Value pairs）的集合，它定义了一系列操作这些键值对的方法。`Map`接口的实现类（如`HashMap`、`TreeMap`等）提供了具体的存储和检索机制。

**HashMap**：它基于哈希表的实现，提供了快速的查找功能，因为它在内部使用哈希表来存储键值对。

**TreeMap：**它基于红黑树的实现，提供了有序的键值对存储。

## 算法类型

### 回溯算法

在回溯算法中，他与动态规划以及分治法不同，其核心思想更多是从数据结构方面考虑，而另外两个则是从问题规模上进行考虑，回溯就是按照多叉数的深度优点遍历或者是广度优先遍历，在遍历的过程中进行查找问题答案，并且当到达叶子节点的时候，将进行返回也就是回溯，回溯到上一个岔路口进行选择其他可能结果，并再次遍历，重复上述的过程，直到找到答案，这就是回溯算法。

```java
/**
给你一个整数数组 nums ，数组中的元素 互不相同 。返回该数组所有可能的子集（幂集）。解集不能包含重复的子集。你可以按任意顺序返回解集。
示例 1：
输入：nums = [1,2,3]
输出：[[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
示例 2：
输入：nums = [0]
输出：[[],[0]]
*/
class Solution {
    List<Integer> t = new ArrayList<Integer>();
    List<List<Integer>> ans = new ArrayList<List<Integer>>();

    public List<List<Integer>> subsets(int[] nums) {
        dfs(0, nums);
        return ans;
    }

    public void dfs(int cur, int[] nums) {
        if (cur == nums.length) {
            ans.add(new ArrayList<Integer>(t));
            return;
        }
        t.add(nums[cur]);
        dfs(cur + 1, nums);
        t.remove(t.size() - 1);
        dfs(cur + 1, nums);
    }
}

```

### 贪心算法

贪心算法的核心思路就是根据题目要求去寻找最优解，一般是去思考题目本意来进行解题。换句话说其核心是 **在每一步选择当前状态下的局部最优解，希望通过这些局部最优解的组合，最终得到全局最优解**。它通常用于解决优化问题，例如最短路径、任务调度、资源分配等。对于复杂问题，可能需要结合动态规划等其他方法。比较难以理解的是如何证明贪心算法的正确性，及局部最优解是不是全局最优解，这个一般需要通过数学归纳法或者交换论证法进行证明。

```java
/*
给定一个长度为 n 的 0 索引整数数组 nums。初始位置为 nums[0]。每个元素 nums[i] 表示从索引 i 向后跳转的最大长度。换句话说，如果你在 nums[i] 处，你可以跳转到任意 nums[i + j] 处:
0 <= j <= nums[i] 
i + j < n
返回到达 nums[n - 1] 的最小跳跃次数。生成的测试用例可以到达 nums[n - 1]。
示例 1:
输入: nums = [2,3,1,1,4]
输出: 2
解释: 跳到最后一个位置的最小跳跃数是 2。
     从下标为 0 跳到下标为 1 的位置，跳 1 步，然后跳 3 步到达数组的最后一个位置。
示例 2:
输入: nums = [2,3,0,1,4]
输出: 2
*/
class Solution {
    public int jump(int[] nums) {
        int position = nums.length - 1;
        int steps = 0;
        while (position > 0) {
            for (int i = 0; i < position; i++) {
                if (i + nums[i] >= position) {
                    position = i;
                    steps++;
                    break;
                }
            }
        }
        return steps;
    }
}
```

### 拓扑排序

拓扑算法通常指的是用于处理图（Graph）中拓扑结构问题的算法，其中最经典的是 **拓扑排序（Topological Sorting）**。拓扑排序是一种对有向无环图（Directed Acyclic Graph，DAG）的顶点进行线性排序的方法，使得图中任意一条有向边 *u*→*v*，顶点 *u* 在排序中都出现在顶点 *v* 的前面。这种排序常用于解决依赖关系问题，例如任务调度、课程安排、编译顺序等。

```java
/*
你这个学期必须选修 numCourses 门课程，记为 0 到 numCourses - 1 。在选修某些课程之前需要一些先修课程。 先修课程按数组 prerequisites 给出，其中 prerequisites[i] = [ai, bi] ，表示如果要学习课程 ai 则 必须 先学习课程  bi 。例如，先修课程对 [0, 1] 表示：想要学习课程 0 ，你需要先完成课程 1 。
请你判断是否可能完成所有课程的学习？如果可以，返回 true ；否则，返回 false 。
示例 1：
输入：numCourses = 2, prerequisites = [[1,0]]
输出：true
解释：总共有 2 门课程。学习课程 1 之前，你需要完成课程 0 。这是可能的。
示例 2：
输入：numCourses = 2, prerequisites = [[1,0],[0,1]]
输出：false
解释：总共有 2 门课程。学习课程 1 之前，你需要先完成​课程 0 ；并且学习课程 0 之前，你还应先完成课程 1 。这是不可能的。
*/
class Solution {
    List<List<Integer>> edges;
    int[] visited;
    boolean valid = true;

    public boolean canFinish(int numCourses, int[][] prerequisites) {
        edges = new ArrayList<List<Integer>>();
        for (int i = 0; i < numCourses; ++i) {
            edges.add(new ArrayList<Integer>());
        }
        visited = new int[numCourses];
        for (int[] info : prerequisites) {
            edges.get(info[1]).add(info[0]);
        }
        for (int i = 0; i < numCourses && valid; ++i) {
            if (visited[i] == 0) {
                dfs(i);
            }
        }
        return valid;
    }

    public void dfs(int u) {
        visited[u] = 1;
        for (int v: edges.get(u)) {
            if (visited[v] == 0) {
                dfs(v);
                if (!valid) {
                    return;
                }
            } else if (visited[v] == 1) {
                valid = false;
                return;
            }
        }
        visited[u] = 2;
    }
}
```

### 动态规划

动态规划（Dynamic Programming，简称DP）是一种用于解决复杂优化问题的算法设计方法。其核心思想是通过将原问题分解为相互重叠的子问题，并利用子问题的解来高效地构建原问题的最优解。其中最为核心的思想就是找到解决问题的状态转移方程，通过实现这个方程就可以解决问题。

**状态转移方程** ：就是指相同问题在不同的规模下的关系。

```java
/*
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
示例 1：
输入：n = 2
输出：2
解释：有两种方法可以爬到楼顶。
1. 1 阶 + 1 阶
2. 2 阶
示例 2：
输入：n = 3
输出：3
解释：有三种方法可以爬到楼顶。
1. 1 阶 + 1 阶 + 1 阶
2. 1 阶 + 2 阶
3. 2 阶 + 1 阶
*/
class Solution {
    int climbStairs(int n){
        if(n==1||n==2){
            return n;
        }else{
            return climbStairs(n-1)+climbStairs(n-2);
        }
    }
}
class Solution {
    /*
    和上面递归实现实际上状态转移方程没有变，只不过是将看问题的方式进行修改，
    前者是有n个台阶我需要去计算，递归到最后进行返回，
    而后者是从头进行计算有这么多的台阶我依次累加
    相同的概率不同实现方式，造成后者时间复杂度低
    */
    public int climbStairs(int n) {
        //这里p存储走一步，q存储走两步，r存储下一阶台阶的可能方法数量
        int p = 0, q = 0, r = 1;
        for (int i = 1; i <= n; ++i) {
            p = q; 
            q = r; 
            r = p + q;
        }
        return r;
    }
}
```



# 八股文

## Java

### HashMap

**底层实现**

### 锁

在Java中有许许多多的锁来实现线程的并发操作，其主要分为三类内置锁、接口Lock实现的锁以及其他机制实现的锁。

### **lammda表达式**

通过简洁的表达式进行展示函数的具体运过程

## Spring

### AOP编程

**使用流程**

**实现原理**

**不同代理区别和优点**

### Bean

**生命周期**

**循环依赖**

**为什么要使用三级缓存**

## SpringBoot

**Spring Boot** 是一个基于 **Spring Framework** 的开源框架，旨在简化 Spring 应用的初始搭建和开发过程。它通过提供**约定优于配置**的设计理念和一系列开箱即用的工具，让开发者能够快速构建独立、生产级的应用程序，而无需繁琐的配置。虽然优化了大量其他插件配置文件的冗余，但是使用SpringBoot还是需要为SpringBoot准备其自身的配置文件的，一般保存在application.yml文件下。

## MYSQL数据库

### 范式

**第二范式和第三范式的区别：**

第一范式实现了数据库的列不可再分，而第二范式主要处理的是当表中是复合主键的时候，所有的列必须和复合主键中的所有列都有关，而不是与其中一部分有关，第三范式实现了非主键之间不能出现传递关系，也就是非主键有且仅有与主键有关，与其他非主键无关。

### SQL中常使用的命令

**select：**

select的后面直接接上的单位一般就是处理对象，而后面的操作关键字基本都是对其进行修饰

### SQL中常使用的函数

**日期和时间函数：**

now() 函数指返回当前的日期和时间

```sql
-- 返回当前日期和时间
SELECT NOW() AS current_date_time;
```

### 事务

**两阶段提交** 其中提交指得是binlog和redolog的提交，为什么叫做两阶段提交是指在一个事务语句中，同时协调提交binlog和redolog文件，既要保持操作的原子性同时需要保证全局数据的一致性。

### 索引

**索引原理**

**失效场景**

**建立索引的场景**

## Redis

### 什么是Redis

 Redis（Remote Dictionary Server）是一个基于内存、支持持久化的高性能键值对数据库，通常被用作缓存、消息队列、分布式锁等。它的数据以键值对形式存储，支持丰富的数据结构，如字符串（String）、哈希（Hash）、列表（List）、集合（Set）、有序集合（Sorted Set）等，Redis 具有高性能、持久化、高并发、支持集群以及支持丰富的数据结构的特点。

- 高性能：基于内存操作，读写速度极快，QPS（每秒查询率）可达数万甚至更高。

- 丰富的数据结构：除基本类型外，还支持复杂数据模型，满足不同场景需求。

- 持久化：提供RDB（快照）和AOF（日志追加）两种持久化方式，保障数据可靠性。

- 高并发：单线程模型结合非阻塞I/O，有效避免多线程切换开销，支持高并发访问。

- 集群模式：通过主从复制、哨兵模式、Cluster集群实现高可用和水平扩展。


### 缓存穿透、缓存雪崩以及缓存击穿

**缓存穿透**

**缓存雪崩**

**缓存击穿**

## Nginx

**内网穿透**：用于让外部网络访问内网服务，解决内网设备无公网IP的问题。通过中转服务器（如frp、ngrok）建立隧道，将公网请求转发到内网，适用于远程办公、开发调试等场景。  **正向代理**：代理客户端访问外部资源，隐藏客户端真实身份。客户端将请求发送给代理服务器（如Shadowsocks、Squid），由代理服务器代为访问目标网站，常用于突破访问限制或保护隐私。  **反向代理**：代理服务器端接收外部请求，隐藏后端真实服务器。反向代理（如Nginx、Cloudflare）将请求按规则分发给后端多台服务器，实现负载均衡、安全防护和缓存加速，提升服务可靠性和性能。而Nginx就是主要用于反向代理的实现，同时还可以进行负载均衡以及网关使用，是大部分web项目进行上线之前的必要使用工具。

##  操作系统

### 页面置换算法

**LRU（最近最久未使用）**就是在一定窗口内，每次访问就把存在的值放入首位，其他位置顺延，当出现新的数值并且超过这个窗口的时候将末尾的数值置换出去

**LFU（最近最少未使用）**就是在一定窗口内，每次访问就把存在的值的计数位加一，当出现新的数值并且超过这个窗口数量的时候，将窗口内计数位最小的数值置换出去

**NRU（最近未使用）**这个算法的每一个页面都有访问位和脏位，每次访问修改访问位，每次修改数据修改访问位和脏位，访问位会定期恢复为未访问，当需要进行页面置换的时候优先将访问位为0，脏位为1的页面置换出去。

# 面试优化

## JVM调优

## SQL优化

## 数据结构优化

**哈希表数据存储优化** 

## 设计模式

**单例模式** 就是指项目中只能有一个实例，单例类只能有一个实例，且单例类必须自己创建自己的唯一实例，同时单例类必须给所有其他对象提供可以获取这一实例的方法。实现方式有多种分别为饿汉类、懒汉类、以及双重检查锁等等，以下为双重锁的实现方式。

```java
package com.atguigu.gulimall.common.utils;

public class Singleton {
    //使用volatile保证可见性和禁止指令重排序
    private volatile static Singleton instance;
    //私有的构造函数禁止外部实例化
    private Singleton(){};
    //双重检查锁实现
    public static Singleton getInstance(){
        //第一次检查避免不必要的同步
        if(instance == null){
            synchronized (Singleton.class){
                //第二次检查确保在同步块内创建实例
                if(instance == null){
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

# 投递情况

美团

字节

小红书

快手
