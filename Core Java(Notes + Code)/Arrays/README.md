## Java Arrays

**Arrays** in Java is a collection of similar data type values.

**Syntax of Arrays**

```
datatype []variable_name;
variable_name = new datatype[size];
```

```
datatype []variable_name = {value1,value2,....,valueN};
```


**Declare an Array**

```
String[] aArray = new String[5];
String[] bArray = {"a","b","c", "d", "e"};
String[] cArray = new String[]{"a","b","c","d","e"};
```

<!-- <hr> -->

### Arrays.toString(array_name)

Print an array with(array_name)

```
import java.util.Arrays;

int[] array = { 1, 2, 3, 4, 5 };
System.out.println(Arrays.toString(array));
// [1, 2, 3, 4, 5]

int[] array = { 1, 2, 3, 4, 5 };
System.out.println(array);
// [I@7150bd4d

int[] array = { 1, 2, 3, 4, 5 };
String intArrayString = Arrays.toString(array);
System.out.println(intArrayString);
// [1, 2, 3, 4, 5]
```

### array_name.length

Returns the length of a Arrays

```
int[] arr = { 1, 2, 3, 4, 5 };
System.out.println(arr.length);
```

### Arrays.asList(array_name)

Create an ArrayList from an array

```
String[] array_name = { "a", "b", "c", "d", "e" };
ArrayList<String> arrayList = new ArrayList<String>(Arrays.asList(array_name));
System.out.println(arrayList);
// [a, b, c, d, e]
```

### Arrays.asList(array_name).contains("a")

Check if an array contains a certain value

```
String[] array_name = { "a", "b", "c", "d", "e" };
boolean b = Arrays.asList(array_name).contains("a");
System.out.println(b);
// true
```

### Arrays.sort(array_name)

Sort an arrays in accending order.

```
String[] array_name = { "a", "b", "c", "d", "e" };
Arrays.sort(array_name);
```

### Arrays.binarySearch(array_name, byteKey)

Searches for the specified element in the array with the help of the Binary Search Algorithm

```
byte byteArr[] = { 10, 20, 15, 22, 35 };
Arrays.sort(byteArr);
byte byteKey = 35;
System.out.println(byteKey + " found at index = " + Arrays.binarySearch(byteArr, byteKey));
```

### binarySearch(array, fromIndex, toIndex, key, Comparator)

Searches a range of the specified array for the specified object using the Binary Search Algorithm

```
int intArr[] = { 1, 2, 3, 4, 5, 6 };
Arrays.sort(intArr);
int intKey = 3;
System.out.println(intKey + " found at index = "+ Arrays.binarySearch(intArr, 1, 4, intKey));
```

### Arrays.equals(arr1, arr2)

Compares two arrays Content.

```
int arr1[] = {1, 2, 3};
int arr2[] = {1, 2, 3};
if (Arrays.equals(arr1, arr2))
    System.out.println("Same");
else
    System.out.println("Not same");

// Same
```

### deepEquals(Object[] a1, Object[] a2)

Returns true if the two specified arrays are deeply equal to one another.

```
// inarr1 and inarr2 have same values
    int inarr1[] = {1, 2, 3};
    int inarr2[] = {1, 2, 3};   
    Object[] arr1 = {inarr1};  // arr1 contains only one element
    Object[] arr2 = {inarr2};  // arr2 also contains only one element
    if (Arrays.equals(arr1, arr2))
        System.out.println("Same");
    else
        System.out.println("Not same");

// Not Same
```

### copyOf(originalArray, newLength)

Copies the specified array, truncating or padding with the default value (if necessary) so the copy has the specified length.

```
int[] org = new int[] {1, 2 ,3};
int[] copy = Arrays.copyOf(org, 5);
```

### copyOfRange(originalArray, fromIndex, endIndex)

Copies the specified range of the specified array into a new Arrays.

```
int arr[] = { 12, 13, 14, 15, 16, 17, 18 };
int[] copy = Arrays.copyOfRange(arr, 2, 6);
//14  15  16  17  
```

### deepHashCode(Object[] a) 

The java.util.Arrays.deepHashCode(Object[]) method returns a hash code based on the "deep contents" of the specified array.For any two arrays a and b such that Arrays.deepEquals(a, b), it is also the case that Arrays.deepHashCode(a) == Arrays.deepHashCode(b).

```
Object[] ob = { "tuts","point" };
// deephashcode for object ob
int retval = Arrays.deepHashCode(ob);
// printing value
System.out.println("The Hash Code of ob is:" + retval);

//The Hash Code of ob is:217575569
```

### deepToString(Object[] a)

Returns a string representation of the “deep contents” of the specified Arrays.

```
// initializing an object array
Object[] ob={"tuts","point"};
// let us print all the values available in list
System.out.println("The array is:");
for (Object value : ob) {
    System.out.println("Value = " + value);
}
System.out.println("The string representation of array is:");
System.out.println(Arrays.deepToString(ob)); 

//The array is:
//Value = tuts
//Value = point
//The string representation of array is:
//[tuts, point]

```

### fill(originalArray, fillValue)

Assigns this fill value to each index of this arrays.

```
int array[] = new int[10];
// Filling the data
Arrays.fill(array, 10);
```

### hashCode(originalArray) 

Returns an integer hashCode of this array instance.

