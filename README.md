# Neo4j
### First step：导入数据：
#### 找到安装目录中的import文件夹，将数据复制过去，然后通过load语句导入:
create index on:device(device_id);
load csv with headers from "file:///user-device.csv" as line
merge (u:device{device_id:line.device_id,status:line.status})

> * Neo4j数据库服务器使用此<node-name>将此节点详细信息存储在Database.As中作为Neo4j DBA或Developer，我们不能使用它来访问节点详细信息。
> * Neo4j数据库服务器创建一个<label-name>作为内部节点名称的别名。作为Neo4j DBA或Developer，我们应该使用此标签名称来访问节点详细信息。

Neo4j图数据库遵循属性图模型来存储和管理其数据。根据属性图模型，关系应该是定向的。否则，Neo4j将抛出一个错误消息。/
基于方向性，Neo4j关系被分为两种主要类型。/
单向关系/
双向关系/
 
>Neo4j CQL DELETE和REMOVE命令之间的主要区别 - 
>>* DELETE操作用于删除节点和关联关系。
>>* REMOVE操作用于删除标签和属性。

>Neo4j CQL DELETE和REMOVE命令之间的相似性 - 
>>* 这两个命令不应单独使用。
>>* 两个命令都应该与MATCH命令一起使用。

load csv with headers from "file:///user-device.csv" as line\
match (fr:user{user_id:line.user_id}),(to:device{device_id:line.device_id})\
merge (fr)-[r:use]->(to)\

##### (x:y) 其中x为结点名字（neo4j并不能用它作为条件查询），y为节点别名（label）：请注意此处label不同与建模中的label，此处label是别名，这个可以用来查询\
##### {x:y} 其中x为属性名称，y为属性值\
##### [x:y] 其中x为关系节点（虚，实际不存在），y为关系别名。关系后面同样可以添加属性。\
##### 节点x.y 此时y为x节点中的属性名，注意此时不是用节点的别名\


>PS:在对节点进行查询时，主要是依靠节点的别名。而节点的名，其实更倾向于是一个变量

分组后筛选：
>match (from:user)-[rel:use]-()
>WITH from, count(rel) AS a
>where a>5
>return from.user_id,a
>>其中with处，from不能换成from.user_id，即此处仅能够填节点名称
>>with 其实就是代替了sql中的gruopby函数，即with就相当于分组了，表内仅剩下分组的内容

直接分组：
>match (from:userip)-[rel:in]-(to:user)
>return from.ip,count(rel)

<img width="906" alt="截屏2021-04-22 下午5 29 55" src="https://user-images.githubusercontent.com/30766357/115691160-5d3f9c00-a390-11eb-8a96-7af82389fb9c.png">

子查询：
<img width="955" alt="截屏2021-04-23 下午4 57 46" src="https://user-images.githubusercontent.com/30766357/115846978-0a7be800-a455-11eb-96f8-630836eac989.png">

