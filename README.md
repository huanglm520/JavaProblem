# Java常见面试题200道
Java 基础

1. JDK 和 JRE 有什么区别？

2. == 和 equals 的区别是什么？

3. 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

4. final 在 Java 中有什么作用？

5. Java 中的 Math.round(-1.5) 等于多少？

6. String 属于基础的数据类型吗？

7. Java 中操作字符串都有哪些类？它们之间有什么区别？

8. String str="i"与 String str=new String(“i”)一样吗？

9. 如何将字符串反转？

10. String 类的常用方法都有那些？

11. 抽象类必须要有抽象方法吗？

12. 普通类和抽象类有哪些区别？

13. 抽象类能使用 final 修饰吗？

14. 接口和抽象类有什么区别？

15. Java 中 IO 流分为几种？

16. BIO、NIO、AIO 有什么区别？

17. Files的常用方法都有哪些？

容器

18. Java 容器都有哪些？

19. Collection 和 Collections 有什么区别？

20. List、Set、Map 之间的区别是什么？

21. HashMap 和 Hashtable 有什么区别？

22. 如何决定使用 HashMap 还是 TreeMap？

23. 说一下 HashMap 的实现原理？

24. 说一下 HashSet 的实现原理？

25. ArrayList 和 LinkedList 的区别是什么？

26. 如何实现数组和 List 之间的转换？

27. ArrayList 和 Vector 的区别是什么？

28. Array 和 ArrayList 有何区别？

29. 在 Queue 中 poll()和 remove()有什么区别？

30. 哪些集合类是线程安全的？

31. 迭代器 Iterator 是什么？

32. Iterator 怎么使用？有什么特点？

33. Iterator 和 ListIterator 有什么区别？

34. 怎么确保一个集合不能被修改？

多线程

35. 并行和并发有什么区别？

36. 线程和进程的区别？

37. 守护线程是什么？

38. 创建线程有哪几种方式？

39. 说一下 runnable 和 callable 有什么区别？

40. 线程有哪些状态？

41. sleep() 和 wait() 有什么区别？

42. notify()和 notifyAll()有什么区别？

43. 线程的 run()和 start()有什么区别？

44. 创建线程池有哪几种方式？

45. 线程池都有哪些状态？

46. 线程池中 submit()和 execute()方法有什么区别？

47. 在 Java 程序中怎么保证多线程的运行安全？

48. 多线程锁的升级原理是什么？

49. 什么是死锁？

50. 怎么防止死锁？

51. ThreadLocal 是什么？有哪些使用场景？

52. 说一下 Synchronized 底层实现原理？

53. Synchronized 和 volatile 的区别是什么？

54. Synchronized 和 Lock 有什么区别？

55. Synchronized 和 ReentrantLock 区别是什么？

56. 说一下 Atomic 的原理？

反射

57. 什么是反射？

58. 什么是 Java 序列化？什么情况下需要序列化？

59. 动态代理是什么？有哪些应用？

60. 怎么实现动态代理？

对象拷贝

61. 为什么要使用克隆？

62. 如何实现对象克隆？

63. 深拷贝和浅拷贝区别是什么？

Java Web

64. JSP 和 servlet 有什么区别？

65. JSP 有哪些内置对象？作用分别是什么？

66. 说一下 JSP 的 4 种作用域？

67. Session 和 Cookie 有什么区别？

68. 说一下 Session 的工作原理？

69. 如果客户端禁止 Cookie 能实现 Session 还能用吗？

70. Spring MVC 和 Struts 的区别是什么？

71. 如何避免 SQL 注入？

72. 什么是 XSS 攻击，如何避免？

73. 什么是 CSRF 攻击，如何避免？

异常

74. throw 和 throws 的区别？

75. final、finally、finalize 有什么区别？

76. try-catch-finally 中哪个部分可以省略？

77. try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

78. 常见的异常类有哪些？

网络

79. HTTP 响应码 301 和 302 代表的是什么？有什么区别？

80. forward 和 redirect 的区别？

81. 简述 TCP 和 UDP 的区别？

82. TCP 为什么要三次握手，两次不行吗？为什么？

83. 说一下 TCP 粘包是怎么产生的？

84. OSI 的七层模型都有哪些？

85. Get和 Post 请求有哪些区别？

86. 如何实现跨域？

87. 说一下 JSONP 实现原理？

设计模式

88. 说一下你熟悉的设计模式？

89. 简单工厂和抽象工厂有什么区别？

Spring/Spring MVC

90. 为什么要使用 Spring？

91. 解释一下什么是 AOP？

92. 解释一下什么是 IOC？

93. Spring 有哪些主要模块？

94. Spring 常用的注入方式有哪些？

95. Spring 中的 Bean 是线程安全的吗？

96. Spring 支持几种 Bean 的作用域？

97. Spring 自动装配 Bean 有哪些方式？

98. Spring 事务实现方式有哪些？

99. 说一下 Spring 的事务隔离？

100. 说一下 Spring MVC 运行流程？

101. Spring MVC 有哪些组件？

102. @RequestMapping 的作用是什么？

103. @Autowired 的作用是什么？

Spring Boot/Spring Cloud

104. 什么是 Spring Boot？

105. 为什么要用 Spring Boot？

106. Spring Boot 核心配置文件是什么？

107. Spring Boot 配置文件有哪几种类型？它们有什么区别？

108. Spring Boot 有哪些方式可以实现热部署？

109. JPA 和 Hibernate 有什么区别？

110. 什么是 Spring Cloud？

