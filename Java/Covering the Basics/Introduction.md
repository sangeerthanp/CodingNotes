>[!refer]
>https://www.google.com/search?q=oracle+java+tutorials&rlz=1C1VDKB_enIN1018IN1018&oq=oracle+java+tu&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyBwgBEAAYgAQyBggCEEUYOTIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIKCAcQABiABBiiBNIBCDY4NjFqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8

In the Java programming language, all source code is first written in plain text files ending with the `.java` extension. 

Those source files are then compiled into `.class` files by the `javac` compiler.

A `.class` file does not contain code that is native to your processor; it instead contains _bytecodes_ — the machine language of the Java Virtual Machine (Java VM). 

The `java` launcher tool then runs your application with 
an instance of the Java Virtual Machine.

![[../../../../Pasted image 20240808104603.png]]

```java
class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}
```

The "Hello World!" application consists of two primary components: 
1) [the `HelloWorldApp` class definition](https://docs.oracle.com/javase/tutorial/getStarted/application/index.html#CLASS_DEF)
2) )[the `main` method](https://docs.oracle.com/javase/tutorial/getStarted/application/index.html#MAIN).

**The `HelloWorldApp` Class Definition**
		
>[!definition]
	class _name_ {
    . . .
	}

As shown above, the most basic form of a class definition.

**The `main` Method**

>[!Definition]
	public static void main(String[] args)

In the Java programming language, every application must contain a `main` method.

The modifiers `public` and `static` can be written in either order (`public static` or `static public`)

You can name the argument anything you want, but most programmers choose "args" or "argv".

The `main` method is similar to the `main` function in C and C++; it's the entry point for your application and will subsequently invoke all the other methods required by your program.

The `main` method accepts a single argument: an array of elements of type `String`.

>[!Definition]
	System.out.println("Hello World!");

The above line uses the `System` class from the core library to print the "Hello World!" message to standard output.

>[!tip]
>https://docs.oracle.com/javase/tutorial/getStarted/QandE/answers.html

 