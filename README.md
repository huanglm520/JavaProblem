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

jsp和servlet的区别和联系：<br>
1. jsp经编译后就变成了Servlet.(JSP的本质就是Servlet，JVM只能识别java的类，不能识别JSP的代码,Web容器将JSP的代码编译成JVM能够识别的java类)<br>
2. jsp更擅长表现于页面显示,servlet更擅长于逻辑控制.<br>
3. Servlet中没有内置对象，Jsp中的内置对象都是必须通过HttpServletRequest对象，HttpServletResponse对象以及HttpServlet对象得到.<br>
Jsp是Servlet的一种简化，使用Jsp只需要完成程序员需要输出到客户端的内容，Jsp中的Java脚本如何镶嵌到一个类中，由Jsp容器完成。而Servlet则是个完整的Java类，这个类的Service方法用于生成对客户端的响应。<br>

联系：<br>
JSP是Servlet技术的扩展，本质上就是Servlet的简易方式。JSP编译后是“类servlet”。Servlet和JSP最主要的不同点在于，Servlet的应用逻辑是在Java文件中，并且完全从表示层中的HTML里分离开来。而JSP的情况是Java和HTML可以组合成一个扩展名为.jsp的文件。JSP侧重于视图，Servlet主要用于控制逻辑.<br>

### 65. JSP 有哪些内置对象？作用分别是什么？

Page，pageContext，request，response，session，application，out，config，exception

Page指的是JSP被翻译成Servlet的对象的引用.

pageContext对象可以用来获得其他8个内置对象,还可以作为JSP的域范围对象使用.pageContext中存的值是当前的页面的作用范围》

request代表的是请求对象,可以用于获得客户机的信息,也可以作为域对象来使用，使用request保存的数据在一次请求范围内有效。

Session代表的是一次会话，可以用于保存用户的私有的信息,也可以作为域对象使用，使用session保存的数据在一次会话范围有效

Application：代表整个应用范围,使用这个对象保存的数据在整个web应用中都有效。

Response是响应对象,代表的是从服务器向浏览器响应数据.

Out:JSPWriter是用于向页面输出内容的对象

Config：指的是ServletConfig用于JSP翻译成Servlet后 获得Servlet的配置的对象.

Exception:在页面中设置isErrorPage=”true”，即可使用，是Throwable的引用.用来获得页面的错误信息。

### 66. 说一下 JSP 的 4 种作用域？

application: 在所有应用程序中有效

session: 在当前会话中有效

request: 在当前请求中有效

page: 在当前页面有效

### 67. Session 和 Cookie 有什么区别？

Cookie实际上是一小段的文本信息。客户端请求服务器，如果服务器需要记录该用户状态，就使用response向客 户端浏览器颁发一个Cookie（写进响应头中）。客户端浏览器会把Cookie保存起来。当浏览器再请求该网站时，浏览器把请求的网址连同该Cookie一同提交给服务器。服务器检查该Cookie，以此来辨认用户状态。服务器还可以根据需要修改Cookie的内容。

Session是另一种记录客户状态的机制，不同的是Cookie保存在客户端浏览器中，而Session保存在服务器上。客户端浏览器访问服务器的时候，服务器把客户端信息以某种形式记录在服务器上。这就是Session。客户端浏览器再次访问时只需要从该Session中查找该客户的状态就可以了。

### 68. 说一下 Session 的工作原理？

浏览器和服务器采用http无状态的通讯，为了保持客户端的状态，使用session来达到这个目的。然而服务端是怎么样标示不同的客户端或用户呢？这里我们可以使用生活中的一个例子，假如你参加一个晚会，认识了很多人，你会采取什么方式来区分不同的人呢！你可能根据脸型，也有可能根据用户的名字，或者人的身份证，即采用一个独一无二的标示。在session机制中，也采用了这样的一个唯一的session_id来标示不同的用户，不同的是：浏览器每次请求都会带上由服务器为它生成的session_id.

简单介绍一下流程：当客户端访问服务器时，服务器根据需求设置session，将会话信息保存在服务器上，同时将标示session的session_id传递给客户端浏览器，浏览器将这个session_id保存在内存中(还有其他的存储方式，例如写在url中)，我们称之为无过期时间的cookie。浏览器关闭后，这个cookie就清掉了，它不会存在用户的cookie临时文件。以后浏览器每次请求都会额外加上这个参数值，再服务器根据这个session_id，就能取得客户端的数据状态。

如果客户端浏览器意外关闭，服务器保存的session数据不是立即释放，此时数据还会存在，只要我们知道那个session_id,就可以继续通过请求获得此session的信息；但是这个时候后台的session还存在，但是session的保存有一个过期时间，一旦超过规定时间没有客户端请求时，他就会清除这个session。

### 69. 如果客户端禁止 Cookie 能实现 Session 还能用吗？

理论上只要在返回的页面里里能带上一个标识会话的令牌，在浏览器下一次提交的时候，能带上这个令牌，会话就可以被保持因此，cookie只是最优雅的实现session的方式，因为cookie对用户来说不可见，同时会自动在HTTP报文中传输但session也可以通过其他方式来保持， 比如放一个sessionId在URL的参数里 

### 70. Spring MVC 和 Struts 的区别是什么？

一、拦截机制的不同<br>
Struts2是类级别的拦截，每次请求就会创建一个Action，和Spring整合时Struts2的ActionBean注入作用域是原型模式prototype，然后通过setter，getter吧request数据注入到属性。Struts2中，一个Action对应一个request，response上下文，在接收参数时，可以通过属性接收，这说明属性参数是让多个方法共享的。Struts2中Action的一个方法可以对应一个url，而其类属性却被所有方法共享，这也就无法用注解或其他方式标识其所属方法了，只能设计为多例。

SpringMVC是方法级别的拦截，一个方法对应一个Request上下文，所以方法直接基本上是独立的，独享request，response数据。而每个方法同时又何一个url对应，参数的传递是直接注入到方法中的，是方法所独有的。处理结果通过ModeMap返回给框架。在Spring整合时，SpringMVC的Controller Bean默认单例模式Singleton，所以默认对所有的请求，只会创建一个Controller，有应为没有共享的属性，所以是线程安全的，如果要改变默认的作用域，需要添加@Scope注解修改。

Struts2有自己的拦截Interceptor机制，SpringMVC这是用的是独立的Aop方式，这样导致Struts2的配置文件量还是比SpringMVC大。

二、底层框架的不同<br>
Struts2采用Filter（StrutsPrepareAndExecuteFilter）实现，SpringMVC（DispatcherServlet）则采用Servlet实现。Filter在容器启动之后即初始化；服务停止以后坠毁，晚于Servlet。Servlet在是在调用时初始化，先于Filter调用，服务停止后销毁。

三、性能方面<br>
Struts2是类级别的拦截，每次请求对应实例一个新的Action，需要加载所有的属性值注入，SpringMVC实现了零配置，由于SpringMVC基于方法的拦截，有加载一次单例模式bean注入。所以，SpringMVC开发效率和性能高于Struts2。

四、配置方面<br>
spring MVC和Spring是无缝的。从这个项目的管理和安全上也比Struts2高。

### 71. 如何避免 SQL 注入？

1、检查变量数据类型和格式

如果你的SQL语句是类似where id={$id}这种形式，数据库里所有的id都是数字，那么就应该在SQL被执行前，检查确保变量id是int类型；如果是接受邮箱，那就应该检查并严格确保变量一定是邮箱的格式，其他的类型比如日期、时间等也是一个道理。总结起来：只要是有固定格式的变量，在SQL语句执行前，应该严格按照固定格式去检查，确保变量是我们预想的格式，这样很大程度上可以避免SQL注入攻击。比如，我们前面接受username参数例子中，我们的产品设计应该是在用户注册的一开始，就有一个用户名的规则，比如5-20个字符，只能由大小写字母、数字以及一些安全的符号组成，不包含特殊字符。此时我们应该有一个check_username的函数来进行统一的检查。不过，仍然有很多例外情况并不能应用到这一准则，比如文章发布系统，评论系统等必须要允许用户提交任意字符串的场景，这就需要采用过滤等其他方案了。

2、过滤特殊符号

对于无法确定固定格式的变量，一定要进行特殊符号过滤或转义处理。

3、绑定变量，使用预编译语句

MySQL的mysqli驱动提供了预编译语句的支持，不同的程序语言，都分别有使用预编译语句的方法。实际上，绑定变量使用预编译语句是预防SQL注入的最佳方式，使用预编译的SQL语句语义不会发生改变，在SQL语句中，变量用问号?表示，黑客即使本事再大，也无法改变SQL语句的结构

### 72. 什么是 XSS 攻击，如何避免？

XSS（Cross Site Scripting），即跨站脚本攻击，是一种常见于web应用程序中的计算机安全漏洞.XSS通过在用户端注入恶意的可运行脚本，若服务器端对用户输入不进行处理，直接将用户输入输出到浏览器，然后浏览器将会执行用户注入的脚本。

如何避免：<br>
1、获取用户输入，不用.innerHTML，用innerText。<br>
2、对用户输入进行过滤，如 HTMLEncode 函数实现应该至少进行 & < > " ' / 等符号转义成 &amp &lt &gt &quot &#x27 &#x2F；<br>

### 73. 什么是 CSRF 攻击，如何避免？

