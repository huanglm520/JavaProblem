# Java常见面试题200道
## Java 基础

### 1. JDK 和 JRE 有什么区别？

Jre 是java runtime environment, 是java程序的运行环境。Jdk 是java development kit，是java的开发工具包，里面包含了各种类库和工具。

### 2. == 和 equals 的区别是什么？

==比较的是对象的内存地址，equals比较的是对象的数据内容。

### 3. 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

不对，hashCode()相同，equals()不一定为true；equals()为true，hashCode()一定相同。

### 4. final 在 Java 中有什么作用？

final修饰变量或者对象时，该变量或者对象即为常量；final修饰方法时，该方法不可被重写；final修饰类时，该类不可被继承。

### 5. Java 中的 Math.round(-1.5) 等于多少？

-1，该方法的原理是在参数的基础上加0.5后向下取整。

### 6. String 属于基础的数据类型吗？

不属于，基础数据类型有：byte,short,int,long,float,double,char,boolean。

### 7. Java 中操作字符串都有哪些类？它们之间有什么区别？

String，StringBuilder，StringBuffer以及Java8中新增的StringJoiner。<br>
String是不可变字符串，不能直接修改字符串本身，线程不安全。<br>
StringBuilder是可变字符串，线程不安全。<br>
StringBuffer也是可变字符串，但是线程安全。<br>
StringJoiner是Java8中新增的字符串处理类，可以使用指定的分隔符将字符串连接在一起。

### 8. String str="i"与 String str=new String(“i”)一样吗？

不一样，String str="i"，这里的str指向的是静态区的"i".<br>
String str=new String("i")，这里的str指向了一个新开辟的内存空间，内存空间中保存的数据时字符串"i"，不保存在静态区。

### 9. 如何将字符串反转？

new StringBuilder(str).reverse().toString()或者new StringBuffer(str).reverse().toString()<br>
但是要注意线程安全问题。

### 10. String 类的常用方法都有那些？

1、public String()<br>
无参构造方法，用来创建空字符串的String对象。<br>
 1 String str1 = new String(); <br>
2、public String(String value)<br>
用已知的字符串value创建一个String对象。<br>
 1 String str2 = new String("asdf"); 2 String str3 = new String(str2); <br>
3、public String(char[] value)<br>
用字符数组value创建一个String对象。<br>

1 char[] value = {"a","b","c","d"};<br>
2 String str4 = new String(value);//相当于String str4 = new String("abcd");<br>

4、public String(char chars[], int startIndex, int numChars)<br>
用字符数组chars的startIndex开始的numChars个字符创建一个String对象。<br>

1 char[] value = {"a","b","c","d"};<br>
2 String str5 = new String(value, 1, 2);//相当于String str5 = new String("bc");<br>

5、public String(byte[] values)<br>
用比特数组values创建一个String对象。<br>

1 byte[] strb = new byte[]{65,66};<br>
2 String str6 = new String(strb);//相当于String str6 = new String("AB");<br>
四、String类常用方法<br>
1、求字符串长度<br>
public int length()//返回该字符串的长度<br>

1 String str = new String("asdfzxc");<br>
2 int strlength = str.length();//strlength = 7<br>

2、求字符串某一位置字符<br>
public char charAt(int index)//返回字符串中指定位置的字符；注意字符串中第一个字符索引是0，最后一个是length()-1。<br>

1 String str = new String("asdfzxc");<br>
2 char ch = str.charAt(4);//ch = z<br>

3、提取子串<br>
用String类的substring方法可以提取字符串中的子串，该方法有两种常用参数:<br>
1)public String substring(int beginIndex)//该方法从beginIndex位置起，从当前字符串中取出剩余的字符作为一个新的字符串返回。<br>
2)public String substring(int beginIndex, int endIndex)//该方法从beginIndex位置起，从当前字符串中取出到endIndex-1位置的字符作为一个新的字符串返回。<br>

1 String str1 = new String("asdfzxc");<br>
2 String str2 = str1.substring(2);//str2 = "dfzxc"<br>
3 String str3 = str1.substring(2,5);//str3 = "dfz"<br>

4、字符串比较<br>
1)public int compareTo(String anotherString)//该方法是对字符串内容按字典顺序进行大小比较，通过返回的整数值指明当前字符串与参数字符串的大小关系。若当前对象比参数大则返回正整数，反之返回负整数，相等返回0。<br>
2)public int compareToIgnore(String anotherString)//与compareTo方法相似，但忽略大小写。<br>
3)public boolean equals(Object anotherObject)//比较当前字符串和参数字符串，在两个字符串相等的时候返回true，否则返回false。<br>
4)public boolean equalsIgnoreCase(String anotherString)//与equals方法相似，但忽略大小写。<br>

1 String str1 = new String("abc");<br>
2 String str2 = new String("ABC");<br>
3 int a = str1.compareTo(str2);//a>0<br>
4 int b = str1.compareToIgnoreCase(str2);//b=0<br>
5 boolean c = str1.equals(str2);//c=false<br>
6 boolean d = str1.equalsIgnoreCase(str2);//d=true<br>

5、字符串连接<br>
public String concat(String str)//将参数中的字符串str连接到当前字符串的后面，效果等价于"+"。<br>

1 String str = "aa".concat("bb").concat("cc");<br>
2 相当于String str = "aa"+"bb"+"cc";<br>

6、字符串中单个字符查找<br>
1)public int indexOf(int ch/String str)//用于查找当前字符串中字符或子串，返回字符或子串在当前字符串中从左边起首次出现的位置，若没有出现则返回-1。<br>
2)public int indexOf(int ch/String str, int fromIndex)//改方法与第一种类似，区别在于该方法从fromIndex位置向后查找。<br>
3)public int lastIndexOf(int ch/String str)//该方法与第一种类似，区别在于该方法从字符串的末尾位置向前查找。<br>
4)public int lastIndexOf(int ch/String str, int fromIndex)//该方法与第二种方法类似，区别于该方法从fromIndex位置向前查找。<br>

