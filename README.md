# JavaInterview
《Java面试笔记》是本人整理归纳Java的常见面试题，并将这些面试知识整理成文方便大家查阅。如果查看面试题时候发现有问题（遗漏、有误等）的话，麻烦联系一下我，我会第一时间更正过来。


### 一、Java 基础

1.JDK 和 JRE 有什么区别？

2.== 和 equals 的区别是什么？
```
== 既可以运用于基本数据类型，也可以运用于引用数据类型，对于基本数据类型，很简单，比较的就是数值是否相等。而对应引用数据类型，比较的其实就是两个对象的地址值是否相等，也就是看两个对象是否是同一个对象。
equals 只能运用于引用数据类型，不能运用于基本数据类型。
一般在String类中，他底层是重写了equals方法的，将字符串变成了字符数组，然后一个字符一个字符的比较。在其他Object类中并没有重写equals方法，所以比较的是地址值，但是比较地址值又没有意思，所以我们需要重写equals方法，然后比较两个对象中内容是否相等。举个例子吧。一个User对象，成员变量姓名，年龄，然后创建一个user1,姓名小明，年龄18，另一个user2，姓名小明，年龄18。然后user1.equals（user2）。如果我们在User实体类中并没有重写equals方法，很显然，结果为false,如果我们重写了equals方法，结果为true。
```

3.两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？
```
不一定，比如“通话”和“重地”的hashcode值相同，但是返回false
```
4.final 在 java 中有什么作用？

5.java 中的 Math.round(-1.5) 等于多少？
```
四舍五入取整(在本来值的基础上加上0.5，再取向下取整)
```
6.String 属于基础的数据类型吗？
```
java中基础数据类型只有8种：
byte，short，int，long，double，float，char，boolean
```

7.java 中操作字符串都有哪些类？它们之间有什么区别？
```
StringBuilder和StringBuffer，后者是线程安全（记忆方法：builder只是高楼，而buffer相当于给楼加了一层外套，所以线程安全）
```
8.String str="i"与 String str=new String("i")一样吗？
```
不一样，前者是常量池一个常量，后者会新建一个对象
```

9.如何将字符串反转？
```
直接调用
把字符串转换成字符数组倒序拼接然后返回值（调用inverse()方法）
```

