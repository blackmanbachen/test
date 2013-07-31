### 利用aop进行事务编程  Spring事务配置的五种方式 
  <a href="http://www.blogjava.net/images/blogjava_net/robbie/WindowsLiveWriter/Spring_9C9C/Spring%E4%BA%8B%E5%8A%A1%E9%85%8D%E7%BD%AE%20(2)_thumb.jpg" target="_blank">Spring事务体系图</a>
	* <a href="https://github.com/zhangkaitao/es/blob/master/src/support/img/1.PNG?raw=true" target="_blank">点击查看1</a>
	* 传统上，J2EE开发者有两个事务管理的选择： 全局 或 本地事务（局部事务）。全局事务由应用服务器管理，使用JTA。局部事务是和资源相关的，比如一个和JDBC连接关联的事务
    
#### 事务种类分为： jdbc事务（局部事务） jta事务（全局事务） 容器事务
		* JDBC事务控制的局限性在一个数据库连接内，但是其使用简单。局部事务
		* JTA事务的功能强大，事务可以跨越多个数据库或多个DAO，使用也比较复杂。全局事务
		* 容器事务，主要指的是J2EE应用服务器提供的事务管理，局限于EJB应用
		
### 两种事务的比较 
		* JDBC事务控制的局限性在一个数据库连接内，但是其使用简单。
		* JTA事务的功能强大，事务可以跨越多个数据库或多个DAO，使用也比较复杂  

### 从实现的角度划分Spring把事务分为两种
		* 一种是：编程式事务:编程式事务是侵入式事务 比较灵活，编程式事务则要操作逻辑代码。存在重复的代码比较多，相对繁琐，而且不利于系统的扩展；
		* 一种是声明式事务:声明式事务是非侵入式的事务。声明式事务只需在配置文件中配置，而不需要去操作逻辑代码。
	   
### Spring配置文件中关于事务配置总是由三个组成部分
		* DataSource
		* TransactionManager
		* Proxy 

#无论哪种配置方式，一般变化的只是代理机制这部 DataSource、TransactionManager这两部分只是会根据数据访问方式有所变化，比如使用Hibernate进行数据访问时，
#DataSource实际为SessionFactory，TransactionManager的实现为HibernateTransactionManager。根据代理机制的不同，总结了五种Spring事务的配置方式
