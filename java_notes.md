# Java Notes

1) Modifier
2) Class, Methods and Variables (Basic)
3) Constructors
4) Arrays, ArrayList and LinkedList
5) Inheritance and Interfaces (Includes comparable and comparator)
6) Polymorphism
7) Abstract and Final
8) Exceptions
9) Design Patterns
10) Recursion 
11) Math Functions
Additional Static vs Dynamic Checking



### 1) Modifier

Accessibility Table:  


|Modifier|Class|Package|Subclass|World|
|--------|-----|-------|--------|-----|
|public  |Yes |Yes|Yes|Yes|
|protected|Yes|Yes|Yes|No|
|no modifier|Yes|Yes|No|No|
|private|Yes|No|No|No|

### 2) Class, methods, variables (Basic)
##### Class
```
class MyClass {
    // field, constructor, and 
    // method declarations
}
```

##### Methods (includes getter and setter)
```
public int getGear() {
    return gear;
}
        
public void setGear(int newValue) {
    gear = newValue;
}
        
public int getSpeed() {
    return speed;
}
        
public void applyBrake(int decrement) {
    speed -= decrement;
}
```

##### Method Overloading  
Allows for the use of same name for different methods, differentiated by the number/type of argument

```
public class DataArtist {
    ...
    public void draw(String s) {
        ...
    }
    public void draw(int i) {
        ...
    }
    public void draw(double f) {
        ...
    }
    public void draw(int i, double f) {
        ...
    }
}
```

##### Variables
```
public int cadence;
public int gear;
public int speed;
```

-Methods and variables can either be instance or static
Instance variables belong to a specific instance  
Instance methods are invoked by an instance of the class
Static variables are shared by all instances of the class(not tied to a specific object)  
Static method can be called without creating an instance of the class

##### Instantiation:   
<(class)> <(variable name)> =new <class(arguments)>


### 3) Constructors
A constructor is used to create objects from the class blueprint.
If no constructor is stated, the default will be a no argument constructor.
```
//no argument constructor
public Bicycle(){
}

public Bicycle(int startCadence, int startSpeed, int startGear) {
    gear = startGear;
    cadence = startCadence;
    speed = startSpeed;
}
```
A new object Bicycle can then be called (eg. constructor with arguments)
```
Bicycle myBike = new Bicycle(30, 0, 8);
```

### 4) Arrays, ArrayList and LinkedList (HashSet included)

#### Arrays and ArrayList
An array type is written as the name of an element type followed by some number of empty pairs of square brackets []  
```
int[] a = new int[101];
//101 is the number of elements within the arraylist

char[] hi= {'a', 'b', 'c'}
```

Array of letters to string:  
```
// Convert char array to String in Java
class Util
{
	public static void main(String[] args)
	{
		char[] chars = {'T', 'e', 'c', 'h', 'i', 'e', ' ',
						'D', 'e', 'l', 'i', 'g', 'h', 't'};

		String string = String.copyValueOf(chars);
		System.out.println(string);
	}
}
```

Commands for array vs linkedlist


|Operation|Array|ArrayList/LinkedList|
|-------|--------|--------|
|Creating an Array/Array List| String[] a= new String[10] | ArrayList<String> = new ArrayList<>();|
|Assessing an element|a[index]|list.get(index)|
|Updating an element|a[index]="London";|list.set(index, "London");|
|Returning size|a.length|list.size();|
|Adding a new element||list.add("London")|
|Inserting a new element||list.add(index,"London");|
|Removing an element||list.remove(index); OR list.remove(object);|
|Removing all elements||list.clear();|


#### LinkedList
```
import java.util.*;  
public class LinkedList1{  
 public static void main(String args[]){  
  
  LinkedList<String> al=new LinkedList<String>();  
  al.add("Ravi");  
  al.add("Vijay");  
  al.add("Ravi");  
  al.add("Ajay");  
  
  Iterator<String> itr=al.iterator();  
  while(itr.hasNext()){  
   System.out.println(itr.next());  
  }  
 }  
} 
```

