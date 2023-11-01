# Lab Report 3
---
## Part 1:
The buggy code I have chosen is the following,
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
The failure inducing input is demonstrated by the following JUnit test,
```
@Test 
public void testReverseInPlace() {
  int[] input1 = {1, 2, 3};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{3, 2, 1}, input1);
}
```
There is no failure for the following, very similar JUnit test,
```
@Test 
public void testReverseInPlace() {
  int[] input1 = {3};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{3}, input1);
}
```
The symptom can be seen in the following screenshot:
![symptoms](./lab-2-imgs/first-string.png)