CSRF 的全称是“跨站请求伪造”，而 XSS 的全称是“跨站脚本”。看起来有点相似，它们都是属于跨站攻击——不攻击服务器端而攻击正常访问网站的用户，但前面说了，它们的攻击类型是不同维度上的分 类。CSRF 顾名思义，是伪造请求，冒充用户在站内的正常操作。

如何避免：<br>
阻止不明外域的访问:<br>
同源检测<br>
Samesite Cookie<br>

提交时要求附加本域才能获取的信息:<br>
CSRF Token<br>
双重Cookie验证<br>

## 异常

### 74. throw 和 throws 的区别？

throws是用来声明一个方法可能抛出的所有异常信息，throws是将异常声明但是不处理，而是将异常往上传，谁调用我就交给谁处理。而throw则是指抛出的一个具体的异常类型。

### 75. final、finally、finalize 有什么区别？

1. final 

在java中，final可以用来修饰类，方法和变量（成员变量或局部变量）。下面将对其详细介绍。

1.1修饰类

当用final修饰类的时，表明该类不能被其他类所继承。当我们需要让一个类永远不被继承，此时就可以用final修饰，但要注意：

final类中所有的成员方法都会隐式的定义为final方法。

1.2 修饰方法

使用final方法的原因主要有两个：

(1) 把方法锁定，以防止继承类对其进行更改。

(2) 效率，在早期的java版本中，会将final方法转为内嵌调用。但若方法过于庞大，可能在性能上不会有多大提升。因此在最近版本中，不需要final方法进行这些优化了。

1.3 修饰变量

final成员变量表示常量，只能被赋值一次，赋值后其值不再改变。类似于C++中的const。

2. finally

finally作为异常处理的一部分，它只能用在try/catch语句中，并且附带一个语句块，表示这段语句最终一定会被执行（不管有没有抛出异常），经常被用在需要释放资源的情况下。（×）（这句话其实存在一定的问题）

3. finalize　　

finalize()是在java.lang.Object里定义的，也就是说每一个对象都有这么个方法。这个方法在gc启动，该对象被回收的时候被调用。其实gc可以回收大部分的对象（凡是new出来的对象，gc都能搞定，一般情况下我们又不会用new以外的方式去创建对象），所以一般是不需要程序员去实现finalize的。 

### 76. try-catch-finally 中哪个部分可以省略？

catch和finally都是可以省略的，但是不能同时省略。

### 77. try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

会执行，在return前执行

### 78. 常见的异常类有哪些？

Java中的异常分为两大类：
　　
1.Checked Exception（非Runtime Exception）

2.Unchecked Exception（Runtime Exception）

算数异常类：ArithmeticExecption

空指针异常类型：NullPointerException

类型强制转换类型：ClassCastException

数组负下标异常：NegativeArrayException

数组下标越界异常：ArrayIndexOutOfBoundsException

违背安全原则异常：SecturityException

文件已结束异常：EOFException

文件未找到异常：FileNotFoundException

字符串转换为数字异常：NumberFormatException

操作数据库异常：SQLException

输入输出异常：IOException

方法未找到异常：NoSuchMethodException

下标越界异常：IndexOutOfBoundsExecption

系统异常：SystemException

创建一个大小为负数的数组错误异常：NegativeArraySizeException

数据格式异常：NumberFormatException

安全异常：SecurityException

不支持的操作异常：UnsupportedOperationException

网络操作在主线程异常：NetworkOnMainThreadException  

请求状态异常： IllegalStateException （extends RuntimeException ，父类：IllegalComponentStateException 在不合理或不正确时间内唤醒一方法时出现的异常信息。换句话说，即 Java 环境或 Java 应用不满足请求操作）

网络请求异常：HttpHostConnectException

子线程Thread更新UI view 异常：ViewRootImpl$CalledFromWrongThreadException

证书不匹配的主机名异常： SSLExceptionero

反射Method.invoke(obj, args...)方法抛出异常：InvocationTargetException

EventBus使用异常：EventBusException

非法参数异常：IllegalArgumentException

参数不能小于0异常：ZeroException

## 网络

### 79. HTTP 响应码 301 和 302 代表的是什么？有什么区别？

301，302 都是HTTP状态的编码，都代表着某个URL发生了转移，不同之处在于： <br>
301 redirect: 301 代表永久性转移(Permanently Moved)。<br>
302 redirect: 302 代表暂时性转移(Temporarily Moved)。<br>

### 80. forward 和 redirect 的区别？

Forward和Redirect代表了两种请求转发方式：直接转发和间接转发。

直接转发方式（Forward），客户端和浏览器只发出一次请求，Servlet、HTML、JSP或其它信息资源，由第二个信息资源响应该请求，在请求对象request中，保存的对象对于每个信息资源是共享的。

间接转发方式（Redirect）实际是两次HTTP请求，服务器端在响应第一次请求的时候，让浏览器再向另外一个URL发出请求，从而达到转发的目的。

### 81. 简述 TCP 和 UDP 的区别？

1、TCP面向连接（如打电话要先拨号建立连接）;UDP是无连接的，即发送数据之前不需要建立连接

2、TCP提供可靠的服务。也就是说，通过TCP连接传送的数据，无差错，不丢失，不重复，且按序到达;UDP尽最大努力交付，即不保证可靠交付

Tcp通过校验和，重传控制，序号标识，滑动窗口、确认应答实现可靠传输。如丢包时的重发控制，还可以对次序乱掉的分包进行顺序控制。

3、UDP具有较好的实时性，工作效率比TCP高，适用于对高速传输和实时性有较高的通信或广播通信。

4.每一条TCP连接只能是点到点的;UDP支持一对一，一对多，多对一和多对多的交互通信

5、TCP对系统资源要求较多，UDP对系统资源要求较少。

### 82. TCP 为什么要三次握手，两次不行吗？为什么？

不行。

3次握手完成两个重要的功能，既要双方做好发送数据的准备工作(双方都知道彼此已准备好)，也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认。现在把三次握手改成仅需要两次握手，死锁是可能发生的。

### 83. 说一下 TCP 粘包是怎么产生的？

采用TCP协议传输数据的客户端与服务器经常是保持一个长连接的状态（一次连接发一次数据不存在粘包），双方在连接不断开的情况下，可以一直传输数据；但当发送的数据包过于的小时，那么TCP协议默认的会启用Nagle算法，将这些较小的数据包进行合并发送（缓冲区数据发送是一个堆压的过程）；这个合并过程就是在发送缓冲区中进行的，也就是说数据发送出来它已经是粘包的状态了

### 84. OSI 的七层模型都有哪些？

物理层：设备之间比特流的传输，物理接口，电气特性等等。常见的设备有网线，网卡等等。数据单位是比特

数据链路层：成帧，用Mac地址访问媒介，错误检测与修正。数据单位是帧

网络层：提供逻辑地址（IP地址）、选路（选择传输路线）。数据单位是报文

传输层：确定传输的可靠性以及每种协议的端口号，传输前的错误检测，流控。数据单位是TPDU

会话层：对应用会话的管理，同步。确定网络数据是否要经过远程会话 。数据单位是SPDU

表示层：数据的表现形式，特定功能的实现，比如加密压缩等。数据单位是PPDU

应用层：用户接口，无限接近用户。数据单位是APDU

### 85. Get和 Post 请求有哪些区别？

GET在浏览器回退时是无害的，而POST会再次提交请求。

GET产生的URL地址可以被Bookmark，而POST不可以。

GET请求会被浏览器主动cache，而POST不会，除非手动设置。

GET请求只能进行url编码，而POST支持多种编码方式。

GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。

GET请求在URL中传送的参数是有长度限制的，而POST没有。

对参数的数据类型，GET只接受ASCII字符，而POST没有限制。

GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。

GET参数通过URL传递，POST放在Request body中。

### 86. 如何实现跨域？

1、通过jsonp跨域

2、通过修改document.domain来跨子域

3、使用window.name来进行跨域

4、使用HTML5中新引进的window.postMessage方法来跨域传送数据

### 87. 说一下 JSONP 实现原理？

在js中，我们直接用XMLHttpRequest请求不同域上的数据时，是不可以的。但是，在页面上引入不同域上的js脚本文件却是可以的，jsonp正是利用这个特性来实现的。

## 设计模式

### 88. 说一下你熟悉的设计模式？

最常用的两种设计模式：工厂模式和单例模式

### 89. 简单工厂和抽象工厂有什么区别？

简单工厂 ： 用来生产同一等级结构中的任意产品。（不支持拓展增加产品）  

抽象工厂 ：用来生产不同产品族的全部产品。（不支持拓展增加产品；支持增加产品族）  

## Spring/Spring MVC

### 90. 为什么要使用 Spring？

1.方便解耦，便于开发（Spring就是一个大工厂，可以将所有对象的创建和依赖关系维护都交给spring管理）

2.spring支持aop编程（spring提供面向切面编程，可以很方便的实现对程序进行权限拦截和运行监控等功能）

3.声明式事务的支持（通过配置就完成对事务的支持，不需要手动编程）

4.方便程序的测试，spring 对junit4支持，可以通过注解方便的测试spring 程序

5.方便集成各种优秀的框架（）

6.降低javaEE API的使用难度（Spring 对javaEE开发中非常难用的一些API 例如JDBC,javaMail,远程调用等，都提供了封装，是这些API应用难度大大降低）

### 91. 解释一下什么是 AOP？