ArrayList and Linked List are similar such that both implement the list interface.  
While the arraylist stores elements in an array, linked list stores elements in a linked list data structure (Arraylist better for random access, linkedlist better for insertion)   
ArrayList and LinkedList both have acollection size that is resizable   

#### HashSet
Similar to ArrayList, h.add(); could be used as well to add new elements to the set
```
import java.util.*; 
  
class Test 
{ 
    public static void main(String[]args) 
    { 
        HashSet<String> h = new HashSet<String>(); 
  
        // Adding elements into HashSet usind add() 
        h.add("India"); 
        h.add("Australia"); 
        h.add("South Africa"); 
        h.add("India");// adding duplicate elements 
  
        // Displaying the HashSet 
        System.out.println(h); 
        System.out.println("List contains India or not:" + 
                           h.contains("India")); 
  
        // Removing items from HashSet using remove() 
        h.remove("Australia"); 
        System.out.println("List after removing Australia:"+h); 
  
        // Iterating over hash set items 
        System.out.println("Iterating over list:"); 
        Iterator<String> i = h.iterator(); 
        while (i.hasNext()) 
            System.out.println(i.next()); 
    } 
}
```
Output:  
[South Africa, Australia, India]  
List contains India or not:true  
List after removing Australia:[South Africa, India]  
Iterating over list:  
South Africa  
India  

We could also create an array then convert it to a list and then pass it to the HashSet constructor that accepts another collection
```
import java.util.*; 
public class Set_example { 
    public static void main(String[] args) 
    { 
        // creating and initializing an array (of non 
        // primitive type) 
        Integer arr[] = { 5, 6, 7, 8, 1, 2, 3, 4, 3 }; 
  
        // Set demonstration using HashSet Constructor 
        Set<Integer> set = new HashSet<>(Arrays.asList(arr)); 
  
        // Duplicate elements are not printed in a set. 
        System.out.println(set); 
    } 
}
```

Using Collections also possible, performs the same function as above so I wont be adding it here.
(Collection.addAll() and Collections.unmodifiableSet())

### 5) Inheritance and Interfaces
In the Java language, classes can be derived from other classes, thereby inheriting fields and methods from those classes.
```
public class Bicycle {
        
    // the Bicycle class has three fields
    public int cadence;
    public int gear;
    public int speed;
        
    // the Bicycle class has one constructor
    public Bicycle(int startCadence, int startSpeed, int startGear) {
        gear = startGear;
        cadence = startCadence;
        speed = startSpeed;
    }
        
    // the Bicycle class has four methods
    public void setCadence(int newValue) {
        cadence = newValue;
    }
        
    public void setGear(int newValue) {
        gear = newValue;
    }
        
    public void applyBrake(int decrement) {
        speed -= decrement;
    }
        
    public void speedUp(int increment) {
        speed += increment;
    }
        
}

public class MountainBike extends Bicycle {
        
    // the MountainBike subclass adds one field
    public int seatHeight;

    // the MountainBike subclass has one constructor
    public MountainBike(int startHeight,
                        int startCadence,
                        int startSpeed,
                        int startGear) {
        super(startCadence, startSpeed, startGear);
        seatHeight = startHeight;
    }   
        
    // the MountainBike subclass adds one method
    public void setHeight(int newValue) {
        seatHeight = newValue;
    }   
}
```

