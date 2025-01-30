# Part3-Exercise4

### A)

The best choice for represeinting temperature is a record class because it fits the characteristics of a temperature value. Temperature has value semantics which means two temperatures with the same numerical value in the same scale should be considered equal, and records provide automatic equality and hashing based on fields. Moreover, since a temperature should not be changed after being created, immutability of record prevents accidental changes to temperature values. Additionally, temperature requires easy printing and conversion between scales (Celsius, Fahrenheit, Kelvin), which can be easily done by defining methods inside the record. Other options such as enum are not suitable because temperature values are not a fixed set but rather a continuous range or anonymous and nested classes are useful because Nested and Anonymous classes are useful when a class needs to be closely linked to another, but Temperature does not need to be tied to another class to function properly. A sealed class is also not useful because restricting inheritance provides no additional benefits, as Temperature can be fully represented using a value and scale without requiring a class hierarchy.


























