# Jedis连接Redis

## 导包

```xml
<!-- https://mvnrepository.com/artifact/redis.clients/jedis -->
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>2.9.0</version>
</dependency>
<!-- 单元测试 -->
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
</dependency>
```

## 测试

```java
package testjedis;

import org.junit.Test;
import redis.clients.jedis.HostAndPort;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisCluster;

import java.io.IOException;
import java.util.HashSet;
import java.util.Set;

public class testone{
    @Test
    public void test1(){//单个redis
        Jedis jedis = new Jedis("192.168.200.126",6379);//不适用于集群.
        System.out.println(jedis);
        //redis.clients.jedis.exceptions.JedisMovedDataException: MOVED 5798 192.168.200.126:6379.不适用于集群.
        String name = jedis.get("name");
        System.out.println(name);
        jedis.close();
    }
    @Test
    public void test2() throws IOException {//集群

        //创建node对象
        Set<HostAndPort> nodes = new HashSet<HostAndPort>();
        nodes.add(new HostAndPort("192.168.200.127", 6379));
        nodes.add(new HostAndPort("192.168.200.126", 6379));
        nodes.add(new HostAndPort("192.168.200.125", 6379));
        nodes.add(new HostAndPort("192.168.200.124", 6379));
        nodes.add(new HostAndPort("192.168.200.123", 6379));
        nodes.add(new HostAndPort("192.168.200.122", 6379));

        //创建jediscluster对象
        JedisCluster cluster = new JedisCluster(nodes);

        String name = cluster.get("name");
        System.out.println(name);

        String age = cluster.get("age");
        System.out.println(age);

        cluster.close();

    }
}

```