1 String str = "I am a good student";<br>
2 int a = str.indexOf('a');//a = 2<br>
3 int b = str.indexOf("good");//b = 7<br>
4 int c = str.indexOf("w",2);//c = -1<br>
5 int d = str.lastIndexOf("a");//d = 5<br>
6 int e = str.lastIndexOf("a",3);//e = 2<br>

7、字符串中字符的大小写转换<br>
1)public String toLowerCase()//返回将当前字符串中所有字符转换成小写后的新串<br>
2)public String toUpperCase()//返回将当前字符串中所有字符转换成大写后的新串<br>

1 String str = new String("asDF");<br>
2 String str1 = str.toLowerCase();//str1 = "asdf"<br>
3 String str2 = str.toUpperCase();//str2 = "ASDF"<br>

8、字符串中字符的替换<br>
1)public String replace(char oldChar, char newChar)//用字符newChar替换当前字符串中所有的oldChar字符，并返回一个新的字符串。<br>
2)public String replaceFirst(String regex, String replacement)//该方法用字符replacement的内容替换当前字符串中遇到的第一个和字符串regex相匹配的子串，应将新的字符串返回。<br>
3)public String replaceAll(String regex, String replacement)//该方法用字符replacement的内容替换当前字符串中遇到的所有和字符串regex相匹配的子串，应将新的字符串返回。<br>

1 String str = "asdzxcasd";<br>
2 String str1 = str.replace('a','g');//str1 = "gsdzxcgsd"<br>
3 String str2 = str.replace("asd","fgh");//str2 = "fghzxcfgh"<br>
4 String str3 = str.replaceFirst("asd","fgh");//str3 = "fghzxcasd"<br>
5 String str4 = str.replaceAll("asd","fgh");//str4 = "fghzxcfgh"<br>

9、其他类方法<br>
1)String trim()//截去字符串两端的空格，但对于中间的空格不处理。<br>

1 String str = " a sd ";<br>
2 String str1 = str.trim();<br>
3 int a = str.length();//a = 6<br>
4 int b = str1.length();//b = 4<br>

2)boolean statWith(String prefix)或boolean endWith(String suffix)//用来比较当前字符串的起始字符或子字符串prefix和终止字符或子字符串suffix是否和当前字符串相同，重载方法中同时还可以指定比较的开始位置offset。<br>

1 String str = "asdfgh";<br>
2 boolean a = str.statWith("as");//a = true<br>
3 boolean b = str.endWith("gh");//b = true<br>

3)regionMatches(boolean b, int firstStart, String other, int otherStart, int length)//从当前字符串的firstStart位置开始比较，取长度为length的一个子字符串，other字符串从otherStart位置开始，指定另外一个长度为length的字符串，两字符串比较，当b为true时字符串不区分大小写。<br>
4)contains(String str)//判断参数s是否被包含在字符串中，并返回一个布尔类型的值。<br>

1 String str = "student";<br>
2 str.contains("stu");//true<br>
3 str.contains("ok");//false<br>

5)String[] split(String str)//将str作为分隔符进行字符串分解，分解后的字字符串在字符串数组中返回。<br>

1 String str = "asd!qwe|zxc#";<br>
2 String[] str1 = str.split("!|#");//str1[0] = "asd";str1[1] = "qwe";str1[2] = "zxc";<br>
五、字符串与基本类型的转换<br>
1、字符串转换为基本类型<br>
java.lang包中有Byte、Short、Integer、Float、Double类的调用方法：<br>
1)public static byte parseByte(String s)<br>
2)public static short parseShort(String s)<br>
3)public static short parseInt(String s)<br>
4)public static long parseLong(String s)<br>
5)public static float parseFloat(String s)<br>
6)public static double parseDouble(String s)<br>
例如：<br>

1 int n = Integer.parseInt("12");<br>
2 float f = Float.parseFloat("12.34");<br>
3 double d = Double.parseDouble("1.124");<br>

2、基本类型转换为字符串类型<br>
String类中提供了String valueOf()放法，用作基本类型转换为字符串类型。<br>
1)static String valueOf(char data[])<br>
2)static String valueOf(char data[], int offset, int count)<br>
3)static String valueOf(boolean b)<br>
4)static String valueOf(char c)<br>
5)static String valueOf(int i)<br>
6)static String valueOf(long l)<br>
7)static String valueOf(float f)<br>
8)static String valueOf(double d)<br>
例如：<br>

1 String s1 = String.valueOf(12);<br>
2 String s1 = String.valueOf(12.34);<br>

3、进制转换<br>
使用Long类中的方法得到整数之间的各种进制转换的方法：<br>
Long.toBinaryString(long l)<br>
Long.toOctalString(long l)<br>
Long.toHexString(long l)<br>
Long.toString(long l, int p)//p作为任意进制<br>

### 11. 抽象类必须要有抽象方法吗？

抽象类可以没有抽象方法，但是如果你的一个类已经声明成了抽象类，即使这个类中没有抽象方法，它也不能再实例化，即不能直接构造一个该类的对象。
如果一个类中有了一个抽象方法，那么这个类必须声明为抽象类，否则编译通不过。

### 12. 普通类和抽象类有哪些区别？

1.抽象类不能被实例化。

2.抽象类可以有构造函数，被继承时子类必须继承父类一个构造方法，抽象方法不能被声明为静态。

3.抽象方法只需申明，而无需实现，抽象类中可以允许普通方法有主体

4.含有抽象方法的类必须申明为抽象类