AOP（Aspect-Oriented Programming）指一种程序设计范型，该范型以一种称为切面（aspect）的语言构造为基础，切面是一种新的模块化机制，用来描述分散在对象、类或方法中的横切关注点（crosscutting concern）。

### 92. 解释一下什么是 IOC？

IOC是Inversion of Control的缩写，多数书籍翻译成“控制反转”，还有些书籍翻译成为“控制反向”或者“控制倒置”。

### 93. Spring 有哪些主要模块？

1，Spring Core<br>
Core模块是Spring的核心类库，Spring的所有功能都依赖于该类库，Core主要实现IOC功能，Sprign的所有功能都是借助IOC实现的。

2，AOP<br>
AOP模块是Spring的AOP库，提供了AOP（拦截器）机制，并提供常用的拦截器，供用户自定义和配置。

3，ORM<br>
Spring 的ORM模块提供对常用的ORM框架的管理和辅助支持，Spring支持常用的Hibernate，ibtas，jdao等框架的支持，Spring本身并不对ORM进行实现，仅对常见的ORM框架进行封装，并对其进行管理

4，DAO模块<br>
Spring 提供对JDBC的支持，对JDBC进行封装，允许JDBC使用Spring资源，并能统一管理JDBC事物，并不对JDBC进行实现。（执行sql语句）

5，WEB模块<br>
WEB模块提供对常见框架如Struts1，WEBWORK（Struts 2），JSF的支持，Spring能够管理这些框架，将Spring的资源注入给框架，也能在这些框架的前后插入拦截器。

6，Context模块<br>
Context模块提供框架式的Bean访问方式，其他程序可以通过Context访问Spring的Bean资源，相当于资源注入。

7，MVC模块<br>
WEB MVC模块为Spring提供了一套轻量级的MVC实现，在Spring的开发中，我们既可以用Struts也可以用Spring自己的MVC框架，相对于Struts，Spring自己的MVC框架更加简洁和方便。

### 94. Spring 常用的注入方式有哪些？

1、接口注入；<br>
2、setter方法注入；<br>
3、构造方法注入；<br>

### 95. Spring 中的 Bean 是线程安全的吗？

Spring容器中的Bean是否线程安全，容器本身并没有提供Bean的线程安全策略，因此可以说Spring容器中的Bean本身不具备线程安全的特性，但是具体还是要结合具体scope的Bean去研究。

### 96. Spring 支持几种 Bean 的作用域？

singleton：单例模式，在整个Spring IoC容器中，使用singleton定义的Bean将只有一个实例

prototype：原型模式，每次通过容器的getBean方法获取prototype定义的Bean时，都将产生一个新的Bean实例

request：对于每次HTTP请求，使用request定义的Bean都将产生一个新实例，即每次HTTP请求将会产生不同的Bean实例。只有在Web应用中使用Spring时，该作用域才有效

session：对于每次HTTP Session，使用session定义的Bean豆浆产生一个新实例。同样只有在Web应用中使用Spring时，该作用域才有效

globalsession：每个全局的HTTP Session，使用session定义的Bean都将产生一个新实例。典型情况下，仅在使用portlet context的时候有效。同样只有在Web应用中使用Spring时，该作用域才有效

### 97. Spring 自动装配 Bean 有哪些方式？

1. 使用XML配置自动装配Bean

2. 使用@Autowired和@Resource注解来自动装配Bean

### 98. Spring 事务实现方式有哪些？

（1）编程式事务管理对基于 POJO 的应用来说是唯一选择。我们需要在代码中调用beginTransaction()、commit()、rollback()等事务管理相关的方法，这就是编程式事务管理。<br>
（2）基于 TransactionProxyFactoryBean的声明式事务管理<br>
（3）基于 @Transactional 的声明式事务管理<br>
（4）基于Aspectj AOP配置事务<br>

### 99. 说一下 Spring 的事务隔离？

ISOLATION_DEFAULT：使用后端数据库默认的隔离级别。<br>
ISOLATION_READ_UNCOMMITTED：允许读取尚未提交的更改。可能导致脏读、幻影读或不可重复读。<br>
ISOLATION_READ_COMMITTED：允许从已经提交的并发事务读取。可防止脏读，但幻影读和不可重复读仍可能会发生。<br>
ISOLATION_REPEATABLE_READ：对相同字段的多次读取的结果是一致的，除非数据被当前事务本身改变。可防止脏读和不可重复读，但幻影读仍可能发生。<br>
ISOLATION_SERIALIZABLE：完全服从ACID的隔离级别，确保不发生脏读、不可重复读和幻影读。这在所有隔离级别中也是最慢的，因为它通常是通过完全锁定当前事务所涉及的数据表来完成的。<br>

### 100. 说一下 Spring MVC 运行流程？

1、用户发送请求至前端控制器DispatcherServlet <br>
2、DispatcherServlet收到请求调用HandlerMapping处理器映射器。 <br>
3、处理器映射器找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。 <br>
4、DispatcherServlet调用HandlerAdapter处理器适配器 <br>
5、HandlerAdapter经过适配调用具体的处理器(Controller，也叫后端控制器)。 <br>
6、Controller执行完成返回ModelAndView <br>
7、HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet <br>
8、DispatcherServlet将ModelAndView传给ViewReslover视图解析器 <br>
9、ViewReslover解析后返回具体View <br>
10、DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。 <br>
11、DispatcherServlet响应用户<br>

### 101. Spring MVC 有哪些组件？

HandlerMapping：管理请求(request)和处理句柄(Handler)之间的映射关系<br>

HandlerAdapter：处理句柄适配器,<br>
1.每个HandlerAdapter包装一个Handler,<br>
2.HandlerAdapter主要用于隔离调用者DispatcherServlet和各式各样的Handler<br>

HandlerExceptionResolver：处理句柄异常解析器<br>

ViewResolver：视图解析器：根据视图名称和Locale解析为具体View对象用来渲染页面<br>

RequestToViewNameTranslator：请求到视图名称的翻译器:从request中获取视图名称,作为ViewResolver的补充<br>

LocaleResolver：Locale地区解析器<br>
处理本地化/国际化语言相关，结合上下文和当前请求分析得到应该使用的Locale地区<br>

ThemeResolver：主题解析器，处理UI主题(look and feel)相关<br>

MultipartResolver：Multipart上传数据解析器<br>

FlashMapManager：管理FlashMap结构的重定向参数<br>

### 102. @RequestMapping 的作用是什么？

@RequestMapping是一个用来处理请求地址映射的注解，可用于类或者方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。

### 103. @Autowired 的作用是什么？

@Autowired默认按类型装配（这个注解是属业spring的），默认情况下必须要求依赖对象必须存在，如果要允许null值，可以设置它的required属性为false，如：@Autowired(required=false) ，如果我们想使用名称装配可以结合@Qualifier注解进行使用。

## Spring Boot/Spring Cloud

### 104. 什么是 Spring Boot？

SpringBoot是一个框架，一种全新的编程规范，他的产生简化了框架的使用，所谓简化是指简化了Spring众多框架中所需的大量且繁琐的配置文件，所以 SpringBoot是一个服务于框架的框架，服务范围是简化配置文件。

### 105. 为什么要用 Spring Boot？

让文件配置变的相当简单、让应用部署变的简单（SpringBoot内置服务器，并装备启动类代码），可以快速开启一个Web容器进行开发。

### 106. Spring Boot 核心配置文件是什么？

Spring Boot项目使用一个全局的配置文件application.properties或者是application.yml

### 107. Spring Boot 配置文件有哪几种类型？它们有什么区别？

Spring Boot提供了两种常用的配置文件，分别是properties文件和yml文件。他们的作用都是修改Spring Boot自动配置的默认值。相对于properties文件而言，yml文件更年轻，也有很多的坑。

### 108. Spring Boot 有哪些方式可以实现热部署？

spring-boot-devtools和Spring Loaded

### 109. JPA 和 Hibernate 有什么区别？

JPA是一个Java编程语言接口规范，它描述了使用标准JAVA平台和JAVA企业版本的关系型数据的管理。Hibernate ORM是JPA规范的一个实现

### 110. 什么是 Spring Cloud？

Spring Cloud是一个微服务框架，相比Dubbo等RPC框架, Spring Cloud提供的全套的分布式系统解决方案。 

Spring Cloud对微服务基础框架Netflix的多个开源组件进行了封装，同时又实现了和云端平台以及和Spring Boot开发框架的集成。 

Spring Cloud为微服务架构开发涉及的配置管理，服务治理，熔断机制，智能路由，微代理，控制总线，一次性token，全局一致性锁，leader选举，分布式session，集群状态管理等操作提供了一种简单的开发方式。

Spring Cloud 为开发者提供了快速构建分布式系统的工具，开发者可以快速的启动服务或构建应用、同时能够快速和云平台资源进行对接。   

### 111. Spring Cloud 断路器的作用是什么？

断路器（Circuit Breaker）模式就是为了防止在分布式系统中出现这种瀑布似的连锁反应导致的灾难。

### 112. Spring Cloud 的核心组件有哪些？

服务发现——Netflix Eureka

客服端负载均衡——Netflix Ribbon

断路器——Netflix Hystrix

服务网关——Netflix Zuul

分布式配置——Spring Cloud Config

## Hibernate

### 113. 为什么要使用 Hibernate？

