---
layout: default
title: EDT DynamicArray
parent: edt
nav_order: 1
---


# DynamicArray
Arrays are cool and all, but they're even cooler when they're dynamic.

##### TABLE OF CONTENTS
1. 
{:toc}

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
Usage documentation for the DynamicArray class is provided through examples. Anything
not clear from the examples should be explained in the JavaDocs for the class. Anything
not explained there can hopefully be explained via code - hopefully, that is.

### Creating a new DynamicArray
DynamicArray construction can be handled in quite a few different ways.

#### Method 1: With a defined size
```java
// 100 is the minimum size, meaning the array won't have to grow so long
// as it's kept under that size. You should set the minimum size to
// about the maximum amount of elements you'll have in the array. It's
// generally better to over-estimate than to under-estimate. 
DynamicArray<String> array = new DynamicArray<>(100);
```

#### Method 2: Based off another `Arrayable<E>`
```java
StaticArray<String> arrayableItem = new StaticArray<>(3) {{
  set(0, "String 1");
  set(1, "String 2");
  set(2, "String 3");
}};

DynamicArray<String> array = new DynamicArray<>(arrayableItem);
```

#### Method 3: Based off an array
```java
DynamicArray<String> array = new DynamicArray<>(new String[] {
  "String 1",
  "String 2",
  "String 3"
});
```

#### Method 4: Based off an `ArrayList<E>`
```java
ArrayList<String> stringArrayList = new ArrayList<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

DynamicArray<String> array = new DynamicArray<>(
  stringArrayList
);
```

#### Method 5: Based off an array, with a defined size
```java
DynamicArray<String> array = new DynamicArray<>(
  3, // min size
  new String[] {
    "String 1",
    "String 2",
    "String 3"
  }
);
```

#### Method 6: With class initializer
```java
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}}
```


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

### Trim, Clear, Reset, and free up memory
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

// The real size of the array. By default, unless otherwise specified, this
// is 10. This means that the array is technically allocated to 10 in length.
// To you, it looks like the array is only 3 in length. But internally, the
// array is over-allocated to accomodate for future expansion.
int realSize = array.realSize(); // 10
int size = array.size();         // 3

// The trim method!
// This method is useful when arrays reach very large sizes and are taking up
// a ton of memory. Using the trim method will help to free up some of this
// memory. It forces re-allocation, which can be rather expensive.
array.trim(); // Trim the array. Let's take a look at the real size now.
realSize = array.realSize(); // Only 3!
size = array.size();         // 3

// Clear!
// This method will set all of the values in the active portion of the array
// to "null".
array.clear(); // clear the array
String test = array.get(0); // null

// Reset the array!
array.reset(); // reset the entire array to the default size 
String asString = Arrays.toString(array.toArray()); // []
```
### Iteration
```java
// Create a new array and add 3 values.
DynamicArray<String> array = new DynamicArray<>() {{
  add("String 1");
  add("String 2");
  add("String 3");
}};

// Iterate over the entire array, print out each of the values
array.itr().forEach(s -> {
  System.out.println(s);
});
// This call will print the following output to the console:
// >> String 1
// >> String 2
// >> String 3

// Iterate over the array, get previous index, current index, next
// index, previous element, current element, and next element.
array.itr().forEach(() -> {
  // TRY! We'll get exceptions otherwise, as we're requesting an
  // element that's not in the array.
  // First execution has no previous index or element.
  try {
    System.out.println("Previous index: " + array.itr().previousIndex());
    System.out.println("Previous element: " + array.itr().previous());
  } catch (ArrayIndexOutOfBoundsException ignored) {
    
  }

  System.out.println("Index: " + array.itr().index());
  System.out.println("Current element: " + array.itr().element());

  // TRY! We'll get exceptions otherwise, as we're requesting an
  // element that's not in the array.
  // Last execution has no next index or element.
  try {
    System.out.println("Next index: " + array.itr().nextIndex());
    System.out.println("Next element: " + array.itr().nextElement());
  } catch (ArrayIndexOutOfBoundsException ignored) {
    
  }

  System.out.println("");
  System.out.println("");
  System.out.println("");
});
// This call will print the following.
// >> Index: 0
// >> Current element: String 1
// >> Next index: 1
// >> Next element: String 2
// >> 
// >> 
// >> 
// >> Previous index: 0
// >> Previous element: String 1
// >> Index: 1
// >> Current element: String 2
// >> Next index: 2
// >> Next element: String 3
// >> 
// >> 
// >> 
// >> Previous index: 1
// >> Previous element: String 2
// >> Index: 2
// >> Current element: String 3
```

### To static array, from static array 
```java
// Create a dynamic array that will be converted to a static array 
DynamicArray<String> dynamicArray = new DynamicArray<>(
  "String 1",
  "String 2",
  "String 3",
  "String 4",
  "String 5",
);
// Convert it to a static array 
StaticArray<String> staticArray = new StaticArray<>(dynamicArray);

// Convert it back to a dynamic array.
// Add an element, just to flex.
dynamicArray = new DynamicArray<>(staticArray);
dynamicArray.add("String 6");

// Convert it back to a static array.
staticArray = new StaticArray<>(dynamicArray);
// At this point, the static array's contents are:
// ["String 1", "String 2", "String 3", "String 4", "String 5", "String 6"]
```
