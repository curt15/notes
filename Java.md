Links: [[PROGRAMMING]]

--- 

[Design Patterns Video tutorial - Derek Banas](https://www.youtube.com/watch?v=vNHpsC5ng_E&list=PLF206E906175C7E07)
1. 

OOP - object oriented programming

class
fields, instance variables ()
methods, functions (parameter->argument <- local variables)
abstract out those features 
override or extend methods

property->
getter=accessors
setter=mutators

Is A? versus has A? 
Is a dog an animal?
is a dog a cat?
dog has a height?

animal.java
```java
public class Animal {
	private String name;
	private int weight;
	private String sound;
	
	public void setName(String newName){ name = newName }
	public String getName() { return name; }
	public void setWeight(int newWeight){
		if(newWeight > 0){
			weight = int newWeight;
		} else {
			System.out.println("Weight must be bigger than 0");
		}
	}
	public int getWeight(){ return weight; }

	public void setSound(String newSound){ sound = newSound; }
	public String getName(){ return name; }
}
```
dog.java
```java
public class Dog extends Animal {
	public void digHole(){
		System.out.println("Dug a hole")
	}
	
	public Dog(){
		super();
		
		setSound("Bark")
	}
	public void changeVar(int randNum){
		randNum = 12
		System.out.println("randNum in method: " + randNum) # 12
	}
}
```
cat.java
```java
public class Cat extends Animal {
	
	public Cat(){
		super();
		
		setSound("Meow")
	}
```
workwithanimals.java
```java

public class WorkWithAnimals{

	public static void main(String[] args){
		Dog fido = new Dog();
		fido.setName("Fido")
		System.out.println(fido.getName());
		
		fido.digHole()
		fido.setWeight(-1)
		
		int randNum = 10
		fido.changeVar(randNum);
		System.out.println("randNum after method call: " + randNum ); # 10
		
		
		changeObjectName(fido);
		System.out.println(fido.getName()); # changed
	}
	
	public static void changeObjectName(Dog fido){
		fido.setName("Marcus")
	}
	
}
```

