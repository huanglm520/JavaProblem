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

所有的并发处理都有排队等候，唤醒，执行至少三个这样的步骤.所以并发肯定是宏观概念，在微观上他们都是序列被处理的，只不过资源不会在某一个上被阻塞(一般是通过时间片轮转)，所以在宏观上看多个几乎同时到达的请求同时在被处理。如果是同一时刻到达的请求也会根据优先级的不同，而先后进入队列排队等候执行。

并发与并行是两个既相似而又不相同的概念：并发性，又称共行性，是指能处理多个同时性活动的能力；并行是指同时发生的两个并发事件，具有并发的含义，而并发则不一定并行，也亦是说并发事件之间不一定要同一时刻发生。

并发的实质是一个物理CPU(也可以多个物理CPU) 在若干道程序之间多路复用，并发性是对有限物理资源强制行使多用户共享以提高效率。 并行性指两个或两个以上事件或活动在同一时刻发生。在多道程序环境下，并行性使多个程序同一时刻可在不同CPU上同时执行。

并发，是在同一个cpu上同时（不是真正的同时，而是看来是同时，因为cpu要在多个程序间切换）运行多个程序。

并发

并行，是每个cpu运行一个程序。

简而言之就是并发是多个事件在同一时间段执行，而并行是多个事件在同一时间点执行。

### 36. 线程和进程的区别？

第一：因为进程拥有独立的堆栈空间和数据段，所以每当启动一个新的进程必须分配给它独立的地址空间，建立众多的数据表来维护它的代码段、堆栈段和数据段，这对于多进程来说十分“奢侈”，系统开销比较大，而线程不一样，线程拥有独立的堆栈空间，但是共享数据段，它们彼此之间使用相同的地址空间，共享大部分数据，比进程更节俭，开销比较小，切换速度也比进程快，效率高，但是正由于进程之间独立的特点，使得进程安全性比较高，也因为进程有独立的地址空间，一个进程崩溃后，在保护模式下不会对其它进程产生影响，而线程只是一个进程中的不同执行路径。一个线程死掉就等于整个进程死掉。

第二：体现在通信机制上面，正因为进程之间互不干扰，相互独立，进程的通信机制相对很复杂，譬如管道，信号，消息队列，共享内存，套接字等通信机制，而线程由于共享数据段所以通信机制很方便。。

第三：属于同一个进程的所有线程共享该进程的所有资源，包括文件描述符。而不同过的进程相互独立。

第四：线程又称为轻量级进程，进程有进程控制块，线程有线程控制块；

第五：线程必定也只能属于一个进程，而进程可以拥有多个线程而且至少拥有一个线程；

第六：体现在程序结构上，举一个简明易懂的列子：当我们使用进程的时候，我们不自主的使用if else嵌套来判断pid，使得程序结构繁琐，但是当我们使用线程的时候，基本上可以甩掉它，当然程序内部执行功能单元需要使用的时候还是要使用，所以线程对程序结构的改善有很大帮助。

### 37. 守护线程是什么？

守护线程（即daemon thread），是个服务线程，准确地来说就是服务其他的线程，这是它的作用

### 38. 创建线程有哪几种方式？

一、继承Thread类创建线程类

（1）定义Thread类的子类，并重写该类的run方法，该run方法的方法体就代表了线程要完成的任务。因此把run()方法称为执行体。

（2）创建Thread子类的实例，即创建了线程对象。

（3）调用线程对象的start()方法来启动该线程。

<pre>
package com.thread;
 
public class FirstThreadTest extends Thread{
	int i = 0;
	//重写run方法，run方法的方法体就是现场执行体
	public void run()
	{
		for(;i&lt;100;i++){
		System.out.println(getName()+"  "+i);
		
		}
	}
	public static void main(String[] args)
	{
		for(int i = 0;i< 100;i++)
		{
			System.out.println(Thread.currentThread().getName()+"  : "+i);
			if(i==20)
			{
				new FirstThreadTest().start();
				new FirstThreadTest().start();
			}
		}
	}
 
}
</pre>

