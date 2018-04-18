# Polymorphism & Composition Homework - Quiz

# Polymorphism

1. What does the ___word___ 'polymorphism' mean?

The work 'polymorphism' refers to the ability of an object to take on many forms.

2. What does it mean when we apply polymorphism to OO design? Give a simple Java example.

Thanks to polymorphism a method can do different things based on the object that it is acting upon. For example, it allows objects of different types to be accessed through the same interface. Each type can provide its own, independent implementation of this interface. For example, we could write an ISound interface that would be implemented by classes for different animals; ISound would specify that each animal should have a method to make a sound, however individual methods could differ, e.g. a cat could meow, a dog bark, a cow moo etc.

```
public interface ISound {
  public String makeSound();
}

public class Cat {
  public String makeSound() {
    return "Meow!";
  }
}

public class Dog {
  public String makeSound() {
    return "Woof!";
  }
}

public class Cow {
  public String makeSound() {
    return "Moo!";
  }
}

```

3. What can we use to implement polymorphism in Java?

We can use method overloading (having several methods with the same name in a class but with a slightly different implementation, e.g. different number of arguments), method overriding (when a child class has its own version of a method present in the parent class), and interfaces (when all classes implementing an interface have their own version of a method).

4. How many 'forms' can an object take when using polymorphism?

The number of forms an object can take using a combination of techniques mentioned above is not constrained by anything other than system memory (although it's worth remembering that in Java and most other programming languages inheritance is only limited to one parent class).

5. Give an example of when you could use polymorphism.

Whenever you want several classes to share a similar functionality (e.g. various attractions in a theme park should be chargeable), but individual implementations of this functionality should be different (e.g. various prices and discounts based on visitor's age).



# Composition

6. What do we mean by 'composition' in reference to object-oriented programming?

Composition is a way to create complex objects or data types by combining less complex ones.

7. When would you use composition? Provide a simple example in Java.

We use composition when we want to break up a desired behaviour into distinct responsibilities and encapsulate the implementation of each into separate objects. For example you can have a Computer class which will include instances of classes implementing the IOutput and IInput interfaces, such as Monitor and Keyboard, which are responsible for outputting and inputting data.

```
public class Computer {
    private int ram;
    private int hddSize;

    private IOutput outputDevice;
    private IInput inputDevice;

    public Computer(int ram, int hddSize, IOutput outputDevice, IInput inputDevice) {
        this.ram = ram;
        this.hddSize = hddSize;
        this.outputDevice = outputDevice;
        this.inputDevice = inputDevice;
    }

    public String outputData(String data) {
        return this.outputDevice.outputData(data);
    }

    public String inputData(String data) {
        return this.inputDevice.sendData(data);
    }
}
```



8. What is/are the advantage(s) of using composition?

It makes our code more reusable and more flexible than when using inheritance. It allows us to use multiple functionality that isn't possible to achieve through inheritance (again, as a class can only extend one other) by using multiple classes implementing a single interface.

9. What happens to the behaviours when the object composed of them is destroyed?
The behaviours are not affected and can still be used independently.
