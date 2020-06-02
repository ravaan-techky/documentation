## Java Code Conventions

### File Names
```markdown
_Usually class name should be noun starting with uppercase letter. If it 
contains multiple word than every inner word should start with uppercase._
```
### Naming Conventions

Java naming conventions are set of rules to make Java code look uniform 
across Java projects and the library. They are not strict rules, but a 
guideline to adhere to as a good programming practice. It is, therefore, 
not a good idea to violate the sanctity of the code uniformity either due 
to haste or rebellion. The rules are pretty simple.

- Package names are types in lowercase: javax.sql, org.junit, java.lang.
- Class, enum, interface, and annotation names are typed in uppercase: 
Thread, Runnable, @Override.
- Methods and field names are typed in a camel case: deleteCharAt, add, isNull.
- Constants are types in uppercase separated by an underscore: SIZE, MIN_VALUE.
- Local variables are typed in camel case: employeeName, birthDate, email.

**_These conventions have become so much apart of Java that almost every programmer 
follows them religiously. As a result, any change in this looks outlandish 
and wrong. An obvious benefit of following these conventions is that the style 
of code aligns with the library or framework code. It also helps other 
programmers to quickly pick up the code when they have to, therefore leveraging 
overall readability of the code._**

**_Coding Standards for Classes:**_ Usually class name should be noun starting 
with uppercase letter. If it contains multiple word than every inner word should 
start with uppercase.
```java
Eg: String, StringBuffer, Dog
```
**_Coding Standards for Interface:**_ Usually interface name should be adjective 
starting with uppercase letter. If it contains multiple word than every inner word 
should start with uppercase.
```java
Eg: Runnable, Serializable, Comparable
```
**_Coding Standards for Methods:**_ Usually method name should either be verb or 
verb noun combination starting with lower letter. If it contains multiple word than 
every inner word should start with uppercase.
```java
Eg: print(), sleep(), setSalary()
```
**_Coding Standards for Variables:**_ Usually variable name should be noun starting 
with lowercase letter. If it contains multiple word than every inner word should 
start with uppercase.
```java
Eg: name, age. mobileNumber
```
**_Coding Standards for Constants:**_ Usually constant name should be noun. It 
should contain only uppercase If it contains multiple word than words are separated 
with ( _ ) underscore symbol. Usually we declare constants with public static and 
final modifiers.<br/>
Java Bean Coding Standards: A Java Bean is a simple java class with private 
properties and public getter and setter methods<br/><br/>
**Getter Methods:**
- It should be public method
- Method name should be prefixed with “get”
- It should not take any argument

**Setter Methods:**
- It should be public method
- Return Type should be void
- Method name should be prefixed with “set”
- It should take some argument with final

```java
public class StudentBean{
	private String name;
	public void setName(final String name){
		this.name=name;
	}
	public String getName(){
		return name;
	}
}
```
**Note:** For boolean properties getter method can be prefixed with “get” or “is”

###  Variable Scopes, Readability, and Lambda Expression
In Java, every variable declared has a scope. This means that the visibility and 
use of the variables must be restricted within the scope only. In case of a local 
variable, it is visible from the point of its declaration to the end of the method 
or code block it is declared in. It is a good practice to declare a variable close 
to the point of its possible use. This not only enhances readability of the code 
but also makes debugging simpler.

```java
try
   final Connection connection = DriverManager.getConnection(DATABASE_URL, USERNAME, PASSWORD);
   final Statement statement = connection.createStatement();
   final ResultSet resultSet = statement.executeQuery(SQL_QUERY)
){
  //...QUERY RETRIVAL LOGIC
} catch (SQLException exception){
   exception.printStackTrace();
}
```
Observe in the code snippet how the scope of the local variables is made limited 
within the blocks they are declared in. The variables are invisible as soon as the 
block ends. Also, the code becomes more intuitive, readable, and clean.<br/>
However, from Java 8 we can leverage lambda expressions to make the code more 
concise and intuitive. To illustrate the idea, note how we can club many utilities 
within a single line of lambda expression.

```java
Integer[] nums={90, 71, 26, 34, 42, 35, 66, 57, 88, 89};
```

Prints original numbers.

```java
final List<Integer> l1 = Arrays.asList(nums);
System.out.printf("Original :%s%n",l1);
```

_Now we use lambda expression to print numbers after sorting in 
ascending order._

```java
final List<Integer> l2 = Arrays.stream(nums).sorted().collect(Collectors.toList());
System.out.printf("After sorting: %s%n",l2);
```
_We can apply more utility, such as printing only those numbers that 
are greater than, say, 50, after sort them in ascending order._

