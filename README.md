# CS-5004-Theory


## Chapter 1: Getting Started with Java 




## Chapter 2: Object Oriented Design with Java 

OOP is a way of creating objects and we do that by creating a class. A class has two things, member data and member functions. 

Classes are pretty much blueprints for objects. Blueprints detail the general structure. For example, let’s say we have a blueprint for making a robot. We would start off by creating a class. 

```c
public class Robot {

} 
```
Class names in Java always are written in TitleCase. Primitive type names, like int and boolean , are lowercase. Note that the class is public. This means that it can be used in other classes. 

As the engineer, we would probably want the Robot to have some attributes or variables. The attributes could be individual strings, numbers, or booleans.

```c
public class Robot {
// Attributes or variables
    private String name;
    private String model;
    private int size;
} 
```
For this example, the attributes could be like its size (number), or model (string), or name(string). These attributes only define what makes up a Robot and what we would want it to have. I like to think of these as empty boxes with labels of what is supposed to go inside of them. 

* Note that the variables are labeled as private. This means that they can only be accessed from inside the Robot class. Keeping these variables private help keep the classes separated from each other so that if you change one thing in a class, you won't be required to make any changes in other classes since the classes are isolated from each other. 

Now in order for the robot to actually recieve a size, model, or name, we would have to create a constructor. A constructor is what actually brings the robot to life by assigning it a name, model, size. But how exactly does it do that? This is where the "this" pointer comes in to play. 

```c
// Constructor to initialize the attributes
    public Robot(String name, String model, int size) {
        this.name = name;
        this.model = model;
        this.size = size;
    }
```
In the constructor, when you use "this.name = name;", it means you're assigning the value of the "name" parameter to the "name" variable of the current robot object. Same goes for "this.model = model;". You're assigning the value of the "model" parameter to the "model" variable of the robot object. So if we're thinking about it in the sense of boxes, when we use "this" in the constructor, it's like the robot talking to itself, saying "Hey, I'm the robot we're talking about, so put my name in my name box, my model in my model box, and my size in my size box." It'w what essentially directing the data into it's corrosponding box. 

But these aren’t enough to create a WHOLE robot. It needs to be able to do something or have a functionality.  Maybe we might want it to walk or lift a box. These actions are known as methods. 

```c
// Method to make the robot walk
    public void walk() {
        System.out.println(name + " is walking.");
    }

    // Method to make the robot lift a box
    public void liftBox() {
        System.out.println(name + " is lifting a box.");
    }
```

These are like commands that we can give to the robot to make them do things. Just like how you may press buttons to make a toy robot move, in Java, you use methods to make our object, the robot, to move. 

So once we bring our robot to life with a constructor, we might want to actually know what's it name is or what it's size is. That's where Getter's come in. Getter's allow us to peek inside the box and see what's inside there. It's like asking the robot to tell us what it's name or model is. Here are some examples of getters. 

```c
    public String getName() {
        return name;
    }


   public String getModel() {
        return model;
    }

```


But what if we want to change what it's inside the box. Maybe we don't like the name of the robot or the size of it. This is where Setters come in. Setters allow is to change what's inside the box. We can tell the robot " Your name is now this ___" or "Your size is now this ___". Here are some examples of setters: 

```c
public void setName(String name) {
        this.name = name;
    }


public void setModel(String model) {
        this.model = model;
    }
```
Now the robot will update what's inside the box accordingly to, for example, what name or size you want it to be. Note the "this." pointer again. It's telling the program to stick the new name value into the name box. Or telling the program to stick the new model value into the model box. It directs where each value should correctly be. 


Now the blueprint is ready! This is the code in it's entirety which we can use for the next part.  

```c
// Define the Robot class
public class Robot {
    // Attributes or variables
    private String name;
    private String model;
    private int size;

    // Constructor to initialize the attributes
    public Robot(String name, String model, int size) {
        this.name = name;
        this.model = model;
        this.size = size;
    }

    // Method to make the robot walk
    public void walk() {
        System.out.println(name + " is walking.");
    }

    // Method to make the robot lift a box
    public void liftBox() {
        System.out.println(name + " is lifting a box.");
    }

    // Getters and setters for the attributes
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public int getSize() {
        return size;
    }

    public void setSize(int size) {
        this.size = size;
    }
}
```


So all of this is part of the Class which is still just a blueprint, so it doesn’t really exist yet. When we create a class, we tell the language what this new data type looks like and what it does, but all we’re doing at this point is DESCRIBING what the data type looks like, we’re not actually creating a robot that we can work with.


Now let's move on to how to actually create the Robot, the object. 


