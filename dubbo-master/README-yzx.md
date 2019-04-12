
基于spring配置文件的扩展的话，有两个接口
NamspaceHandler
注册BeanDefinitionParser，利用它来解析
BeanDefinitionParser：解析配置文件的元素
spring会默认加载jar包下/MATA-INF、spring.handlers，找到对应的Namspace

1.根据以上，所以我们在dubbo-config 下面的/MATA-INF、spring.handlers 找到标签解析的入口
2.ServiceBean<T> extends ServiceConfig<T> implements InitializingBean, DisposableBean, ApplicationContextAware, ApplicationListener, BeanNameAware 

**InitializingBean, （这里也是一个入口）**
**这个bean初始化完，会调用afterPropertiesSet方法**
DisposableBean, 
被销毁调用destroy方法
ApplicationContextAware, 
注入applicationContent对象，可以获取spring容器的一些东西
ApplicationListener, 
事件监听，启动后触发事件通知
BeanNameAware 
会获取bean本身的属性