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
The symptom can be seen in the following screenshot,
![symptoms](./lab-2-imgs/symptom.png)
The following is the now edited code to avoid the bug,
```
static void reverseInPlace(int[] arr) {
  int[] tempArr = new int[arr.length];
  for(int i = 0; i < arr.length; i++)
    tempArr[i] = arr[i];
  for(int i = 0; i < arr.length; i += 1) 
    arr[i] = tempArr[arr.length - i - 1];
}
```
The original method iterates forward through the array it is passed, replacing the first element with the last, then the second with the second to last, and so on.  This breaks when the loop gets to the second half of the array, since the first half has already been overwritten, so the data copied to the end of the array will be incorrect.  This is not picked up by the second JUnit test, as there is only one element in that array, so when it is replaced by itself there is no effect.  My fixed version works, because it first copies the given array to a second array, caled tempArr.  The original array is then iterated through, and the first element of the original array is set to the last element of the temp array, and then the second to the second to last, and so on.  There will be no overlapping issue, as the array being read from is not being changed.  
