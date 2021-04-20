# Neo4j

First step：导入数据：找到安装目录中的import文件夹，将数据复制过去，然后通过load语句导入</n>
load csv with headers from 'file:///user-device.csv' as line 
merge(u:user_device{user_id:line.user_id,status:line.status})