1. 对JDBC访问数据库的代码做了封装，大大简化了数据访问层繁琐的重复性代码。<br>
2. Hibernate是一个基于JDBC的主流持久化框架，是一个优秀的ORM实现。他很大程度的简化DAO层的编码工作<br>
3. hibernate使用Java反射机制，而不是字节码增强程序来实现透明性。<br>
4. hibernate的性能非常好，因为它是个轻量级框架。映射的灵活性很出色。它支持各种关系数据库，从一对一到多对多的各种复杂关系。<br>

### 114. 什么是 ORM 框架？

ORM，即Object-Relational Mapping（对象关系映射），它的作用是在关系型数据库和业务实体对象之间作一个映射，这样，我们在具体的操作业务对象的时候，就不需要再去和复杂的SQL语句打交道，只需简单的操作对象的属性和方法。

### 115. Hibernate 中如何在控制台查看打印的 SQL 语句？

1.spring的配置文件中增加： <br>
&lt;prop key="hibernate.show_sql"&gt;true&lt;/prop&gt;  

或者在hibernate的配置文件中增加： <br>
&lt;property name="show_sql"&gt;true&lt;/property&gt;  

2.在log4j.properties中做如下配置： <br>
log4j.appender.STDOUT.Threshold=trace  <br>
log4j.category.org.hibernate.SQL=trace  <br>
log4j.category.org.hibernate.type=trace  <br>

### 116. Hibernate 有几种查询方式？

一、HQL查询

HQL（Hibernate Query Language）提供了丰富灵活的查询方式，使用HQL进行查询也是Hibernate官方推荐使用的查询方式。

HQL在语法结构上和SQL语句十分的相同，所以可以很快的上手进行使用。使用HQL需要用到Hibernate中的Query对象，该对象专门执行HQL方式的操作。

二、QBC（Query By Criteria）查询

Criteria对象提供了一种面向对象的方式查询数据库。Criteria对象需要使用Session对象来获得。

一个Criteria对象表示对一个持久化类的查询。

三、原生SQL查询

### 117. Hibernate 实体类可以被定义为 final 吗？

是的，你可以将Hibernate的实体类定义为final类，但这种做法并不好。因为Hibernate会使用代理模式在延迟关联的情况下提高性能，如果你把实体类定义成final类之后，因为 Java不允许对final类进行扩展，所以Hibernate就无法再使用代理了，如此一来就限制了使用可以提升性能的手段。

### 118. 在 Hibernate 中使用 Integer 和 int 做映射有什么区别？

返回数据库字段值是null的话，int类型会报错。int是基本数据类型，其声明的是变量，而null则是对象。所以Hibernate实体建议用Integer

### 119. Hibernate 是如何工作的？

（1）SessionFactory：这是Hibernate的关键对象，它是单个数据库映射关系经过编译后的内存镜像，它也是线程安全的。它是生成Session的工厂，本身要应用到ConnectionProvider，该对象可以在进程和集群的级别上，为那些事务之间可以重用的数据提供可选的二级缓存。

2）Session：它是应用程序和持久存储层之间交互操作的一个单线程对象。它也是Hibernate持久化操作的关键对象，所有的持久化对象必须在Session的管理下才能够进行持久化操作。此对象的生存周期很短，其隐藏了JDBC连接，也是Transaction 的工厂。Session对象有一个一级缓存，现实执行Flush之前，所有的持久化操作的数据都在缓存中Session对象处。

（3）持久化对象：系统创建的POJO实例一旦与特定Session关联，并对应数据表的指定记录，那该对象就处于持久化状态，这一系列的对象都被称为持久化对象。程序中对持久化对象的修改，都将自动转换为持久层的修改。持久化对象完全可以是普通的Java Beans/POJO，唯一的特殊性是它们正与Session关联着。

（4）瞬态对象和脱管对象：系统进行new关键字进行创建的Java 实例，没有Session 相关联，此时处于瞬态。瞬态实例可能是在被应用程序实例化后，尚未进行持久化的对象。如果一个曾今持久化过的实例，但因为Session的关闭而转换为脱管状态。

（5）事务(Transaction)：代表一次原子操作，它具有数据库事务的概念。但它通过抽象，将应用程序从底层的具体的JDBC、JTA和CORBA事务中隔离开。在某些情况下，一个Session 之内可能包含多个Transaction对象。虽然事务操作是可选的，但是所有的持久化操作都应该在事务管理下进行，即使是只读操作。

（6）连接提供者(ConnectionProvider)：它是生成JDBC的连接的工厂，同时具备连接池的作用。他通过抽象将底层的DataSource和DriverManager隔离开。这个对象无需应用程序直接访问，仅在应用程序需要扩展时使用。

（7）事务工厂(TransactionFactory)：他是生成Transaction对象实例的工厂。该对象也无需应用程序的直接访问。

Hibernate进行持久化操作离不开SessionFactory对象，这个对象是整个数据库映射关系经过编译后的内存镜像，该对象的openSession()方法可打开Session对象。SessionFactory对想是由Configuration对象产生。

每个Hibernate配置文件对应一个configuration对象。在极端情况下，不使用任何配置文件，也可以创建Configuration对象。

### 120. get()和 load()的区别？

1. 对于Hibernate get方法，Hibernate会确认一下该id对应的数据是否存在，首先在session缓存中查找，然后在二级缓存中查找，还没有就查询数据库，数据 库中没有就返回null。这个相对比较简单，也没有太大的争议。主要要说明的一点就是在这个版本(bibernate3.2以上)中get方法也会查找二级缓存！

2. Hibernate load方法加载实体对象的时候，根据映射文件上类级别的lazy属性的配置(默认为true)，分情况讨论： 

(1)若为true,则首先在Session缓存中查找，看看该id对应的对象是否存在，不存在则使用延迟加载，返回实体的代理类对象(该代理类为实体类的子类，由CGLIB动态生成)。等到具体使用该对象(除获取OID以外)的时候，再查询二级缓存和数据库，若仍没发现符合条件的记录，则会抛出一个ObjectNotFoundException。

(2)若为false,就跟Hibernateget方法查找顺序一样，只是最终若没发现符合条件的记录，则会抛出一个ObjectNotFoundException。

这里get和load有两个重要区别: 

如果未能发现符合条件的记录，Hibernate get方法返回null，而load方法会抛出一个ObjectNotFoundException。

load方法可返回没有加载实体数据的代 理类实例，而get方法永远返回有实体数据的对象。

### 121. 说一下 Hibernate 的缓存机制？

首先说下Hibernate缓存的作用（即为什么要用缓存机制），然后再具体说说Hibernate中缓存的分类情况，最后可以举个具体的例子。<br>
Hibernate缓存的作用：<br>
Hibernate是一个持久层框架，经常访问物理数据库，为了降低应用程序对物理数据源访问的频次，从而提高应用程序的运行性能。缓存内的数据是对物理数据源中的数据的复制，应用程序在运行时从缓存读写数据，在特定的时刻或事件会同步缓存和物理数据源的数据Hibernate缓存分类：<br>
Hibernate缓存包括两大类：Hibernate一级缓存和Hibernate二级缓存Hibernate一级缓存又称为“Session的缓存”，它是内置的，不能被卸载（不能被卸载的意思就是这种缓存不具有可选性，必须有的功能，不可以取消session缓存）。由于Session对象的生命周期通常对应一个数据库事务或者一个应用事务，因此它的缓存是事务范围的缓存。第一级缓存是必需的，不允许而且事实上也无法卸除。在第一级缓存中，持久化类的每个实例都具有唯一的OID。 Hibernate二级缓存又称为“SessionFactory的缓存”，由于SessionFactory对象的生命周期和应用程序的整个过程对应，因此Hibernate二级缓存是进程范围或者集群范围的缓存，有可能出现并发问题，因此需要采用适当的并发访问策略，该策略为被缓存的数据提供了事务隔离级别。第二级缓存是可选的，是一个可配置的插件，在默认情况下，SessionFactory不会启用这个插件。<br>
什么样的数据适合存放到第二级缓存中？<br>
1 很少被修改的数据<br>
2 不是很重要的数据，允许出现偶尔并发的数据<br>
3 不会被并发访问的数据<br>
4 常量数据<br>
不适合存放到第二级缓存的数据？<br>
1 经常被修改的数据<br>
2 .绝对不允许出现并发访问的数据，如财务数据，绝对不允许出现并发<br>
3 与其他应用共享的数据。<br>
Hibernate查找对象如何应用缓存？<br>
当Hibernate根据ID访问数据对象的时候，首先从Session一级缓存中查；查不到，如果配置了二级缓存，那么从二级缓存中查；如果都查不到，再查询数据库，把结果按照ID放入到缓存,删除、更新、增加数据的时候，同时更新缓存。Hibernate管理缓存实例无论何时，当你给save()、update()或saveOrUpdate()方法传递一个对象时，或使用load()、 get()、list()、iterate() 或scroll()方法获得一个对象时, 该对象都将被加入到Session的内部缓存中。 当随后flush()方法被调用时，对象的状态会和数据库取得同步。 如果你不希望此同步操作发生，或者你正处理大量对象、需要对有效管理内存时，你可以调用evict() 方法，从一级缓存中去掉这些对象及其集合。<br>

### 122. Hibernate 对象有哪些状态？

1，Transient 瞬时 ：对象刚new出来，还没设id，设了其他值。

2，Persistent 持久：调用了save()、saveOrUpdate()，就变成Persistent，有id

3，Detached  脱管 ： 当session  close()完之后，变成Detached。