上述代码中Thread.currentThread()方法返回当前正在执行的线程对象。GetName()方法返回调用该方法的线程的名字。

二、通过Runnable接口创建线程类

（1）定义runnable接口的实现类，并重写该接口的run()方法，该run()方法的方法体同样是该线程的线程执行体。

（2）创建 Runnable实现类的实例，并依此实例作为Thread的target来创建Thread对象，该Thread对象才是真正的线程对象。

（3）调用线程对象的start()方法来启动该线程。

示例代码为：

<pre>
package com.thread;
 
public class RunnableThreadTest implements Runnable
{
 
	private int i;
	public void run()
	{
		for(i = 0;i &lt;100;i++)
		{
			System.out.println(Thread.currentThread().getName()+" "+i);
		}
	}
	public static void main(String[] args)
	{
		for(int i = 0;i < 100;i++)
		{
			System.out.println(Thread.currentThread().getName()+" "+i);
			if(i==20)
			{
				RunnableThreadTest rtt = new RunnableThreadTest();
				new Thread(rtt,"新线程1").start();
				new Thread(rtt,"新线程2").start();
			}
		}
 
	}
 
}
</pre>

三、通过Callable和Future创建线程

（1）创建Callable接口的实现类，并实现call()方法，该call()方法将作为线程执行体，并且有返回值。

（2）创建Callable实现类的实例，使用FutureTask类来包装Callable对象，该FutureTask对象封装了该Callable对象的call()方法的返回值。

（3）使用FutureTask对象作为Thread对象的target创建并启动新线程。

（4）调用FutureTask对象的get()方法来获得子线程执行结束后的返回值

实例代码：

<pre>
package com.thread;
 
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;
 
public class CallableThreadTest implements Callable&lt;Integer&gt;
{
 
	public static void main(String[] args)
	{
		CallableThreadTest ctt = new CallableThreadTest();
		FutureTask&lt;Integer&gt; ft = new FutureTask<>(ctt);
		for(int i = 0;i < 100;i++)
		{
			System.out.println(Thread.currentThread().getName()+" 的循环变量i的值"+i);
			if(i==20)
			{
				new Thread(ft,"有返回值的线程").start();
			}
		}
		try
		{
			System.out.println("子线程的返回值："+ft.get());
		} catch (InterruptedException e)
		{
			e.printStackTrace();
		} catch (ExecutionException e)
		{
			e.printStackTrace();
		}
 
	}
 
	@Override
	public Integer call() throws Exception
	{
		int i = 0;
		for(;i&lt;100;i++)
		{
			System.out.println(Thread.currentThread().getName()+" "+i);
		}
		return i;
	}
 
}
</pre>

二、创建线程的三种方式的对比

采用实现Runnable、Callable接口的方式创见多线程时，优势是：

线程类只是实现了Runnable接口或Callable接口，还可以继承其他类。

在这种方式下，多个线程可以共享同一个target对象，所以非常适合多个相同线程来处理同一份资源的情况，从而可以将CPU、代码和数据分开，形成清晰的模型，较好地体现了面向对象的思想。

劣势是：

编程稍微复杂，如果要访问当前线程，则必须使用Thread.currentThread()方法。

使用继承Thread类的方式创建多线程时优势是：

编写简单，如果需要访问当前线程，则无需使用Thread.currentThread()方法，直接使用this即可获得当前线程。

劣势是：

线程类已经继承了Thread类，所以不能再继承其他父类。


### 39. 说一下 runnable 和 callable 有什么区别？

相同点：

两者都是接口；<br>
两者都可用来编写多线程程序；<br>
两者都需要调用Thread.start()启动线程；<br>

不同点：

两者最大的不同点是：实现Callable接口的任务线程能返回执行结果；而实现Runnable接口的任务线程不能返回结果；<br>
Callable接口的call()方法允许抛出异常；而Runnable接口的run()方法的异常只能在内部消化，不能继续上抛；<br>

