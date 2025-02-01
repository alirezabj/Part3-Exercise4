# Part3-Exercise4

### A)

The best choice for represeinting temperature is a record class because it fits the characteristics of a temperature value. Temperature has value semantics which means two temperatures with the same numerical value in the same scale should be considered equal. Moreover, since a temperature should not be changed after being created, immutability of a record prevents accidental changes to temperature values. Additionally, temperature requires easy printing and conversion between scales (Celsius, Fahrenheit, Kelvin), which can be easily done by defining methods inside the record. Other options such as enum are not suitable because temperature values are not a fixed set but rather a continuous range. Similarly, nested and anonymous classes are useful when a class needs to be closely linked to another, but temperature does not need to be tied to another class to function properly. A sealed class is also not useful because restricting inheritance provides no additional benefits as temperature can be fully represented using a value and scale without requiring a class hierarchy.

### B)

The best choice for representing diseases is a static inner class because it allows related classes to be grouped together without relying on an instance of the outer class. For example, a Disease class could be defined inside a larger MedicalDatabase or Hospital class to keep disease information organized. Moreover, this structure allows for the creation and updating of diseases, as new ones might appear in the future. Other options are less suitable. An instance-specific inner class requires a specific outer instance, which diseases don’t need. An anonymous class is meant for temporary, one time use and is not reusable. An enum defines a fixed set of constant values and is too restrictive, making it unsuitable since new diseases appear in the future. Record classes are immutable, but disease attributes like symptoms may change. Finally, sealed classes limit inheritance, which isn’t practical when new diseases are discovered.




### C)

For representing university student database query results, a record class is the best choice because each row in the query result consists of immutable data fields (name, postal address, email, degree program, and number of credits), which cannot be changed. A record provides an efficient way to model these values due to its immutable nature. However, other class types are less suitable for this task. For example, an instance-specific inner class is not appropriate because the student record is not tied to an outer class. Additionally, anonymous classes are intended for temporary use cases rather than data storage, making them unsuitable. Similarly, enum classes are designed for predefined fixed values, but the number of students is dynamic and can change over time. Finally, sealed classes restrict inheritance, causing unnecessary complexity for this simple data representation.

### D)

The most appropriate Java mechanism for this task is Function literals and interfaces. Instead of writing a loop every time, we define a function that takes a student’s data and checks if their credits are 280 or more. This function acts as a rule that can be reused whenever we need to filter students. Since Java allows functional interfaces to be implemented using function literals , we can define this rule in a short and clear way without creating extra classes. This makes the filtering process simpler, more reusable, and easier to read compared to manually writing a loop each time. Other options such as enum, sealed, and record are not suitable since they are designed for data representation and inheritance rather than defining reusable filtering logic.

### E)

```java
class Point {
    final int[] values = new int[2];
    
    Point(int x, int y) {
        values[0] = x;
        values[1] = y;
    }
}
```
**Behavior:**
- Reading: x and y coordinates can be accessed using values[0] and values[1]
- Modification: It is possible even though the values array is final because final only prevents reassignment of the reference, not modifications to the array itself. For example, point.values[0] = 10; will change the x coordinate.
- Sharing: Risky since arrays are mutable, if the values array is shared with other objects or clients, they can modify the coordinates. 

---


```java
record Point(int x, int y) {}
```
**Behavior:**
- Reading: x and y coordinates can be accessed using (point.x(), point.y())
- Modification: It is not possible becasue record fields are immutable.
- Sharing: Safe becasue each instance of Point is immutable.
In this example, objects are immutable and safe to share and cannot be modified after creation.

---

```java
record Point(Number x, Number y) {
    Point(int x, int y) {
        this(new Number(x), new Number(y));
    }
}

```
**Behavior:** 
- Reading: x and y coordinates can be accessed using (point.x().value, point.y().value)
- Modification: Although the record is immutable and we cannot assign new Number objects to x or y, the contents of the Number objects are mutable. For example, point.x().value = 20; will change the x coordinate. 
- Sharing: Risky since although the record itself is immutable, sharing the Number objects allows other clients to modify the coordinate values. 






