### 123. 在 Hibernate 中 getCurrentSession 和 openSession 的区别是什么？

1. openSession 从字面上可以看得出来，是打开一个新的session对象，而且每次使用都是打开一个新的session，假如连续使用多次，则获得的session不是同一个对象，并且使用完需要调用close方法关闭session。

2. getCurrentSession ，从字面上可以看得出来，是获取当前上下文一个session对象，当第一次使用此方法时，会自动产生一个session对象，并且连续使用多次时，得到的session都是同一个对象，这就是与openSession的区别之一，简单而言，getCurrentSession 就是：如果有已经使用的，用旧的，如果没有，建新的。

### 124. Hibernate 实体类必须要有无参构造函数吗？为什么？

Hibernate进行反转的时候需要这个无参的构造函数作为支持<br>
因此必须要有这个东西<br>
否则Hibernate无法进行反转<br>

## Mybatis

### 125. Mybatis 中 #{}和 ${}的区别是什么？

1. #将传入的数据都当成一个字符串，会对自动传入的数据加一个双引号。如：order by #user_id#，如果传入的值是111,那么解析成sql时的值为order by "111", 如果传入的值是id，则解析成的sql为order by "id".
　　
2. $将传入的数据直接显示生成在sql中。如：order by $user_id$，如果传入的值是111,那么解析成sql时的值为order by user_id,  如果传入的值是id，则解析成的sql为order by id.
　　
3. #方式能够很大程度防止sql注入。
　　
4. $方式无法防止Sql注入。

5. $方式一般用于传入数据库对象，例如传入表名.
　　
6. 一般能用#的就别用$.

### 126. Mybatis 有几种分页方式？

一.数组分页

原理：进行数据库查询操作时，获取到数据库中所有满足条件的记录，保存在应用的临时数组中，再通过List的subList方法，获取到满足条件的所有记录。

二.借助Sql语句进行分页

在了解到通过数组分页的缺陷后，我们发现不能每次都对数据库中的所有数据都检索。然后在程序中对获取到的大量数据进行二次操作，这样对空间和性能都是极大的损耗。所以我们希望能直接在数据库语言中只检索符合条件的记录，不需要在通过程序对其作处理。这时，Sql语句分页技术横空出世。

三.RowBounds实现分页

原理：通过RowBounds实现分页和通过数组方式分页原理差不多，都是一次获取所有符合条件的数据，然后在内存中对大数据进行操作，实现分页效果。只是数组分页需要我们自己去实现分页逻辑，这里更加简化而已。

### 127. RowBounds 是一次性查询全部结果吗？为什么？

也不是, jdbc有个Fetch Size的设置, 只有当需要更多数据时, 它才会从数据库查询更多数据.

### 128. Mybatis 逻辑分页和物理分页的区别是什么？

逻辑分页时在内存中进行, 一次查询出很多数据, 在内存进行分页, 这种方式占用大量内存, 可能导致内存溢出; 物理分页是直接查询出所需数据, 在数据库分页, 这种分页按需返回数据, 但数据库压力可能较大.

### 129. Mybatis 是否支持延迟加载？延迟加载的原理是什么？

支持. 可以设置lazyLoadingEnable=true启用.

### 130. 说一下 Mybatis 的一级缓存和二级缓存？

一级缓存是基于PerpetualCache的HashMap本地缓存, 生命周期与SQLSession相同, 可能会出现脏数据, 在session关闭或清空后缓存失效. 默认开启. 二级缓存也是基于PerpetualCache的HashMap本地缓存, 不同的是作用域为Mapper级别, 可以在多个Session间共享, 可以自定义缓存如使用EhCache. 使用二级缓存需要类实现Serializable接口.

### 131. Mybatis 和 Hibernate 的区别有哪些？

Mybatis更灵活, 可以自己写sql; 可移植性hibernate要好; 二级缓存hibernate可以自行更换;

### 132. Mybatis 有哪些执行器（Executor）？

有三种基本执行器: (1). SimpleExecutor: 每执行一次update或select就开启一个statement对象, 用完立即关闭statement对象; (2). ReuseExecutor: 执行update,select, 以sql语句作为key查找statement对象, 存在则使用, 不存在则创建, 用完存在Map以备后面再用. (3). BatchExecutor: 执行update, 将多个sql添加到批处理中, 等待统一执行, 它缓存了多个statement对象, 等待统一处理.

### 133. Mybatis 分页插件的实现原理是什么？

拦截器实现, 拦截sql, 然后重写为对应的分页sql.

### 134. Mybatis 如何编写一个自定义插件？

1. 插件要实现interceptor接口

2. 插件应用的目标对象: Executor, StatementHandler,ParameterHandler, ResultSetHandler.

## RabbitMQ

### 135. RabbitMQ 的使用场景有哪些？

rabbitmq是目前比较流行的amqp消息队列, 适合使用的场景有: 1. 系统削峰填谷; 2. 延迟队列; 3. 系统解耦

### 136. RabbitMQ 有哪些重要的角色？

问题问的是构成rabbitmq的系统角色, rabbitmq是生产者/消费者模式的结构. 因此分为生产者: 消息的创建方, 负责发送消息到消息服务器; 消费者: 消息接收方, 用于处理数据; 中介代理: 即rabbitmq本身, 用来接受消息并按一定数据格式存储, 并为消费者提供消息.

### 137. RabbitMQ 有哪些重要的组件？

1. ConnectionFactory: 建议链接的工厂类<br>
2. Channal: 信道, 消息通道<br>
3. Exchange: 交换器, 用于接收分配消息<br>
4. Queue: 队列, 用来存储消息<br>
5. RoutingKey: 路由键, 用来把生产者数据分配到交换机<br>
6. BindingKey: 用来把交换机的消息绑定到队列<br>

### 138. RabbitMQ 中 VHost 的作用是什么？

类似数据库的实例, 每个vhost有自己的一套队列,交换机和绑定以及自己的权限机制.

### 139. RabbitMQ 的消息是怎么发送的？

客户端通过tcp链接到RabbitMQ服务器, 一旦通过了认证, 客户端和服务器之间就创建了一条amqp信道, 信道是创建在真实tcp上的虚拟链接, amqp命令是通过信道发出去的, 每个信道都有一个唯一的id, 不论发布还是订阅均通过此信道完成.

### 140. RabbitMQ 怎么保证消息的稳定性？

提供了事务支持; 可以将channel设置为confirm模式.

### 141. RabbitMQ 怎么避免消息丢失？

把消息持久化到磁盘, 保证重启数据不丢失; 集群中至少有个物理磁盘, 保证消息落入磁盘.

### 142. 要保证消息持久化成功的条件有哪些？

队列queue必须设置持久化durable为true; 消息推送投递模式必须设置持久化, deliveryMode=2; 消息已经到达持久化交换机; 消息已经到达持久化队列.

### 143. RabbitMQ 持久化有什么缺点？

持久化需要将数据写入磁盘, 跟其他磁盘io的系统一样,这样会降低服务器吞吐量, 降低性能.

### 144. RabbitMQ 有几种广播类型？

direct, 默认方式, 发送消息给订阅方, 对于多个订阅方采用轮询的方式进行; headers, 性能较差, 此类型几乎用不到; fanout, 分发模式, 分发给所有订阅者; topic: 匹配订阅, 可以使用正则匹配到消息队列, 能匹配到的都能接收到.

### 145. RabbitMQ 怎么实现延迟消息队列？

有两种方式: 一是消息过期后进入死信交换机, 再由交换机转发到延迟消费队列, 实现延迟功能; 二是使用delayed-message-exchange插件实现延迟功能.

### 146. RabbitMQ 集群有什么用？

高可用, 高容量

### 147. RabbitMQ 节点的类型有哪些？

磁盘节点, 可持久化数据; 内存节点, 高效.

### 148. RabbitMQ 集群搭建需要注意哪些问题？

各节点之间用"-link"连接; 各节点使用erlang coolie值必须相同, 相当于密钥, 用于认证; 整个集群中必须包含一个磁盘节点.

### 149. RabbitMQ 每个节点是其他节点的完整拷贝吗？为什么？

不是, 原因有二: 存储空间和性能.

### 150. RabbitMQ 集群中唯一一个磁盘节点崩溃了会发生什么情况？

集群可以保持运行, 只是不能修改任何东西了. (1)不能创建队列;(2)不能创建交换器;(3)不能创建绑定;(4)不能添加用户;(5)不能更改权限;(6)不能添加删除节点.

### 151. RabbitMQ 对集群节点停止顺序有要求吗？

需要先关闭内存节点, 再关闭磁盘节点, 否则可能会导致数据丢失.

## Kafka

### 152. Kafka 可以脱离 ZooKeeper 单独使用吗？为什么？

不可以, kafka使用zookeeper协调管理kafka的节点服务器.

### 153. Kafka 有几种数据保留的策略？

两种: 按过期时间保留, 按存储消息大小保留.

### 154. Kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 Kafka 将如何处理？

两个规则为或的关系, 只要一个满足要求即清除数据.

### 155. 什么情况会导致 Kafka 运行变慢？

cpu, io, 网络

### 156. 使用 Kafka 集群需要注意什么？

集群节点最好不要超过7个, 节点越多消息复制需要的时间越长, 整个群组的吞吐量就越低. 集群数为2N+1个较好. 超过一半故障集群就不能用了, 单数容错更高一点.

## ZooKeeper

### 157. ZooKeeper 是什么？

