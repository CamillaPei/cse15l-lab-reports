note: code was taken from week 7 lab. 
### Part 1 Debugging Scenario
## Original Post from Student:

Title: Help! My Bash script isn't running my Java program correctly.

Post:
Hi everyone,

I'm having trouble with my Bash script that's supposed to compile and run my Java program. 
The script runs without errors, but my Java program doesn't seem to produce the expected output. 
Here is a screenshot of my terminal:

screenshot

I think the issue might be with how the merge function is handling the input lists. 
My Java program merges two sorted lists, but the result seems incorrect. Any ideas on what might be wrong?

Here's the relevant part of my Bash script:

bash
Copy code
#!/bin/bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests

And here's the merge method in my Java program:

java
Copy code
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
        if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
            result.add(list1.get(index1));
            index1 += 1;
        }
        else {
            result.add(list2.get(index2));
            index2 += 1;
        }
    }
    while(index1 < list1.size()) {
        result.add(list1.get(index1));
        index1 += 1;
    }
    while(index2 < list2.size()) {
        result.add(list2.get(index2));
        // change index1 below to index2 to fix test
        index1 += 1;
    }
    return result;
}

Any hints would be appreciate!

Response from TA:

Hi there!

It looks like your script is intended to compile and run JUnit tests for your Java program, but let's focus on the specific method you're having trouble with. 
Can you add a print statement to your merge method to see what the lists look like before and after merging? Also, it seems there's a comment suggesting a possible fix.
Can you try modifying the index1 increment to index2 in the last while loop?

Here's the updated merge method to try:

java
Copy code
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
        if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
            result.add(list1.get(index1));
            index1 += 1;
        }
        else {
            result.add(list2.get(index2));
            index2 += 1;
        }
    }
    while(index1 < list1.size()) {
        result.add(list1.get(index1));
        index1 += 1;
    }
    while(index2 < list2.size()) {
        result.add(list2.get(index2));
        index2 += 1;  // Changed from index1 to index2
    }
    return result;
}
Try running your script again after making this change.

Student's Follow-Up Post:

Title: Update: Tried modifying the merge method

Post:
Hi,

I tried modifying the merge method as you suggested. Here's the screenshot of my terminal after running the script:

screenshot

The lists are now merged correctly:

csharp
Copy code
[a, b, c, d, e, f]
Looks like the issue was indeed with the incorrect index increment in the last while loop. Thanks for the help!

Setup Information:

File & Directory Structure:

lua
Copy code
/project
    |-- ListExamples.java
    |-- ListExamplesTests.java
    |-- run.sh
    |-- lib/
        |-- hamcrest-core-1.3.jar
        |-- junit-4.13.2.jar
Contents of Each File Before Fixing the Bug:

ListExamples.java:

java
Copy code
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }

  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index1 += 1;
    }
    return result;
  }

}
ListExamplesTests.java:

java
Copy code
import static org.junit.Assert.*;
import org.junit.Test;
import java.util.Arrays;
import java.util.List;

public class ListExamplesTests {
  
  @Test
  public void testMerge() {
    List<String> list1 = Arrays.asList("a", "c", "e");
    List<String> list2 = Arrays.asList("b", "d", "f");
    List<String> result = ListExamples.merge(list1, list2);
    assertEquals(Arrays.asList("a", "b", "c", "d", "e", "f"), result);
  }

  @Test
  public void testFilter() {
    List<String> list = Arrays.asList("apple", "banana", "cherry");
    List<String> result = ListExamples.filter(list, s -> s.contains("a"));
    assertEquals(Arrays.asList("banana", "apple"), result);
  }
}
run.sh:

bash
Copy code
#!/bin/bash
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
Full Command Line to Trigger the Bug:

bash
Copy code
bash run.sh
Description of What to Edit to Fix the Bug:

To fix the bug, update the index increment in the last while loop of the merge method from index1 to index2:

Fixed merge method:

java
Copy code
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
        if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
            result.add(list1.get(index1));
            index1 += 1;
        }
        else {
            result.add(list2.get(index2));
            index2 += 1;
        }
    }
    while(index1 < list1.size()) {
        result.add(list1.get(index1));
        index1 += 1;
    }
    while(index2 < list2.size()) {
        result.add(list2.get(index2));
        index2 += 1;  // Changed from index1 to index2
    }
    return result;
}
Part 2 – Reflection

In the second half of this quarter, I learned about the importance of carefully reviewing code logic and how subtle mistakes, like an incorrect index variable, can lead to significant issues. This experience has made me more diligent in debugging and understanding the flow of my programs.






