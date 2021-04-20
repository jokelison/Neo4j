# Neo4j
### First step：导入数据：
#### 找到安装目录中的import文件夹，将数据复制过去，然后通过load语句导入:
create index on:device(device_id);
load csv with headers from "file:///user-device.csv" as line
merge (u:device{device_id:line.device_id,status:line.status})

> * Neo4j数据库服务器使用此<node-name>将此节点详细信息存储在Database.As中作为Neo4j DBA或Developer，我们不能使用它来访问节点详细信息。
> * Neo4j数据库服务器创建一个<label-name>作为内部节点名称的别名。作为Neo4j DBA或Developer，我们应该使用此标签名称来访问节点详细信息。
 
 
>Neo4j CQL DELETE和REMOVE命令之间的主要区别 - 
>>* DELETE操作用于删除节点和关联关系。
>>* REMOVE操作用于删除标签和属性。

>Neo4j CQL DELETE和REMOVE命令之间的相似性 - 
>>* 这两个命令不应单独使用。
>>* 两个命令都应该与MATCH命令一起使用。

load csv with headers from "file:///user-device.csv" as line\
match (fr:user{user_id:line.user_id}),(to:device{device_id:line.device_id})\
merge (fr)-[r:use]->(to)\

(x:y) 其中x为结点名字（neo4j并不能用它作为条件查询），y为节点别名（label）：请注意此处label不同与建模中的label，此处label是别名，这个可以用来查询\
{x:y} 其中x为属性名称，y为属性值\
[x:y] 其中x为关系节点（虚，实际不存在），y为关系别名。关系后面同样可以添加属性。\