zookeeper是分布式协调调度RPC框架, 它为分布式应用提供一致性服务, 包括配置注册中心,域名服务,分布式锁等.

数据采用树形方式, 可以支持临时和永久, 有序和无序两种方式的任意组合.

### 158. ZooKeeper 都有哪些功能？

事件监听, 文件存储; 适用的场景包括: 发布订阅,配置注册中心, 命名服务, leader选举, 负载均衡, 分布式队列, 分布式锁等.

### 159. ZooKeeper 有几种部署模式？

单实例部署, 集群部署.

### 160. ZooKeeper 怎么保证主从节点的状态同步？

 Zookeeper 的核心是原子广播，这个机制保证了各个Server之间的同步。实现这个机制的协议叫做Zab协议。Zab协议有两种模式，它们分别是恢复模式（选主）和广播模式（同步）。当服务启动或者在领导者崩溃后，Zab就进入了恢复模式，当领导者被选举出来，且大多数Server完成了和 leader的状态同步以后，恢复模式就结束了。状态同步保证了leader和Server具有相同的系统状态。

为了保证事务的顺序一致性，zookeeper采用了递增的事务id号（zxid）来标识事务。所有的提议（proposal）都在被提出的时候加上了zxid。实现中zxid是一个64位的数字，它高32位是epoch用来标识leader关系是否改变，每次一个leader被选出来，它都会有一个新的epoch，标识当前属于那个leader的统治时期。低32位用于递增计数。

### 161. 集群中为什么要有主节点？

分布式环境中, 有些业务逻辑只需要在集群中的某台服务器执行, 这样可以保证这些事务逻辑的原子性, 同时也保证只在一台服务器执行,这样可以提高性能, 减少重复计算.等执行完成后结果被其他的节点共享.

### 162. 集群中有 3 台服务器，其中一个节点宕机，这个时候 ZooKeeper 还可以使用吗？

可以使用, 一般集群的机器节点数为2N+1, 只要有大于一半的服务器在线即可正常提供服务, 三台宕机一台依然有两台可用.

### 163. 说一下 ZooKeeper  的通知机制？

zookeeper采用注册/监听方式, 使用`Watcher`来实现对节点和路径事件的监控.

## MySQL

### 164. 数据库的三范式是什么？

1. 原子性, 每个字段都只表示一个属性;

2. 每个字段均依赖于主键, 也就是一张表只表示一个对象;

3. 属性不能传递依赖,也就是有传递依赖的地方要拆分为不同表;

### 165. 一张自增表里面总共有 7 条数据，删除了最后 2 条数据，重启 MySQL 数据库，又插入了一条数据，此时 ID 是几？

Innodb和myIASM两种执行引擎的方式不同, Innodb会在内存中存储表中的自增id, myiasm是在表中保留, 因此innodb重启后会丢失最大id, 而会从现有表中计算所以结果为6, myiasm为8.

### 166. 如何获取当前数据库版本？

select version()

### 167. 说一下 ACID 是什么？

ACID是数据库事务的特性, A是atomicity, 即原子性, 原子性保证一个事务以一个整体逻辑执行, 要么成功, 要么失败, 执行完成后不会发生中间状态; C是consistency, 即一致性, 即事务执行开始和结束后, 数据的完整性没有遭到破坏; I是Isolation, 隔离性, 多个并发的事务对数据来说不会因为交叉执行而导致数据不一致, 数据库存在四个隔离级别, 分别解决不同程度的数据隔离;D 是 durability, 是持久性, 事务执行后对数据修改时永久的, 数据保持完成.

### 168. Char 和 VarChar 的区别是什么？

char是固定长度的, varchar是可变长度的,char可能会存在空间浪费的情况, varchar使用的空间是n+1, 其中有一个char单位用来保存长度, 性能方法, char的性能要高一点,

### 169. Float 和 Double 的区别是什么？

大小不同, float是4字节的, double是8字节的.

### 170. MySQL 的内连接、左连接、右连接有什么区别？

内连接是两个表能匹配的数据, 左连接和右连接则分别以左表或右边为主, 展示出左表或右表的数据, 对于匹配不到的, 右表或左表展示为null.

### 171. MySQL索引是怎么实现的？

mysql或其他数据库的索引大多采用B+树数据结构, B+树本身就是有序结构, 可以达到二分法的性能.

### 172. 怎么验证 MySQL的索引是否满足需求？

explain 查询语句, 查看执行计划

### 173. 说一下数据库的事务隔离？

MySql.ini配置文件有默认的事务隔离配置, transaction-isolution=REPEATABLE-READ.

事务有四个级别的隔离方式, 分别为:

READ-UNCOMMITED: 未提交读, 隔离级别最低, 可能导致脏读,幻读,不可重复读<br>
READ-COMMITED: 提交读, 可能导致幻读, 不可重复读, 可以避免脏读. 事务提交后其他事务才可见<br>
REPEATABLE-READ: 可重复读, 会造成幻读<br>
SERIALIZABLE: 序列化, 完全保证了事务是隔离的,但性能最低.<br>

### 174. 说一下 MySQL常用的引擎？

InnoDB: 提供了对数据库的acid事务支持, 并提供行级锁和外键约束, 它设计的目标就是处理大数据容量的数据库系统. 它会在启动时建立缓冲池, 用来缓存数据和索引. 但不支持全文索引, 启动也比较慢. 不会保存行数, 但并发环境下的读取效率很高.
MyIASM: 默认引擎, 不提供事务支持, 不支持行锁和外键. 所以变更时会锁表,效率比较低. 但其保存了行数, 读多余写的操作可以使用此搜索引擎.

### 175. 说一下 MySQL的行锁和表锁？

行锁是在数据变更时仅会在当前行加锁, 其他行还是可以访问的, 锁的级别较小, 不容易发生阻塞.表锁是变更时会对整个表加锁, 性能低下, 不利于并发.

### 176. 说一下乐观锁和悲观锁？

乐观锁是默认没有别的进程修改数据, 仅在提交更新时判定数据版本号是否与修改前一致; 悲观锁是默认认为数据在同一时间可能被其他进程修改, 因此先锁定数据, 修改后释放锁.

### 177. MySQL问题排查都有哪些手段？

show processlist, explain, 查看日志

### 178. 如何做 MySQL的性能优化？

索引, 合适的查询语句, 表分区, 正确的搜索引擎

## Redis

### 179. Redis 是什么？都有哪些使用场景？

redis是一种nosql数据库, 是用C实现的, 具有高性能, 单线程, 支持持久化, 支持集群的高可用内存数据库.

用来做数据库, 缓存, 消息中间件

### 180. Redis 有哪些功能？

复制, 集群, 持久化, 事务, 分布式锁,LUA脚本, LRU

### 181. Redis 和 MemeCache 有什么区别？

(1) 持久化的支持, 数据可靠性: redis可以做持久化, memcache是内存无法持久化; (2) 底层实现方面: redis利用单线程, memcache多线程, 可以使用多核CPU; (3). 数据结构方面: redis支持较多的数据结构, memcache仅仅是k-v结构;(4). 数据大小, 小于100kredis比较快, 大于100k,memcache较快, 但redis支持最大512M的数据, memcache最大为1M; (5)应用场景: memcache适合读多写少, 或数据比较大的对象,redis适合读写都很多, 比较复杂的数据结构.

### 182. Redis 为什么是单线程的？

redis是基于内存操作的, CPU不会存在瓶颈, 既然CPU不是瓶颈, 单线程又很容易实现, 那么redis自然就选择用单线程了.

对于多个CPU的服务器, 可以开多个redis实例来提高服务器资源使用率. 注意: redis4.0 开始可能会有条件地在某些操作时使用多线程.

### 183. 什么是缓存穿透？怎么解决？

缓存穿透，是指查询一个数据库一定不存在的数据。正常的使用缓存流程大致是，数据查询先进行缓存查询，如果key不存在或者key已经过期，再对数据库进行查询，并把查询到的对象，放进缓存。如果数据库查询对象为空，则不放进缓存。

解决方式：

1、在某些特定场景下（登录），进行验证码，这种方法并不是很安全，因为目前图像识别技术在很大程度上能够解决验证码的问题，所以仅供简单使用。

2、布隆过滤器

### 184. Redis 支持的数据类型有哪些？

String, Set, ZSet, List, Hash

不常见的有: Bitmaps，Hyperloglogs 和地理空间（Geospatial）索引半径查询

### 185. Redis 支持的 Java 客户端都有哪些？

Jedis, Redisson等, 官方推荐Redisson

### 186. Jedis 和 Redisson 有哪些区别？

jedis是对原生redis的简单封装, redisson是官方推荐的客户端程序, 除了基本的命令, 还有更丰富的数据结构以及锁的实现.

### 187. 怎么保证缓存和数据库数据的一致性？

更新时先删除缓存, 设置数据过期时间, 异步更新数据.

### 188. Redis 持久化有几种方式？

aof, rdb

### 189. Redis 怎么实现分布式锁？

setNX命令, 返回1表示成功, 0位失败.

### 190. Redis 分布式锁有什么缺陷？

执行时间超过锁超时时间时会导致并发问题.

### 191. Redis 如何做内存优化？

尽量使用Redis的散列表, 把相关信息放在散列表里面, 而不是各个字段单独存储, 这样可以有效减少内存.

### 192. Redis 淘汰策略有哪些？