10.String 类的常用方法都有那些？
![3081f5313965ece8e329303c6b6b08cf.png](evernotecid://2BD76724-DEDE-45A5-B592-69F159394558/appyinxiangcom/23275444/ENResource/p22)

11.抽象类必须要有抽象方法吗？
不一定，但是有抽象方法的一定是抽象类

12.普通类和抽象类有哪些区别？
```
a.抽象类不能被实例化。
b.抽象类可以有构造函数，被继承时子类必须继承父类一个构造方法，抽象方法不能被声明为静态。
c.抽象方法只需申明，而无需实现，抽象类中可以允许普通方法有主体
d.含有抽象方法的类必须申明为抽象类
e.抽象的子类必须实现抽象类中所有抽象方法，否则这个子类也是抽象类。
```
13.抽象类能使用 final 修饰吗？
```
不能
```
14.接口和抽象类有什么区别？
```
a.抽象类和接口都不能直接实例化，如果要实例化，抽象类变量必须指向实现所有抽象方法的子类对象，接口变量必须指向实现所有接口方法的类对象。
b.抽象类要被子类继承，接口要被类实现。
c.接口只能做方法申明，抽象类中可以做方法申明，也可以做方法实现
d.接口里定义的变量只能是公共的静态的常量，抽象类中的变量是普通变量。
e.抽象类里的抽象方法必须全部被子类所实现，如果子类不能全部实现父类抽象方法，那么该子类只能是抽象类。同样，一个实现接口的时候，如不能全部实现接口方法，那么该类也只能为抽象类。
f.抽象方法只能申明，不能实现，接口是设计的结果 ，抽象类是重构的结果
g.抽象类里可以没有抽象方法
h.如果一个类里有抽象方法，那么这个类只能是抽象类
i.抽象方法要被实现，所以不能是静态的，也不能是私有的。
j.接口可继承接口，并可多继承接口，但类只能单根继承。
k.从JDk1.8开始，接口中可以定义default修饰的默认方法
l.从jdk1.9开始，接口中可以定义private修饰的方法，但是只能在接口中调用
```
15.java 中 IO 流分为几种？
![02b8ffdb6d4a2a63c58d65cee8166120.png](evernotecid://2BD76724-DEDE-45A5-B592-69F159394558/appyinxiangcom/23275444/ENResource/p23)

16.BIO、NIO、AIO 有什么区别？
```
BIO，同步阻塞式IO，简单理解：一个连接一个线程
    你到饭馆点餐，然后在那等着，还要一边喊：好了没啊！ 
NIO，同步非阻塞IO，简单理解：一个请求一个线程
    在饭馆点完餐，就去遛狗了。不过溜一会儿，就回饭馆喊一声：好了没啊！
AIO，异步非阻塞IO，简单理解：一个有效请求一个线程
    饭馆打电话说，我们知道您的位置，一会给你送过来，安心遛狗就可以了。
```
17.Files的常用方法都有哪些？
```
createNewFile()：在指定位置创建一个空文件，成功就返回true，如果已存在就不创建，然后返回false。
mkdirs() 在指定位置创建一个多级文件夹。
mkdir() 在指定位置创建一个单级文件夹。
delete() 删除文件或者一个空文件夹，不能删除非空文件夹，马上删除文件，返回一个布尔值。
exists() 文件或文件夹是否存在。
isFile() 是否是一个文件，如果不存在，则始终为false。
isDirectory() 是否是一个目录，如果不存在，则始终为false。
```
### 二、容器

18.java 容器都有哪些？
![1173d0c66bd878de60bceee6f867ab60.png](evernotecid://2BD76724-DEDE-45A5-B592-69F159394558/appyinxiangcom/23275444/ENResource/p24)

19.Collection 和 Collections 有什么区别？
```
Collection 是一个集合接口，List，Set，Queue继承自Collection;
Collections是一个工具类，包含有各种有关集合操作的静态方法
```
20.List、Set、Map 之间的区别是什么？
```
list和set属于collection接口的子接口，list存储的数据有序，可重复，可用普通for循环遍历，实现类一般有：vector(线程安全)，arrayList(底层数据结构为数组（查询快，增删慢，），线程不安全)
List:列表;
Set:集合;
Map:映射;
```
21.HashMap 和 Hashtable 有什么区别？
```
1.HashTable先出来;
2.HashMap允许空键空值,因此线程不安全,非synchronized，只有一个线程访问的情况下，效率较高;
3.Hashtable继承自Dictionary类，而HashMap继承自AbstractMap类。但二者都实现了Map接口;
4.HashMap把Hashtable的contains方法去掉了，改成containsValue和containsKey。因为contains方法容易让人引起误解。 
5.两个遍历方式的内部实现上不同。Hashtable、HashMap都使用了Iterator。而由于历史原因，Hashtable还使用了Enumeration的方式
```
22.如何决定使用 HashMap 还是 TreeMap？
```
如果需要在map中进行插入、删除、定位元素这些操作，HashMap是最好的选择。如果只需要对一个有序的key集合进行遍历，TreeMap是更好的选择
```
23.说一下 HashMap 的实现原理？
```
通过hash的方法，通过put和get存储和获取对象。存储对象时，我们将K/V传给放方法时，它调用hashCode计算hash从而得到到bucket位置，进一步存储，HashMap会根据当前桶的占用情况自动调整容量（超过LoadFactor则resize为原来的2倍）。获取对象时，我们将K传给get，它调用hashCode计算hash从而得到到bucket位置，并进一步调用equals（）方法确定键值对。如果发生碰撞的时候，Hashmap通过链表将产生碰撞冲突的元素组织起来，在Java8中，如果一个桶中碰撞冲突的元素超过某个限制（默认是8），则使用红黑树来替换链表，从而提高速度。
```
24.说一下 HashSet 的实现原理？
```
HashSet 的内部采用 HashMap来实现。由于 Map 需要 key 和 value，所以HashSet中所有 key 的都有一个默认 value。类似于HashMap，HashSet 不允许重复的 key，只允许有一个null key，意思就是 HashSet 中只允许存储一个 null 对象。
```

25.ArrayList 和 LinkedList 的区别是什么？
```
ArrayList底层是数组，每个元素对应有数组下标，因此能查询效率快,而增加删除效率慢,因为数组每个元素的位置都需要向后移动；
而LinkedList底层是链表，每个元素有一个起始位置，一个结束位置，这个元素的结束位置指向下一个元素的起始位置。因此增加删除效率快，只需要将指向位置开边即可，而查询效率慢，需要遍历所有元素。
```
26.如何实现数组和 List 之间的转换？
```
List->数组：List.toArray
Set->数组：Set.toArray
```
27.ArrayList 和 Vector 的区别是什么？
```
1.Vector线程安全，效率较低
2.当元素超过它的初始大小时,Vector会将它的容量翻倍,而ArrayList只增加50%的大小，这样,ArrayList就有利于节约内存空间。
```
28.Array 和 ArrayList 有何区别？
```
Array:数组
1.Array可以包含基本类型和引用类型，ArrayList只能包含对象类型。
2.数组大小是固定的，ArrayList的大小是动态变化的。
3.ArrayList提供了更多的方法和特性，比如：addAll()，removeAll()，iterator()等等。
4.数组是连续的存储结构，List是不连续的存储结构，每个节点都有一个Next属性，记录着下一个节点的地址。
5.如果插入、删除操作频繁时，使用List；需要大量查找操作时候，最好使用Array
6.给出个不太重要的补充，由于List需要存储他下一个节点的地址，所以List 比Array相对起来浪费了更多的空间。
```
29.在 Queue 中 poll()和 remove()有什么区别？
```
remove() 和 poll() 方法都是从队列中删除第一个元素。如果队列元素为空，调用remove() 的行为与 Collection 接口的版本相似会抛出异常，但是新的 poll() 方法在用空集合调用时只是返回 null。因此新的方法更适合容易出现异常条件的情况。
```

30.哪些集合类是线程安全的？
```
Vector、HashTable、CocurrentHashMap
```

31.迭代器 Iterator 是什么？
```
Iterator接口提供了很多对集合元素进行迭代的方法。每一个集合类都包括了可以返回迭代器实例的迭代方法。迭代器可以在迭代过程中删除底层集合的元素，但是不可以直接调用集合的remove(Object obj)删除，可以通过迭代器的remove()方法删除
```
32.Iterator 怎么使用？有什么特点？


33.Iterator 和 ListIterator 有什么区别？
```
1.ListIterator有add()方法，可以向List中添加对象，而Iterator不能
2.ListIterator和Iterator都有hasNext()和next()方法，可以实现顺序向后遍历，但是ListIterator有hasPrevious()和previous()方法，可以实现逆向（顺序向前）遍历。Iterator就不可以。
3.ListIterator可以定位当前的索引位置，nextIndex()和previousIndex()可以实现。Iterator没有此功能。
4.ListIterator可以实现对象的修改 ->set()方法。Iterator仅能遍历。
```

34.怎么确保一个集合不能被修改？
```
Collections.unmodifiableMap(map);
```
### 三、多线程

35.并行和并发有什么区别？
```
并发和并行的区别就是一个处理器同时处理多个任务和多个处理器或者是多核的处理器同时处理多个不同的任务。

来个比喻：并发和并行的区别就是一个人同时吃三个馒头和三个人同时吃三个馒头。
```

36.线程和进程的区别？
```
进程：程序的一次运行；
线程：进程中一个执行单元

线程没有单独的地址空间，共享进程的；
进程有单独的地址空间

进程是有单独的资源分配；
同一个进程内的线程共享该进程的资源

线程是处理器调度的基本单位，但进程不是

两者均可并发执行
```
37.守护线程是什么？
```
服务于其他线程的线程，其他线程没有退出时，守护线程不会退出。例如GC线程就是最典型的守护线程。
```

38.创建线程有哪几种方式？
```
1.继承Thread类;
2.实现Runnable接口的run方法;
3.实现Callable接口的call方法，使用FutureTask类包裹Callable对象，再用Thread类包裹FutureTask对象，调用start方法；
4.Java6之后，可以通过线程池来创建线程。
```

39.说一下 runnable 和 callable 有什么区别？
```
相同点：
1.都是接口；
2.都可用来编写多线程程序；
3.都需要调用Thread.start（）来启动线程；

不同点：
1.Callable的call方法能返回执行结果，Runnable的run方法没有返回结果；
2.call（）方法允许抛异常，run（）方法的异常只能在内部消化，不能继续上抛。
```
40.线程有哪些状态？
```
1.新建（new）
2.可运行（runnable）
3.运行（running）
4.阻塞（blocked）
5.死亡（dead）
```
45.线程池都有哪些状态？
```
1.running(运行)
(1) 状态说明：线程池处在RUNNING状态时，能够接收新任务，以及对已添加的任务进行处理。 
(2) 状态切换：线程池的初始化状态是RUNNING。换句话说，线程池被一旦被创建，就处于RUNNING状态，并且线程池中的任务数为0！
2.shutdown
(1) 状态说明：线程池处在SHUTDOWN状态时，不接收新任务，但能处理已添加的任务。 
3.stop
不接受新任务，不处理已添加任务，中断正在处理的任务
4.tidying(整理，收拾)
当线程池在STOP状态下，线程池中执行的任务为空时，就会由STOP -> TIDYING
5.terminated(终止)
线程池彻底终止
```

41.sleep() 和 wait() 有什么区别？
```
1.sleep（）是Tread类的方法，wait（）是Object类的方法；
2.sleep（）可以指定时间让其醒过来，如果时间不到只能调用interrupt（）来强行打断，wait（）可以用notify（）直接唤起。
3.最重要的一点：sleep（）后，程序并不会释放同步锁，wait（）后，程序会释放同步锁。
```
42.notify()和 notifyAll()有什么区别？

43.线程的 run()和 start()有什么区别？
```
start（）才是真正启动一条线程，无需等待run方法体代码执行完毕就可以直接执行下面的代码；
run（）当做普通方法的方式调用，程序还是要顺序执行，要等待run方法体执行完毕后，才可以继续执行后续代码。程序中只有主线程这一个线程。
```



46.线程池中 submit()和 execute()方法有什么区别？
```
1.execute（）只能提交一个Runnable的对象，没有返回值
2.submit（）提交Callable对象，返回一个Future对象
3.submit（）方便异常处理
```

47.在 java 程序中怎么保证多线程的运行安全？
```
synchronized,lock
```

48.多线程锁的升级原理是什么？
```
偏向锁，轻量级锁，重量级锁。
```
49.什么是死锁？
```
由于两个或者多个线程互相持有对方所需要的资源，导致线程一直处于等待状态。

死锁的产生是必须要满足一些特定条件的： 
1.互斥条件：一个资源同时只能被一个线程占用； 
2.请求和保持条件：一个进程阻塞时，不会放弃已获得的资源。
3.不剥夺条件：资源没有被线程释放前，
4.循环等待条件：当发生死锁时，所等待的进程必定会形成一个环路（类似于死循环），造成永久阻塞。
```
50.怎么防止死锁？
```
1.按照同一顺序访问对象
2.避免事务中的用户交互
3.保持事务简短并在一个批处理中
4.使用低隔离级别
```
51.ThreadLocal 是什么？有哪些使用场景？
```
所谓ThreadLocal，简单一点想，就是一个全局的Map，Map的key是当前线程对象，value是你要保存的对象。进入某个线程后，就可以从map中取得之前存储的相应线程关联的对象。当然，ThreadLocal并不是一个Map，但用Map来理解是没有问题的

最常见的ThreadLocal使用场景为 用来解决数据库连接、Session管理等
```
52.说一下 synchronized 底层实现原理？
```
同步方法和同步代码块底层都是通过monitor来实现同步的。
两者的区别：同步方式是通过方法中的access_flags中设置ACC_SYNCHRONIZED标志来实现；同步代码块是通过monitorenter和monitorexit来实现
我们知道了每个对象都与一个monitor相关联。而monitor可以被线程拥有或释放。
```
53.synchronized 和 volatile 的区别是什么？
```
1.volatile只能修饰变量，synchronized可以用在变量、方法、类上；
2.volatile修饰的变量，如果某一个线程修改了该值，新值对其他线程立即可见；
3.volatile仅能实现变量的修改可见性，并不能保证原子性，synchronized则可以保证变量的修改可见性和原子性
4.volatile不会造成线程的阻塞，synchronized可能会造成线程的阻塞。
```
54.synchronized 和 Lock 有什么区别？
```
1.synchronized是java内置关键字，Lock是一个类
2.synchronized无法判断是否获取到锁，Lock可以判断
3.synchronized会自动释放锁，Lock需要手动释放锁，否则容易造成线程死锁
4.synchronized的锁可重入、不可中断、非公平，而Lock锁可重入、可判断、可公平
5.Lock适合代码量大的情况，synchronized适合代码量少的情况
```
55.synchronized 和 ReentrantLock 区别是什么？

56.说一下 atomic 的原理？

### 四、反射

57.什么是反射？
```
指程序可以访问、检测和修改它本身状态或者行为的一种能力
```
58.什么是 java 序列化？什么情况下需要序列化？
```
对象序列化是java的一个特征，可以将对象写作一组字节码，当在其他位置读到这些字节码时，可以依此创建一个新的对象，而且新对象的状态与原对象完全相同。

1.对象序列化可以实现分布式对象。RMI（远程调用方法）时，利用序列化运行远程主机上的服务，就像在本地机上运行一样
2.java序列化会递归保存对象引用的每个对象的数据--“深复制”：即复制对象本身及引用的对象本身。
```
59.动态代理是什么？有哪些应用？
```
当想给实现了某个接口的类中的方法，加一些额外的处理。例如加日志、事务等。可以给这个类创建一个代理类，不禁包含原来类方法的功能，而且还在原来的基础上添加了额外处理的功能。这个代理类并不是定义好的，是在运行时动态生成的。

Spring的AOP，事务，权限，日志
```
60.怎么实现动态代理？
```
两个重要的类和接口：
InvocationHandler（接口）
Proxy（类）
```
[B站讲解](https://www.bilibili.com/video/av41318523?from=search&seid=9479794230104769697)

### 五、对象拷贝

61.为什么要使用克隆？
```
开发中多个地方需要共同引用和操作一个引用变量，但是引用指向的物理存储堆地址是相同的，操作之间会互相影响。因此需要将操作的对象进行克隆，避免多操作带来的相互影响。
```
62.如何实现对象克隆？
```
1.实现Cloneable接口并重写Object类中的clone()方法；
2.实现Serializable接口，通过对象的序列化和反序列化实现克隆，可以实现真正的深度克隆
```
63.深拷贝和浅拷贝区别是什么？
```
浅拷贝只复制了对象的引用地址；
深拷贝将对象和值复制过来
```
### 六、Java Web

64.jsp 和 servlet 有什么区别？
```
jsp本质就是servlet，
jvm只能识别java类，jsp页面执行时候，web容器将jsp的代码编译成jvm能识别的java类
```
65.jsp 有哪些内置对象？作用分别是什么？
```
1.request        用户端请求
2.response       用户端回应
3.pageContext    网页的属性在这里管理
4.session        与请求有关会话期
5.application    servlet正在执行的内容
6.out           用来传送回应的输出
7.config        servlet的架构部件
8.page          jsp网页本身
9.exception     针对错误网页，未捕捉的除外
```
66.说一下 jsp 的 4 种作用域？
```
application     在所有应用程序中有效
session         在当前会话中有效
request         在当前请求中有效
page            在当前页面有效
```
67.session 和 cookie 有什么区别？
```
1.存储session保存在服务端，cookie保存在客户端
2.cookie保存的数据不能超过4k，session没有大小限制
3.cookie不安全，别人可以分析本地的cookie并进行cookie欺骗。用户登录这种场景应当使用session
4.session会在一定时间内保存在服务器上，会占用服务器的性能，如果并发量大的情况，应当使用cookie
```
68.说一下 session 的工作原理？

69.如果客户端禁止 cookie 能实现 session 还能用吗？

70.spring mvc 和 struts 的区别是什么？

71.如何避免 sql 注入？
```
采用PreparedStatement预编译SQL，PreparedStatement会将sql预先编译好，执行阶段只是把所有的输入内容作为数据处理，不会再对sql语句进行解析。
```
72.什么是 XSS 攻击，如何避免？

73.什么是 CSRF 攻击，如何避免？

### 七、异常

74.throw 和 throws 的区别？
```
throws是用来声明一个方法可能抛出的所有异常信息，放在方法体后面；
throw自己进行异常处理，处理时候有两种方式，要么使用try catch捕捉，要么声明抛出（throws Exception），throw一旦执行，程序会立刻转入异常处理阶段，后面的语句不再执行，并且所在的方法不再返回有意义的值。
```
75.final、finally、finalize 有什么区别？
```
final可以用来修饰类、方法、变量
1.修饰类时候，表示类不能被继承。（final类中所有的成员方法都会隐式的定义为final）
2.修饰方法的时候，继承类无法对其更改
3.修饰变量，只能被赋值一次，无法再更改。

finally
异常处理的一部分，它只能用在try/catch语句块之后，表示这段语句最终一定会被执行（不管是否抛出异常）
并不一定是一定会执行，例如：
![c9a5bc9bcb804bf65c15895ddb240da2.png](evernotecid://2BD76724-DEDE-45A5-B592-69F159394558/appyinxiangcom/23275444/ENResource/p33)


```


76.try-catch-finally 中哪个部分可以省略？

77.try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

78.常见的异常类有哪些？

### 八、网络

79.http 响应码 301 和 302 代表的是什么？有什么区别？

80.forward 和 redirect 的区别？

81.简述 tcp 和 udp的区别？

82.tcp 为什么要三次握手，两次不行吗？为什么？

83.说一下 tcp 粘包是怎么产生的？

84.OSI 的七层模型都有哪些？

85.get 和 post 请求有哪些区别？

86.如何实现跨域？

87.说一下 JSONP 实现原理？

### 九、设计模式

88.说一下你熟悉的设计模式？

89.简单工厂和抽象工厂有什么区别？

### 十、Spring/Spring MVC

90.为什么要使用 spring？

91.解释一下什么是 aop？

92.解释一下什么是 ioc？

93.spring 有哪些主要模块？

94.spring 常用的注入方式有哪些？

95.spring 中的 bean 是线程安全的吗？

96.spring 支持几种 bean 的作用域？

97.spring 自动装配 bean 有哪些方式？

98.spring 事务实现方式有哪些？

99.说一下 spring 的事务隔离？

100.说一下 spring mvc 运行流程？

101.spring mvc 有哪些组件？

102.@RequestMapping 的作用是什么？

103.@Autowired 的作用是什么？

### 十一、Spring Boot/Spring Cloud

104.什么是 spring boot？

105.为什么要用 spring boot？

106.spring boot 核心配置文件是什么？

107.spring boot 配置文件有哪几种类型？它们有什么区别？

108.spring boot 有哪些方式可以实现热部署？

109.jpa 和 hibernate 有什么区别？

110.什么是 spring cloud？

111.spring cloud 断路器的作用是什么？

112.spring cloud 的核心组件有哪些？

### 十二、Hibernate

113.为什么要使用 hibernate？

114.什么是 ORM 框架？

115.hibernate 中如何在控制台查看打印的 sql 语句？

116.hibernate 有几种查询方式？

117.hibernate 实体类可以被定义为 final 吗？

118.在 hibernate 中使用 Integer 和 int 做映射有什么区别？

119.hibernate 是如何工作的？

120.get()和 load()的区别？

121.说一下 hibernate 的缓存机制？

122.hibernate 对象有哪些状态？

123.在 hibernate 中 getCurrentSession 和 openSession 的区别是什么？

124.hibernate 实体类必须要有无参构造函数吗？为什么？

### 十三、Mybatis

125.mybatis 中 #{}和 ${}的区别是什么？

126.mybatis 有几种分页方式？

127.RowBounds 是一次性查询全部结果吗？为什么？

128.mybatis 逻辑分页和物理分页的区别是什么？

129.mybatis 是否支持延迟加载？延迟加载的原理是什么？

130.说一下 mybatis 的一级缓存和二级缓存？

131.mybatis 和 hibernate 的区别有哪些？

132.mybatis 有哪些执行器（Executor）？

133.mybatis 分页插件的实现原理是什么？

134.mybatis 如何编写一个自定义插件？

### 十四、RabbitMQ

135.rabbitmq 的使用场景有哪些？

136.rabbitmq 有哪些重要的角色？

137.rabbitmq 有哪些重要的组件？

138.rabbitmq 中 vhost 的作用是什么？

139.rabbitmq 的消息是怎么发送的？

140.rabbitmq 怎么保证消息的稳定性？

141.rabbitmq 怎么避免消息丢失？

142.要保证消息持久化成功的条件有哪些？

143.rabbitmq 持久化有什么缺点？

144.rabbitmq 有几种广播类型？

145.rabbitmq 怎么实现延迟消息队列？

146.rabbitmq 集群有什么用？

147.rabbitmq 节点的类型有哪些？

148.rabbitmq 集群搭建需要注意哪些问题？

149.rabbitmq 每个节点是其他节点的完整拷贝吗？为什么？

150.rabbitmq 集群中唯一一个磁盘节点崩溃了会发生什么情况？

151.rabbitmq 对集群节点停止顺序有要求吗？

### 十五、Kafka

152.kafka 可以脱离 zookeeper 单独使用吗？为什么？

153.kafka 有几种数据保留的策略？

154.kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 kafka 将如何处理？

155.什么情况会导致 kafka 运行变慢？

156.使用 kafka 集群需要注意什么？

### 十六、Zookeeper

157.zookeeper 是什么？

158.zookeeper 都有哪些功能？

159.zookeeper 有几种部署模式？

160.zookeeper 怎么保证主从节点的状态同步？

161.集群中为什么要有主节点？

162.集群中有 3 台服务器，其中一个节点宕机，这个时候 zookeeper 还可以使用吗？

163.说一下 zookeeper 的通知机制？

### 十七、MySql

164.数据库的三范式是什么？

165.一张自增表里面总共有 7 条数据，删除了最后 2 条数据，重启 mysql 数据库，又插入了一条数据，此时 id 是几？

166.如何获取当前数据库版本？

167.说一下 ACID 是什么？

168.char 和 varchar 的区别是什么？

169.float 和 double 的区别是什么？

170.mysql 的内连接、左连接、右连接有什么区别？

171.mysql 索引是怎么实现的？

172.怎么验证 mysql 的索引是否满足需求？

173.说一下数据库的事务隔离？

174.说一下 mysql 常用的引擎？

175.说一下 mysql 的行锁和表锁？

176.说一下乐观锁和悲观锁？

177.mysql 问题排查都有哪些手段？

178.如何做 mysql 的性能优化？

### 十八、Redis

179.redis 是什么？都有哪些使用场景？

180.redis 有哪些功能？

181.redis 和 memecache 有什么区别？

182.redis 为什么是单线程的？

183.什么是缓存穿透？怎么解决？

184.redis 支持的数据类型有哪些？

185.redis 支持的 java 客户端都有哪些？

186.jedis 和 redisson 有哪些区别？

187.怎么保证缓存和数据库数据的一致性？

188.redis 持久化有几种方式？

189.redis 怎么实现分布式锁？

190.redis 分布式锁有什么缺陷？

191.redis 如何做内存优化？

192.redis 淘汰策略有哪些？

193.redis 常见的性能问题有哪些？该如何解决？

### 十九、JVM

194.说一下 jvm 的主要组成部分？及其作用？

195.说一下 jvm 运行时数据区？

196.说一下堆栈的区别？

197.队列和栈是什么？有什么区别？

198.什么是双亲委派模型？

199.说一下类加载的执行过程？

200.怎么判断对象是否可以被回收？

201.java 中都有哪些引用类型？

202.说一下 jvm 有哪些垃圾回收算法？

203.说一下 jvm 有哪些垃圾回收器？

204.详细介绍一下 CMS 垃圾回收器？

205.新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？

206.简述分代垃圾回收器是怎么工作的？

207.说一下 jvm 调优的工具？

208.常用的 jvm 调优的参数都有哪些？

209.Java创建对象有哪几种方式？

### 二十、Maven

### 二十一、SpringCloud

### 二十二、ES

### 
