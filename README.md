# Winsoft-Technology-Tasks

Q1: Merge two arrays by satisfying given constraints
Given two sorted arrays X[] and Y[] of size m and n each where m >= n and X[] has exactly n vacant cells,
 merge elements of Y[] in their correct position in array X[], i.e., merge (X, Y) by keeping the sorted order.

For example,

Input: X[] = { 0, 2, 0, 3, 0, 5, 6, 0, 0 }
Y[] = { 1, 8, 9, 10, 15 } The vacant cells in X[] is represented by 0 
Output: X[] = { 1, 2, 3, 5, 6, 8, 9, 10, 15 }

Answer:- 

    public class MergeArrays {
    public static void merge(int[] X, int[] Y) {
        int m = X.length;
        int n = Y.length;
        
        // Start from the last non-vacant cell in X and end of Y
        int i = m - n - 1;
        int j = n - 1;
        int k = m - 1;
        
        // Merge elements of X and Y in sorted order
        while (i >= 0 && j >= 0) {
            if (X[i] > Y[j]) {
                X[k] = X[i];
                i--;
            } else {
                X[k] = Y[j];
                j--;
            }
            k--;
        }
        while (j >= 0) {
            X[k] = Y[j];
            j--;
            k--;
        }
    }
    
    public static void main(String[] args) {
        int[] X = {0, 2, 0, 3, 0, 5, 6, 0, 0};
        int[] Y = {1, 8, 9, 10, 15};
        
        merge(X, Y);
        
        for (int num : X) {
            System.out.print(num + " ");
        }
    }


Q2:Find maximum sum path involving elements of given arrays
Given two sorted arrays of integers, find a maximum sum path involving elements of both arrays whose sum is maximum. 
We can start from either array, but we can switch between arrays only through its common elements.

For example,

Input: X = { 3, 6, 7, 8, 10, 12, 15, 18, 100 }
Y = { 1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50 }  
The maximum sum path is: 1 —> 2 —> 3 —> 6 —> 7 —> 9 —> 10 —> 12 —> 15 —> 16 —> 18 —> 100 
The maximum sum is 199

Answer:- 

    public class MaximumSumPath {
    public static int findMaxSumPath(int[] X, int[] Y) {
        int sumX = 0, sumY = 0, result = 0;
        int i = 0, j = 0;
        int m = X.length, n = Y.length;
        
        // Traverse both arrays
        while (i < m && j < n) {
            // If current element in X is smaller, add it to sumX
            if (X[i] < Y[j]) {
                sumX += X[i++];
            }
            // If current element in Y is smaller, add it to sumY
            else if (X[i] > Y[j]) {
                sumY += Y[j++];
            }
            // If current elements are equal (common element found), 
            // take the maximum sum and reset sumX and sumY
            else {
                result += Math.max(sumX, sumY) + X[i];
                sumX = 0;
                sumY = 0;
                i++;
                j++;
            }
        }
        
        // Add remaining elements of X, if any
        while (i < m) {
            sumX += X[i++];
        }
        
        // Add remaining elements of Y, if any
        while (j < n) {
            sumY += Y[j++];
        }
        
        // Add the maximum of sumX and sumY to the result
        result += Math.max(sumX, sumY);
        
        return result;
    }
    
    public static void main(String[] args) {
        int[] X = {3, 6, 7, 8, 10, 12, 15, 18, 100};
        int[] Y = {1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50};
        
        int maxSum = findMaxSumPath(X, Y);
        
        // Output the maximum sum
        System.out.println("Maximum sum path: " + maxSum);
    }
    }

Q3:Write a Java Program to count the number of words in a string using HashMap.

Answer:- 

    import java.util.HashMap;

    public class WordCounter {
      public static void main(String[] args) {
          String inputString = "This is a sample string with words, sample words.";
          
          // Remove punctuation and convert to lowercase
          inputString = inputString.replaceAll("[^a-zA-Z ]", "").toLowerCase();
          
          // Split the string into words
          String[] words = inputString.split("\\s+");
          
          // Create a HashMap to store word counts
          HashMap<String, Integer> wordCounts = new HashMap<>();
          
          // Count the occurrences of each word
          for (String word : words) {
              wordCounts.put(word, wordCounts.getOrDefault(word, 0) + 1);
          }
          
          // Output the word counts
          System.out.println("Word Counts:");
          for (String word : wordCounts.keySet()) {
              System.out.println(word + ": " + wordCounts.get(word));
          }
          
          // Total number of words
          int totalWords = words.length;
          System.out.println("Total Number of Words: " + totalWords);
      }
    }

Q4:Write a Java Program to find the duplicate characters in a string.

Answer:- 

    import java.util.HashMap;

    public class DuplicateCharacters {
      public static void main(String[] args) {
          String inputString = "Hello World";
          
          // Convert the string to lowercase to consider case-insensitive duplicates
          inputString = inputString.toLowerCase();
          
          // Create a HashMap to store character counts
          HashMap<Character, Integer> charCounts = new HashMap<>();
          
          // Count the occurrences of each character
          for (char ch : inputString.toCharArray()) {
              if (Character.isLetter(ch)) {
                  charCounts.put(ch, charCounts.getOrDefault(ch, 0) + 1);
              }
          }
          
          // Output the duplicate characters
          System.out.println("Duplicate Characters:");
          for (char ch : charCounts.keySet()) {
              if (charCounts.get(ch) > 1) {
                  System.out.println(ch);
              }
          }
      }
    }
