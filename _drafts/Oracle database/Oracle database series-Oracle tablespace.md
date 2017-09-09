
**创建表空间**

```
    CREATE [ TEMPORARY | UNDO ] TALBESPACE tablespace_name
    [
       DATAFILE | TEMPFILE 'file_name' SIZE size K | M [ REUSE ]
       [
          AUTOEXTEND OFF | ON
          [NEXT number K | M MAXSIZE UNLIMITED | number K | M ]
       ]
       [, ...]

    ] 

    [ MININUM EXTENT number K | M]
    [ BLOCKSIZE number K ]
    [ ONLINE | OFFLINE ]
    [ LOGGING | NOLOGGING ]
    [ FORCE LOGGING ]
    [ DEFAULT STORAGE storage ]
    [ COMPRESS | NOCOMPRESS ]
    [ PERMANENT | TEMPORARY ]
    [
       EXTENT MANAGEMENT DICTIONARY | LOCAL
       [ AUTOALLOCATE | UNIFORM SIZE number K | M]

    ]
    [  SEGMENT SPACE MANAGERMENT AUTO | MUNUAL]
```       
> 创建一个永久性表空间myspace,数据文件大小为20MB,自动增长,每次增长为5MB,最大可为100MB
 

```sql
   CREATE TABLESPACE myspace
   DATAFILE 'myspace.dbf'
   SIZE 20M
   AUTOEXTEND ON NEXT 5M
   MAXSIZE 100M;
```

> 查看创建的表空间的状态和属性


```sql
   SELECT tablespace_name, logging , allocation_type,
   extent_management, segment_space_management
   FROM dba_tablespaces
   WHERE tablespace_name = 'MYSPACE';
```

 **<span style="color:#338DCD">表空间的属性</span>**
 > 表空间的状态属性分为4个
  
  + 在线(ONLINE)
  + 离线(OFFLINE)
  + 只读(READONLY)
  + 读写(READWRITE)

  在线: 当表空间为在线状态时候，允许访问该表空间的数据。</br>
  离线: 当表空间为离线状态时候，不允许访问该表空间中的数据, 创建表和读取表空间的表的数据都是不允许的</br>
  只读: 当表空间为READ ONLY 时，只能访问表空间的数据，但是不能进行任何的修改和更新的操作。</br>
  读写: 当表空间的状态为读写时候，可以对表空间进行正常的访问包括查询、更新和删除的操作。


修改表空间的状态

```
    语法: ALTER TABLESPACE tablespace_name [ONLINE | OFFLINE | READ ONLY | READWRITE] parameter;

```     

    修改表空间的状态为离线状态


```sql
   SELECT tablespace_name , status  FROM dba_tablespaces; //查看表空间
   ALTER TABLESPACE myspace OFFLINE; 
   SELECT tablespace_name , status  FROM dba_tablespaces; //查看当前表空间的状态
```

 
    修改表空间的状态为在线状态

```sql
    SELECT tablespace_name, status FROM dba_tablespaces;
    ALTER TABLESPACE myspace ONLINE;
    SELECT tablespace_name , status FROM dba_tablespaces; 
```
     
     修改表空间的状态为READ ONLY状态

```sql
    SELECT tablespace_name, status FROM dba_tablespaces;
    ALTER TABLESPACE myspace READ ONLY;
    SELECT tablespace_name , status FROM dba_tablespaces;
```
注意: 当将表空间的状态修改为READ ONLY 之前，需要注意如下事项:

    1. 表空间必须处于ONLINE状态。
    2. 表空间不能包含任何事务的回退段。
    3. 表空间不能正处于在线数据库备份时期。         
   

     修改表空间的状态为READ　WRITE状态

```sql
    SELECT tablespace_name, status FROM dba_tablespaces;
    ALTER TABLESPACE myspace READ WRITE;
    SELECT tablespace_name , status FROM dba_tablespaces;
```  

注意: 当将表空间的状态修改为READ WRITE之前,需要保证表空间处于ONLINE状态。

