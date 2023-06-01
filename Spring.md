# **What is Spring?**

Spring is a **Dependency Injection Framework** to make java applications loosely coupled.
<br/>
Spring framework makes development of JavaEE applications easy. Developed by **Rod Johnson in 2003**

## **Dependency Injection**

> It is a design pattern. Dependency Injection is the main functionality provided by **Spring IOC(Inversion of Control)**. The Spring-Core module is responsible for injecting dependencies through either Constructor or Setter methods. The design principle of Inversion of Control emphasizes keeping the Java classes independent of each other and the container frees them from object creation and maintenance.
<br>

### **What is dependency and IOC ?**

<br>

Dependency in programming is an approach where a class uses specific functionalities of another class. So, for example, If you consider two classes A and B, and say that class A uses functionalities of class B, then its implied that class A has a dependency of class B. Now, if you are coding in Java then you must know that, you have to create an instance of class B before the objects are being used by class A.

![Dependency Injection](Images/Screenshot%202023-05-22%20184936.png)
> **Dependency Injection** is a fundamental aspect of the Spring framework, through which the Spring container “injects” objects into other objects or “dependencies”
<br/>
<br>

### **Tight Coupling Example**

* ProductDao is a dependency for ProductService.
* If an object of ProductDao is created using **new** keyword, the application becomes Tightly copupled.
* The problem here is, suppose in future if the ProductDao changes, then entire application should be changed(configured) accordingly.
* So, instead of ***we*** creating the objects with **new** keyword, we will let ***SPRING*** do this magic : It creates the objects of the dependencies and injects it in the required classes.
* Since there is an inversion of control over the object creation and maintainance, this is termed as ***INVERSION OF CONTROL***

![Tight Coupling](Images/Screenshot%202023-05-22%20185810.png)

>**Inversion of Control** is a principle in software engineering which transfers the control of objects or portions of a program to a container or framework.
<br>
So Spring-Core module is responsible for injecting these dependencies
Spring IOC resolves such dependencies with Dependency Injection, which makes the code easier to test and reuse.

![DI across various layers](Images/Screenshot%202023-05-22%20002531.png)

<br>

# **Spring Modules**

