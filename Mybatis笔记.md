## 如何创建SqlSessionFactory
在基础的 MyBatis 用法中，是通过 SqlSessionFactoryBuilder 来创建 SqlSessionFactory 的。 而在 MyBatis-Spring 中，则使用 SqlSessionFactoryBean 来创建。

## 缓存

MyBatis默认没有开启二级缓存，需要在setting全局参数中配置开启二级缓存。

