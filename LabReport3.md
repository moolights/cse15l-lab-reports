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
![Image](Test1.png)

### After Fix:
![Image](Test1.png)