5.抽象的子类必须实现抽象类中所有抽象方法，否则这个子类也是抽象类。

### 13. 抽象类能使用 final 修饰吗？

不能，因为抽象类设计初衷就是一定要被继承的，而final是不允许该类被继承，显然这两个关键字是冲突的。

### 14. 接口和抽象类有什么区别？

1、抽象类和接口都不能直接实例化，如果要实例化，抽象类变量必须指向实现所有抽象方法的子类对象，接口变量必须指向实现所有接口方法的类对象。

2、抽象类要被子类继承，接口要被类实现。

3、接口只能做方法申明，抽象类中可以做方法申明，也可以做方法实现

4、接口里定义的变量只能是公共的静态的常量，抽象类中的变量是普通变量。

5、抽象类里的抽象方法必须全部被子类所实现，如果子类不能全部实现父类抽象方法，那么该子类只能是抽象类。同样，一个实现接口的时候，如不能全部实现接口方法，那么该类也只能为抽象类。

6、抽象方法只能申明，不能实现，接口是设计的结果 ，抽象类是重构的结果

7、抽象类里可以没有抽象方法

8、如果一个类里有抽象方法，那么这个类只能是抽象类

9、抽象方法要被实现，所以不能是静态的，也不能是私有的。

10、接口可继承接口，并可多继承接口，但类只能单根继承。

### 15. Java 中 IO 流分为几种？

按流向分（站在程序角度考虑）

输入流(input)

输出流(output)

按类型分:

字节流(InputStream/OutputStream)

任何文件都可以通过字节流进行传输。

字符流(Reader/Writer)

非纯文本文件，不能用字符流，会导致文件格式破坏，不能正常执行。

节点流(低级流:直接跟输入输出源对接)

FileInputStream/FileOutputStream/FileReader/FileWriter/PrintStream/PrintWriter.

处理流(高级流:建立在低级流的基础上)

转换流：InputStreamReader/OutputStreamWriter，字节流转字符流/字符流转字节流

缓冲流：BufferedInputStream/BufferedOutputStream   BufferedReader/BufferedReader可对节点流经行包装，使读写更快

### 16. BIO、NIO、AIO 有什么区别？

一、BIO

在JDK1.4出来之前，我们建立网络连接的时候采用BIO模式，需要先在服务端启动一个ServerSocket，然后在客户端启动Socket来对服务端进行通信，默认情况下服务端需要对每个请求建立一堆线程等待请求，而客户端发送请求后，先咨询服务端是否有线程相应，如果没有则会一直等待或者遭到拒绝请求，如果有的话，客户端会线程会等待请求结束后才继续执行。

二、NIO

NIO本身是基于事件驱动思想来完成的，其主要想解决的是BIO的大并发问题： 在使用同步I/O的网络应用中，如果要同时处理多个客户端请求，或是在客户端要同时和多个服务器进行通讯，就必须使用多线程来处理。也就是说，将每一个客户端请求分配给一个线程来单独处理。这样做虽然可以达到我们的要求，但同时又会带来另外一个问题。由于每创建一个线程，就要为这个线程分配一定的内存空间（也叫工作存储器），而且操作系统本身也对线程的总数有一定的限制。如果客户端的请求过多，服务端程序可能会因为不堪重负而拒绝客户端的请求，甚至服务器可能会因此而瘫痪。

NIO基于Reactor，当socket有流可读或可写入socket时，操作系统会相应的通知引用程序进行处理，应用再将流读取到缓冲区或写入操作系统。  也就是说，这个时候，已经不是一个连接就要对应一个处理线程了，而是有效的请求，对应一个线程，当连接没有数据时，是没有工作线程来处理的。

BIO与NIO一个比较重要的不同，是我们使用BIO的时候往往会引入多线程，每个连接一个单独的线程；而NIO则是使用单线程或者只使用少量的多线程，每个连接共用一个线程。

三、AIO

与NIO不同，当进行读写操作时，只须直接调用API的read或write方法即可。这两种方法均为异步的，对于读操作而言，当有流可读取时，操作系统会将可读的流传入read方法的缓冲区，并通知应用程序；对于写操作而言，当操作系统将write方法传递的流写入完毕时，操作系统主动通知应用程序。  即可以理解为，read/write方法都是异步的，完成后会主动调用回调函数。

简单来说就是：<br>
BIO是一个连接一个线程。<br>
NIO是一个请求一个线程。<br>
AIO是一个有效请求一个线程。<br>

### 17. Files的常用方法都有哪些？

创建：<br>
createNewFile()在指定位置创建一个空文件，成功就返回true，如果已存在就不创建，然后返回false。<br>
mkdir()  在指定位置创建一个单级文件夹。<br>
mkdirs()  在指定位置创建一个多级文件夹。<br>
renameTo(File dest)如果目标文件与源文件是在同一个路径下，那么renameTo的作用是重命名， 如果目标文件与源文件不是在同一个路径下，那么renameTo的作用就是剪切，而且还不能操作文件夹。 <br>

删除：<br>
delete()  删除文件或者一个空文件夹，不能删除非空文件夹，马上删除文件，返回一个布尔值。<br>
deleteOnExit()jvm退出时删除文件或者文件夹，用于删除临时文件，无返回值。<br>

判断：<br>
exists()  文件或文件夹是否存在。<br>
isFile()  是否是一个文件，如果不存在，则始终为false。<br>
isDirectory()  是否是一个目录，如果不存在，则始终为false。<br>
isHidden()  是否是一个隐藏的文件或是否是隐藏的目录。<br>
isAbsolute()  测试此抽象路径名是否为绝对路径名。<br>

