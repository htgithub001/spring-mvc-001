# 注意Jedis对象并不是线程安全的

在多线程下使用同一个Jedis对象会出现并发问题。

为了避免每次使用Jedis对象时都需要重新构建，Jedis提供了JedisPool。

JedisPool是基于Commons Pool 2实现的一个线程安全的连接池。

来源：https://www.jianshu.com/p/7913f9984765

```
<dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>2.8.0</version>
    </dependency>
```

创建Jedis对象，调用set方法，并通过get方法获取到值并打印：

```
    Jedis jedis = new Jedis("localhost", 6379);
    jedis.set("singleJedis", "hello jedis!");
    System.out.println(jedis.get("singleJedis"));
    jedis.close();
```

注意Jedis对象并不是线程安全的，在多线程下使用同一个Jedis对象会出现并发问题。为了避免每次使用Jedis对象时都需要重新构建，
Jedis提供了JedisPool。JedisPool是基于Commons Pool 2实现的一个线程安全的连接池。
```
    JedisPoolConfig jedisPoolConfig = new JedisPoolConfig();
    jedisPoolConfig.setMaxTotal(10);
    JedisPool pool = new JedisPool(jedisPoolConfig, "localhost", 6379);

    Jedis jedis = null;
    try{
        jedis = pool.getResource();
        jedis.set("pooledJedis", "hello jedis pool!");
        System.out.println(jedis.get("pooledJedis"));
    }catch(Exception e){
        e.printStackTrace();
    }finally {
        //还回pool中
        if(jedis != null){
            jedis.close();
        }
    }

    pool.close();
```

使用完后记得主动调一下close方法，将Jedis对象归还到连接池中。Jedis的close方法：

```
  public void close() {
    //如果使用了连接池，检查客户端状态，归还到池中
    if (dataSource != null) {
      if (client.isBroken()) {
        this.dataSource.returnBrokenResource(this);
      } else {
        this.dataSource.returnResource(this);
      }
    } else {
      //未使用连接池，直接关闭
      client.close();
    }
  } 
```
