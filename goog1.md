## Properties
*Lorem ipsum...*

## Methods

### `findNeedles(String haystack, String[] needles)`

`findNeedles()` determines the number of times (total count) one or several terms appear in a text.

#### Usage notes
- This method will not run if the search string array `needles[]` contains more than `5` elements.  
- This method returns exact matches (case-sensitive), see the example below for how this affects use.  
- A haystack's needles are only retreivable if the needles and the haystack are in the same base language. For example, searching for `'fuego'` needles (Spanish for *fire*), will not return any instance of semantically identical needles, i.e,. `'fire'` (EN), `'feu'` (FR), or `'火'` (JP). In such cases, desired translations should be added as part of the search string array `needles[]`.

This differs from [`hitTheHay()`](http://www.google.com), which suspends the progression of time in the farm context, and is useful for recharging farmer batteries.

### Syntax
```java
public static void findNeedles(String haystack, String[] needles)
```

The `haystack` string argument is split into an array of substrings based on the following delimiters:
- Space
- Double quote character
- Single quote character
- Tab
- Newline
- Backspace
- Formfeed, and
- Carriage return


### Returns
`findNeedles()` prints to console the count for each word in the search string array (i.e., `needles`)


### Example
The snippet below is from our [*Searching High and Low* Walkthrough](http://www.google.com). 

```java
public static void main(String[] args) {
  String haystack = "Cheese and butter and both dairy products and they are delicious! Cheese is great on sandwiches and butter is 
      a natural match for toast. But eating too much cheese or butter is not good for one's health.";
  String[] needles = {"cheese","butter"};
  findNeedles(haystack, needles);
}
```

This code prints to console:

```
cheese:1
butter:3
```

Even though the words "cheese" and "butter" appear 3 times each in the sample string, "cheese" is capitalized (i.e., "Cheese") in 2 cases, and these do not count towards the total number of instances.

### Specifications
* [Search API](www.google.com)

### See also
[`eyeOfTheNeedle()`](http://www.google.com), [`fineToothComb()`](http://www.google.com)

## Events
*Lorem ipsum...*

---

# Comments to developer

Code:

- Would it be helpful to make it a case-insensitive search?
- Would it be helpful to include an index of where the word was found (I know this goes in a different direction and adds some complexity)
- Is there a performance benefit if all needles were checked at once (e.g., instead of *Is the first word X? Is the second word X? Is the third word X?... Is the first word Y?...*   something like *Is the first word X or Y? Is the second word X or Y? Is the third word...*
- Is there a benefit to a user-defined exception for the array size limit?, e.g.;
  - *This method will throw an exception if the string array argument `needles[]` contains more than `5` elements.*

Style:
- Note block indentation should be 2 spaces (https://google.github.io/styleguide/javaguide.html#s4.2-block-indentation)
- Would renaming the local variables (2 j's) increase legibility?

The code sample below reflects these edits

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
    for (int k = 0; k < needles.length; k++) {
      System.out.println(needles[k] + ':' + countArray[k]);
    }
  }
}
```