获取：<br>
getName()  获取文件或文件夹的名称，不包含上级路径。<br>
getAbsolutePath()获取文件的绝对路径，与文件是否存在没关系。<br>
length()  获取文件的大小（字节数），如果文件不存在则返回0L，如果是文件夹也返回0L。<br>
getParent()  返回此抽象路径名父目录的路径名字符串；如果此路径名没有指定父目录，则返回null。<br>
lastModified()获取最后一次被修改的时间。<br>

文件夹相关：<br>
static File[] listRoots()列出所有的根目录（Window中就是所有系统的盘符）<br>
list()  返回目录下的文件或者目录名，包含隐藏文件。对于文件这样操作会返回null。<br>
listFiles()  返回目录下的文件或者目录对象（File类实例），包含隐藏文件。对于文件这样操作会返回null。<br>
list(FilenameFilter filter)返回指定当前目录中符合过滤条件的子文件或子目录。对于文件这样操作会返回null。<br>
listFiles(FilenameFilter filter)返回指定当前目录中符合过滤条件的子文件或子目录。对于文件这样操作会返回null。<br>

## 容器

### 18. Java 容器都有哪些？

1. 数组<br>
2. List<br>
3. Set<br>
4. Map<br>
5. Vector<br>

### 19. Collection 和 Collections 有什么区别？

java.util.Collection 是一个集合接口（集合类的一个顶级接口）。它提供了对集合对象进行基本操作的通用接口方法。Collection接口在Java 类库中有很多具体的实现。Collection接口的意义是为各种具体的集合提供了最大化的统一操作方式，其直接继承接口有List与Set。

Collections则是集合类的一个工具类/帮助类，其中提供了一系列静态方法，用于对集合中元素进行排序、搜索以及线程安全等各种操作。

### 20. List、Set、Map 之间的区别是什么？

List(列表)<br>
List的元素以线性方式存储，可以存放重复对象，List主要有以下两个实现类：<br>

ArrayList : 长度可变的数组，可以对元素进行随机的访问，向ArrayList中插入与删除元素的速度慢。 JDK8 中ArrayList扩容的实现是通过grow()方法里使用语句newCapacity = oldCapacity + (oldCapacity >> 1)（即1.5倍扩容）计算容量，然后调用Arrays.copyof()方法进行对原数组进行复制。<br>
LinkedList: 采用链表数据结构，插入和删除速度快，但访问速度慢。<br>

Set(集合)<br>
Set中的对象不按特定(HashCode)的方式排序，并且没有重复对象，Set主要有以下两个实现类：<br>

HashSet： HashSet按照哈希算法来存取集合中的对象，存取速度比较快。当HashSet中的元素个数超过数组大小*loadFactor（默认值为0.75）时，就会进行近似两倍扩容（newCapacity = (oldCapacity << 1) + 1）。<br>
TreeSet ：TreeSet实现了SortedSet接口，能够对集合中的对象进行排序。<br>

Map(映射)<br>
Map是一种把键对象和值对象映射的集合，它的每一个元素都包含一个键对象和值对象。 Map主要有以下两个实现类：<br>

HashMap：HashMap基于散列表实现，其插入和查询<K,V>的开销是固定的，可以通过构造器设置容量和负载因子来调整容器的性能。<br>
LinkedHashMap：类似于HashMap，但是迭代遍历它时，取得<K,V>的顺序是其插入次序，或者是最近最少使用(LRU)的次序。<br>
TreeMap：TreeMap基于红黑树实现。查看<K,V>时，它们会被排序。TreeMap是唯一的带有subMap()方法的Map，subMap()可以返回一个子树。<br>

### 21. HashMap 和 Hashtable 有什么区别？

HashMap和Hashtable的区别

1. HashMap和Hashtable都实现了Map接口，但决定用哪一个之前先要弄清楚它们之间的分别。主要的区别有：线程安全性，同步(synchronization)，以及速度。<br>
2. HashMap几乎可以等价于Hashtable，除了HashMap是非synchronized的，并可以接受null(HashMap可以接受为null的键值(key)和值(value)，而Hashtable则不行)。<br>
3. HashMap是非synchronized，而Hashtable是synchronized，这意味着Hashtable是线程安全的，多个线程可以共享一个Hashtable；而如果没有正确的同步的话，多个线程是不能共享HashMap的。Java 5提供了ConcurrentHashMap，它是HashTable的替代，比HashTable的扩展性更好。<br>
4. 另一个区别是HashMap的迭代器(Iterator)是fail-fast迭代器，而Hashtable的enumerator迭代器不是fail-fast的。所以当有其它线程改变了HashMap的结构（增加或者移除元素），将会抛出ConcurrentModificationException，但迭代器本身的remove()方法移除元素则不会抛出ConcurrentModificationException异常。但这并不是一个一定发生的行为，要看JVM。这条同样也是Enumeration和Iterator的区别。<br>
5. 由于Hashtable是线程安全的也是synchronized，所以在单线程环境下它比HashMap要慢。如果你不需要同步，只需要单一线程，那么使用HashMap性能要好过Hashtable。<br>
6. HashMap不能保证随着时间的推移Map中的元素次序是不变的。<br>

### 22. 如何决定使用 HashMap 还是 TreeMap？

TreeMap<K,V>的Key值是要求实现java.lang.Comparable，所以迭代的时候TreeMap默认是按照Key值升序排序的；TreeMap的实现也是基于红黑树结构。

而HashMap<K,V>的Key值实现散列hashCode(),分布是散列的均匀的，不支持排序；数据结构主要是桶(数组),链表或红黑树。

大多情况下HashMap有更好的性能，所以大多不需要排序的时候我们会使用HashMap.

### 23. 说一下 HashMap 的实现原理？

HashMap的主干是一个Entry数组。Entry是HashMap的基本组成单元，每一个Entry包含一个key-value键值对。<br>

