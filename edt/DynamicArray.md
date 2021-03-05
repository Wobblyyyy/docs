---
layout: default
title: EDT DynamicArray
parent: edt
nav_order: 1
---


# DynamicArray
Arrays are cool and all, but they're even cooler when they're dynamic.

### Performance
DynamicArray is similiar in function to the ArrayList class provided by java.utils.
The intention of this class is to improve performance on ArrayList elements by increasing
the memory footprint of the internal array and thus decreasing the amount of CPU
cycles dedicated to memory deallocation and reallocation. By utilizing a more aggressive
allocation system, DynamicArray elements spend less time on memory management and more
time on storing items. In addition to providing a performant implementation of the
dynamic array concept commonly seen throughout computer science, DynamicArray contains
an iterator that allows for faster iteration over (a) the entire data set or (b)
a given range of the data set.

## Usage 

### Add
```java
// Create a new dynamic array.
DynamicArray<String> array = new DynamicArray<>();

// Add elements to the array.
array.add("String 1");    // ["String 1"]
array.add("String 2");    // ["String 1", "String 2"]
array.add("String 3");    // ["String 1", "String 2", "String 3"]
array.add(0, "String 0"); // ["String 0", "String 1"...]
// The last of those calls adds at a specific index.
array.add(new String[] {
  "String 4",
  "String 5"
});
// Add an array of string elements to the dynamic array.
```

### Set
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 2");
}};

// Whoops! That's so terrible! We accidentally added "String 2"
// twice. Let's go fix that.
array.set(2, "String 3"); // Set the second "String 2" to "String 3"
``` 

### Remove
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
  add("String 3");
  add("String 3");
}};
// Dammit! We added String 3 too many times. Let's get rid of all 
// the instances of "String 3" in the array.

// Method 1: No parameter remove call.
array.remove();
array.remove();
array.remove();

// Method 2: Remove-by-index call.
int index;
while ((index = array.indexOf("String 3")) >= 0) {
  // Set the index to the index of the next "String 3" in the array.
  // If the index is above -1, meaning the element is contained in the
  // array, remove it from the array.
  array.remove(index);
}

// Method 3: Remove-by-indicies call.
array.remove(new int[] {2, 3, 4});

// Method 4: Remove after call.
array.removeAfter(array.indexOf("String 3"));
``` 

### Index
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

// Get the index of each of the strings.
int index1 = array.indexOf("String 1"); // 0
int index2 = array.indexOf("String 2"); // 1
int index3 = array.indexOf("String 3"); // 2
``` 

### Is empty, contains
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

// Get the index of each of the strings.
boolean empty = array.isEmpty(); // no, it's not empty: false
boolean containsA = array.contains("String 3"); // yes : true
boolean containsB = array.contains("String 4"); // no  : false
``` 

### As Array, ArrayList, List
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

// As an array of objects
Object[] asObjectArray = array.toArray();

// As an array of String elements
String[] strings = new String[array.size()];
strings = array.toArray(strings);

// As an ArrayList of objects
ArrayList<Object> asArrayList = array.toArrayList();

// As an ArrayList of String elements
ArrayList<String> swagList = new ArrayList<>().addAll(array.toArray(new String[array.size()]));
``` 

##### TABLE OF CONTENTS
1. 
{:toc}

## Controlling a Single Motor 

## Using a Pre-Built Drivetrain

## Creating a Drivetrain
