# Writing a Java object to a file

```java
final String PATH_TO_FILE = "/path/to/file";
Object object = new Object(); // The object you want to write to file

ObjectOutputStream outStream = new ObjectOutputStream(new FileOutputStream(PATH_TO_FILE));
outStream.writeObject(object);

outStream.close(); // Make sure you close the output stream
```

# Reading a Java object from a file

```java
final String PATH_TO_FILE = "/path/to/file";
Object object;

ObjectInputStream inStream = new ObjectInputStream(new FileInputStream(PATH_TO_FILE));
object = (Object) inStream.readObject(); // readObject() returns type of Oject so a cast is needed to whatever type is of interest ie. List

inStream.close();
```