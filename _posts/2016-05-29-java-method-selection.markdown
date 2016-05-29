Here is a interesting java overloading and overriding problem from [stackoverflow](http://stackoverflow.com/questions/14676395/java-overloading-method-selection/14676432#14676432). It has a great help for me to understand the complile-time type and run-time type, and how java select methods dynamicly.

```java
	//Example 1 prints Square:add(Figure)
	Figure fs = new Square();
	fs.add(fs);
		
	//Example 2 prints Square:add(Figure)
	Rectangle rs = new Square();
	rs.add(fs);
		
	//Example 3 prints Rectangle:add(Rectangle). Expected Square:add(Square)
	rs.add(new Square());
		
	//Example 4 prints Rectangle:add(Rectangle). Expected Square:add(Figure)
	Square ss = new Square();
	ss.add(rs);
	
	class Figure
	{
		public void add(Figure f){ System.out.println("Figure:add(Figure)"); }
	}
	
	class Rectangle extends Figure
	{
		@Override
		public void add(Figure f){ System.out.println("Rectangle:add(Figure)"); }
		public void add(Rectangle r){ System.out.println("Rectangle:add(Rectangle)"); }
	}
	
	class Square extends Rectangle
	{
		@Override
		public void add(Figure f){ System.out.println("Square:add(Figure)"); }
		public void add(Square s){ System.out.println("Square:add(Square)"); }
	}
````

Answer from Jon Skeet is very clear and useful!
> However, I don't understand the result of example 3 and 4.

Okay, let's look at them individually.

**Example 3**
```java
    //Example 3 prints Rectangle:add(Rectangle). Expected Square:add(Square)
    rs.add(new Square());
```

The important parts are the *compile-time* types of the expressions `rs` and `new Square()`.

`rs` is only declared as `Rectangle`, so the compiler will look at the methods declared by `Rectangle` and its superclasses:

```java
    public void add(Figure f)
    public void add(Rectangle r)
```

The type of the expression `new Square()` is `Square`, so both methods are *applicable* - but the second one is more *specific*.

So the compiler will call `add(Rectangle)` on the object that `rs` refers to. That's it for the compile-time side.

At execution time, the value of `rs` refers to an instance of `Square` - but `Square` doesn't override `add(Rectangle)` so the method picked is the implementation in `Rectangle`:

```java
    public void add(Rectangle r){ System.out.println("Rectangle:add(Rectangle)"); }
```

**Example 4**

```java
    //Example 4 prints Rectangle:add(Rectangle). Expected Square:add(Figure)
    Square ss = new Square();
    ss.add(rs);
```

Again, let's consider the compile-time types involved... `ss` is of type `Square`, and `rs` is of type `Rectangle` (compile-time types, remember).

The methods declared by `Square` and its superclasses are:

```java
  	public void add(Figure f)
    public void add(Rectangle r)
    public void add(Square s)
```

As the compile-time type of `rs` is only `Rectangle` (not `Square`), the first two methods are applicable, but the third isn't. Therefore, again, `add(Rectangle)` is picked at compile time (as it's more specific than `add(Figure)`).

Again, the execution time type of `ss` is `Square`, which doesn't override `add(Rectangle)`, so the implementation in `Rectangle` is used.