## Chapter 3:  Getting Deeper with Class Objects 

As a refresher, this is our newly made class: 

```c
// Define the Robot class
public class Robot {
    // Attributes or variables
    private String name;
    private String model;
    private int size;

    // Constructor to initialize the attributes
    public Robot(String name, String model, int size) {
        this.name = name;
        this.model = model;
        this.size = size;
    }

    // Method to make the robot walk
    public void walk() {
        System.out.println(name + " is walking.");
    }

    // Method to make the robot lift a box
    public void liftBox() {
        System.out.println(name + " is lifting a box.");
    }

    // Getters and setters for the attributes
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public int getSize() {
        return size;
    }

    public void setSize(int size) {
        this.size = size;
    }
}
```

To create an object of Robot, we need to do it in the main class. We will specify the class name , followed by the object name, which can be Robbie, and use the keyword new:

```c
// Main class to test the Robot class
public class Main {
    public static void main(String[] args) {
Robot myRobot = new Robot("Robbie", "Ultron", 3);
```
This is how we create a Robot object. We have to ask the program to make a Robot for us. But just making the robot isn't enough; you also need to give it some the features, like its name, model, and size. So when you write new, it tells Java to make a new robot and it follows instructions from the constructor to make sure the robot has everything it needs.

So to make it clearer, it this example, 
- "Robot" is the class name 
- myRobot is the object name. 

The arguments are the name "Robbie", model "Ultron", size "3". That's where the constructor comes in. It's like a set of instructions that tells the machine how to build the robot with all those features. These arguments invoke the constructor to start assigning those parameters to the correct "box". 

But what if we wanted to change the variables again. Let's say that we hate the name Robbie and want to update the name. We can use Setters! 

```c
// Update student age
        myRobot.setName(Jeremy);
```

So now we've created an object. A Robot that goes by the name of Jeremy, Model Ultron, and Size 3.  

Now how do we make class objects actually do things? That's where methods come in to play. We have to call the methods in the main class for the object to start doing them. 

```c
myRobot.walk();
myRobot.liftBox();
```

The output for this would be: 

```c
Jeremy is walking.
Jeremy is lifting a box.
```

Now let's talk about dynamic and static variables. In the Robot class, the variables name, model, and size are all dynamic variables. Why? Because they can vary from one robot instance to another. For example, one robot "Robbie" has the name "Robbie", the model "Ultron", and the size 3, while another robot "Jeremy" could have different values for these variables. 

Another dynamic variables would be the methods we created. The methods walk() and liftBox() are dynamic functions because they perform actions specific to each robot object. When we call myRobot.walk(), it prints out "Robbie is walking.", indicating that "Robbie" is the one walking. If we had another robot named "Jeremy", calling jeremyRobot.walk() would print "Jeremy is walking.". 

So essentially, dynamic variables mean that they are variables that can constantly be changed. They are variables that are unique to each object. 

Static variables, on the other hand, are shared among all objects of the class and are not unique to each object. They have the same value for all of the objects. 

 In this code, there are no static variables or functions defined. However, let's create one. 

 Let's add a static variable manufacturer to the Robot class. This variable will store the name of the manufacturer of all robot objects.
```c
 public class Robot {
    // Attributes or variables
    private String name;
    private String model;
    private int size;
    private static String manufacturer = "Stark Industries"; // Static variable for the manufacturer


.... rest of the code


// Static method to get the manufacturer
    public static String getManufacturer() {
        return manufacturer;
    }

    // Static method to set the manufacturer
    public static void setManufacturer(String newManufacturer) {
        manufacturer = newManufacturer;
    }
}
```
So as you can see, I've added a manufactor variable. So one thing that I remember I was intially confused about when I was learning about this is why do the other methods not have getters or setter, but the static one does? I realized this is because the static variable is an actual variable that is instansized in the class, like name or size, and so it need's to have a getter or setter. The methods to lift a box or walk don't need getters or setters because they are not actual variables instanized in the class.  

Now, manufacturer is a static variable that stores the name of the manufacturer of all robot objects. We can access it using Robot.getManufacturer() and modify it using Robot.setManufacturer(). This variable is shared among all objects of the Robot class. Note how we had to use the word "static" when setting up our methods. 

This is an example of what it would look like if the method was called. 

```c
public class Main {
    public static void main(String[] args) {
        // Create two Robot objects
        Robot myRobot1 = new Robot("Robbie", "Ultron", 3);
        Robot myRobot2 = new Robot("Jeremy", "Transformer", 2);

        // Display the initial manufacturer
        System.out.println("The Manufacturer: " + Robot.getManufacturer());
```
        




