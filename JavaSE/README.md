## JavaSE编程基础

![](../image/R-C-1-1.img)

### JDK,JRE,JVM 三者关系？

1.  JDK 是 JAVA 程序开发时用的开发工具包，其内部也有 JRE 运行环境 JRE。
2.  JRE 是 JAVA 程序运行时需要的运行环境，就是说如果你光是运行 JAVA 程序而不是去搞开发的话，只安装 JRE 就能运行已经存在的 JAVA 程序了。
3.  JDk、JRE 内部都包含 JAVA 虚拟机 JVM，JAVA 虚拟机内部包含许多应用程序的类的解释器和类加载器等等。

### 面向过程和面向对象的区别？

1.  两者都是软件开发思想，先有面向过程，后有面向对象。在大型项目中，针对面向过程的不足推出了面向对象开发思想。
2.  编程思路不同：面向过程以实现功能的函数开发为主，而面向对象要首先抽象出类、属性及其方法，然后通过实例化类、执行方法来完成功能。
3.  封装性：都具有封装性，但是面向过程是封装的是功能，而面向对象封装的是数据和功能。面向对象具有继承性和多态性， 而面向过程没有继承性和多态 性，所以面向对象优势是明显。

### Java 有哪些基本数据类型？

定义：Java 语言是强类型语言，对于每一种数据都定义了明确的具体的数据类型，在内存中分配了不同大小的内存空间。

*   数值型：整数类型 (byte,short,int,long)
*   数值型：浮点类型 (float,double)
*   字符型 (char)
*   布尔型 (boolean)

### 什么 Java 注释？

1.  定义：用于解释说明程序的
2.  文字分类：
    *   单行注释：格式： // 注释文字多
    *   行注释：格式： /\* 注释文字 \*/
    *   文档注释：格式：/\*\* 注释文字 \*/
3.  作用：在程序中，尤其是复杂的程序中，适当地加入注释可以增加程序的可读性，有利于程序的修改、调试和交流。注释的内容在程序编译的时候会被忽视，不会产生目标代码，注释的部分不会对程序的执行结果产生任何影响。

注意事项：多行和文档注释都不能嵌套使用。

### 数组和集合有什么区别？

1.  数组的长度是固定的，集合的长度是可变的。
2.  数组中存储的是一种类型的元素，可以存储任意类型数据。
3.  集合存储的都是引用数据类型，如果想存储基本类型数据需要存储对应的包装类型。

### final 有什么用？

用于修饰类、属性和方法；

1.  被 final 修饰的类不可以被继承
2.  被 final 修饰的方法不可以被重写
3.  被 final 修饰的变量不可以被改变，被 final 修饰不可变的是变量的引用，而不是引用指向的内容，引用指向的内容是可以改变的

### final fially finalize 区别

1.  final 可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。
2.  finally 一般作用在 try-catch 代码块中，在处理异常的时候，通常我们将一定要执行的代码方法放在 finally 代码块中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
3.  finalize 是一个方法，属于 Object 类的一个方法，而 Object 类是所有类的父类，该方法一般由垃圾回收器来调用，当我们调用 System.gc () 方法的时候，由垃圾回收器调用 finalize ()，回收垃圾，一个对象是否可回收的最后判断。

### 面向对象三大特性

1.  封装：隐藏对象的属性和实现细节，仅对外提供公共访问方式，将变化隔离，便于使用，提高复用性和安全性。
2.  继承：继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承可以提高代码复用性。继承是多态的前提。
3.  所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量到底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

### == 和 equals 的区别是什么？

1.  == : 它的作用是判断两个对象的地址是不是相等。即判断两个对象是不是同一个对象。(基本数据类型 == 比较的是值，引用数据类型 == 比较的是内存地址)
2.  equals () : 它的作用也是判断两个对象是否相等。但它一般有两种使用情况：
    *   情况 1：类没有覆盖 equals () 方法。则通过 equals () 比较该类的两个对象时，等价于通过 “==” 比较这两个对象。
    *   情况 2：类覆盖了 equals () 方法。一般，我们都覆盖 equals () 方法来两个对象的内容相等；若它们的内容相等，则返回 true (即，认为这两个对象相等)。

### String 类的常用方法都有那些？

1.  indexOf ()：返回指定字符的索引。
2.  charAt ()：返回指定索引处的字符。
3.  replace ()：字符串替换。
4.  trim ()：去除字符串两端空白。
5.  split ()：分割字符串，返回一个分割后的字符串数组。
6.  getBytes ()：返回字符串的 byte 类型数组。
7.  length ()：返回字符串长度。
8.  toLowerCase ()：将字符串转成小写字母。
9.  toUpperCase ()：将字符串转成大写字符。
10.  substring ()：截取字符串。
11.  equals ()：字符串比较。

### String 和 StringBuffer、StringBuilder 的区别是什么？String 为什么是不可变的？

StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

对于三者使用的总结：如果要操作少量的数据用 = String，单线程操作字符串缓冲区 下操作大量数据 = StringBuilder，多线程操作字符串缓冲区 下操作大量数据 = StringBuffer

ChatGPT 的回答：

![](../image/chatgpt.jpg)

### 自动装箱与拆箱

1.  装箱：将基本类型用它们对应的引用类型包装起来；
2.  拆箱：将包装类型转换为基本数据类型；

### int 和 Integer 有什么区别？

Java 是一个近乎纯洁的面向对象编程语言，但是为了编程的方便还是引入了基本数据类型，但是为了能够将这些基本数据类型当成对象操作，Java 为每一个基本数据类型都引入了对应的包装类型（wrapper class），int 的包装类就是 Integer，从 Java 5 开始引入了自动装箱 / 拆箱机制，使得二者可以相互转换。