//HashMap的主干数组，可以看到就是一个Entry数组，初始值为空数组{}，主干数组的长度一定是2的次幂，至于为什么这么做，后面会有详细分析。<br>
transient Entry<K,V>[] table = (Entry<K,V>[]) EMPTY_TABLE;<br>
 Entry是HashMap中的一个静态内部类。代码如下<br>
<pre>
    static class Entry&lt;K,V&gt; implements Map.Entry&lt;K,V&gt; {
        final K key;
        V value;
        Entry&lt;K,V&gt; next;//存储指向下一个Entry的引用，单链表结构
        int hash;//对key的hashcode值进行hash运算后得到的值，存储在Entry，避免重复计算

        /**
         * Creates new entry.
         */
        Entry(int h, K k, V v, Entry&lt;K,V&gt; n) {
            value = v;
            next = n;
            key = k;
            hash = h;
        }


 所以，HashMap的整体结构如下

　　简单来说，HashMap由数组+链表组成的，数组是HashMap的主体，链表则是主要为了解决哈希冲突而存在的，如果定位到的数组位置不含链表（当前entry的next指向null）,那么对于查找，添加等操作很快，仅需一次寻址即可；如果定位到的数组包含链表，对于添加操作，其时间复杂度为O(n)，首先遍历链表，存在即覆盖，否则新增；对于查找操作来讲，仍需遍历链表，然后通过key对象的equals方法逐一比对查找。所以，性能考虑，HashMap中的链表出现越少，性能才会越好。

其他几个重要字段//实际存储的key-value键值对的个数 transient int size; //阈值，当table == {}时，该值为初始容量（初始容量默认为16）；当table被填充了，也就是为table分配内存空间后，threshold一般为 capacity*loadFactory。HashMap在进行扩容时需要参考threshold，后面会详细谈到 int threshold; //负载因子，代表了table的填充度有多少，默认是0.75 final float loadFactor; //用于快速失败，由于HashMap非线程安全，在对HashMap进行迭代时，如果期间其他线程的参与导致HashMap的结构发生变化了（比如put，remove等操作），需要抛出异常ConcurrentModificationException transient int modCount;

HashMap有4个构造器，其他构造器如果用户没有传入initialCapacity 和loadFactor这两个参数，会使用默认值

initialCapacity默认为16，loadFactory默认为0.75

我们看下其中一个



public HashMap(int initialCapacity, float loadFactor) {
　　　　　//此处对传入的初始容量进行校验，最大不能超过MAXIMUM_CAPACITY = 1&lt;&lt;30(230)
        if (initialCapacity &lt; 0)
            throw new IllegalArgumentException("Illegal initial capacity: " +
                                               initialCapacity);
        if (initialCapacity > MAXIMUM_CAPACITY)
            initialCapacity = MAXIMUM_CAPACITY;
        if (loadFactor <= 0 || Float.isNaN(loadFactor))
            throw new IllegalArgumentException("Illegal load factor: " +
                                               loadFactor);

        this.loadFactor = loadFactor;
        threshold = initialCapacity;
　　　　　
        init();//init方法在HashMap中没有实际实现，不过在其子类如 linkedHashMap中就会有对应实现
    }


　　从上面这段代码我们可以看出，在常规构造器中，没有为数组table分配内存空间（有一个入参为指定Map的构造器例外），而是在执行put操作的时候才真正构建table数组

　　OK,接下来我们来看看put操作的实现吧



    public V put(K key, V value) {
        //如果table数组为空数组{}，进行数组填充（为table分配实际内存空间），入参为threshold，此时threshold为initialCapacity 默认是1&lt;&lt;4(24=16)
        if (table == EMPTY_TABLE) {
            inflateTable(threshold);
        }
       //如果key为null，存储位置为table[0]或table[0]的冲突链上
        if (key == null)
            return putForNullKey(value);
        int hash = hash(key);//对key的hashcode进一步计算，确保散列均匀
        int i = indexFor(hash, table.length);//获取在table中的实际位置
        for (Entry&lt;K,V&gt; e = table[i]; e != null; e = e.next) {
        //如果该对应数据已存在，执行覆盖操作。用新value替换旧value，并返回旧value
            Object k;
            if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
                V oldValue = e.value;
                e.value = value;
                e.recordAccess(this);
                return oldValue;
            }
        }
        modCount++;//保证并发访问时，若HashMap内部结构发生变化，快速响应失败
        addEntry(hash, key, value, i);//新增一个entry
        return null;
    }    


 先来看看inflateTable这个方法



private void inflateTable(int toSize) {
        int capacity = roundUpToPowerOf2(toSize);//capacity一定是2的次幂
        threshold = (int) Math.min(capacity * loadFactor, MAXIMUM_CAPACITY + 1);//此处为threshold赋值，取capacity*loadFactor和MAXIMUM_CAPACITY+1的最小值，capaticy一定不会超过MAXIMUM_CAPACITY，除非loadFactor大于1
        table = new Entry[capacity];
        initHashSeedAsNeeded(capacity);
    }


　　inflateTable这个方法用于为主干数组table在内存中分配存储空间，通过roundUpToPowerOf2(toSize)可以确保capacity为大于或等于toSize的最接近toSize的二次幂，比如toSize=13,则capacity=16;to_size=16,capacity=16;to_size=17,capacity=32.



 private static int roundUpToPowerOf2(int number) {
        // assert number >= 0 : "number must be non-negative";
        return number >= MAXIMUM_CAPACITY
                ? MAXIMUM_CAPACITY
                : (number > 1) ? Integer.highestOneBit((number - 1) << 1) : 1;
    }