```
// initializing Object array
Object[] ob = new Object[] { 22, 7 };
// hashcode for value1
int retval = ob.hashCode();
// printing hash code value
System.out.println("The hash code of value1 is: " + retval);
// value2 for Object array
ob = new Object[] { 3.5, 8.5 };
// hashcode for value2
retval = ob.hashCode();
// printing hash code value
System.out.println("The hash code of value2 is: " + retval);

//The hash code of value1 is: 4072869
//The hash code of value2 is: 1671711

```

### mismatch(array1, array2) 

Finds and returns the index of the first unmatched element between the two specified arrays.

```
double array1[] = { 11.21, 22.31, 33.15, 44.18, 55.19, 66.666 };
double array2[] = { 11.21, 22.31, 33.15, 44.18, 55.19, 66.666 };
int index1 = Arrays.mismatch(array1, array2);
System.out.println("The index at which array1 and array2 have first unequal element: " + index1);

//The index at which array1 and array2 have first unequal element: -1
```

### parallelSort(originalArray)

Sorts the specified array using parallel sort.

```
int numbers[] = { 9, 8, 7, 6, 3, 1 };
System.out.print("Unsorted Array: ");
Arrays.stream(numbers).forEach(n -> System.out.print(n + " "));
System.out.println();
// Using Arrays.parallelSort()
Arrays.parallelSort(numbers);
// Printing sorted Array
System.out.print("Sorted Array: ");
// Iterating the Elements using stream
Arrays.stream(numbers).forEach(n -> System.out.print(n + " "));

//Unsorted Array: 9 8 7 6 3 1 
//Sorted Array: 1 3 6 7 8 9

```

### sort(originalArray, fromIndex, endIndex)

Sorts the specified range of array in ascending order.

```
int[] arr = { 7, 8, 4, 5, 2 };
Arrays.sort(arr, 1, 4);
```

### sort(T[] a, int fromIndex, int toIndex, Comparator< super T> c)

Sorts the specified range of the specified array of objects according to the order induced by the specified comparator.

```
// initializing unsorted short array
Short sArr[] = new Short[]{3, 13, 1, 9, 21};
// let us print all the elements available in list
for (short number : sArr) {
    System.out.println("Number = " + number);
}
// create a comparator
Comparator<Short> comp = Collections.reverseOrder();
// sorting array with reverse order using comparator from 0 to 2
Arrays.sort(sArr, 0, 2, comp);
// let us print all the elements available in list
System.out.println("short array with some sorted values(1 to 4) is:");
for (short number : sArr) {
    System.out.println("Number = " + number);
}

// Number = 3
// Number = 13
// Number = 1
// Number = 9
// Number = 21
// short array with some sorted values(1 to 4) is:
// Number = 13
// Number = 3
// Number = 1
// Number = 9
// Number = 21
```


### ArrayUtils.addAll(array_name_1, array_name_2)

Concatenate two arrays

```
int[] array_name_1 = { 1, 2, 3, 4, 5 };
int[] array_name_2 = { 6, 7, 8, 9, 10 };
int[] combined_array_name = ArrayUtils.addAll(array_name_1, array_name_2);
```

### method_name(new variable_name[]{pass_the_value})

Declare an array inline

```
method(new String[]{"a", "b", "c", "d", "e"});
```

### StringUtils.join(new String[] { "a", "b", "c" }, ", ");

Joins the elements of the provided array into a single String

```
String j = StringUtils.join(new String[] { "a", "b", "c" }, ", ");
System.out.println(j);
// a, b, c
```

### arrayList.toArray(array_name);

Covnert an ArrayList to an array

```
String[] stringArray = { "a", "b", "c", "d", "e" };
ArrayList<String> arrayList = new ArrayList<String>(Arrays.asList(stringArray));
String[] stringArr = new String[arrayList.size()];
arrayList.toArray(stringArr);
for (String s : stringArr)
	System.out.println(s);
```

### Set<String> set = new HashSet<String>(Arrays.asList(array_name));

Convert an array to a set

```
Set<String> set = new HashSet<String>(Arrays.asList(stringArray));
System.out.println(set);
//[d, e, b, c, a]
```

### ArrayUtils.reverse(array_name);

Reverse an array

```
int[] intArray = { 1, 2, 3, 4, 5 };
ArrayUtils.reverse(intArray);
System.out.println(Arrays.toString(intArray));
//[5, 4, 3, 2, 1]
```

### ArrayUtils.removeElement(array_name, 3)

Remove element of an array

```
int[] intArray = { 1, 2, 3, 4, 5 };
int[] removed = ArrayUtils.removeElement(intArray, 3);//create a new array
System.out.println(Arrays.toString(removed));
```

### byte[] bytes = ByteBuffer.allocate(4).putInt(8).array();

convert int to byte array

```
byte[] bytes = ByteBuffer.allocate(4).putInt(8).array();

for (byte t : bytes) {
   System.out.format("0x%x ", t);
}
```
## Screenshots

### Arrays 1D

![App Screenshot](https://raw.githubusercontent.com/ayeujjawalsingh/DSA-Notes/master/Images/1D_arrays.png)
-

### Arrays 2D

![App Screenshot](https://raw.githubusercontent.com/ayeujjawalsingh/DSA-Notes/master/Images/2D_arrays.png)
-