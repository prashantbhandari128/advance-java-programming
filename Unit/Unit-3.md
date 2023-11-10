<div align="center">

[**_``Go Back``_**](../README.md)

# JavaBeans

</div>

## What is JavaBean
--------------------

``JavaBeans`` is a programming component model for Java that defines a standard for creating reusable software components. A JavaBean is essentially a Java class that follows certain conventions to enable its use in various development environments and frameworks. These conventions make it easier to use and manipulate JavaBeans without needing to know their implementation details.

> JavaBeans are classes that encapsulate many objects into a single object (the bean).

Here are the key characteristics of a JavaBean:

- **Serializable:** ``JavaBeans`` should implement the ``java.io.Serializable`` interface if they need to be serializable to allow for persistence or ``Remote Method Invocation (RMI)``.

- **Public Default Constructor:** The class must have a public ``no-argument`` constructor (``default constructor``) so that it can be instantiated using the **``newInstance()``** method of ``java.beans.Beans`` class or through various development tools that rely on this convention.

- **Properties:** The ``JavaBean`` should provide ``getter`` and ``setter`` methods for its properties, which are typically ``private`` instance variables. The ``getter`` and ``setter`` methods should follow the naming convention **``getProperty()``** and **``setProperty()``** for a property named ``"property"`` respectively. For example, if the property is ``"name"`` the methods would be **``getName()``** and **``setName()``**. A JavaBean property may be ``read``, ``write``, ``read-only``, or ``write-only``. 

Example:

```Java
import java.io.Serializable;

public class Student implements Serializable{ 
    private int id;
    private String name;
    public Student(){

    }
    public void setId(int id){
        this.id = id;
    }
    public int getId(){
        return id;
    }
    public void setName(String name){
        this.name = name;
    }
    public String getName(){
        return name;
    }
}
```

```Java
// Java program to access JavaBean class
public class Program {
public static void main(String args[]){
        Student s = new Student();
        s.setId(34);
        s.setName("Prashant Bhandari");
        System.out.println("Id : " + s.getId());
        System.out.println("Name : " + s.getName());
    }
}
```

## Advantage of JavaBeans
-------------------------
A software component architecture provides standard mechanisms to deal with software building blocks. The following list enumerates some of the specific benefits that Java technology provides for a component developer:

- **Reusability:** ``JavaBeans`` promote component-based development, allowing developers to create reusable software components that can be easily integrated into different applications. This reusability reduces duplication of code and increases development efficiency.

- **Ease of Use:** By adhering to the ``JavaBeans`` conventions, components become self-descriptive and easy to understand. The standard naming conventions for properties, methods, and events make it straightforward for other developers to work with these components without needing to know their internal implementation details.

- **Interoperability:** ``JavaBeans`` are designed to be platform-independent, which means they can be used in any Java-based environment, regardless of the operating system or architecture. This interoperability enables the seamless integration of components across different systems and platforms.

- **Serialization Support:** ``JavaBeans`` can implement the ``java.io.Serializable`` interface, making them capable of being ``serialized`` and ``deserialized``. This feature enables the persistence of ``JavaBean`` instances, allowing them to be stored in files or transmitted over networks.

- **Event Handling:** ``JavaBeans`` support an event handling mechanism that allows decoupled communication between components, facilitating the development of loosely coupled and flexible applications.

- **Execution:** With auxiliary software, there is no difficulty during runtime; beans may be configured in advance.

## Introspection
-----------------

``Introspection`` in the context of ``JavaBeans`` refers to the process of examining the ``properties``, ``methods``, and ``events`` of a ``JavaBean`` at runtime. This capability allows development tools, IDEs (Integrated Development Environments), and frameworks to analyze and interact with ``JavaBeans`` dynamically without requiring detailed knowledge of their internal implementation.

``JavaBeans`` support introspection through the use of the ``JavaBeans API``, which provides a set of classes and methods to inspect the properties, methods, and events of a ``JavaBean``. The primary class involved in introspection is ``java.beans.Introspector``. It uses reflection to analyze the target ``JavaBean`` and generate information about its characteristics.

Here's how introspection works in JavaBeans:

- **Class Discovery:** The introspection process starts by discovering the ``properties``, ``methods``, and ``events`` of the JavaBean class.

- **Property Detection:** The introspector looks for pairs of methods in the JavaBean class following the JavaBeans naming conventions for properties. For example, for a property ``"name"`` it searches for methods **``getName()``** and **``setName()``**.

- **Event Detection:** If the ``JavaBean`` supports event handling, the introspector looks for event listener methods that adhere to specific naming conventions.

- **Method Detection:** The introspector identifies other methods and their signatures within the ``JavaBean`` class.