roundUpToPowerOf2中的这段处理使得数组长度一定为2的次幂，Integer.highestOneBit是用来获取最左边的bit（其他bit位为0）所代表的数值.

hash函数



//这是一个神奇的函数，用了很多的异或，移位等运算，对key的hashcode进一步进行计算以及二进制位的调整等来保证最终获取的存储位置尽量分布均匀
final int hash(Object k) {
        int h = hashSeed;
        if (0 != h && k instanceof String) {
            return sun.misc.Hashing.stringHash32((String) k);
        }

        h ^= k.hashCode();

        h ^= (h >>> 20) ^ (h >>> 12);
        return h ^ (h >>> 7) ^ (h >>> 4);
    }


以上hash函数计算出的值，通过indexFor进一步处理来获取实际的存储位置



　　/**
     * 返回数组下标
     */
    static int indexFor(int h, int length) {
        return h & (length-1);
    }


h&（length-1）保证获取的index一定在数组范围内，举个例子，默认容量16，length-1=15，h=18,转换成二进制计算为

        1  0  0  1  0
    &   0  1  1  1  1
    __________________
        0  0  0  1  0    = 2
　　最终计算出的index=2。有些版本的对于此处的计算会使用 取模运算，也能保证index一定在数组范围内，不过位运算对计算机来说，性能更高一些（HashMap中有大量位运算）

所以最终存储位置的确定流程是这样的：



再来看看addEntry的实现：



void addEntry(int hash, K key, V value, int bucketIndex) {
        if ((size >= threshold) && (null != table[bucketIndex])) {
            resize(2 * table.length);//当size超过临界阈值threshold，并且即将发生哈希冲突时进行扩容
            hash = (null != key) ? hash(key) : 0;
            bucketIndex = indexFor(hash, table.length);
        }

        createEntry(hash, key, value, bucketIndex);
    }


　　通过以上代码能够得知，当发生哈希冲突并且size大于阈值的时候，需要进行数组扩容，扩容时，需要新建一个长度为之前数组2倍的新的数组，然后将当前的Entry数组中的元素全部传输过去，扩容后的新数组长度为之前的2倍，所以扩容相对来说是个耗资源的操作。
</pre>

### 24. 说一下 HashSet 的实现原理？

HashSet的实现原理总结如下：

①是基于HashMap实现的，默认构造函数是构建一个初始容量为16，负载因子为0.75 的HashMap。封装了一个 HashMap 对象来存储所有的集合元素，所有放入 HashSet 中的集合元素实际上由 HashMap 的 key 来保存，而 HashMap 的 value 则存储了一个 PRESENT，它是一个静态的 Object 对象。

②当我们试图把某个类的对象当成 HashMap的 key，或试图将这个类的对象放入 HashSet 中保存时，重写该类的equals(Object obj)方法和 hashCode() 方法很重要，而且这两个方法的返回值必须保持一致：当该类的两个的 hashCode() 返回值相同时，它们通过 equals() 方法比较也应该返回 true。通常来说，所有参与计算 hashCode() 返回值的关键属性，都应该用于作为 equals() 比较的标准。

③HashSet的其他操作都是基于HashMap的。

### 25. ArrayList 和 LinkedList 的区别是什么？

ArrayList和Vector使用了数组的实现，可以认为ArrayList或者Vector封装了对内部数组的操作，比如向数组中添加，删除，插入新的元素或者数据的扩展和重定向。

LinkedList使用了循环双向链表数据结构。与基于数组ArrayList相比，这是两种截然不同的实现技术，这也决定了它们将适用于完全不同的工作场景。

LinkedList链表由一系列表项连接而成。一个表项总是包含3个部分：元素内容，前驱表和后驱表。

### 26. 如何实现数组和 List 之间的转换？

List.toArray() 和 Arrays.asList()

### 27. ArrayList 和 Vector 的区别是什么？

1） Vector的方法都是同步的(Synchronized),是线程安全的(thread-safe)，而ArrayList的方法不是，由于线程的同步必然要影响性能，因此,ArrayList的性能比Vector好。<br>
2） 当Vector或ArrayList中的元素超过它的初始大小时,Vector会将它的容量翻倍,而ArrayList只增加50%的大小，这样,ArrayList就有利于节约内存空间。

### 28. Array 和 ArrayList 有何区别？

Array可以包含基本类型和对象类型，ArrayList只能包含对象类型

Array大小固定，ArrayList的大小是动态变化的。

ArrayList提供了更多的方法和特性：比如 ：addAll(),removeAll(),iterator()等等。

对于基本数据类型，集合使用自动装箱来减少编码工作量。但是，当处理固定大小基本数据类型的时候，这种方式相对较慢。

### 29. 在 Queue 中 poll()和 remove()有什么区别？

remove方法和poll方法都是删除队列的头元素，remove方法在队列为空的情况下将抛异常，而poll方法将返回null；

### 30. 哪些集合类是线程安全的？

Vector：就比arraylist多了个同步化机制（线程安全），因为效率较低，现在已经不太建议使用。在web应用中，特别是前台页面，往往效率（页面响应速度）是优先考虑的。

Stack：堆栈类，先进后出

Hashtable：就比hashmap多了个线程安全

Enumeration：枚举，相当于迭代器

### 31. 迭代器 Iterator 是什么？

为了方便的处理集合中的元素,Java中出现了一个对象,该对象提供了一些方法专门处理集合中的元素.例如删除和获取集合中的元素.该对象就叫做迭代器(Iterator).

### 32. Iterator 怎么使用？有什么特点？

