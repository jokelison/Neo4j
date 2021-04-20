# Neo4j
### First step：导入数据：
#### 找到安装目录中的import文件夹，将数据复制过去，然后通过load语句导入:
load csv with headers from 'file:///user-device.csv' as line 
merge(u:user_device{user_id:line.user_id,status:line.status})

 * Neo4j数据库服务器使用此<node-name>将此节点详细信息存储在Database.As中作为Neo4j DBA或Developer，我们不能使用它来访问节点详细信息。
 * Neo4j数据库服务器创建一个<label-name>作为内部节点名称的别名。作为Neo4j DBA或Developer，我们应该使用此标签名称来访问节点详细信息。
 
 
>Neo4j CQL DELETE和REMOVE命令之间的主要区别 - 
>>DELETE操作用于删除节点和关联关系。
>>REMOVE操作用于删除标签和属性。

>Neo4j CQL DELETE和REMOVE命令之间的相似性 - 
>>这两个命令不应单独使用。
>>两个命令都应该与MATCH命令一起使用。

