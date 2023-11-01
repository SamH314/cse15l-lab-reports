# Part 1 - Bugs

* A failure-inducing input for the buggy program, as a JUnit test and any associated code:

```
public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = {1,2,3,4};
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
}
```

* An input that doesn’t induce a failure, as a JUnit test and any associated code:

```
public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```

* The symptom, as the output of running the tests:

<img width="958" alt="Screenshot 2023-11-01 at 12 34 54 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/b83d4bdd-a308-4edf-97ab-0e52a82686ba">


<img width="321" alt="Screenshot 2023-11-01 at 12 33 08 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/29c5cd38-3a11-47b9-aa41-32c5d485d6f2">


* The bug, as the before-and-after code change required to fix it:

```
//before:
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
}
```
```
//after:
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
}
```