注意点：

Callable接口支持返回执行结果，此时需要调用FutureTask.get()方法实现，此方法会阻塞主线程直到获取‘将来’结果；当不调用此方法时，主线程不会阻塞！

### 40. 线程有哪些状态？

1.新建状态<br>
当用new操作符创建一个线程时。此时程序还没有开始运行线程中的代码。<br>

2.就绪状态<br>
一个新创建的线程并不自动开始运行，要执行线程，必须调用线程的start()方法。当线程对象调用start()方法即启动了线程，start()方法创建线程运行的系统资源，并调度线程运行run()方法。当start()方法返回后，线程就处于就绪状态。<br>

处于就绪状态的线程并不一定立即运行run()方法，线程还必须同其他线程竞争CPU时间，只有获得CPU时间才可以运行线程。因为在单CPU的计算机系统中，不可能同时运行多个线程，一个时刻仅有一个线程处于运行状态。因此此时可能有多个线程处于就绪状态。对多个处于就绪状态的线程是由Java运行时系统的线程调度程序来调度的。<br>

3.运行状态（running）<br>
当线程获得CPU时间后，它才进入运行状态，真正开始执行run()方法。<br>

4.阻塞状态（blocked）<br>
线程运行过程中，可能由于各种原因进入阻塞状态：<br>

①线程通过调用sleep方法进入睡眠状态；<br>

②线程调用一个在I/O上被阻塞的操作，即该操作在输入输出操作完成之前不会返回到它的调用者；<br>

③线程试图得到一个锁，而该锁正被其他线程持有；<br>

④线程在等待某个触发条件；<br>

所谓阻塞状态是正在运行的线程没有运行结束，暂时让出CPU，这时其他处于就绪状态的线程就可以获得CPU时间，进入运行状态。<br>

5.死亡状态（dead）<br>
有两个原因会导致线程死亡：<br>

①run方法正常退出而自然死亡；<br>

②一个未捕获的异常终止了run方法而使线程猝死；<br>

为了确定线程在当前是否存活着（就是要么是可运行的，要么是被阻塞了），需要使用isAlive方法，如果是可运行或被阻塞，这个方法返回true；如果线程仍旧是new状态且不是可运行的，或者线程死亡了，则返回false。<br>

### 41. sleep() 和 wait() 有什么区别？

对于sleep()方法，我们首先要知道该方法是属于Thread类中的。而wait()方法，则是属于Object类中的。

sleep()方法导致了程序暂停执行指定的时间，让出cpu该其他线程，但是他的监控状态依然保持者，当指定的时间到了又会自动恢复运行状态。

在调用sleep()方法的过程中，线程不会释放对象锁。

而当调用wait()方法的时候，线程会放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象调用notify()方法后本线程才进入对象锁定池准备。

### 42. notify()和 notifyAll()有什么区别？

如果线程调用了对象的 wait()方法，那么线程便会处于该对象的等待池中，等待池中的线程不会去竞争该对象的锁。

当有线程调用了对象的 notifyAll()方法（唤醒所有 wait 线程）或 notify()方法（只随机唤醒一个 wait 线程），被唤醒的的线程便会进入该对象的锁池中，锁池中的线程会去竞争该对象锁。也就是说，调用了notify后只要一个线程会由等待池进入锁池，而notifyAll会将该对象等待池内的所有线程移动到锁池中，等待锁竞争。

优先级高的线程竞争到对象锁的概率大，假若某线程没有竞争到该对象锁，它还会留在锁池中，唯有线程再次调用 wait()方法，它才会重新回到等待池中。而竞争到对象锁的线程则继续往下执行，直到执行完了 synchronized 代码块，它会释放掉该对象锁，这时锁池中的线程会继续竞争该对象锁。


### 43. 线程的 run()和 start()有什么区别？

