# findNeedles() API Documentation

## Overview

findNeedles() API method searches up to five words in an input argument string, count and log the number of occurrence(s) for each word. The method uses split function to split the given input argument string using following literals: ```\"\'\t\n\b\f\r ```

```\"``` double quotes character  
```\'``` single quote character  
```\t``` tab space character  
```\n``` new line character  
```\b``` back space character  
```\f``` form feed character  
```\r``` carriage return character    
### findNeedles()
 ```
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
            for (int j = 0; j < needles.length; j++) {
                System.out.println(needles[j] + ": " + countArray[j]);
            }
        }
    }
 
 ```  
**Inputs:**  
 This method uses following input parameters:  
* 	```haystack```a string of any length  
* 	```needles``` an array of words used to search against the text in haystack

**Console Outputs:**  
* If ```needles``` (words) length is less than or equal to five, the method returns a list of words along with the number of occurrences of each word from ```haystack``` (sentence) as shown below:  
    * needles[0]: number of occurrences in haystack  
    * needles[1]: number of occurrences in haystack  
    * needles[2]: number of occurrences in haystack  
    * needles[3]: number of occurrences in haystack  
    * needles[4]: number of occurrences in haystack  
 * If ```needles``` (words) length is greater five, method returns following error message:  
    “Too many words!”  

 
 ## Calling the Method  
 
  This method requires an input string: ```haystack``` and an array of search words: ```needles```  
  
  ```
  String[] needles = {"hello", "there", "mac", "one", "123"};
  String haystack = "hello there hello! There is an apple macbook";
  findNeedles(haystack, needles);
```  
## Limitations
  
* This method can only accept five or less search arguments (words). If else, an error message will be logged in the console.  
* Input arguments with punctuation are recognized as different words. Example, “Hello” and “Hello!” considered as two different words.  
* Input arguments are case sensitive. Example, “There” and “there” considered as two different words.  
 
## Test Cases  

  ### Test Case 1:
  ```findNeedles("hello there hello! There is an apple macbook", {"hello", "there", "mac", "one", "123"});```  

  **Console Output:**  
 ![Test case 1 output](https://github.com/hemsmalli5/Writing-Sample-findNeedle-/blob/main/testCase1_Output.png)  

  ### Test Case 2:
  ```findNeedles("hello'there hello! There is an apple macbook", {"hello", "there", "There"});```  

  **Console Output:**  
  ![Test case 2 output](https://github.com/hemsmalli5/Writing-Sample-findNeedle-/blob/main/testCase2_Output.png)    

  ### Test Case 3:
  ```findNeedles("hello'there hello! There is an apple macbook", {"hello", "there", "time", "apple", "test", "orange"});```  

  **Console Output:**  
  ![Test case 3 output](https://github.com/hemsmalli5/Writing-Sample-findNeedle-/blob/main/testCase3_Output.png)    

## Suggested Future Improvements
  ### Performance:

   * **Split function can be called before the ```For Loop```**  
     * This reduces CPU and memory usage since current code regex computation and split call happens for each iteration.  

  ```
  else {
            int[] countArray = new int[needles.length];
            String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
            for (int i = 0; i < needles.length; i++) {
                for (int j = 0; j < words.length; j++) {
                    if (words[j].compareTo(needles[i]) == 0) {
                        countArray[i]++;
                    }
                }
            }
  ```  
  ### Accessibility:
   * **Method can return an output**  
      * Current code logs outputs in the console, instead an array containing the list of outputs can be returned.   
   * **Too many arguments can return error**
     * Instead of logging error in the console, send an error message back to the calling routine.