1. Iterator遍历集合元素的过程中不允许线程对集合元素进行修改，否则会抛出ConcurrentModificationEception的异常。<br>
2. Iterator遍历集合元素的过程中可以通过remove方法来移除集合中的元素。<br>
3. Iterator必须依附某个Collection对象而存在，Iterator本身不具有装载数据对象的功能。<br>
4. Iterator.remove方法删除的是上一次Iterator.next()方法返回的对象。<br>
5. 强调以下next（）方法，该方法通过游标指向的形式返回Iterator下一个元素。<br>

### 33. Iterator 和 ListIterator 有什么区别？

1. iterator()方法在set和list接口中都有定义，但是ListIterator（）仅存在于list接口中（或实现类中）；<br>
2. ListIterator有add()方法，可以向List中添加对象，而Iterator不能<br>
3. ListIterator和Iterator都有hasNext()和next()方法，可以实现顺序向后遍历，但是ListIterator有hasPrevious()和previous()方法，可以实现逆向（顺序向前）遍历。Iterator就不可以。<br>
4. ListIterator可以定位当前的索引位置，nextIndex()和previousIndex()可以实现。Iterator没有此功能。<br>
5. 都可实现删除对象，但是ListIterator可以实现对象的修改，set()方法可以实现。Iierator仅能遍历，不能修改。<br>

### 34. 怎么确保一个集合不能被修改？

使用Collections.unmodifiable系列方法包装。<br>
Collections.unmodifiableList();<br>
Collections.unmodifiableMap();<br>
Collections.unmodifiableSet();<br>

## 多线程

### 35. 并行和并发有什么区别？

### 36. 线程和进程的区别？

### 37. 守护线程是什么？

### 38. 创建线程有哪几种方式？

### 39. 说一下 runnable 和 callable 有什么区别？

### 40. 线程有哪些状态？

### 41. sleep() 和 wait() 有什么区别？

### 42. notify()和 notifyAll()有什么区别？

### 43. 线程的 run()和 start()有什么区别？

### 44. 创建线程池有哪几种方式？

### 45. 线程池都有哪些状态？

### 46. 线程池中 submit()和 execute()方法有什么区别？

### 47. 在 Java 程序中怎么保证多线程的运行安全？

### 48. 多线程锁的升级原理是什么？

### 49. 什么是死锁？

### 50. 怎么防止死锁？

### 51. ThreadLocal 是什么？有哪些使用场景？

### 52. 说一下 Synchronized 底层实现原理？

### 53. Synchronized 和 volatile 的区别是什么？

### 54. Synchronized 和 Lock 有什么区别？

### 55. Synchronized 和 ReentrantLock 区别是什么？

### 56. 说一下 Atomic 的原理？

## 反射

### 57. 什么是反射？

### 58. 什么是 Java 序列化？什么情况下需要序列化？

### 59. 动态代理是什么？有哪些应用？

### 60. 怎么实现动态代理？

## 对象拷贝

### 61. 为什么要使用克隆？

### 62. 如何实现对象克隆？

### 63. 深拷贝和浅拷贝区别是什么？

## Java Web

### 64. JSP 和 servlet 有什么区别？

### 65. JSP 有哪些内置对象？作用分别是什么？

### 66. 说一下 JSP 的 4 种作用域？

### 67. Session 和 Cookie 有什么区别？

### 68. 说一下 Session 的工作原理？

### 69. 如果客户端禁止 Cookie 能实现 Session 还能用吗？

### 70. Spring MVC 和 Struts 的区别是什么？

### 71. 如何避免 SQL 注入？

### 72. 什么是 XSS 攻击，如何避免？

### 73. 什么是 CSRF 攻击，如何避免？

## 异常

### 74. throw 和 throws 的区别？

### 75. final、finally、finalize 有什么区别？

### 76. try-catch-finally 中哪个部分可以省略？

### 77. try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

### 78. 常见的异常类有哪些？

## 网络

### 79. HTTP 响应码 301 和 302 代表的是什么？有什么区别？

### 80. forward 和 redirect 的区别？

### 81. 简述 TCP 和 UDP 的区别？

### 82. TCP 为什么要三次握手，两次不行吗？为什么？

### 83. 说一下 TCP 粘包是怎么产生的？

### 84. OSI 的七层模型都有哪些？

### 85. Get和 Post 请求有哪些区别？

### 86. 如何实现跨域？

### 87. 说一下 JSONP 实现原理？

## 设计模式

### 88. 说一下你熟悉的设计模式？

### 89. 简单工厂和抽象工厂有什么区别？

## Spring/Spring MVC

### 90. 为什么要使用 Spring？

### 91. 解释一下什么是 AOP？

### 92. 解释一下什么是 IOC？

### 93. Spring 有哪些主要模块？

### 94. Spring 常用的注入方式有哪些？

### 95. Spring 中的 Bean 是线程安全的吗？

### 96. Spring 支持几种 Bean 的作用域？

### 97. Spring 自动装配 Bean 有哪些方式？

### 98. Spring 事务实现方式有哪些？

### 99. 说一下 Spring 的事务隔离？

### 100. 说一下 Spring MVC 运行流程？

### 101. Spring MVC 有哪些组件？

### 102. @RequestMapping 的作用是什么？

### 103. @Autowired 的作用是什么？

## Spring Boot/Spring Cloud

### 104. 什么是 Spring Boot？

### 105. 为什么要用 Spring Boot？

### 106. Spring Boot 核心配置文件是什么？

### 107. Spring Boot 配置文件有哪几种类型？它们有什么区别？

### 108. Spring Boot 有哪些方式可以实现热部署？

### 109. JPA 和 Hibernate 有什么区别？

### 110. 什么是 Spring Cloud？

### 111. Spring Cloud 断路器的作用是什么？

### 112. Spring Cloud 的核心组件有哪些？

## Hibernate

### 113. 为什么要使用 Hibernate？

### 114. 什么是 ORM 框架？

### 115. Hibernate 中如何在控制台查看打印的 SQL 语句？

