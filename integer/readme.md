# Autoboxing

* This is the automatic conversion between Java's primitive types and their corresponding object wrapper classes. ie. `int` to/from `Integer` and `boolean` to/from `Boolean`

For example, you may want to write the following:

```java
Integer a = new Integer(12); // OR
Integer b = Integer.valueOf(12);
```

However, it is sufficient to simply write the following and autoboxing will automatically assign `a` with an Integer object with the value of 12

```java
Integer a = 12;
```

# Unboxing

* This is the automatic conversion from a Java object to its corresponding primitive type. ie. `Integer` to `int` and `Boolean` to `boolean`

Similarly, Java will implicitly invoke the `intValue()` method at runtime to convert an `Integer` object to an `int` primitive type when necessary. For example:

```java
Integer a = 12;

if (a == 12){
	System.out.println("a is 12");
}
```

## Caveats

* The first call to `Integer.valueOf(a)` where `a` is od type `int` and is satifies the following `-128 <= a <= 127` results in the JVM caching the objects `Integer.valueOf(i)` from `i = -128` to `i = 127` in memory. This results in some unintuitive behaviour when comparing `Integer.valueOf()` objects using `==`. For example:

```java
System.out.println(Integer.valueOf(1) == Integer.valueOf(1)); // true
System.out.println(Integer.valueOf(127) == Integer.valueOf(127)); // true
System.out.println(Integer.valueOf(-128) == Integer.valueOf(-128)); // true
System.out.println(Integer.valueOf(128) == Integer.valueOf(128)); // false
``` 

What is actually happening is that the memory addresses are being compared and since the Integer objects for `valueOf()` from -128 to 127 have been cached in memory, those memory addresses are being used in the comparison.