### Java 为每个原始类型提供了哪些包装类型？

*   原始类型: boolean，char，byte，short，int，long，float，double
*   包装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double

### ArrayList、LinkedList、Vector 的区别？

1.  ArrayList,Vector 底层是由数组实现，LinkedList 底层是由双线链表实现，从底层的实现可以得出它们的性能问题。
2.  ArrayList,Vector 插入速度相对较慢，查询速度相对较快，而 LinkedList 插入速度较快，而查询速度较慢。再者由于 Vevtor 使用了线程安全锁，所以 ArrayList 的运行效率高于 Vector。

### HashMap 和 Hashtable 的区别？

1.  线程是否安全： HashMap 是非线程安全的，HashTable 是线程安全的；HashTable 内部的方法基本都经过 synchronized 修饰。（如果你要保证线程安全的话就使用 ConcurrentHashMap 吧！）；
2.  效率： 因为线程安全的问题，HashMap 要比 HashTable 效率高一点。另外，HashTable 基本被淘汰，不要在代码中使用它；
3.  对 Null key 和 Null value 的支持： HashMap 中，null 可以作为键，这样的键只有一个，可以有一个或多个键所对应的值为 null。但是在 HashTable 中 put 进的键值只要有一个
4.  初始容量大小和每次扩充容量大小的不同 ： ①创建时如果不指定容量初始值，Hashtable 默认的初始大小为 11，之后每次扩充，容量变为原来的 2n+1。HashMap 默认的初始化大小为 16。之后每次扩充，容量变为原来的 2 倍。②创建时如果给定了 容量初始值，那么 Hashtable 会直接使用你给定的大小，而 HashMap 会将其扩充为 2 的幂次方大小。也就是说 HashMap 总是使用 2 的幂作为哈希表的大小
5.  底层数据结构： JDK1.8 以后的 HashMap 在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）时，将链  
    表转化为红黑树，以减少搜索时间。Hashtable 没有这样的机制。

### Synchronized 用过吗，其原理是什么？

1.  Synchronized 是由 JVM 实现的一种实现互斥同步的一种方式，如果你查看被 Synchronized 修饰过的程序块编译后的字节码，会发现被 Synchronized 修饰过的程 序块，在编译前后被编译器生成了 monitorenter 和 monitorexit 两个字节码指令。
2.  这两个指令是什么意思呢？当虚拟机执行到 monitorenter 指令时，首先要尝试获取对象的锁：如果这个对象没有被其他线程锁定，或者当前线程已经拥有了这个对象的锁，那么就将锁的计数器加 1。当执行 monitorexit 指令时，需要释放对象的锁，将锁计数器减 1。
3.  如果获取对象的锁失败，当前线程就会被阻塞等待，直到对象的锁被另外一个线程释放为止。在 Java 中，使用 synchronized 关键字来实现同步操作，它通过在对象头部设置标记来达到获取锁和释放锁的目的。

### 为什么说 Synchronized 是非公平锁？

非公平锁的主要表现在获取锁的行为上，它并不按照申请锁的时间前后给等待线程分配锁，而是每当锁被释放后，任何一个线程都有机会竞争到锁。这样做的目的是为了提高执行性能，但缺点是可能会产生线程饥饿现象。

### 为什么说 Synchronized 是一个悲观锁？乐观锁的实现原理又是什么？什么是 CAS，它有什么特性？

1.  Synchronized 显然是一个悲观锁，因为它的并发策略是悲观的：不管是否会产生竞争，任何的数据操作都必须要加锁、用户态和核心态转换、维护锁计数器和检查是否有被阻塞的线程需要被唤醒等操作。
2.  随着硬件指令集的发展，我们可以使用基于冲突检测的乐观并发策略。先进行操作，如果没有其他线程征用数据，那操作就成功了；如果共享数据被征用，产生了冲突，那就再进行其他的补偿措施。这种乐观的并发策略的许多实现不需要线程挂起，所以被称为非阻塞同步。
3.  乐观锁的核心算法是 CAS（Compare and Swap，比较并交换），它涉及到三个操作数：内存值、期望值、新值。当且仅当期望值和内存值相等时才将内存值修改为新值。这样处理的逻辑是，首先检查某块内存的值是否跟之前我读取时的一样。如果不一样，则表示期间此内存值已经被其他线程更改过，舍弃本次操作；否则说明期间没有其他线程对此内存值操作，可以把新值设置给此块内存。
4.  CAS 具有原子性，它的原子性由 CPU 硬件指令实现保证，即使用 JNI 调用 Native 方法调用由 C++ 编写的硬件级别指令，JDK 中提供了 Unsafe 类执行这些操作

### 乐观锁一定就是好的吗？

乐观锁避免了悲观锁独占对象的现象，同时也提高了并发性能，但它也有缺点：

1.  乐观锁只能保证一个共享变量的原子操作。如果多一个或几个变量，乐观锁将变得力不从心，但互斥锁能轻易解决，不管对象数量多少及对象颗粒度大小。
2.  长时间自旋可能导致开销大。假如 CAS 长时间不成功而一直自旋，会给 CPU 带来很大的开销。
3.  ABA 问题。CAS 的核心思想是通过比对内存值与预期值是否一样而判断内存值是否被改过，但这个判断逻辑不严谨。假如内存值原来是 A，后来被一条线程改为 B，最后又被改成了 A，则 CAS 认为此内存值并没有发生改变，但实际上是有被其他线程改过的。这种情况对依赖过程值的场景的运算结果影响很大。解决的思路是引入版本号，每次变量更新都把版本号加一。