### 116. Hibernate 有几种查询方式？

### 117. Hibernate 实体类可以被定义为 final 吗？

### 118. 在 Hibernate 中使用 Integer 和 int 做映射有什么区别？

### 119. Hibernate 是如何工作的？

### 120. get()和 load()的区别？

### 121. 说一下 Hibernate 的缓存机制？

### 122. Hibernate 对象有哪些状态？

### 123. 在 Hibernate 中 getCurrentSession 和 openSession 的区别是什么？

### 124. Hibernate 实体类必须要有无参构造函数吗？为什么？

## Mybatis

### 125. Mybatis 中 #{}和 ${}的区别是什么？

### 126. Mybatis 有几种分页方式？

### 127. RowBounds 是一次性查询全部结果吗？为什么？

### 128. Mybatis 逻辑分页和物理分页的区别是什么？

### 129. Mybatis 是否支持延迟加载？延迟加载的原理是什么？

### 130. 说一下 Mybatis 的一级缓存和二级缓存？

### 131. Mybatis 和 Hibernate 的区别有哪些？

### 132. Mybatis 有哪些执行器（Executor）？

### 133. Mybatis 分页插件的实现原理是什么？

### 134. Mybatis 如何编写一个自定义插件？

## RabbitMQ

### 135. RabbitMQ 的使用场景有哪些？

### 136. RabbitMQ 有哪些重要的角色？

### 137. RabbitMQ 有哪些重要的组件？

### 138. RabbitMQ 中 VHost 的作用是什么？

### 139. RabbitMQ 的消息是怎么发送的？

### 140. RabbitMQ 怎么保证消息的稳定性？

### 141. RabbitMQ 怎么避免消息丢失？

### 142. 要保证消息持久化成功的条件有哪些？

### 143. RabbitMQ 持久化有什么缺点？

### 144. RabbitMQ 有几种广播类型？

### 145. RabbitMQ 怎么实现延迟消息队列？

### 146. RabbitMQ 集群有什么用？

### 147. RabbitMQ 节点的类型有哪些？

### 148. RabbitMQ 集群搭建需要注意哪些问题？

### 149. RabbitMQ 每个节点是其他节点的完整拷贝吗？为什么？

### 150. RabbitMQ 集群中唯一一个磁盘节点崩溃了会发生什么情况？

### 151. RabbitMQ 对集群节点停止顺序有要求吗？

## Kafka

### 152. Kafka 可以脱离 ZooKeeper 单独使用吗？为什么？

### 153. Kafka 有几种数据保留的策略？

### 154. Kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 Kafka 将如何处理？

### 155. 什么情况会导致 Kafka 运行变慢？

### 156. 使用 Kafka 集群需要注意什么？

## ZooKeeper

### 157. ZooKeeper 是什么？

### 158. ZooKeeper 都有哪些功能？

### 159. ZooKeeper 有几种部署模式？

### 160. ZooKeeper 怎么保证主从节点的状态同步？

### 161. 集群中为什么要有主节点？

### 162. 集群中有 3 台服务器，其中一个节点宕机，这个时候 ZooKeeper 还可以使用吗？

### 163. 说一下 ZooKeeper  的通知机制？

## MySQL

### 164. 数据库的三范式是什么？

### 165. 一张自增表里面总共有 7 条数据，删除了最后 2 条数据，重启 MySQL 数据库，又插入了一条数据，此时 ID 是几？

### 166. 如何获取当前数据库版本？

### 167. 说一下 ACID 是什么？

### 168. Char 和 VarChar 的区别是什么？

### 169. Float 和 Double 的区别是什么？

### 170. MySQL 的内连接、左连接、右连接有什么区别？

### 171. MySQL索引是怎么实现的？

### 172. 怎么验证 MySQL的索引是否满足需求？

### 173. 说一下数据库的事务隔离？

### 174. 说一下 MySQL常用的引擎？

### 175. 说一下 MySQL的行锁和表锁？

### 176. 说一下乐观锁和悲观锁？

### 177. MySQL问题排查都有哪些手段？

### 178. 如何做 MySQL的性能优化？

## Redis

### 179. Redis 是什么？都有哪些使用场景？

### 180. Redis 有哪些功能？

### 181. Redis 和 MemeCache 有什么区别？

### 182. Redis 为什么是单线程的？

### 183. 什么是缓存穿透？怎么解决？

### 184. Redis 支持的数据类型有哪些？

### 185. Redis 支持的 Java 客户端都有哪些？

### 186. Jedis 和 Redisson 有哪些区别？

### 187. 怎么保证缓存和数据库数据的一致性？

### 188. Redis 持久化有几种方式？

### 189. Redis 怎么实现分布式锁？

### 190. Redis 分布式锁有什么缺陷？

### 191. Redis 如何做内存优化？

### 192. Redis 淘汰策略有哪些？

### 193. Redis 常见的性能问题有哪些？该如何解决？

## JVM

### 194. 说一下 JVM 的主要组成部分？及其作用？

### 195. 说一下 JVM 运行时数据区？

### 196. 说一下堆栈的区别？

### 197. 队列和栈是什么？有什么区别？

### 198. 什么是双亲委派模型？

### 199. 说一下类加载的执行过程？

### 200. 怎么判断对象是否可以被回收？

### 201. Java 中都有哪些引用类型？

### 202. 说一下 JVM 有哪些垃圾回收算法？

### 203. 说一下 JVM 有哪些垃圾回收器？

### 204. 详细介绍一下 CMS 垃圾回收器？

### 205. 新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？

### 206. 简述分代垃圾回收器是怎么工作的？

### 207. 说一下 JVM 调优的工具？

### 208. 常用的 JVM 调优的参数都有哪些？