六种, 分别是volatile-ttl, 过期的数据集中清除超时的;volatile-lru,过期的里面清除不常用的数据;volatile-random,过期的数据里面随机清除; allkeys-random, allkeys-lru, 与上面一样, 只是范围为所有的数据集.no-enviction,禁止淘汰

### 193. Redis 常见的性能问题有哪些？该如何解决？

redis是在进行持久化的时候会导致性能问题. 写内存快照会阻塞主线程, 当快照较大时会较长时间的导致服务暂停, 所有主服务器最好不要写快照. 主从复制的性能问题, 复制的速度和稳定性. 主从最好在一个局域网内.

## JVM

### 194. 说一下 JVM 的主要组成部分？及其作用？

类加载器(Class Loader) 用来将类文件加载到内存.<br>
执行引擎(Execution Engine) 用来解析指令, 提供给操作系统执行<br>
本地方法接口(Native Interface) 一些Java无法完成的任务 (1)与环境外交互;(2)与操作系统交互;<br>
运行时数据区(Runtime Data Area) 加载的程序和运行时的对象都存储在这里,主要分堆和栈, 这里(特别是堆)也是GC的主要区域.<br>
总的来说就是类加载器会将java代码转化为字节码, 运行时区把字节码加载到内存, 为了调用操作系统功能, 执行引擎需要调用本地方法.<br>

### 195. 说一下 JVM 运行时数据区？

线程私有的数据区

程序计数器

作用<br>
记录当前线程所执行到的字节码的行号。字节码解释器工作的时候就是通过改变这个计数器的值来选取下一条需要执行的字节码指令。

意义 <br>
JVM的多线程是通过线程轮流切换并分配处理器来实现的，对于我们来说的并行事实上一个处理器也只会执行一条线程中的指令。所以，为了保证各线程指令的安全顺利执行，每条线程都有独立的私有的程序计数器。

存储内容 <br>
当线程中执行的是一个Java方法时，程序计数器中记录的是正在执行的线程的虚拟机字节码指令的地址。 <br>
当线程中执行的是一个本地方法时，程序计数器中的值为空。

可能出现异常 <br>
此内存区域是唯一一个在JVM上不会发生内存溢出异常（OutOfMemoryError）的区域。<br>

虚拟机栈

作用 <br>
描述Java方法执行的内存模型。每个方法在执行的同时都会开辟一段内存区域用于存放方法运行时所需的数据，成为栈帧，一个栈帧包含如：局部变量表、操作数栈、动态链接、方法出口等信息。

意义 <br>
JVM是基于栈的，所以每个方法从调用到执行结束，就对应着一个栈帧在虚拟机栈中入栈和出栈的整个过程。

存储内容 <br>
局部变量表（编译期可知的各种基本数据类型、引用类型和指向一条字节码指令的returnAddress类型）、操作数栈、动态链接、方法出口等信息。 <br>
值得注意的是：局部变量表所需的内存空间在编译期间完成分配。在方法运行的阶段是不会改变局部变量表的大小的。<br>

可能出现的异常 <br>
如果线程请求的栈深度大于虚拟机所允许的深度，将抛出StackOverflowError异常。 <br>
如果在动态扩展内存的时候无法申请到足够的内存，就会抛出OutOfMemoryError异常。

本地方法栈

作用 <br>
为JVM所调用到的Nativa即本地方法服务。<br>

可能出现的异常 <br>
和虚拟机栈出现的异常很相像。<br>

所有线程共有的数据区

Java堆

作用 <br>
所有线程共享一块内存区域，在虚拟机开启的时候创建。<br>

意义 <br>
1、存储对象实例，更好地分配内存。 <br>
2、垃圾回收（GC）。堆是垃圾收集器管理的主要区域。更好地回收内存。

存储内容 <br>
存放对象实例，几乎所有的对象实例都在这里进行分配。堆可以处于物理上不连续的内存空间，只要逻辑上是连续的就可以。 <br>
值得注意的是：在JIT编译器等技术的发展下，所有对象都在堆上进行分配已变得不那么绝对。有些对象实例也可以分配在栈中。<br>

可能出现的异常 <br>
实现堆可以是固定大小的，也可以通过设置配置文件设置该为可扩展的。 <br>
如果堆上没有内存进行分配，并无法进行扩展时，将会抛出OutOfMemoryError异常。

方法区

作用 <br>
用于存储运行时常量池、已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

意义 <br>
对运行时常量池、常量、静态变量等数据做出了规定。

存储内容 <br>
运行时常量池（具有动态性）、已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

可能出现的异常 <br>
当方法区无法满足内存分配需求时，将抛出OutOfMemoryError异常。

### 196. 说一下堆栈的区别？

栈内存:栈内存首先是一片内存区域，存储的都是局部变量，凡是定义在方法中的都是局部变量（方法外的是全局变量），for循环内部定义的也是局部变量，是先加载函数才能进行局部变量的定义，所以方法先进栈，然后再定义变量，变量有自己的作用域，一旦离开作用域，变量就会被释放。栈内存的更新速度很快，因为局部变量的生命周期都很短。

堆内存:存储的是数组和对象（其实数组就是对象），凡是new建立的都是在堆中，堆中存放的都是实体（对象），实体用于封装数据，而且是封装多个（实体的多个属性），如果一个数据消失，这个实体也没有消失，还可以用，所以堆是不会随时释放的，但是栈不一样，栈里存放的都是单个变量，变量被释放了，那就没有了。堆里的实体虽然不会被释放，但是会被当成垃圾，Java有垃圾回收机制不定时的收取。


### 197. 队列和栈是什么？有什么区别？

队列和栈是两种不同的数据结构。它们有以下区别：

（1）操作的名称不同。队列的插入称为入队，队列的删除称为出队。栈的插入称为进栈，栈的删除称为出栈。

（2）可操作的方式不同。队列是在队尾入队，队头出队，即两边都可操作。而栈的进栈和出栈都是在栈顶进行的，无法对栈底直接进行操作。

（3）操作的方法不同。队列是先进先出（FIFO），即队列的修改是依先进先出的原则进行的。新来的成员总是加入队尾（不能从中间插入），每次离开的成员总是队列头上（不允许中途离队）。而栈为后进先出（LIFO）,即每次删除（出栈）的总是当前栈中最新的元素，即最后插入（进栈）的元素，而最先插入的被放在栈的底部，要到最后才能删除。

### 198. 什么是双亲委派模型？

双亲委派模型要求除顶层启动类加载器外其余类加载器都应该有自己的父类加载器；类加载器之间通过复用关系来复用父加载器的代码。

### 199. 说一下类加载的执行过程？

1、加载：这个很简单，程序运行之前jvm会把编译完成的.class二进制文件加载到内存，供程序使用，用到的就是类加载器classLoader ，这里也可以看出java程序的运行并不是直接依   靠底层的操作系统，而是基于jvm虚拟机。如果没有类加载器，java文件就只是磁盘中的一个普通文件。

2、连接：连接是很重要的一步，过程比较复杂，分为三步  验证  》准备  》解析  　　

验证：确保类加载的正确性。一般情况由javac编译的class文件是不会有问题的，但是可能有人的class文件是自己通过其他方式编译出来的，这就很有可能不符合jvm的编 译规则，这一步就是要过滤掉这部分不合法文件　

准备：为类的静态变量分配内存，将其初始化为默认值 。我们都知道静态变量是可以不用我们手动赋值的，它自然会有一个初始值 比如int 类型的初始值就是0 ；boolean类型初始值为false，引用类型的初始值为null 。 这里注意，只是为静态变量分配内存，此时是没有对象实例的　

解析：把类中的符号引用转化为直接引用。解释一下符号引用和直接引用。比如在方法A中使用方法B，A（）{B（）；}，这里的B（）就是符号引用，初学java时我们都是知道这是java的引用，以为B指向B方法的内存地址，但是这是不完整的，这里的B只是一个符号引用，它对于方法的调用没有太多的实际意义，可以这么认为，他就是给程序员看的一个标志，让程序员知道，这个方法可以这么调用，但是B方法实际调用时是通过一个指针指向B方法的内存地址，这个指针才是真正负责方法调用，他就是直接引用。

3、初始化：为类的静态变量赋予正确的初始值，上述的准备阶段为静态变量赋予的是虚拟机默认的初始值，此处赋予的才是程序编写者为变量分配的真正的初始值

### 200. 怎么判断对象是否可以被回收？

根搜索算法。这个算法的思路其实很简单，它把内存中的每一个对象都看作一个节点，并且定义了一些对象作为根节点“GC Roots”。如果一个对象中有另一个对象的引用，那么就认为第一个对象有一条指向第二个对象的边，如下图所示。JVM会起一个线程从所有的GC Roots开始往下遍历，当遍历完之后如果发现有一些对象不可到达，那么就认为这些对象已经没有用了，需要被回收。

### 201. Java 中都有哪些引用类型？

一，强引用

只要强引用存在，垃圾回收器将永远不会回收被引用的对象，哪怕内存不足时，JVM也会直接抛出OutOfMemoryError，不会去回收。如果想中断强引用与对象之间的联系，可以显示的将强引用赋值为null，这样一来，JVM就可以适时的回收对象了

二，软引用

软引用是用来描述一些非必需但仍有用的对象。在内存足够的时候，软引用对象不会被回收，只有在内存不足时，系统则会回收软引用对象，如果回收了软引用对象之后仍然没有足够的内存，才会抛出内存溢出异常。这种特性常常被用来实现缓存技术，比如网页缓存，图片缓存等。