- **Generation of ``BeanInfo``:** Based on the discovered ``properties``, ``methods``, and ``events``, the introspector generates a ``BeanInfo`` class that contains ``metadata`` about the ``JavaBean``. This metadata provides information about the ``JavaBean's`` structure, including its properties, methods, and events.

- **Accessibility:** The generated ``BeanInfo`` class is made accessible to the development tools or frameworks, allowing them to work with the ``JavaBean`` and provide design-time support, such as automatic property editing, event handling, and customizer integration in IDEs.

**Example:**

```Java
import java.io.Serializable;

public class Student implements Serializable{ 
    private int id;
    private String name;
    public Student(){

    }
    public void setId(int id){
        this.id = id;
    }
    public int getId(){
        return id;
    }
    public void setName(String name){
        this.name = name;
    }
    public String getName(){
        return name;
    }
}
```

```Java
import java.beans.BeanInfo;
import java.beans.Introspector;
import java.beans.PropertyDescriptor;
import java.beans.IntrospectionException;

public class Program {
public static void main(String args[]){
        try {
            // Get the BeanInfo for the Student class
            BeanInfo beanInfo = Introspector.getBeanInfo(Student.class);
            // Get the PropertyDescriptors for the Student class
            PropertyDescriptor[] propertyDescriptors = beanInfo.getPropertyDescriptors();
            // Iterate through the PropertyDescriptors and display property names
            System.out.println("Properties of Student Class:");
            for (PropertyDescriptor propertyDescriptor : propertyDescriptors) {
                System.out.println("- " + propertyDescriptor.getName());
            }
        } catch (IntrospectionException ex) {
             e.printStackTrace();
        }
    }
}
```

let's explain the introspection process using the example code provided:

- **``Step 1``: Import Necessary Classes:** We begin by importing the required classes from the ``java.beans`` package. These classes include ``BeanInfo``, ``Introspector``, and ``PropertyDescriptor``, which are essential for performing introspection on ``JavaBeans``.

- **``Step 2``: Define the JavaBean Class:** In this example, we have a simple ``Student`` class with properties ``"id"`` and ``"name"`` and their corresponding ``getter`` and ``setter`` methods, following the JavaBeans naming conventions.

- **``Step 3``: Perform Introspection:** The main method is used to demonstrate introspection. Here's what happens in this method:

    - **``Introspector.getBeanInfo(Student.class)``**: We use the ``Introspector`` class to obtain the ``BeanInfo`` for the ``Student`` class. The **``Introspector.getBeanInfo(Class<?> beanClass)``** method returns an instance of ``BeanInfo``, which contains information about the properties, methods, and events of the ``JavaBean`` class.

    - **``beanInfo.getPropertyDescriptors()``**: Once we have the ``BeanInfo``, we retrieve an array of ``PropertyDescriptor`` objects using the **``getPropertyDescriptors()``** method. The ``PropertyDescriptor`` class represents a property of the ``JavaBean`` and provides information about the property's name, getter method, and setter method.

    - **Iterating Through ``PropertyDescriptors``**: Next, we iterate through the array of ``PropertyDescriptor`` objects and display the names of the properties. In this case, the properties are ``"id"`` and ``"name"``.

- **``Step 4``: Output:** When you run the code, the output will be:

```
Properties of Student Class:
- class
- id
- name
```

The ``class`` property is automatically included in all Java objects and represents the class of the object itself. As you can see, the introspection process successfully discovered the properties ``"id"`` and ``"name"`` of the Student class.

## Properties , Methods and Event Design Pattern 
--------------------------------------------------

### **Properties**
Properties are a fundamental concept that represents the attributes or characteristics of an object. Properties encapsulate the state of an object and allow controlled access to that state through getter and setter methods. Properties are crucial for encapsulation, data integrity, and providing a well-defined interface for interacting with JavaBean components.

### **Methods**
In JavaBeans, methods are an integral part of the Java class that encapsulates the behavior or operations that the bean can perform. Methods represent the functionality that can be executed on the object's data (properties) and define how the JavaBean responds to various interactions and events.

### **Event**
In JavaBeans, events are a mechanism that allows objects to communicate and interact in a decoupled and flexible manner. Events are typically used to notify one object (the listener or observer) when a specific action or change occurs in another object (the source or publisher). This mechanism is commonly used in graphical user interfaces (GUIs) and other event-driven programming scenarios. 

### **Design Pattern**

#### Design Patterns for Properties

##### Simple Properties

A simple property has a single value. It can be identified by the following design patterns, where ``N`` is the name of the property and ``T`` is its type:

```Java
public T getN()
public void setN(T arg)
```
A read/write property has both of these methods to access its values. A read-only property has only a get method. A write-only property has only a set method.

```Java
private int age; // Private field representing the "age" property

public int getAge() { // Getter method for the "age" property
    return age;
}

public void setAge(int age) { // Setter method for the "age" property
    if (age >= 0) {
        this.age = age;
    }
}
```

##### Boolean Properties:
A Boolean property has a value of ``true`` or ``false``. It can be identified by the following design
patterns, where ``N`` is the name of the property:

```Java
public boolean isN();
public boolean getN();
public void setN(boolean value);
```
Either the first or second pattern can be used to retrieve the value of a ``Boolean`` property. However, if a class has both of these methods, the first pattern is used.

```Java
// Boolean property: active
private boolean active;

// Getter method using the 'is' prefix
public boolean isActive() {
    return active;
}

// Alternative getter method using the 'get' prefix
public boolean getActive() {
    return active;
}

// Setter method
public void setActive(boolean active) {
    this.active = active;
}
```

##### Indexed Properties
An indexed property consists of multiple values. It can be identified by the following design
patterns, where ``N`` is the name of the property and ``T`` is its type:

```Java
public T getN(int index);
public void setN(int index, T value); 
public T[ ] getN( );
public void setN(T values[ ]);
```

Here is an indexed property called ``scores`` along with its getter and setter methods:

```Java
// Indexed property: scores
private int[] scores = new int[10]; // An array to hold the values

// Getter method for the indexed property
public int getScores(int index) {
    if (index >= 0 && index < scores.length) {
        return scores[index];
    } else {
        throw new IndexOutOfBoundsException("Index out of bounds");
    }
}

// Setter method for the indexed property
public void setScores(int index, int value) {
    if (index >= 0 && index < scores.length) {
        scores[index] = value;
    } else {
        throw new IndexOutOfBoundsException("Index out of bounds");
    }
}

// Getter method for the entire array of scores
public int[] getScores() {
    return scores;
}

// Setter method for the entire array of scores
public void setScores(int[] values) {
    if (values.length == scores.length) {
        System.arraycopy(values, 0, scores, 0, values.length);
    } else {
        throw new IllegalArgumentException("Array length must match");
    }
}
```

#### Design Patterns for Events

Beans use the delegation event model. Beans can generate events and send them to other
objects. These can be identified by the following design patterns, where ``T`` is the type of the
event:
```Java
public void addTListener(TListener eventListener);
public void addTListener(TListener eventListener) throws TooManyListeners;
public void removeTListener(TListener eventListener);
```

```Java
import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;

// Custom event class representing an event of type T
class MyEvent {
    private String message;

    public MyEvent(String message) {
        this.message = message;
    }

    public String getMessage() {
        return message;
    }
}

// Custom event listener interface for events of type MyEvent
interface MyEventListener {
    void handleMyEvent(MyEvent event);
}

// Custom exception class for handling too many listeners
class TooManyListenersException extends Exception {
    public TooManyListenersException(String message) {
        super(message);
    }
}

// JavaBean class that generates events
public class MyBean implements Serializable {
    private List<MyEventListener> listeners = new ArrayList<>();

    // Method to add a listener for MyEvent
    public void addMyEventListener(MyEventListener listener) throws TooManyListenersException {
        if (listeners.size() >= 5) { // Limit the number of listeners to 5
            throw new TooManyListenersException("Too many listeners for MyEvent");
        }
        listeners.add(listener);
    }

    // Method to remove a listener for MyEvent
    public void removeMyEventListener(MyEventListener listener) {
        listeners.remove(listener);
    }

    // Method to generate and send MyEvent to all registered listeners
    public void fireEvent(String message) {
        MyEvent event = new MyEvent(message);
        for (MyEventListener listener : listeners) {
            listener.handleMyEvent(event);
        }
    }
}
```

## BeanInfo Interface
----------------------
n JavaBeans, the ``BeanInfo`` interface allows you to provide information about a JavaBean's properties, methods, events, and other features. You can customize this information to control how the JavaBean is displayed and manipulated in design-time environments such as visual development tools or IDEs (Integrated Development Environments).

While you can override various methods in a ``BeanInfo`` class, some of the important methods include:

- **``getPropertyDescriptors()``**:
    - This method returns an array of ``PropertyDescriptor`` objects, each representing a property of the JavaBean.
    - You can customize the properties by specifying attributes like the property name, display name, description, editor, and more.
    - This method allows you to control how properties are presented and edited in design-time environments.