每个线程都有要执行的任务。线程的任务处理逻辑可以在Tread类的run实例方法中直接实现或通过该方法进行调用，因此

run()相当于线程的任务处理逻辑的入口方法，它由Java虚拟机在运行相应线程时直接调用，而不是由应用代码进行调用。

而start()的作用是启动相应的线程。启动一个线程实际是请求Java虚拟机运行相应的线程，而这个线程何时能够运行是由线程调度器决定的。start()调用结束并不表示相应线程已经开始运行，这个线程可能稍后运行，也可能永远也不会运行。

### 44. 创建线程池有哪几种方式？

newSingleThreadExecutor<br>
创建一个单线程的线程池。这个线程池只有一个线程在工作，也就是相当于单线程串行执行所有任务。如果这个唯一的线程因为异常结束，那么会有一个新的线程来替代它。此线程池保证所有任务的执行顺序按照任务的提交顺序执行。<br>

newFixedThreadPool<br>
创建固定大小的线程池。每次提交一个任务就创建一个线程，直到线程达到线程池的最大大小。线程池的大小一旦达到最大值就会保持不变，如果某个线程因为执行异常而结束，那么线程池会补充一个新线程。<br>

newCachedThreadPool<br>
创建一个可缓存的线程池。如果线程池的大小超过了处理任务所需要的线程，那么就会回收部分空闲（60秒不执行任务）的线程，当任务数增加时，此线程池又可以智能的添加新线程来处理任务。此线程池不会对线程池大小做限制，线程池大小完全依赖于操作系统（或者说JVM）能够创建的最大线程大小。<br>

newScheduledThreadPool<br>
创建一个大小无限的线程池。此线程池支持定时以及周期性执行任务的需求。<br>

### 45. 线程池都有哪些状态？

1、RUNNING

(1) 状态说明：线程池处在RUNNING状态时，能够接收新任务，以及对已添加的任务进行处理。 <br>
(2) 状态切换：线程池的初始化状态是RUNNING。换句话说，线程池被一旦被创建，就处于RUNNING状态，并且线程池中的任务数为0！<br>

2、 SHUTDOWN

(1) 状态说明：线程池处在SHUTDOWN状态时，不接收新任务，但能处理已添加的任务。 <br>
(2) 状态切换：调用线程池的shutdown()接口时，线程池由RUNNING -> SHUTDOWN。<br>

3、STOP

(1) 状态说明：线程池处在STOP状态时，不接收新任务，不处理已添加的任务，并且会中断正在处理的任务。 <br>
(2) 状态切换：调用线程池的shutdownNow()接口时，线程池由(RUNNING or SHUTDOWN ) -> STOP。<br>

4、TIDYING

(1) 状态说明：当所有的任务已终止，ctl记录的”任务数量”为0，线程池会变为TIDYING状态。当线程池变为TIDYING状态时，会执行钩子函数terminated()。terminated()在ThreadPoolExecutor类中是空的，若用户想在线程池变为TIDYING时，进行相应的处理；可以通过重载terminated()函数来实现。 <br>
(2) 状态切换：当线程池在SHUTDOWN状态下，阻塞队列为空并且线程池中执行的任务也为空时，就会由 SHUTDOWN -> TIDYING。 <br>
当线程池在STOP状态下，线程池中执行的任务为空时，就会由STOP -> TIDYING。<br>

5、 TERMINATED

(1) 状态说明：线程池彻底终止，就变成TERMINATED状态。 <br>
(2) 状态切换：线程池处在TIDYING状态时，执行完terminated()之后，就会由 TIDYING -> TERMINATED。<br>

### 46. 线程池中 submit()和 execute()方法有什么区别？

1、接收的参数不一样

2、submit有返回值，而execute没有

用到返回值的例子，比如说我有很多个做validation的task，我希望所有的task执行完，然后每个task告诉我它的执行结果，是成功还是失败，如果是失败，原因是什么。然后我就可以把所有失败的原因综合起来发给调用者。

