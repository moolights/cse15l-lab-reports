# Part 1
## Failure-Inducing Input
```ruby
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3, 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 3 }, input1);
}
```

## Non-Failure Inducing Input
```ruby
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

## The Symptom
![Image](Symptom.png)

## The Bug
### Before Fix:
```ruby
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
### After Fix:
```ruby
static void reverseInPlace(int[] arr) {
    int temp = 0;
    for(int i = 0; i < arr.length / 2; i += 1) {
        temp = arr[i];
        arr[i] = arr[arr.length - 1 - i];
        arr[arr.length - 1 - i] = temp;
    }
}
```
### Why this fix works
This fix to the code works because, initially, the code would loop through the array and swap places but once reaching halfway
through the array it would flip the places again. This just created the same array as we started with. The fix cuts the array
in half and only loops through ``array.length / 2``. Then, because this a pass by value, I had to create a new ``temp`` variable 
to store the current value then swap it with ``arr[arr.length - 1 - i]``

# Part 2 (Using ``find``)

## ``find -name``:
### Example 1
This command finds all the ``.txt`` files in ``\technical`` that start with "chapter" then
prints it to the terminal. These can be files in any directory nested under ``\technical``.

Input:
```ruby
find technical -name "chapter*.txt"
```
Output:
```
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```
### Example 2
This command finds all the ``.txt`` files in ``\technical`` that start with "cc" then
prints it to the terminal. These can be files in any directory nested under ``\technical``.

Input:
```ruby
find technical -name "cc*.txt"
```
Output:
```
technical/biomed/cc991.txt
technical/biomed/cc4.txt
technical/biomed/cc367.txt
technical/biomed/cc3.txt
technical/biomed/cc2190.txt
technical/biomed/cc1843.txt
technical/biomed/cc1856.txt
technical/biomed/cc105.txt
technical/biomed/cc1498.txt
technical/biomed/cc1538.txt
technical/biomed/cc1882.txt
technical/biomed/cc300.txt
technical/biomed/cc1529.txt
technical/biomed/cc103.txt
technical/biomed/cc303.txt
technical/biomed/cc1477.txt
technical/biomed/cc1852.txt
technical/biomed/cc713.txt
technical/biomed/cc1476.txt
technical/biomed/cc2172.txt
technical/biomed/cc2358.txt
technical/biomed/cc2167.txt
technical/biomed/cc2171.txt
technical/biomed/cc2160.txt
technical/biomed/cc1044.txt
technical/biomed/cc1497.txt
technical/biomed/cc1495.txt
technical/biomed/cc350.txt
technical/biomed/cc973.txt
technical/biomed/cc1547.txt
technical/biomed/cc343.txt
```

## ``find -type d``:
### Example 1

### Example 2

## ``find size``:
### Example 1

### Example 2

## ``find empty``:
### Example 1

### Example 2