[*Spring Modules : Spring Official Docs*](https://docs.spring.io/spring-framework/docs/3.0.0.M4/reference/html/ch01s02.html)

![Spring Modules](Images/Screenshot%202023-05-22%20195740.png)

![Modules](Images/Screenshot%202023-05-23%20215517.png)

1. The **Core Container** consists of the Core, Beans, Context and Expression modules.
    * The ***Core and Beans modules*** provide the most fundamental parts of the framework and provides the ***IoC and Dependency Injection features***.
    * The ***Context module*** build on the solid base provided by the Core and Beans modules: it provides a way to access objects in a framework-style manner. <br>
    The Context module *inherits its features from the Beans module* and adds support for internationalization (I18N) (using for example resource bundles), event-propagation, resource-loading, and the transparent creation of contexts by, for example, a servlet container. The Context module also contains support for some Java EE features like EJB, JMX and basic remoting support. The ***ApplicationContext interface*** is the focal point of the Context module that provides these features.
    * The ***Expression Language module*** provides a powerful expression language for querying and manipulating an object graph at runtime. It can be seen as an extension of the unified expression language (unified EL) as specified in the JSP 2.1 specification.
2. The ***Data Access/Integration layer*** consists of the JDBC, ORM, OXM, JMS and Transaction modules
    * The ***JDBC module*** provides a JDBC-abstraction layer that removes the need to do tedious JDBC coding and parsing of database-vendor specific error codes.
    * The ***ORM module*** provides integration layers for popular object-relational mapping APIs, including JPA, JDO, Hibernate, and iBatis. Using the ORM package you can use all those O/R-mappers in combination with all the other features Spring offers, such as the simple declarative transaction management feature mentioned previously.
    * The ***OXM module*** provides an abstraction layer for using a number of Object/XML mapping implementations. Supported technologies include JAXB, Castor, XMLBeans, JiBX and XStream.
    * The ***JMS module*** provides Spring's support for the Java Messaging Service. It contains features for both producing and consuming messages.
    * The ***Transaction module*** provides a way to do programmatic as well as declarative transaction management, not only for classes implementing special interfaces, but for all your POJOs (plain old Java objects).
3. The ***Web layer*** consists of the Web, Web-Servlet and Web-Portlet modules.
    * Spring's ***Web module*** provides basic web-oriented integration features, such as multipart file-upload functionality, the initialization of the IoC container using servlet listeners and a web-oriented application context. It also contains the web related parts of Spring's remoting support.
    * The ***Web-Servlet module*** provides Spring's Model-View-Controller (MVC) implementation for web-applications. Spring's MVC framework is not just any old implementation; it provides a clean separation between domain model code and web forms, and allows you to use all the other features of the Spring Framework.
    * The ***Web-Portlet module*** provides the MVC implementation to be used in a portlet environment and mirrors what is provided in the Web-Servlet module.
4. ***AOP and Instrumentation***
    * Spring's ***AOP module*** provides an AOP Alliance-compliant *aspect-oriented programming implementation allowing you to define, for example, method-interceptors and pointcuts to cleanly decouple code implementing functionality that should logically speaking be separated.* Using source-level metadata functionality you can also incorporate all kinds of behavioral information into your code, in a manner similar to that of .NET attributes.
    * There is also a separate Aspects module that provides integration with AspectJ.
    * The ***Instrumentation module*** provides class instrumentation support and classloader implementations to be used in certain application servers.
5. ***Test***
    * The ***Test module*** contains the Test Framework that supports testing Spring components using JUnit or TestNG. It provides consistent loading of Spring ApplicationContexts and caching of those contexts. It also contains a number of Mock objects that are usful in many testing scenarios to test your code in isolation.

<br>

# **Spring IoC Container**

[***IOC Container : Official Documentation***](https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/beans.html)

* Spring IoC Container is the core of Spring Framework.
* It creates the objects, configures and assembles their dependencies, manages their ***entire life cycle***. The IoC container is responsible to ***instantiate, configure and assemble the objects.***
* The Container uses *Dependency Injection(DI)* to manage the components that make up the application.
* It gets the information about the objects from a configuration file(XML) or Java Code or Java Annotations and Java POJO class. These objects are called Beans. Since the Controlling of Java objects and their lifecycle is not done by the developers, hence the name *Inversion Of Control*.

The following diagram depicts how the Container makes use of Configuration metadata and Java POJO classes to manage beans.

<br>

<img src="Images/Spring%20IOC%20container.png" width="600" height="400">
<br>

There are two types of IoC containers. They are:

1. BeanFactory
2. ApplicationContext

* The *org.springframework.beans.factory.**BeanFactory*** and the *org.springframework.context.**ApplicationContext*** interfaces acts as the IoC container.
* The ApplicationContext interface is built on top of the BeanFactory interface.
* On the other hand, the ***ApplicationContext*** is a sub-interface of the BeanFactory. Therefore, it offers all the functionalities of BeanFactory. Furthermore, it provides more ***enterprise-specific functionalities.***
* It adds some extra functionality than BeanFactory such as simple integration with Spring's AOP, message resource handling (for I18N), event propagation, application layer specific context (e.g. WebApplicationContext) for web application. So it is better to use ApplicationContext than BeanFactory.

### [***ApplicationContext Interface and It's Implementation Classes***](https://www.javaguides.net/2022/01/what-is-applicationcontext-interface.html)

<br>

# **Types of DI**

## 1. Setter Injection (Property Injectoion)

```java
public class Student {
    int id;
    String name;
    Address address;  //dependency

    public void setId(int id) {
        this.id = id;
    }
    public void setName(String name) {
        this.name = name;
    }
    public void setAddress(Address address) { //setter Injection
        this.address = address;
    }

}
```

```java
public class Address {
    String street;
    String city;

    public void setStreet(String street) {
        this.street = street;
    }

    public void setCity(String city) {
        this.city = city;
    }

}
```

## 2. Contructor Injection

```java
public class Student {
    int id;
    String name;
    Address address; //dependency

    public Student(int id, String name, Address address) { //constructor injection
        this.id = id;
        this.name = name;
        this.address = address;
    }

}
```

```java
public class Address {
    String street;
    String city;

    public Address(String street, String city) {
        this.street = street;
        this.city = city;
    }

}

```

## **Configuration File**

The file where we declare beans and its dependencies.
<br>

*Data Types(Dependencies)*

1. **Primitive** : byte, char, short, int, float, double, long, boolean
2. **Collection** : List, Set, Map and Properties
3. **Reference** type : Other class objects. Ex. Address address.

<br>

## ***DI Practical Hands-On :***

1. Create a simple maven project in eclipse. (select artifact = *maven-archtype-quickstart*)
2. Add dependencies for Spring Core and Spring Context modules in *pom.xml*
3. Create beans => Java POJO's Ex: Student.class with properties id, name, address.
4. Create configuration file => config.xml
5. Define the properties using ***property*** tags in ***bean*** tag.

> Basic format of the XML config file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.springframework.org/schema/beans
  https://www.springframework.org/schema/beans/spring-beans.xsd">
  <bean id="..." class="..."> ① ②
  <!-- collaborators and configuration for this bean go here -->
  </bean>
  <bean id="..." class="...">
  <!-- collaborators and configuration for this bean go here -->
  </bean>
  <!-- more bean definitions go here -->
</beans>

```

In our example: Student class is having 3 properties.
***Student.java***

```java
package com.springcore;

public class Student {
 private int id;
 private String name;
 private String address;

 public Student() {
  super();
  System.out.println("default constructor trigerred");
  // TODO Auto-generated constructor stub
 }

 public Student(int id, String name, String address) {
  super();
  System.out.println("parameterized constructor trigerred");
  this.id = id;
  this.name = name;
  this.address = address;
 }

 public int getId() {
  return id;
 }

 public void setId(int id) {
  System.out.println("setId method trigerred");
  this.id = id;
 }

 public String getName() {
  return name;
 }

 public void setName(String name) {
  System.out.println("setName method trigerred");
  this.name = name;
 }

 public String getAddress() {
  return address;
 }

 public void setAddress(String address) {
  System.out.println("setAddress method trigerred");
  this.address = address;
 }

 @Override
 public String toString() {
  return "Student [id=" + id + ", name=" + name + ", address=" + address + "]";
 }

}

```

Corresponding XML config file: ***config.xml***

```xml

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://www.springframework.org/schema/beans
  https://www.springframework.org/schema/beans/spring-beans.xsd">

 <bean id="Student" class="com.springcore.Student">
  <property name="id">
   <value>1608</value>
  </property>

  <property name="name">
   <value>Srivathsa</value>
  </property>

  <property name="address">
   <value>Mysore</value>
  </property>

 </bean>

</beans>
```

Pulling Object of Student Class in Main class using Application Context: ***App.java***

```java
package com.springcore;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

/**
 * Hello world!
 *
 */
public class App {
 public static void main(String[] args) {
  System.out.println("Hello World!");
  ApplicationContext context = new ClassPathXmlApplicationContext("config.xml");
  Student student1 = (Student) context.getBean("Student");
  System.out.println(student1);
 }
}
```

Output:

```text
Hello World!
default constructor trigerred
setId method trigerred
setName method trigerred
setAddress method trigerred
Student [id=1608, name=Srivathsa, address=Mysore]

```
