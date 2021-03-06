# Visual Studio + C# + .NET studies

## [1: The famous HelloWorld]()

### Simple code:
```csharp
using System;

class HelloWorld
{
  public static void Main()
  {
    Console.WriteLine("Hello World!");
  }
}
```
### Compile with:
```csc HelloWorld.cs```
### Run with: 
```HelloWorld.exe```

## [2: Little concepts]()

### Entity framework:
A framework to work easily with database inside the code. It auto creates connections, and we don't need to take care about many things.

### Scaffolding:
Framework that creates methods and views of CRUD.

### Anonymous methods
A method that have not

## [3: Events and Delegate](https://github.com/felipeaugustox/csharp-studies/tree/master/EventsAndDelegate)

### Event
> A mechanism for communication between objects

> This is a way to use some methods without the needy of the entire class.

### Delegate

> It's similar to pointers in C/C++

> A agreement/contract between publisher and subscriber

> Determines the signature of the event handler method in subscriber

### Way to use them:

- [x] **Define a delegate and define an event based on that delegate**

**First way:**

```csharp
Public delegate void MethodNameEventHandler(object source, EventArgs args)
```
* Source: the class that is pusblishing/sending the event
* Args: any arguments we could pass
* In .NET there is a convention to name the delegate method as Name + EventHandler ( ```MethodNameEventHandler``` )
	
```csharp
Public event MethodNameEventHandler VideoEncoded;
```

**Other (best) way:**

Define a without args as parameters

```csharp
public event EventHandler VideoEncoded;
```

Define a with args as parameters

```csharp
public event EventHandler<EventArgs> VideoEncoded;
```

* The event. It's just a pointer to the events that we can define after.
* ○ The event has the same name of the eventHandler

- [x] **Raise the event**

```csharp
Protected virtual void OnEventName(){}
```
* The method that calls the event
* .NET suggestions that the event publisher methods should be protected, virtual and void, start with the word On and the name of the event (VideoEncoded)

### The benefits
We can see that it's not necessary to change the class that have the delegates, we can just put more and more events.

## [4: Lambda expressions](https://github.com/felipeaugustox/csharp-studies/tree/master/EventsAndDelegate)
Lambda expression is *anonymous function* that can be used to create *delegates* or types of *expression threes*

### Seeing the logic 
As a way to see how it's possible, we can separate in steps the transformation of a normal function to a anonymous function, you can see a example below:

1. First we normal function, that makes a filter of a list:
```csharp
var list = new List<int>() {1, 2, 3, 4, 5, 6, 7, 8};

var filteredList = list.Where(
  public bool filter(int x){
    return x > 4;
  }
);
```

2. Then, we can make some modifications to tranform to a anonymous function:

    1. The previous method would be executed only inside the ```Where```, then we don't need the ```public``` modificator
    2. The ```Where``` already waits for a return ```boolean```, then we don't need to specify the type of the return
    3. The ```Where``` already waits for the type ```int``` of the parameter (according to the type of the list), then we don't need to specify that
    4. The function would be executed at only one place, then we don't need to specify the name of the function
    5. We don't need the curly braces if the function has only one line
    6. if return is a boolean we don't need the word ```return```
    7. If we have only one parameter, we don't need to put the parentheses
    8. The final thing is put a arrow between the parameter and the function


```csharp
var list = new List<int>() {1, 2, 3, 4, 5, 6, 7, 8};

var filteredList = list.Where(x => x > 4;);
```


### The benefits

* We can use a function without that beeing coupled with the class.
* That turns the function smaller

## [Web.config and package.config]()

**Web.config** - used to define DLLs (including the versions) for our projects
**Package.config*** - used to define the packages for Visual Studio

**Web.config vs App.config**

The choice of the configuration file name is determined by the hosting environment you choose for the service. If you are using IIS to host your service, use a Web.config file. If you are using any other hosting environment, use an App.config file.

TODO - https://weblogs.asp.net/jongalloway/10-things-asp-net-developers-should-know-about-web-config-inheritance-and-overrides

## [LINQ]()

TODO

## [MVC Modularity]()

### Html.Partial
```
@Html.Partial("ButtonBuy", new { text = "I'm modular", color = "red" });
```
It's possible to make Views and invoke inside them other pieces of code (like a button). That makes the code more modular and improve the speed of coding. There is a new way is using _View Components_ through [ASP .NET Core MVC](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/view-components) with a benefit to be able to work with database.

### View Components

## Links of study:

* [Fundamentals for absolute beginners](https://mva.microsoft.com/en-US/training-courses/c-fundamentals-for-absolute-beginners-16169?l=Lvld4EQIC_2706218949)

* [How to become a backend developer](https://enterwell.net/become-c-sharp-backend-developer/)

* [Step by step C# 2013](https://ptgmedia.pearsoncmg.com/images/9780735681835/samplepages/9780735681835.pdf)