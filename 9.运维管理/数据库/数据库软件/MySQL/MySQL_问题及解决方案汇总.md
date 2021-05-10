#MySQL_问题及解决方案汇总

* mysql社区版下载地址
https://downloads.mysql.com/archives/community/




* mysql-5.1.48-win32.msi安装详细图解
https://wenku.baidu.com/view/ba83fca0aa00b52acfc7cab1.html

* SpringBoot启动出现java.sql.SQLNonTransientConnectionException: CLIENT_PLUGIN_AUTH is required
https://blog.csdn.net/Demorea/article/details/86509421


* mysql远程连接 Host * is not allowed to connect to this MySQL server
https://blog.csdn.net/qq_39781497/article/details/81302950

* 日期格式0000-00-00 00:00:00的处理方法
https://www.jianshu.com/p/e04c9085f3f1
https://www.cnblogs.com/wang666/p/9186559.html

* CentOS7安装MySQL8.0图文教程
    * 【RPM方式】
https://blog.csdn.net/weixin_42266606/article/details/80879571?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase

    * 【压缩包方式】
https://blog.csdn.net/qq_40181063/article/details/90713153?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-4.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-4.nonecase
https://blog.csdn.net/qq_36564461/article/details/99824707?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-9.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-9.nonecase

MySQL5.7版本sql_mode=only_full_group_by问题解决办法
https://blog.csdn.net/weixin_43064185/article/details/99646535

使用MYSQL实现Oracle的Start with...Connect By递归树查询
https://blog.csdn.net/jarniyy/article/details/72772525

# 查询所有子节点
```sql
BEGIN 
	 DECLARE pTemp VARCHAR(16383);  
	 DECLARE cTemp VARCHAR(16383);  
	
	 SET pTemp = '$';  
	 SET cTemp =rootDm;  
	
	 WHILE cTemp is not null DO  
		 SET pTemp = concat(pTemp,',',cTemp);  
		 SELECT group_concat(DM) INTO cTemp FROM zygl_ys_zzjgxxb   
		 WHERE FIND_IN_SET(FDM,cTemp)>0;
	 END WHILE;  
	 RETURN pTemp;  
END
```

# 查询所有父节点
```sql
BEGIN 
	 DECLARE pTemp VARCHAR(16383);  
	 DECLARE cTemp VARCHAR(16383);  
	
	 SET pTemp = '$';  
	 SET cTemp =rootDm;  
	
	 WHILE cTemp is not null DO  
		 SET pTemp = concat(pTemp,',',cTemp);  
		 SELECT group_concat(FDM) INTO cTemp FROM zygl_ys_zzjgxxb   
		 WHERE FIND_IN_SET(DM,cTemp)>0;
	 END WHILE;  
	 RETURN pTemp;
END
```

SQL函数Group_concat用法
https://blog.csdn.net/qq_35531549/article/details/90383022

mysql中find_in_set()函数的使用及in()用法详解
https://www.jb51.net/article/143105.htm