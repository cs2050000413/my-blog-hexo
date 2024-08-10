---
layout: text
title: 测试类空指针异常报错
date: 2023-09-15 23:53:17
tags: 精选 java
cover: /img/pwa/favicon.png
description: 测试类空指针异常报错
recommend: true
---
<h2>报错信息：</h2>
<p>java.lang.NullPointerException<br>
at cn.itsource.mapper.IShopMapperTest.selectAll(IShopMapperTest.java:21)</p>
<h3>在写入注解@Test时是引用的Junit4</h3>
<p>在测试类里面：</p>
<p>解决办法：加上两个注解，如下：App.class是我们的启动类<br>
@RunWith(SpringRunner.class)<br>
@SpringBootTest(classes = App.class)</p>
<h1>@RunWith(SpringRunner.class) ：</h1>
<h3>1.指定使用的单元测试执行类，不使用这个注解会采用默认的执行类</h3>
<h3>2.让测试在Spring容器环境下执行【</h3>
<p>2.1Spring的容器环境是啥呢？ 比如常见的 Service Dao 也就是业务层实体层里面是方法，都在Spring容器里，junit需要将他们找到拿到，并且使用来测试。】</p>
<h3>3.没有这个会导致业务层和持久层注入失败【</h3>
<p>3.1为什么失败？<br>
答：接2.1不能将Spring和Junit连接起来，进入不了spring容器看不见我们的业务层或者持久层】</p>
<h3>4.是 Junit4 提供的注解，将 Spring 和 Junit 连接起来了</h3>
<h3>5.是一个运行器</h3>
<h1>@SpringBootTest ：</h1>
<h3>1.目的是加载ApplicationContext，启动spring容器</h3>
<h3>2.使用 @SpringBootTest 后，Spring 将加载所有被管理的 bean，基本等同于启动了整个服务，此时便可以开始功能测试</h3>
<p>到这里勾起了我的好奇心，我想看看，去掉里面的参数或者减少一个注解会怎么样</p>
<h4>空指针异常，情况一：去掉整个@RunWith注解</h4>
<h4>bean依赖报错，情况二：去掉整个@SpringBootTest</h4>
<p>报错信息：org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'cn.itsource.service.impl.IDepartmentServiceImplTest': Unsatisfied dependency expressed through field 'departmentService'; nested exception is org.springframework.beans.factory.NoSuchBeanDefinitionException: No qualifying bean of type 'cn.itsource.service.IDepartmentService' available: expected at least 1 bean which qualifies as autowire candidate. Dependency annotations: {@org.springframework.beans.factory.annotation.Autowired(required=true)}</p>
<h3>error情况三：保留整个@SpringBootTest注解，但是去掉了@RunWith注解的参数（里面必须有参数）</h3>
<p>情况四：保留整个@RunWith注解，去掉@SpringBootTest注解里面的参数（没问题）</p>
<p>这俩个注解的用途结合我尝试得到的各种结果，我感觉俺理解到了耶，顺便还发现了两个报错，很好，哈哈哈。<br>
最后，新的一天就要开始了，希望自己砥砺前行，希望大家前途光明！</p>