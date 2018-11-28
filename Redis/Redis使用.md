# Redis使用

## Redis数据结构

Key-value键值对存值,下面是key的类型

* String
  * set key value
  * get key
  * getset key value 取值的同时存值
  * del key
  * incr key 增一
  * incr key increment 增指定大小
  * decr key decrment 减指定大小
  * append key value 添加字符串
* hash
  * 存的是key-value
  * hset key field value 设置一个键值对
  * hmset key field value (filed value) 设置多个
  * hmget key fileds 获取多个值
  * hgetall Key 获取所有键值
  * hget key field 获取指定键值
  * hdel key field
  * hincrby key field increment
  * hexists key filed 判断filed是否存在
  * hlen Key 获取key包含filed的数据量?
  * hkeys Key 获取Key的所有key
  * hval Key 获取Key的所有value
* list
  * lpush Key values(v1 v2 v3)
  * rpush Key values(v1 v2 v3)
  * lrange Key start end  从零开始计数 -1表示链表尾 -2表示倒数第二个
  * lpop key 头部弹出
  * rpop key 尾部弹出
  * llen key 获取个数
  * lpushx key value key存在时插入value,不存在时不做添加.相当于修改
  * rpushx key value key
  * lrem key count value 遍历删除值为value的元素 count表示开始下标 正数表示从头到尾负数表示从尾到头
  * lset key index value 设置指定下标的值
  * linsert key before | after pivot value 在pivot元素前面或者后面插入value
  * rpoplpush 源 目标 源尾部元素移动到目标头部
* set
* sorted set

## Keys通用操作

* keys pattern 获取与pattern匹配的key *表示一个或多个字符 ?表示一个字符
* exists key 判断是否存在 1表示存在 0表示不存在
* rename key newkey 重命名key
* expire key 设置过期时间,单位秒 过期后删除
* ttl key 获取key剩余的时间,没有设置过期时间返回-1,不存在返回-2
* type key 返回key的数据类型

## Redis多数据库

一个Redis实例有16个数据库,默认使用第0个数据库

* select 0~15 切换数据库

## Redis常见服务器命令

* ping 连接是否存活
* echo 打印内容
* quit 退出连接
* dbsize 返回当前数据库key的数目
* info 服务器信息
* flushdb 删除当前数据库所有key
* flushall 删除所有数据库所有key
