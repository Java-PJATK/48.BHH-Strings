# 48.BHH-Strings
Listing 48 BHH-Strings/Strings.java Page 83

Cont. from [47.ELN-Rec](https://github.com/Java-PJATK/47.ELN-Rec)  

# Section 9. Strings and StringBuilders

## 9.1 Class String

The type String is an object type (not a primitive type). This means that there is no way go give a string a name — we always operate on strings using references to strings
(variables holding, as their values, addresses of objects allocated on the heap).

There are several ways of creating objects of type String (and references to them). As String is so often used, there exist some syntactic simplifications when dealing with objects of this type. Normally, objects are created using new operator, but for Strings we can use:

```java
String s = "Pernambuco";
```

or, if we have an `int` named `a`,

```java
String s = "a = " + a;
```      

Of course, we can also use ‘normal’ form, for example

```java
    String s = new String("Pernambuco");
```

A string can also be created from an array of characters:

```java
    char[] arr = {'A', 'B', 'C'};
    String s = new String(arr); 
```

and in a few other ways (see documentation).

Objects of type `String` are _objects_ (as opposed to variables of primitive types), so we can invoke _methods_ on them. They will never modify an existing string (in particular the one a method is invoked on), but many such methods return the reference to a newly created objects, created on the basis of the original one. Examples — out of many, see documentation — include (we assume that s is the reference to a `String` object):

* `s.length()` — returns the size (number of characters) of s (`"ABC".length()` is 3) — note that this is a _method_, not a field as for arrays;

* `s.equals(anotherstring)` — returns `true` if and only if the string `s` is equal (contains the same characters) as `anotherstring`; this is the correct way to compare strings for equality — note that `s == anotherstring` or `s != anotherstrin`g compares addresses of objects, not their contents;

* `s.equalsIgnoreCase(anotherstring)` — as `equals`, but the case of characters is ignored (’A’ and ’a’ are considered equivalent);

* `s.trim()` — returns the reference to a newly created string which is as s but with all leading and trailing white spaces removed (`"    ABC  " → "ABC"`);

* `s.toLowerCase()`, `s.toUpperCase()` — return the reference to a newly created string which is as s but with all upper- (lower-) case letters replaced by lower-(upper-) case ones — non-letters are not modified (`"aBC".toLowerCase()` → "abc");

* `s.substring(from, to)` — returns the reference to a newly created string which is a substring of s from character with index from (inclusive) to character with index to _exclusive_ (indexing starts with 0), for example `"abcd".substring(1,3)` → "bc";

* `s.substring(from)` — equivalent to `s.substring(from, s.length())`;

* `s.charAt(ind)` — returns (as value of type `char`) the character with index `ind` (indexing starts with 0), for example `"abcd".charAt(2)` → ’c’;

* `s.contains(anotherstring)` — returns true if s contains as its substring the string anotherstring, and false otherwise;

* `s.startsWith(anotherstring)`, s.endsWith(anotherstring) — returns true if s starts (ends) with the substring anotherstring, and false otherwise;

* `s.indexOf(anotherstring)`, `s.indexOf(char)` — returns the first index where the substring `anotherstring` (character `char`) occurs in s, or −1 when such substring (character) doesn’t occur in s (```"abcdcd`".indexOf("cd")``` → 2);

* `s.lastIndexOf(anotherstring)`, `s.lastIndexOf(char)` — returns the last index where the substring anotherstring (character `char`) occurs in s, or −1 when such substring (character) doesn’t occur in s (`"abcdcd".lastIndexOf("cd")` → 4);
  
* `s.indexOf(anotherstring, ind)`, `s.indexOf(char, ind)` — as `s.indexOf(anotherstring)` and `s.indexOf(char)`, but searching starts at index `ind`;

* `s.lastIndexOf(anotherstring, ind)`, `s.lastIndexOf(char, ind)` — as `s.lastIndexOf(anotherstring)` and `s.lastIndexOf(char)` – searching starts at index `ind`;

* `s.toCharArray()` — returns the reference to an array of characters (`char[]`) of length `s.length()` and containing individual characters of the string `s`;

* `s.split(regex)` — returns the reference to an array of strings (`String[]`) containing substrings of `s` where regex is treated as a separator between elements.  

This is a regex (regular expression) which we don’t know about yet: very often you can use a string containing a single character, or "`\\s+`" which means _any nonempty sequence of white characters_. 

For example, if s is the reference to string "`aa:bb:cc`", then `s.split(":")` will give us an array of Strings containing three elements: `"aa"`, `"bb"` and `"cc"`.  

Some of these methods are used in the program below  

## Listing 48 BHH-Strings/Strings.java

which prints

```
a.length() -> 15
b.length() -> 11
         trim(): " Shakespeare   " -> "Shakespeare"
 substring(3,6): "abcdefgh" -> "def"
   substring(3): "abcdefgh" -> "defgh"
  toUpperCase(): "abcdefgh" -> "ABCDEFGH"
one two three
ONE TWO THREE
N e w   Y o r k
kroY weN
```

Next 9.2 Class StringBuilder Listing 49 BHI-StrBuilder 