111. Spring Cloud 断路器的作用是什么？

112. Spring Cloud 的核心组件有哪些？

Hibernate

113. 为什么要使用 Hibernate？

114. 什么是 ORM 框架？

115. Hibernate 中如何在控制台查看打印的 SQL 语句？

116. Hibernate 有几种查询方式？

117. Hibernate 实体类可以被定义为 final 吗？

118. 在 Hibernate 中使用 Integer 和 int 做映射有什么区别？

119. Hibernate 是如何工作的？

120. get()和 load()的区别？

121. 说一下 Hibernate 的缓存机制？

122. Hibernate 对象有哪些状态？

123. 在 Hibernate 中 getCurrentSession 和 openSession 的区别是什么？

124. Hibernate 实体类必须要有无参构造函数吗？为什么？

Mybatis

125. Mybatis 中 #{}和 ${}的区别是什么？

126. Mybatis 有几种分页方式？

127. RowBounds 是一次性查询全部结果吗？为什么？

128. Mybatis 逻辑分页和物理分页的区别是什么？

129. Mybatis 是否支持延迟加载？延迟加载的原理是什么？

130. 说一下 Mybatis 的一级缓存和二级缓存？

131. Mybatis 和 Hibernate 的区别有哪些？

132. Mybatis 有哪些执行器（Executor）？

133. Mybatis 分页插件的实现原理是什么？

134. Mybatis 如何编写一个自定义插件？

RabbitMQ

135. RabbitMQ 的使用场景有哪些？

136. RabbitMQ 有哪些重要的角色？

137. RabbitMQ 有哪些重要的组件？

138. RabbitMQ 中 VHost 的作用是什么？

139. RabbitMQ 的消息是怎么发送的？

140. RabbitMQ 怎么保证消息的稳定性？

141. RabbitMQ 怎么避免消息丢失？

142. 要保证消息持久化成功的条件有哪些？

143. RabbitMQ 持久化有什么缺点？

144. RabbitMQ 有几种广播类型？

145. RabbitMQ 怎么实现延迟消息队列？

146. RabbitMQ 集群有什么用？

147. RabbitMQ 节点的类型有哪些？

148. RabbitMQ 集群搭建需要注意哪些问题？

149. RabbitMQ 每个节点是其他节点的完整拷贝吗？为什么？

150. RabbitMQ 集群中唯一一个磁盘节点崩溃了会发生什么情况？

151. RabbitMQ 对集群节点停止顺序有要求吗？

Kafka

152. Kafka 可以脱离 ZooKeeper 单独使用吗？为什么？

153. Kafka 有几种数据保留的策略？

154. Kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 Kafka 将如何处理？

155. 什么情况会导致 Kafka 运行变慢？

156. 使用 Kafka 集群需要注意什么？

ZooKeeper

157. ZooKeeper 是什么？

158. ZooKeeper 都有哪些功能？

159. ZooKeeper 有几种部署模式？

160. ZooKeeper 怎么保证主从节点的状态同步？

161. 集群中为什么要有主节点？

162. 集群中有 3 台服务器，其中一个节点宕机，这个时候 ZooKeeper 还可以使用吗？

163. 说一下 ZooKeeper  的通知机制？

MySQL

164. 数据库的三范式是什么？

165. 一张自增表里面总共有 7 条数据，删除了最后 2 条数据，重启 MySQL 数据库，又插入了一条数据，此时 ID 是几？

166. 如何获取当前数据库版本？

167. 说一下 ACID 是什么？

168. Char 和 VarChar 的区别是什么？

169. Float 和 Double 的区别是什么？

170. MySQL 的内连接、左连接、右连接有什么区别？

171. MySQL索引是怎么实现的？

172. 怎么验证 MySQL的索引是否满足需求？

173. 说一下数据库的事务隔离？

174. 说一下 MySQL常用的引擎？

175. 说一下 MySQL的行锁和表锁？

176. 说一下乐观锁和悲观锁？

177. MySQL问题排查都有哪些手段？

178. 如何做 MySQL的性能优化？

Redis

179. Redis 是什么？都有哪些使用场景？

180. Redis 有哪些功能？

181. Redis 和 MemeCache 有什么区别？

182. Redis 为什么是单线程的？

183. 什么是缓存穿透？怎么解决？

184. Redis 支持的数据类型有哪些？

185. Redis 支持的 Java 客户端都有哪些？

186. Jedis 和 Redisson 有哪些区别？

187. 怎么保证缓存和数据库数据的一致性？

188. Redis 持久化有几种方式？

189. Redis 怎么实现分布式锁？

190. Redis 分布式锁有什么缺陷？

191. Redis 如何做内存优化？

192. Redis 淘汰策略有哪些？

193. Redis 常见的性能问题有哪些？该如何解决？

JVM

194. 说一下 JVM 的主要组成部分？及其作用？

195. 说一下 JVM 运行时数据区？

196. 说一下堆栈的区别？

197. 队列和栈是什么？有什么区别？

198. 什么是双亲委派模型？

199. 说一下类加载的执行过程？

200. 怎么判断对象是否可以被回收？

201. Java 中都有哪些引用类型？

202. 说一下 JVM 有哪些垃圾回收算法？

203. 说一下 JVM 有哪些垃圾回收器？

204. 详细介绍一下 CMS 垃圾回收器？

205. 新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？

206. 简述分代垃圾回收器是怎么工作的？

207. 说一下 JVM 调优的工具？

208. 常用的 JVM 调优的参数都有哪些？
