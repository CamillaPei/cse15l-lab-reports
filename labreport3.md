# Part 1 Bugs 
1. Failure-incuding input: 
```
@Test
  public void testReversedwError() {
    int[] input1 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
  }
```
2. Input that doesn't induce a failure:
```
@Test
  public void testReversedNoError(){
    int [] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
3. Symptom: 
![SYMPTOM](labreport3symptom.jpg) 
4. Bug:

Before: 
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

After: 
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
5. Explanation
   
By changing `arr[i] = newArray[arr.length - i - 1]` to `newArray[i] = arr[arr.length - i - 1]` and changing `return arr` to `return newArray`,
the error is fixed by irritating through `arr` and putting elements into `newArray` in reversed order, then return `newArray`.
Previously, the code was irritating through `newArray` (whihc is empty) and putting elements into `arr`, and returning `arr` at the end, which is logically incorrect.
This error also explains why the code doesn't produce any error when `arr` is empty.     
   
