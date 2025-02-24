JDBC 事务

事务隔离性用于指定事务中对数据操作对其他事务的可见性

* 脏读

	发生在数据允许读取未提交的数据。

	A 修改事务未提交，A 修改数据对其他事务可见。B能够读取修改的数据，一旦A发生回滚，B读取的就是错误的数据。

* 不可重复读
	1. A 读取一行数据
	2. B修改该行数据
	3. A再次读取该行数据，将得到不同的结果

* 幻读
	1. A通过where读取多行数据
	2. B插入若干条数据
	3. A再次通过相同条件再次读取数据时，将会读取到插入的数据

事务隔离级别

* TRANSACTION_NONE: 表示驱动不支持事务。
* TRANSACTION_READ_UNCOMMITED : 允许事务读取未提交更改的数据，意味着会出现脏读，不可重复读，幻读等现象。
* TRANSACTION_READ_COMMITED: 表示事务对任何数据更改，在未提交前对其他事务是不可见的。防止脏读，不能解决不可重复读和幻读。
* TRANSACTION_REPEATABLE_READ : 表示能够解决脏读和不可重复读，不能解决幻读。
* TRANSACTION_SERIALIZABLE: 该事务级别下，所有事务串行执行，能够解决脏读，不可重复读，幻读问题。但是并发效率较低。