3、submit方便Exception处理
意思就是如果你在你的task里会抛出checked或者unchecked exception，而你又希望外面的调用者能够感知这些exception并做出及时的处理，那么就需要用到submit，通过捕获Future.get抛出的异常。

### 47. 在 Java 程序中怎么保证多线程的运行安全？

java的同步机制，大概是通过:

1.synchronized；<br>
2.Object方法中的wait,notify；<br>
3.ThreadLocal机制<br>

其中synchronized有两种用法:<br>

1.对类的方法进行修饰<br>
2.synchronized(对象）的方法进行修饰<br>

或者可以使用线程安全的包装类

### 48. 多线程锁的升级原理是什么？（这部分有点乱，有时间好好整理一下）

因为Sycronized是重量级锁（也是悲观锁），每次在要进行锁的请求的时候，如果当前资源被其他线程占有要将当前的线程阻塞加入到阻塞队列，然后清空当前线程的缓存，等到锁释放的时候再通过notify或者notifyAll唤醒当前的线程，并让其处于就绪状态。这样线程的来回切换是非常消耗系统资源的，而且有的时候，线程刚挂起资源就释放了。而Java的线程是映射到操作系统的原生线程之上的每次线程的阻塞或者唤醒都要经过用户态到核心态或者核心态到用户态的转化，这样是十分浪费资源的，这样就会造成性能上的降低，因此JVM对Sychronized进行了优化，将Sycronized分为三种锁的级别：偏向锁，轻量级锁，重量级锁。 <br>
很多的时候，对于一个可能发生并发访问的对象而言，其实很少会被竞争，就算有些资源存在竞争也是在很少的一段时间资源就会被释放，而这样的情况下将线程挂起是十分浪费性能的。 <br>

偏向锁（乐观锁）： <br>
当锁对象第一次被线程获取的时候，虚拟机会将锁对象的对象头中的锁标志位设置成为01，并将偏向锁标志设置为1，线程通过CAS的方式将自己的ID值放置到对象头中（因为在这个过程中有可能会有其他线程来竞争锁，所以要通过CAS的方式，一旦有竞争就会升级为轻量级锁了），如果成功线程就获得了该轻量级锁。这样每次再进入该锁对象的时候不用进行任何的同步操作，直接比较当前锁对象的对象头是不是该线程的ID，如果是就可以直接进入。<br>

偏向锁升级为轻量级锁 <br>
偏向锁是一种无竞争锁，一旦出现了竞争大多数情况下就会升级为轻量级锁。现在我们假设有线程1持有偏向锁，线程2来竞争偏向锁会经历以下几个过程：<br> 
1. 首先线程2会先检查偏向锁标记，如果是1，说明当前是偏向锁，那么JVM会找到线程1，看线程1是否还存活着2 <br>
2. 如果线程1已经执行完毕，就是说线程1不存在了（线程1自己是不会去释放偏向锁的），那么先将偏向锁置为0，对象头设置成为无锁的状态，用CAS的方式尝试将线程2的ID放入对象头中，不进行锁升级，还是偏向锁 <br>
3. 如果线程1还活着，先暂停线程1，将锁标志位变成00（轻量级锁）然后在线程1的栈帧中开辟出一块空间（Display Mark Word）将对象头的Mark Word置换到线程一的栈帧当中，而对象头中此时存储的是指向当前线程栈帧的指针。此时就变成了轻量级锁。继续执行线程1，然后线程2采用CAS的方式尝试获取锁。<br>

轻量级锁与偏向锁最大的不同之处 <br>
轻量级锁和偏向锁的不同之处就在于轻量级锁对于获取锁对象采用CAS的同步方式而偏向锁直接是把整个同步过程给取消。<br>

轻量级锁(乐观锁) <br>
轻量级锁如何创建在上面已经讲过了，接下来说说轻量级锁如何获取锁对象，轻量级锁是通过CAS也就是自旋的方式尝试获取锁对象，一旦失败会先检查，对象头中存储的是否是指向当前线程栈帧的指针，如果是，就可以获取对象，如果不是说明存在竞争那么就要膨胀为重量级锁。轻量级锁的解锁也是通过CAS的方式尝试将对象头的Mark Word和线程中的Display Mark Word替换回来，如果成功，就释放锁，如果失败说明还有许多其他等待锁的线程（说明此时已经不是轻量级锁而是重量级锁了），会将这些线程唤醒，然后释放锁。<br>

轻量级锁膨胀为重量级锁 <br>
一旦有两条以上的线程竞争锁，轻量级锁膨胀为重量级锁，锁的状态变成10，此时对象头中存储的就是指向重量级锁的栈帧的指针。而且其他等待锁的线程要进入阻塞状态，等待重量级锁释放再来被唤醒然后去竞争。<br>

### 49. 什么是死锁？

线程死锁是指由于两个或者多个线程互相持有对方所需要的资源，导致这些线程处于等待状态，无法前往执行。当线程进入对象的synchronized代码块时，便占有了资源，直到它退出该代码块或者调用wait方法，才释放资源，在此期间，其他线程将不能进入该代码块。当线程互相持有对方所需要的资源时，会互相等待对方释放资源，如果线程都不主动释放所占有的资源，将产生死锁。

当然死锁的产生是必须要满足一些特定条件的： <br>
1.互斥条件：进程对于所分配到的资源具有排它性，即一个资源只能被一个进程占用，直到被该进程释放 <br>
2.请求和保持条件：一个进程因请求被占用资源而发生阻塞时，对已获得的资源保持不放。 <br>
3.不剥夺条件：任何一个资源在没被该进程释放之前，任何其他进程都无法对他剥夺占用 <br>
4.循环等待条件：当发生死锁时，所等待的进程必定会形成一个环路（类似于死循环），造成永久阻塞。<br>

### 50. 怎么防止死锁？

在有些情况下死锁是可以避免的。本文将展示三种用于避免死锁的技术：

1. 加锁顺序
2. 加锁时限
3. 死锁检测

### 51. ThreadLocal 是什么？有哪些使用场景？

翻译过来中文意思就叫线程局部变量（thread local variable）,就是为每个线程都创建一个这样的变量(以ThreadLocal对象为键、任意对象为值的存储结构),这个变量被附带在线程上,每个线程之接相互隔离,互不干扰,该变量副本只能创建它的线程能使用。

当某一个类的对象需要针对每一个线程都创建一个副本时可以考虑使用。

### 52. 说一下 Synchronized 底层实现原理？（这个答案可能不太准确，有时间完善一下）

每个对象有一个监视器锁（monitor）。当monitor被占用时就会处于锁定状态，线程执行monitorenter指令时尝试获取monitor的所有权，过程如下：

1、如果monitor的进入数为0，则该线程进入monitor，然后将进入数设置为1，该线程即为monitor的所有者。

2、如果线程已经占有该monitor，只是重新进入，则进入monitor的进入数加1.

3.如果其他线程已经占用了monitor，则该线程进入阻塞状态，直到monitor的进入数为0，再重新尝试获取monitor的所有权。

执行monitorexit的线程必须是objectref所对应的monitor的所有者。

指令执行时，monitor的进入数减1，如果减1后进入数为0，那线程退出monitor，不再是这个monitor的所有者。其他被这个monitor阻塞的线程可以尝试去获取这个 monitor 的所有权。 

### 53. Synchronized 和 volatile 的区别是什么？

1. volatile本质是在告诉jvm当前变量在寄存器（工作内存）中的值是不确定的，需要从主存中读取； synchronized则是锁定当前变量，只有当前线程可以访问该变量，其他线程被阻塞住。<br>
2. volatile仅能使用在变量级别；synchronized则可以使用在变量、方法、和类级别的<br>
3. volatile仅能实现变量的修改可见性，不能保证原子性；而synchronized则可以保证变量的修改可见性和原子性<br>
4. volatile不会造成线程的阻塞；synchronized可能会造成线程的阻塞。<br>
5. volatile标记的变量不会被编译器优化；synchronized标记的变量可以被编译器优化<br>

### 54. Synchronized 和 Lock 有什么区别？

1. 首先synchronized是java内置关键字，在jvm层面，Lock是个java类；<br>
2. synchronized无法判断是否获取锁的状态，Lock可以判断是否获取到锁；<br>
3. synchronized会自动释放锁(a 线程执行完同步代码会释放锁 ；b 线程执行过程中发生异常会释放锁)，Lock需在finally中手工释放锁（unlock()方法释放锁），否则容易造成线程死锁；<br>
4. 用synchronized关键字的两个线程1和线程2，如果当前线程1获得锁，线程2线程等待。如果线程1阻塞，线程2则会一直等待下去，而Lock锁就不一定会等待下去，如果尝试获取不到锁，线程可以不用一直等待就结束了；<br>
5. synchronized的锁可重入、不可中断、非公平，而Lock锁可重入、可判断、可公平（两者皆可）<br>
6. Lock锁适合大量同步的代码的同步问题，synchronized锁适合代码少量的同步问题。<br>

### 55. Synchronized 和 ReentrantLock 区别是什么？

这两种方式最大区别就是对于Synchronized来说，它是java语言的关键字，是原生语法层面的互斥，需要jvm实现。而ReentrantLock它是JDK1.5之后提供的API层面的互斥锁，需要lock()和unlock()方法配合try/finally语句块来完成。

### 56. 说一下 Atomic 的原理？

Atomic包中的类基本的特性就是在多线程环境下，当有多个线程同时对单个（包括基本类型及引用类型）变量进行操作时，具有排他性，即当多个线程同时对该变量的值进行更新时，仅有一个线程能成功，而未成功的线程可以向自旋锁一样，继续尝试，一直等到执行成功。

## 反射

### 57. 什么是反射？

Java反射就是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意方法和属性；并且能改变它的属性。而这也是Java被视为动态（或准动态，为啥要说是准动态，因为一般而言的动态语言定义是程序运行时，允许改变程序结构或变量类型，这种语言称为动态语言。

### 58. 什么是 Java 序列化？什么情况下需要序列化？

序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化,将数据分解成字节流，以便存储在文件中或在网络上传输。

### 59. 动态代理是什么？有哪些应用？

动态代理：当想要给实现了某个接口的类中的方法，加一些额外的处理。比如说加日志，加事务等。可以给这个类创建一个代理，故名思议就是创建一个新的类，这个类不仅包含原来类方法的功能，而且还在原来的基础上添加了额外处理的新类。这个代理类并不是定义好的，是动态生成的。具有解耦意义，灵活，扩展性强。

动态代理的应用：Spring的AOP，加事务，加权限，加日志。

### 60. 怎么实现动态代理？

动态代理实现：首先必须定义一个接口，还要有一个InvocationHandler(将实现接口的类的对象传递给它)处理类。再有一个工具类Proxy(习惯性将其称为代理类，因为调用他的newInstance()可以产生代理对象,其实他只是一个产生代理对象的工具类）。利用到InvocationHandler，拼接代理类源码，将其编译生成代理类的二进制码，利用加载器加载，并将其实例化产生代理对象，最后返回。

## 对象拷贝

### 61. 为什么要使用克隆？

想对一个对象进行处理，又想保留原有的数据进行接下来的操作，就需要克隆了.

### 62. 如何实现对象克隆？

可以用反射的方式或序列化的方式实现。

### 63. 深拷贝和浅拷贝区别是什么？

克隆分浅克隆和深克隆，浅克隆后的对象中非基本对象和原对象指向同一块内存，因此对这些非基本对象的修改会同时更改克隆前后的对象。深克隆可以实现完全的克隆.

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