三，弱引用

弱引用的引用强度比软引用要更弱一些，无论内存是否足够，只要 JVM 开始进行垃圾回收，那些被弱引用关联的对象都会被回收。在 JDK1.2 之后，用 java.lang.ref.WeakReference 来表示弱引用。

四，虚引用

虚引用是最弱的一种引用关系，如果一个对象仅持有虚引用，那么它就和没有任何引用一样，它随时可能会被回收，在 JDK1.2 之后，用 PhantomReference 类来表示，通过查看这个类的源码，发现它只有一个构造函数和一个 get() 方法，而且它的 get() 方法仅仅是返回一个null，也就是说将永远无法通过虚引用来获取对象，虚引用必须要和 ReferenceQueue 引用队列一起使用。

五，引用队列（ReferenceQueue）

引用队列可以与软引用、弱引用以及虚引用一起配合使用，当垃圾回收器准备回收一个对象时，如果发现它还有引用，那么就会在回收对象之前，把这个引用加入到与之关联的引用队列中去。程序可以通过判断引用队列中是否已经加入了引用，来判断被引用的对象是否将要被垃圾回收，这样就可以在对象被回收之前采取一些必要的措施。

与软引用、弱引用不同，虚引用必须和引用队列一起使用。

### 202. 说一下 JVM 有哪些垃圾回收算法？

1.对象是否“已死”算法——引用计数器算法

对象中添加一个引用计数器，如果引用计数器为0则表示没有其它地方在引用它。如果有一个地方引用就+1，引用失效时就-1。看似搞笑且简单的一个算法，实际上在大部分Java虚拟机中并没有采用这种算法，因为它会带来一个致命的问题——对象循环引用。对象A指向B，对象B反过来指向A，此时它们的引用计数器都不为0，但它们俩实际上已经没有意义因为没有任何地方指向它们。所以又引出了下面的算法。

2.对象是否“已死”算法——可达性分析算法

这种算法可以有效地避免对象循环引用的情况，整个对象实例以一个树呈现，根节点是一个称为“GC Roots”的对象，从这个对象开始向下搜索并作标记，遍历完这棵树过后，未被标记的对象就会判断“已死”，即为可被回收的对象。

GC算法

1.标记-清除算法

等待被回收对象的“标记”过程在上文已经提到过，如果在被标记后直接对对象进行清除，会带来另一个新的问题——内存碎片化。如果下次有比较大的对象实例需要在堆上分配较大的内存空间时，可能会出现无法找到足够的连续内存而不得不再次触发垃圾回收。

2.复制算法（Java堆中新生代的垃圾回收算法）

此GC算法实际上解决了标记-清除算法带来的“内存碎片化”问题。首先还是先标记处待回收内存和不用回收的内存，下一步将不用回收的内存复制到新的内存区域，这样旧的内存区域就可以全部回收，而新的内存区域则是连续的。它的缺点就是会损失掉部分系统内存，因为你总要腾出一部分内存用于复制。

3.标记-压缩算法（或称为标记-整理算法，Java堆中老年代的垃圾回收算法）

对于新生代，大部分对象都不会存活，所以在新生代中使用复制算法较为高效，而对于老年代来讲，大部分对象可能会继续存活下去，如果此时还是利用复制算法，效率则会降低。标记-压缩算法首先还是“标记”，标记过后，将不用回收的内存对象压缩到内存一端，此时即可直接清除边界处的内存，这样就能避免复制算法带来的效率问题，同时也能避免内存碎片化的问题。老年代的垃圾回收称为“Major GC”。

### 203. 说一下 JVM 有哪些垃圾回收器？

1, 串行回收器

1.1, 新生代串行回收器

1.2, 老年代串行回收器

2, 并行回收器

2.1, 新生代ParNew回收器

2.2, 新生代ParallelGC回收器

2.3, 老年代ParallelOldGC回收器

3, CMS回收器(Concurrent Mark Sweep，并发标记清除)

3.1, 老年代的并发回收器

3.2, Class的回收(永久区的回收)

4, G1回收器(jdk1.7后全新的回收器, 用于取代CMS)

### 204. 详细介绍一下 CMS 垃圾回收器？

CMS收集器是为了低延迟而生，通过尽可能的并行执行垃圾回收的几个阶段来把延迟控制到最低。CMS收集器是老年代的垃圾收集器，一般情况下会有ParNew来配合执行(默认情况下也是ParNew)，ParNew也是使用并行的算法来执行年轻代的回收。当然除此之外，你还可以选择使用Serial收集器来收集年轻代，不过一般很少这样使用。通过咱们说的CMS收集器是指广义上的CMS收集器，包含以下几个：ParNew（Young）GC + CMS（Old）GC ＋ Serial GC 算法（应对核心的CMS GC某些时候的不赶趟，开销很大）。

### 205. 新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？

CMS gc

CMS，全称Concurrent Low Pause Collector，是jdk1.4后期版本开始引入的新gc算法，在jdk5和jdk6中得到了进一步改进，它的主要适合场景是对响应时间的重要性需求大于对吞吐量的要求，能够承受垃圾回收线程和应用线程共享处理器资源，并且应用中存在比较多的长生命周期的对象的应用。CMS是用于对tenured generation的回收，也就是年老代的回收，目标是尽量减少应用的暂停时间，减少full gc发生的几率，利用和应用程序线程并发的垃圾回收线程来标记清除年老代。在我们的应用中，因为有缓存的存在，并且对于响应时间也有比较高的要求，因此希望能尝试使用CMS来替代默认的server型JVM使用的并行收集器，以便获得更短的垃圾回收的暂停时间，提高程序的响应性。

CMS并非没有暂停，而是用两次短暂停来替代串行标记整理算法的长暂停，它的收集周期是这样：

初始标记(CMS-initial-mark) -> 并发标记(CMS-concurrent-mark) -> 重新标记(CMS-remark) -> 并发清除(CMS-concurrent-sweep) ->并发重设状态等待下次CMS的触发(CMS-concurrent-reset)。

其中的1，3两个步骤需要暂停所有的应用程序线程的。第一次暂停从root对象开始标记存活的对象，这个阶段称为初始标记；第二次暂停是在并发标记之后，暂停所有应用程序线程，重新标记并发标记阶段遗漏的对象（在并发标记阶段结束后对象状态的更新导致）。第一次暂停会比较短，第二次暂停通常会比较长，并且 remark这个阶段可以并行标记。

而并发标记、并发清除、并发重设阶段的所谓并发，是指一个或者多个垃圾回收线程和应用程序线程并发地运行，垃圾回收线程不会暂停应用程序的执行，如果你有多于一个处理器，那么并发收集线程将与应用线程在不同的处理器上运行，显然，这样的开销就是会降低应用的吞吐量。Remark阶段的并行，是指暂停了所有应用程序后，启动一定数目的垃圾回收进程进行并行标记，此时的应用线程是暂停的。

 

full  gc

full gc是对新生代，旧生代，以及持久代的统一回收，由于是对整个空间的回收，因此比较慢，系统中应当尽量减少full gc的次数。

如下几种情况下会发生full gc：

《旧生代空间不足》

《持久代空间不足》

《CMS GC时出现了promotion failed和concurrent mode failure》

《统计得到新生代minor gc时晋升到旧生代的平均大小小于旧生代剩余空间》

《直接调用System.gc，可以DisableExplicitGC来禁止》

《存在rmi调用时，默认会每分钟执行一次System.gc，可以通过-Dsun.rmi.dgc.server.gcInterval=3600000来设置大点的间隔。》

### 206. 简述分代垃圾回收器是怎么工作的？

虚拟机中的共划分为三个代：年轻代（Young Generation）、年老点（Old Generation）和持久代（Permanent Generation）。其中持久代主要存放的是Java类的类信息，与垃圾收集要收集的Java对象关系不大。年轻代和年老代的划分是对垃圾收集影响比较大的。

年轻代:

所有新生成的对象首先都是放在年轻代的。年轻代的目标就是尽可能快速的收集掉那些生命周期短的对象。年轻代分三个区。一个Eden区，两个Survivor区(一般而言)。大部分对象在Eden区中生成。当Eden区满时，还存活的对象将被复制到Survivor区（两个中的一个），当这个Survivor区满时，此区的存活对象将被复制到另外一个Survivor区，当这个Survivor去也满了的时候，从第一个Survivor区复制过来的并且此时还存活的对象，将被复制“年老区(Tenured)”。需要注意，Survivor的两个区是对称的，没先后关系，所以同一个区中可能同时存在从Eden复制过来 对象，和从前一个Survivor复制过来的对象，而复制到年老区的只有从第一个Survivor去过来的对象。而且，Survivor区总有一个是空的。同时，根据程序需要，Survivor区是可以配置为多个的（多于两个），这样可以增加对象在年轻代中的存在时间，减少被放到年老代的可能。

年老代:

在年轻代中经历了N次垃圾回收后仍然存活的对象，就会被放到年老代中。因此，可以认为年老代中存放的都是一些生命周期较长的对象。

持久代:

用于存放静态文件，如今Java类、方法等。持久代对垃圾回收没有显著影响，但是有些应用可能动态生成或者调用一些class，例如Hibernate等，在这种时候需要设置一个比较大的持久代空间来存放这些运行过程中新增的类。持久代大小通过-XX:MaxPermSize=<N>进行设置。