```java
final List<Integer> l3 = Arrays.stream(nums).filter(num -> num > 50).collect(Collectors.toList());
System.out.printf("Sorting only of numbers > 50 : %s%n", l3);
```
### Treating Method Arguments as Local Variables
In Java, a variable once declared can be reused. Therefore, the non-final local variables
declared in the method arguments can also be reused with a different value. However, this 
is not a good idea because the variable sends as a method argument what is supposed to 
hold the value it has brought, the original value that the method with work upon. 
If we change the value, we'll completely lose the original content that is brought forth 
in the method. Instead, what we must do is copy the value to another variable and do the 
necessary processing. We, however, can completely restrict and make the argument variable 
a constant by using the final keyword as follows.

```java
public double calculate(final double newVal){
   double tmp = newVal;
    // ...
   return tmp;
}
```
### String Usage
No other types in Java have be extended as much as String. Java strings are represented 
in UTF-16 format and are immutable objects. This means that every time we perform an operation 
like concatenation, that needs modification of the original string, a new string object is created.<br/>
This intermediate string object, created only to perform the needed operation, is a waste and 
inefficient. This is because intermediary object creation is extraneous; it involves garbage collection, 
although we can avoid it.<br/>
**_There are two companion string classes, called StringBuffer and StringBuilder, which can aptly facilitate 
the kind of string manipulation we may need. These two classes are built for that. The only difference 
between StringBuffer and StringBuilder is that the former is thread-safe. We can use these two classes 
whenever need extensive string manipulation rather than using the immutable String instance._**

```java
final StringBuilder stringBuilder = new StringBuilder();
stringBuilder.append("Hello");
stringBuilder.append(108);
stringBuilder.deleteCharAt(0);
stringBuilder.insert(0, "h");
stringBuilder.replace(stringBuilder.length() - 3, stringBuilder.length(), ".");
System.out.println(stringBuilder);
```
### Comments

**_Documentation / Package Level Comment:**_

**_Class Level Comment:**_
Every class should have proper comment with proper description about class using "JavaDoc" convention.
```java
/** 
* <h1>Find average of three numbers!</h1> 
* The FindAvg program implements an application that 
* simply calculates average of three integers and Prints 
* the output on the screen. 
* 
* @author  Bhushan Patil 
* @version 1.0 
* @since   2020-05-18 
*/
public class AverageFinder {
	//....
}
```

**_Constant Variable Comment:**_

**_Instance Variable Comment:**_
Every instance variable should be preceded with a descriptive comment using the "JavaDoc" convention. 
The comment should describe the purpose for the public variable.
```java
/** Toggles between frame and no frame mode. */
private boolean frameMode = true;
```

**_Method Level Comment:**_
Every method definition should be preceded with a descriptive comment using the "Javadoc" convention.<br/>
The comment should include a description of the method, the name and description of each parameter, 
a description of the return value, and the name and description of any exceptions thrown within 
the method using Javadoc keywords and formatting.
```java
/**
 * Prints a word, prints a number, and returns integer 1
 *
 * @param word any string of Class String
 * @param number an integer of any value
 * @return the integer 1 
 * @exception MyException if the word starts with the letter 'z'
 * @exception YourException if the number is a zero(0)
 */ 
public static int method1 (String word, Integer number) throws MyException, YourException {
  //code...
  if (word.charAt(0) == 'z') {
    //thrown, but not caught in method, so put in JavaDocs above 
    throw new MyException();
  }
  if (number == 0) {
    //thrown, but not caught in method, so put in JavaDocs above
    throw new YourException();
  }
  try {
    int x = 5 / 0;
  } catch (ArithmeticException exception) {
    System.out.println("ERROR: Division by zero! " + exception); 
  }
  return 1; 
}
```

### Immutability
The concept of immutability is very important. We must decide whether the classes we 
intend to design can be made immutable or not, because immutability guarantees that it 
could be used almost everywhere without any trouble from concurrent modification. 
Unfortunately, not all classes can be designed as immutable.<br/> 
But, make sure we must do so whenever we can. This makes life much easier.

### Testing
Test driven practices (TDD) are a symbol of quality code among the Java community. 
Testing is a part of modern-day Java development, and the Java Standard Library has the 
**Junit framework** OR **TestNG framework** to assist in that direction.<br/>
So, a budding Java programmer should not shy away from writing test cases with the code. 
Try to keep tests simple and short, focusing on one thing at a time. There can be hundreds 
of test cases in production environment. An obvious benefit of writing test cases is that 
they provide immediate feedback of the features under development.
