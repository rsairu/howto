## Properties
*Lorem ipsum...*

## Methods

*Also inherits properties from its parent interface,* [e](google.com).

### `findNeedles(String haystack, String[] needles)`

The `haystack` string argument is split into an array of substrings based on the following delimiters:
- Space
- Double quote character
- Single quote character
- Tab
- Newline
- Backspace
- Formfeed, and
- Carriage return

Note that a haystack's needles are only retreivable if the needles and the haystack are in the same base language. For example, searching for `'fuego'` needles (Spanish for *fire*), will not return any instance of semantically identical needles, i.e,. `'fire'` (EN), `'feu'` (FR), or `'火'` (JP). In such cases, desired translations should be added as part of the search string array `needles[]`.

**Note**, however, that this method will not run if the search string array `needles[]` contains more than `5` elements.*

This differs from [`hitTheHay()`](google.com), which suspends the progression of time in the farm context, and is useful for recharging farmer batteries.



### Syntax
```java

```

### Returns



### Example
The snippet below is from our [*Searching High and Low* Walkthrough](google.com). 


### Specifications
* [Search API](google.com)

### See also
* [`dontHoldYourBeath()`](google.com)
* [`fineToothComb()`](google.com)

## Events
*Lorem ipsum...*

---

# Comments to developer

- Is there a benefit to a user-defined exception for the array size limit?, e.g.;
  - *This method will throw an exception if the string array argument `needles[]` contains more than `5` elements.*
- 

```java
public static void findNeedles(String haystack, String[] needles) {
if (needles.length > 5) {
  System.err.println("Too many words!");
} else {
  int[] countArray = new int[needles.length];
  for (int i = 0; i < needles.length; i++) {
   String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
   for (int j = 0; j < words.length; j++) {
    if (words[j].compareTo(needles[i]) == 0) {
     countArray[i]++;
    }
   }
  }
  for int j = 0; j < needles.length; j++) {
   System.out.println(needles[j] + ':' + countArray[j]);
  }
}
}
```
