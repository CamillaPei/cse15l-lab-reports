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
   
# Part 2 Researching Command 
`grep` 

I goggled "grep command line options", and found a website with a list of `grep` command. [source link](https://www.geeksforgeeks.org/grep-command-in-unixlinux/) 
1. `grep -i ` Ignores, case for mathing.

Example 1:
```
(base) CamillasMacbook:docsearch CosmoNil$ grep -i "cardiovascular" technical/biomed/1468-6708-3-1.txt
        trials to detect survival differences or cardiovascular
          Study design: The Cardiovascular Health
          The Cardiovascular Health Study (CHS) is a
          cardiovascular disease (prevalent heart disease,
        CHS Cardiovascular Health Study
```
In this example, `grep -i ` searches for the word "cardiovascular" in the given file while ignoring the case of the letters. This command is useful for finding occurances of a specific word in a file without concerns about the case of the letter. 

Example 2:
```
CamillasMacbook:docsearch CosmoNil$ grep -i "complex" technical/plos/journal.pbio.0030076.txt
        preinitiation complex (PIC), promoter clearance, pausing, and arrest, and ended with
        (reviewed in [2]). This phosphorylation is critical for the recruitment of complexes that
        complex clears the promoter, the negative transcription elongation factor (N-TEF) is
        the promoter cooperatively. Such arrested transcription complexes have now been found on
        and one of four possible C-type cyclins. When recruited to stalled transcription complexes,
        TAF-independent transcription complexes to the HIV LTR [14] (Figure 1). Possibly, this
        The assembly and disassembly of the complex between PTEFb, Tat, and TAR is a regulated
        process in vivo. Whereas the phosphorylation of CDK9 strengthens this complex [16], the
        Of interest, P-TEFb exists in two complexes in cells [22,23]. The larger measures
        complex, Cdk9 is enzymatically inactive. HEXIM1 was identified as the inducible gene
        growth signals liberate P-TEFb from the large complex in the course of cardiac hypertrophy
        actinomycin D and DRB to cells, the large complex is converted to the small complex to
        complexes play in the transcription of specific genes? How central will the regulation of
```
In this example, `grep -i ` searches for lines that includes "complex" in the given file while ignoring the case of letters, and I noticed that the plural form of "complex" is also included in the result. This flexibility accommodates variations in case and pluralization, making the search more inclusive. 

2. `grep -l ` Displays list of filenames only.
Example:
```

```

```

```
3. `grep -i ` Ignores, case for matching.
  Example:
```

```

```

```
4. `grep -l ` Display list of filenames only.
Example:
```

```

```

```

