<http://www.iocoder.cn/Spring-Boot/autoconfigure/?github>

1.spring boot 自动配置原理
1.1 围绕下面三个问题展开自动配置（一个对象能自动注册为Spring bean，并根据配置文件初始化属性）
① 配置类：类上有@Configuration，声明这是一个配置类
② 条件注解：@ConditionalOnClass 满足一定条件才生效；方法上添加 @Bean 注解，声明该方法创建一个 Spring Bean。
③ 配置属性： 在 Spring Boot 定义了 @ConfigurationProperties 注解，用于声明配置属性类，将指定前缀的配置项批量注入到该类中

Spring Boot 约定读取 application.yaml、application.properties 等配置文件 举例 @ConfigurationProperties(prefix = "yunai.server")
Spring Boot 的 spring-boot-autoconfigure 项目，提供了大量框架的自动配置

1.2 spring.factories定义加载哪些自动配置类（Spring Boot 自己的 SPI 机制）
启动 Spring Boot 应用的时候，有个非常重要的组件 SpringFactoriesLoader 类，会读取 META-INF 目录下的 spring.factories 文件，获得每个框架定义的需要自动配置的配置类。


条件注解扩展：
Spring4 提交的 @Conditional 注解非常不方便，需要我们自己去拓展。因此，Spring Boot 进一步增强，提供了常用的条件注解：
@ConditionalOnBean：当容器里有指定 Bean 的条件下
@ConditionalOnMissingBean：当容器里没有指定 Bean 的情况下
@ConditionalOnSingleCandidate：当指定 Bean 在容器中只有一个，或者虽然有多个但是指定首选 Bean
@ConditionalOnClass：当类路径下有指定类的条件下
@ConditionalOnMissingClass：当类路径下没有指定类的条件下
@ConditionalOnProperty：指定的属性是否有指定的值
@ConditionalOnResource：类路径是否有指定的值
@ConditionalOnExpression：基于 SpEL 表达式作为判断条件
@ConditionalOnJava：基于 Java 版本作为判断条件
@ConditionalOnJndi：在 JNDI 存在的条件下差在指定的位置
@ConditionalOnNotWebApplication：当前项目不是 Web 项目的条件下
@ConditionalOnWebApplication：当前项目是 Web项 目的条件下



2.spring starter
spring boot 内置的start
第三方提供的start
自定义的start

2.1如何自定义starter
参考自动配置原理
2.1.1 自动配置包
① 配置类：类上有@Configuration，声明这是一个配置类
② 条件注解：@ConditionalOnClass 满足一定条件才生效；方法上添加 @Bean 注解，声明该方法创建一个 Spring Bean。
③ 配置属性：@ConfigurationProperties 注解 
2.1.2 spring.factories定义加载哪些自动配置类



