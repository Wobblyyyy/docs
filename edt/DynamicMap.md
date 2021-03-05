---
layout: default
title: EDT DynamicMap
parent: EDT
nav_order: 2
---

# DynamicMap
Maps, a very cool concept. Who doesn't love them?

##### TABLE OF CONTENTS
1. 
{:toc}

### Performance
The `DynamicMap` class seeks to improve overall performance when compared to other
implementations of the map concept, such as the well-loved `HashMap`. When compared
to the `HashMap`, the `DynamicMap` outperforms it in every category except for getting
values. This translates to huge performance boosts on everything except for the largest
of maps with thousands of keys. Specifically, the `DynamicMap` is faster than the
`HashMap` until the size of the map increases above 13,000 entries, which, in case you
weren't aware, is quite a few entries. 

## Usage 
Usage documentation for the DynamicMap class is provided through examples. Anything
not clear from the examples should be explained in the JavaDocs for the class. Anything
not explained there can hopefully be explained via code - hopefully, that is.

### Creating a new DynamicMap
Dynamic map creation can be accomplished via a couple different methods.

#### Method 1: No parameters
```java
DynamicMap<String, String> map = new DynamicMap<>();
```

#### Method 2: With a defined size
```java
// The integer parameter here is the minimum size of the map. 
// This is the size the map will allocate upon creation. If the map needs
// to grow, re-allocation costs can be rather expensive. Thus, this size 
// should be slightly larger than the maximum amount of elements you
// think you'll ever have in your map.
DynamicMap<String, String> map = new DynamicMap<>(100);
```

#### Method 3: From a Map
Create a map using another map. The input map should implement the map
interface provided by Java. This allows you to create a dynamic map based
on a HashMap or any other type of map you'd like.
```java
Map<String, String> javaMap = { map goes here };
DynamicMap<String, String> map = new DynamicMap<>(javaMap);
```

#### Method 4: With an array of `KeyValue<K, V>` pairs
Create a map by using an array of `KeyValue<K, V>` pairs, where K is the key
type and V is the value type.
```java
KeyValue<String, String>[] pairs = new KeyValue<>[] {
  new KeyValue<>("String 1 Key", "String 1 Value"),
  new KeyValue<>("String 2 Key", "String 2 Value"),
  new KeyValue<>("String 3 Key", "String 3 Value"),
};
DynamicMap<String, String> map = new DynamicMap<>(pairs);
```

### Add an entry
Add an entry to a map using a variety of different methods. This will add the 
entry to the map, regardless of that key or value already exists in the map. If
you'd like to add an entry to the map without creating situations in which
there's two of the same key or two of the same value, you can use the
`put(K, V)` method instead.
```java
DynamicMap<String, String> map = new DynamicMap<>();
```

#### Add without index
Add an entry to the map without an index. 
```java
map.add("String 1 Key", "String 1 Value");
map.add("String 2 Key", "String 2 Value");
map.add("String 3 Key", "String 3 Value");
// The map now contains 3 entries:
// String 1 Key - String 1 Value
// String 2 Key - String 2 Value
// String 3 Key - String 3 Value
```

#### Add with index 
Add an entry to the map with an index. Unless you have an advanced use case, you
probably shouldn't use index whatsoever. 
```java
map.add(2, "String 3 Key", "String 3 Value");
map.add(1, "String 2 Key", "String 2 Value");
map.add(0, "String 1 Key", "String 1 Value");
// The map now contains 3 entries:
// String 1 Key - String 1 Value
// String 2 Key - String 2 Value
// String 3 Key - String 3 Value
```

### Put an entry
Putting an entry into the map will overwrite any existing instances of that key.
If you'd like to add a key/value pair to the map instead of overwriting an 
existing key, check out the `add()` method.
```java
DynamicMap<String, String> map = new DynamicMap<>();

map.put("String 1 Key", "ABC");
map.put("String 2 Key", "XYZ");
map.put("String 1 Key", "XYZ");
// The map now contains the following entries:
// String 1 Key - XYZ
// String 2 Key - XYZ
// Remember, the first value set to String 1 was over-written. 
```

### Remove an entry
Remove an entry from the map, thus deleting the desired key and value. Let's say
we added too many values here - let's remove them, shall we?
```java
DynamicMap<String, String> map = new DynamicMap<>() {
  {
    add("String 1 Key", "String 1 Value");
    add("String 2 Key", "String 2 Value");
    add("String 3 Key", "String 3 Value");
    add("String 4 Key", "String 4 Value");
    add("String 5 Key", "String 5 Value");
  }
};
```

#### Remove by index
```java
map.remove(3);
map.remove(4);
// Remove the 3rd and 4th entries (String 4, String 5) from the map.
```

#### Remove by key 
```java
map.remove("String 4 Key");
map.remove("String 5 Key");
// Remove the entries with the desired keys. The map is now: 
// String 1 Key - String 1 Value
// String 2 Key - String 2 Value
// String 3 Key - String 3 Value
```

#### Remove by value
```java
map.removeByValue("String 4 Value");
map.removeByValue("String 5 Value");
// The map now contains: 
// String 1 Key - String 1 Value
// String 2 Key - String 2 Value
// String 3 Key - String 3 Value
```

#### Remove by key and value
```java
map.remove("String 4 Key", "String 4 Value");
map.remove("String 5 Key", "String 5 Value");
// The map now contains the following values:
// String 1 Key - String 1 Value
// String 2 Key - String 2 Value
// String 3 Key - String 3 Value
```

### Index of
Get the index of a requested key or value.
```java
DynamicMap<String, String> map = new DynamicMap<>() {
  {
    add("String 1 Key", "String 1 Value");
    add("String 2 Key", "String 2 Value");
    add("String 3 Key", "String 3 Value");
    add("String 4 Key", "String 4 Value");
    add("String 5 Key", "String 5 Value");
  }
};
```

#### Index of key 
```java
int index = map.indexOfKey("String 1 Key"); // 0
```

```java
int index = map.indexOfKey("String 4 Key"); // 3
```

#### Index of value 
```java
int index = map.indexOfValue("String 1 Value"); // 0
```

```java
int index = map.indexOfValue("String 4 Value"); // 3
```

### Get
Get a key/value pair or a key (or a value) based on a specified query.
```java
DynamicMap<String, String> map = new DynamicMap<>() {
  {
    add("String 1 Key", "String 1 Value");
    add("String 2 Key", "String 2 Value");
    add("String 3 Key", "String 3 Value");
    add("String 4 Key", "String 4 Value");
    add("String 5 Key", "String 5 Value");
  }
};
```

#### Get value (default)
```java
String value = map.get("String 1 Key");
// This value is now "String 1 Value".
```

#### Get key from value  
```java
String key = map.get("String 1 Value");
// This value is now "String 1 Key".
```

### Get keys and values
```java
DynamicMap<String, String> map = new DynamicMap<>();
DynamicArray<String> keys = map.getKeys();
DynamicArray<String> values = map.getValues();
```

### Contains
```java
DynamicMap<String, String> map = new DynamicMap<>() {
  {
    add("String 1 Key", "String 1 Value");
    add("String 2 Key", "String 2 Value");
    add("String 3 Key", "String 3 Value");
    add("String 4 Key", "String 4 Value");
    add("String 5 Key", "String 5 Value");
  }
};
```

#### Contains key
```java
boolean containsKey = map.containsKey("String 1 Key"); // true
```

#### Contains value 
```java
boolean containsValue = map.containsValue("String 6 Value"); // false
```

### Reset, resize, trim, clear 

#### Reset

#### Trim

#### Clear 

### Size

#### Real Size 

#### Size 

### Map iteration
