## MySQL删除/更新数据时报1175错误

[原文地址](https://blog.csdn.net/yhawaii/article/details/7941948)

##### 今天删除mysql数据库中的一条记录的时候，一直不能删除，提示错误信息如下：
> 1 Error Code: 1175. You are using safe update mode and you tried to update a table without a WHERE that
> 2 uses a KEY column To disable safe mode, toggle the option in Preferences -> SQL Editor -> Query Editor and reconnect.  

**后来通过搜索资料，发现mysql有个叫SQL_SAFE_UPDATES的变量，为了数据库更新操作的安全性，此值默认为1，所以才会出现更新失败的情况。**

---
#### 下面是SQL_SAFE_UPDATES变量为0和1时的取值说明：
+ SQL_SAFE_UPDATES有两个取值0和1，
+ SQL_SAFE_UPDATES = 1时，不带where和limit条件的update和delete操作语句是无法执行的，即使是有where和limit条件但不带key column的update和delete也不能执行。
+ SQL_SAFE_UPDATES = 0时，update和delete操作将会顺利执行。那么很显然，此变量的默认值是1。  