Subclass inherits all the fields and methods of the superclass, and adds any additional fields/methods on top of those.
If the subclass is in the same package as its parent, it will also inherit the package-private members of its parents.  
You can write a subclass constructor that invokes the constructor of the superclass, either implicitly or by using the keyword super.  
Subclass does not inherit private members of its parent class, unless the superclass has public or protected methods to access the private fields(can be used by the subclass).  
A subclass can also be used in instances where object type is their parent class (eg. Mountainbike can be used when object type "Bicycle" or "Object is required) . 


Casting shows the use of one object in place of another
(Mountainbike is an Object but not the other way around)
```
Object obj = new MountainBike();
```

#### Interfaces  (Can be used as an API)
Similar to a class, but can contain only constants, method signatures, default methods, static methods, and nested types.  
Cannot be instantiated, only IMPLEMENTED by other classes or EXTENDED by other interfaces.  
Interfaces can contain abstract, default and static types.  
A class that implements an interface must implement all of that interface's method
Implementation of interface:
```
public class Example implements Interface{
...
}
```

Interface methods
```
public interface Animal {
    default public String identifyMyself() {
        return "I am an animal.";
    }
}
public interface EggLayer extends Animal {
    default public String identifyMyself() {
        return "I am able to lay eggs.";
    }
}
public interface FireBreather extends Animal { }
public class Dragon implements EggLayer, FireBreather {
    public static void main (String... args) {
        Dragon myApp = new Dragon();
        System.out.println(myApp.identifyMyself());
    }
}
//The method Dragon.identifyMyself returns the string I am able to lay eggs.
```

```
abstract class Dog{ 
 
 public void bark(){ System.out.println("woof"); }
 public void drool(){ System.out.println("drool");}

 public static void main(String[] args) {
  Dog f = new Hound();
  f.bark();
  f.drool();
  
 // Hound g = new Hound();
 // g.bark();   //retry
 // g.drool();
 
 }
}


class Hound extends Dog{
 public void sniff(){ System.out.println("sniff ");}
 @Override public void bark(){ System.out.println("growl");}
 public void drool(int time){ System.out.println("drool" + time);
 }
}
```
Dog g = new Hound();  
g.bark() returns growl  
g.drool(1) returns nothing  
g.drool() returns drool  
g.sniff returns nothing  
(WHY? g is of type Dog and will not run new methods from Hound. Will however have method bark overwritten.)  

Comparable
```
//Modify the class header and implement any necessary methods
public class Octagon implements Comparable<Octagon> {
    private double side;
    public Octagon(double side){
        this.side = side;
    }
    public double getSide() {
        return side;
    }

    public int compareTo(Octagon o){
        if(this.side>o.side){
            return 1;}
        else if (this.side==o.side){
            return 0;}
        else{
            return -1;}
        }
}
```

Comparator
```
import java.util.Comparator;

public class OctagonComparator implements Comparator<Octagon>{
    public int compare(Octagon a,Octagon b) {
        if(a.getSide()>b.getSide()) {
            return 1;
        }
        else if(a.getSide()==b.getSide()){
            return 0;
        }
        else{
            return -1;
        }
    }
}
```


### 6) Polymorphism  
Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class  
```
//in super class bicycle
public void printDescription(){
    System.out.println("\nBike is " + "in gear " + this.gear
        + " with a cadence of " + this.cadence +
        " and travelling at a speed of " + this.speed + ". ");
}
...
//in sub class mountainbike
public void printDescription() {
        super.printDescription();
        System.out.println("The " + "MountainBike has a" +
            getSuspension() + " suspension.");
    }
...
//in sub class roadbike
public void printDescription(){
        super.printDescription();
        System.out.println("The RoadBike" + " has " + getTireWidth() +
            " MM tires.");
    }

//output given that each class is instantiated and method 'printDescription' is used for each object
Bike is in gear 1 with a cadence of 20 and travelling at a speed of 10. 

Bike is in gear 5 with a cadence of 20 and travelling at a speed of 10. 
The MountainBike has a Dual suspension.

Bike is in gear 8 with a cadence of 40 and travelling at a speed of 20. 
The RoadBike has 23 MM tires.
```
By using the super keyword, you can invoke overridden method, as seen above (super.printDescription();).  
Superclass constructors can also be called using super(); or super(parameter list);  
Invocation of a superclass constructor must be the first line in the subclass constructor.  
```
public MountainBike(int startHeight, 
                    int startCadence,
                    int startSpeed,
                    int startGear) {
    super(startCadence, startSpeed, startGear);
    seatHeight = startHeight;
} 
```
If a constructor does not explicitly invoke a superclass constructor, the Java compiler automatically inserts a call to the no-argument constructor of the superclass. If the super class does not have a no-argument constructor, you will get a compile-time error. Object does have such a constructor, so if Object is the only superclass, there is no problem.

### 7) Abstract and Final
#### Abstract
An abstract class is a class that is declared abstract-may ior may not include abstract methods. (Cannot be instantiated, but can be subclassed)
An abstract method is a method that is declared without an implementation (without braces, followed by a semicolon)  
```
abstract void moveTo(double deltaX, double deltaY);
```
If a class includes abstract methods then it itself(the class) must be declared abstract
```
public abstract class GraphicObject {
   // declare fields
   // declare nonabstract methods
   abstract void draw();
}

class Circle extends GraphicObject {
    void draw() {
        ...
    }
    void resize() {
        ...
    }
}
```
Abstract classes are similar to interfaces in the sense that they cannot be instantiated, and may contain a mix of methods declared with or without implementation 

#### Final
You use the final keyword in a method declaration to indicate that the method cannot be overridden by subclasses.  
Note that you can also declare an entire class final. A class that is declared final cannot be subclassed. This is particularly useful, for example, when creating an immutable class like the String class.


### 8) Exceptions
``` 
public static testException(int i, int j){
    try{
        result = i/j;
        return result;
        }
    catch(ArithmeticException ex){
        return "It does not work"
        }
    finally{
        return "That's all"
        }
    }
```

Types of Exceptions:  
Arithmetic Exceptions, ArrayIndexOutOfBoundsException, ClassNotFoundException, FileNotFoundException, IOException, InterruptedException, NoSuchFieldException, NoSuchMethodException, NullPointerException, NumberFormatException, RuntimeException, StringIndexOutOfBoundsException 

"Finally" is executed regardless of the outcome (pass/fail)

### 9) Design Patterns
Types of Design Patterns covered:
- Singleton
- Observer
- Visitor

#### Singleton
Ensure a class has only one instance and provide a global point of access to it (eg. Log file for a pool of applications)  
Creational pattern used to construct objects
```
public class Singleton{
	private static Singleton instance=null;
	private Singleton(){
	}
	
	public static Singleton getInstance(){
	if(instance==null){
		instance=new Singleton();
		}
	return instance;
}
```

#### Observer
Useful when you are interested in the state of an object and want to get notified whenever there is any change  
Subject(Publisher) maintains a list of its dependents(observers/subscribers)  
Subject notifies them of any state changes  
A one-to-many dependency between objects so that when one object changes state,, all its dependents are notified and updated automatically  (eg. message board/notiofication on phone for weather)  
```
import java.lang.reflect.Array;
import java.util.ArrayList;

interface Observer{
    void update(double airPollutionIndex);
}

class Subscriber implements Observer{
    private Subject subject;
    private String observerId;
    public static String outputMessage = "";

    public Subscriber(String observerId, Subject subject){
        this.subject=subject;
        this.observerId = observerId;
        this.subject.register(this);		// register itself
    }

    @Override
    public void update(double airPollutionIndex) {
        String s = this.observerId + " received notification: " + airPollutionIndex;
        System.out.println(s);
        outputMessage += (s + " ");
    }
}

interface Subject{
    void register(Observer o);
    void unregister(Observer o);
    void notifyObservers();
}

//TODO: modify AirPollutionAlert to implement interface Subject, under Observer design pattern
class AirPollutionAlert implements Subject{
    private double airPollutionIndex;
    private ArrayList<Observer> observers;

    public AirPollutionAlert(){
        observers = new ArrayList<Observer>();
    }
    public void notifyObservers() {
        for (Observer o : observers)
            o.update(this.airPollutionIndex);
    }
    public void register(Observer o){
        observers.add(o);
    }

    public void unregister(Observer o){
        observers.remove(o);
    }

    public void setAirPollutionIndex(double airPollutionIndex) {
        this.airPollutionIndex = airPollutionIndex;
        if (this.airPollutionIndex>100){ notifyObservers();}
    }
    public static void main(String[] args) {
        AirPollutionAlert singaporeAlert = new AirPollutionAlert();
        Subscriber man = new Subscriber("man",singaporeAlert);
        Subscriber simon = new Subscriber("simon", singaporeAlert);

        singaporeAlert.setAirPollutionIndex(200);
        singaporeAlert.setAirPollutionIndex(50);
        singaporeAlert.setAirPollutionIndex(120);

        singaporeAlert.unregister(man);
        singaporeAlert.setAirPollutionIndex(300);
    }
}
```

#### Visitor
Useful if you need to perform operations across a diverse set of objects  
Allows for one or more operations to be applied to a set of objects at runtime, decoupling the operations from the object structure  
Use method overloading to pick the method for processing (different methods for different objects)  
```
interface ItemElement 
{ 
	public int accept(ShoppingCartVisitor visitor); 
} 

class Book implements ItemElement 
{ 
	private int price; 
	private String isbnNumber; 

	public Book(int cost, String isbn) 
	{ 
		this.price=cost; 
		this.isbnNumber=isbn; 
	} 

	public int getPrice() 
	{ 
		return price; 
	} 

	public String getIsbnNumber() 
	{ 
		return isbnNumber; 
	} 

	@Override
	public int accept(ShoppingCartVisitor visitor) 
	{ 
		return visitor.visit(this); 
	} 

} 

class Fruit implements ItemElement 
{ 
	private int pricePerKg; 
	private int weight; 
	private String name; 

	public Fruit(int priceKg, int wt, String nm) 
	{ 
		this.pricePerKg=priceKg; 
		this.weight=wt; 
		this.name = nm; 
	} 

	public int getPricePerKg() 
	{ 
		return pricePerKg; 
	} 

	public int getWeight() 
	{ 
		return weight; 
	} 

	public String getName() 
	{ 
		return this.name; 
	} 

	@Override
	public int accept(ShoppingCartVisitor visitor) 
	{ 
		return visitor.visit(this); 
	} 

} 

interface ShoppingCartVisitor 
{ 

	int visit(Book book); 
	int visit(Fruit fruit); 
} 

class ShoppingCartVisitorImpl implements ShoppingCartVisitor 
{ 

	@Override
	public int visit(Book book) 
	{ 
		int cost=0; 
		//apply 5$ discount if book price is greater than 50 
		if(book.getPrice() > 50) 
		{ 
			cost = book.getPrice()-5; 
		} 
		else
			cost = book.getPrice(); 
			
		System.out.println("Book ISBN::"+book.getIsbnNumber() + " cost ="+cost); 
		return cost; 
	} 

	@Override
	public int visit(Fruit fruit) 
	{ 
		int cost = fruit.getPricePerKg()*fruit.getWeight(); 
		System.out.println(fruit.getName() + " cost = "+cost); 
		return cost; 
	} 

} 

class ShoppingCartClient 
{ 

	public static void main(String[] args) 
	{ 
		ItemElement[] items = new ItemElement[]{new Book(20, "1234"), 
							new Book(100, "5678"), new Fruit(10, 2, "Banana"), 
							new Fruit(5, 5, "Apple")}; 

		int total = calculatePrice(items); 
		System.out.println("Total Cost = "+total); 
	} 

	private static int calculatePrice(ItemElement[] items) 
	{ 
		ShoppingCartVisitor visitor = new ShoppingCartVisitorImpl(); 
		int sum=0; 
		for(ItemElement item : items) 
		{ 
			sum = sum + item.accept(visitor); 
		} 
		return sum; 
	} 

} 
```




### 10) Recursion
Possibility of a method to call itself  
2 main requirements:  
-Stop condition: function returns a value when a certain condition is satisfied, without a further recursive call
-The recursive call: function calls itseld with an input which is a step closer to the stop condition
```
public int sum(int n) {
    if (n >= 1) {
        return sum(n - 1) + n;
    }
    return n;
}
```

Example of Tail recursion(Recursive call is the last thing the function does):
```
public int tailSum(int currentSum, int n) {
    if (n <= 1) {
        return currentSum + n;
    }
    return tailSum(currentSum + n, n - 1);
}
```

Another example of recursion:
```
public int powerOf10(int n) {
    if (n == 0) {
        return 1;
    }
    return powerOf10(n-1) * 10;
}
```

### 11) Math Functions
|Method|Description|
|------|-----------|
|Math.abs()|	It will return the Absolute value of the given value.|
|Math.max()|	It returns the Largest of two values.|
|Math.min()|	It is used to return the Smallest of two values.|
|Math.round()|	It is used to round of the decimal numbers to the nearest value.|
|Math.sqrt()|	It is used to return the square root of a number.|
|Math.cbrt()|	It is used to return the cube root of a number.|
|Math.pow()|	It returns the value of first argument raised to the power to second argument.|
|Math.signum()|	It is used to find the sign of a given value.|
|Math.ceil()|	It is used to find the smallest integer value that is greater than or equal to the argument or mathematical integer.|
|Math.copySign()|	It is used to find the Absolute value of first argument along with sign specified in second argument.|
|Math.nextAfter()|	It is used to return the floating-point number adjacent to the first argument in the direction of the second argument.|
|Math.nextUp()|	It returns the floating-point value adjacent to d in the direction of positive infinity.|
|Math.nextDown()|	It returns the floating-point value adjacent to d in the direction of negative infinity.|
|Math.floor()|	It is used to find the largest integer value which is less than or equal to the argument and is equal to the mathematical integer of a double value.|
|Math.floorDiv()|	It is used to find the largest integer value that is less than or equal to the algebraic quotient.|
|Math.random()|	It returns a double value with a positive sign, greater than or equal to 0.0 and less than 1.0.|
|Math.rint()|	It returns the double value that is closest to the given argument and equal to mathematical integer.|
|Math.hypot()|	It returns sqrt(x2 +y2) without intermediate overflow or underflow.|
|Math.ulp()|	It returns the size of an ulp of the argument.|
|Math.getExponent()|	It is used to return the unbiased exponent used in the representation of a value.|
|Math.IEEEremainder()|	It is used to calculate the remainder operation on two arguments as prescribed by the IEEE 754 standard and returns value.|
|Math.addExact()|	It is used to return the sum of its arguments, throwing an exception if the result overflows an int or long.|
|Math.subtractExact()|	It returns the difference of the arguments, throwing an exception if the result overflows an int.|
|Math.multiplyExact()|	It is used to return the product of the arguments, throwing an exception if the result overflows an int or long.|
|Math.incrementExact()|	It returns the argument incremented by one, throwing an exception if the result overflows an int.|
|Math.decrementExact()|	It is used to return the argument decremented by one, throwing an exception if the result overflows an int or long.|
|Math.negateExact()|	It is used to return the negation of the argument, throwing an exception if the result overflows an int or long.|
|Math.toIntExact()|	It returns the value of the long argument, throwing an exception if the value overflows an int|


### Static VS Dynamic Checking (from MIT 6.005)
It’s useful to think about three kinds of automatic checking that a language can provide:

Static checking: the bug is found automatically before the program even runs.
Dynamic checking: the bug is found automatically when the code is executed.
No checking: the language doesn’t help you find the error at all. You have to watch for it yourself, or end up with wrong answers.
Needless to say, catching a bug statically is better than catching it dynamically, and catching it dynamically is better than not catching it at all.

Here are some rules of thumb for what errors you can expect to be caught at each of these times.

Static checking can catch:

syntax errors, like extra punctuation or spurious words. Even dynamically-typed languages like Python do this kind of static checking. If you have an indentation error in your Python program, you’ll find out before the program starts running.
wrong names, like Math.sine(2). (The right name is sin.)
wrong number of arguments, like Math.sin(30, 20).
wrong argument types, like Math.sin("30").
wrong return types, like return "30"; from a function that’s declared to return an int.
Dynamic checking can catch:

illegal argument values. For example, the integer expression x/y is only erroneous when y is actually zero; otherwise it works. So in this expression, divide-by-zero is not a static error, but a dynamic error.
unrepresentable return values, i.e., when the specific return value can’t be represented in the type.
out-of-range indexes, e.g., using a negative or too-large index on a string.
calling a method on a null object reference (null is like Python None).
Static checking tends to be about types, errors that are independent of the specific value that a variable has. A type is a set of values. Static typing guarantees that a variable will have some value from that set, but we don’t know until runtime exactly which value it has. So if the error would be caused only by certain values, like divide-by-zero or index-out-of-range then the compiler won’t raise a static error about it.

Dynamic checking, by contrast, tends to be about errors caused by specific values.