- **``getMethodDescriptors()``**:
    - This method returns an array of ``MethodDescriptor`` objects, each representing a method of the JavaBean.
    - You can customize method descriptions, display names, and other attributes.
    - It allows you to provide additional information about the methods of the JavaBean.

- **``getEventSetDescriptors()``**:
    - This method returns an array of ``EventSetDescriptor`` objects, each representing an event set in the JavaBean.
    - Event set descriptors specify details about the events that the JavaBean can generate.
    - You can customize event set descriptors to provide information about events and event listeners.

- **``getBeanDescriptor()``**:
    - This method returns a ```BeanDescriptor`` object that provides information about the JavaBean itself.
    - You can specify attributes like the display name and icon for the JavaBean.
    - It allows you to customize how the JavaBean is represented at the bean level.

- **``getIcon(int iconKind)``**:
    - This method allows you to provide custom icons for the JavaBean in design-time environments.
    - You can return different icons based on the ``iconKind`` parameter, which specifies the icon's purpose (e.g., for the bean, for properties, for methods).
    - Custom icons can enhance the visual representation of the JavaBean.

- **``getDefaultEventIndex()``** and **``getDefaultPropertyIndex()``**:
    - These methods allow you to specify the default event and property for the JavaBean.
    - The default event and property are typically used by design-time environments when working with the JavaBean.

- **``getAdditionalBeanInfo()``**:
    - This method returns an array of ``BeanInfo`` objects for classes that this JavaBean class extends or implements.
    - It provides additional information about the bean's superclass or implemented interfaces.

## Bound and Constrained Porperties
------------------------------------
In JavaBeans, properties can be categorized into two main types: bound properties and constrained properties. These categories define how changes to a property are handled and how events are generated when a property's value is modified.

- **Bound Property**:
    - A bound property is a property that generates events when its value changes.
    - It allows other objects (listeners) to be notified when the property's value changes, so they can react to the change.
    - Bound properties are often used in user interface components to notify the UI of changes in data.

- **Constrained Property**:

    - A constrained property is a property that generates events and allows vetoing the change if a listener decides that the new value is not acceptable.
    - When the value of a constrained property changes, it gives listeners the opportunity to veto the change, preventing it from taking effect if necessary.
    - Constrained properties are often used in scenarios where strict validation or business rules need to be enforced before accepting a new value.

## Persistance
----------------

In the context of JavaBeans, persistence refers to the ability to save and restore the state of a JavaBean to and from a persistent storage medium such as a file, database, or network. This capability is valuable for maintaining the state of JavaBeans across application sessions or for sharing data between different instances of an application. Persistence is often used in scenarios where data needs to be preserved beyond the runtime of an application.

**Serialization and Deserialization:**

- JavaBeans can be made serializable by implementing the ``java.io.Serializable`` interface. This allows the JavaBean's state to be converted into a byte stream, which can then be saved to a file or transmitted over a network.
- Serialization and deserialization can be achieved using Java's built-in ``ObjectOutputStream`` and ``ObjectInputStream`` classes.

## Customizer
---------------
In JavaBeans, a customizer is a user interface component or dialog box that allows developers or users to customize the properties of a JavaBean visually. Customizers are used to provide a more user-friendly and interactive way to set the properties of a bean, especially when dealing with complex or numerous properties.

Here are the key concepts and components related to customizers in JavaBeans:

- **Customizer Interface (``java.beans.Customizer``)**:
    - The ``Customizer`` interface is a part of the JavaBeans API and serves as the contract for creating customizers.
    - A customizer class must implement this interface and provide the necessary methods to customize a JavaBean.

- **Customizer Dialog (``java.beans.CustomizerDialog``)**:
    - A customizer is typically launched in a dialog box, referred to as a customizer dialog.
    - The ``CustomizerDialog`` class can be used to create a dialog that hosts a customizer component.
    - Developers can customize the appearance and behavior of the customizer dialog.

- **``setObject`` Method in ``Customizer``**:
    - ``Customizer`` implementations often provide a **``setObject(Object bean)``** method that accepts the ``JavaBean`` instance to be customized.
    - This method allows the customizer to access and modify the properties of the bean.

- ``BeanInfo`` and ``Customizer`` Association:
    - The association between a JavaBean and its customizer is typically defined in the bean's BeanInfo class.
    - The BeanInfo class specifies which customizer should be used for a particular bean by overriding the **``getCustomizerClass()``** method.

## JavaBean APIs
-----------------
The JavaBeans API is a set of specifications and conventions for building reusable software components, known as JavaBeans, in the Java programming language. JavaBeans are self-contained, reusable, and easily connectable components that can be used to create complex applications. The JavaBeans API defines a set of rules and guidelines that allow developers to create these components in a consistent and standardized way.
