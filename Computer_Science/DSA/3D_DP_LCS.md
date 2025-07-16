```java
// A memoize recursive implementation of LCS problem
import java.io.*;
class GFG
{
  
  public static int[][][] arr = new int[100][100][100];

  // Returns length of LCS for X[0..m-1], Y[0..n-1] */
  // memoization applied in recursive solution
  static int lcs(String X, String Y, String Z,
                 int m, int n, int o)
  {
    
      // base case
      if (m == 0 || n == 0 || o == 0)
          return 0;

      // if the same state has already been
      // computed
      if (arr[m - 1][n - 1][o - 1] != -1)
          return arr[m - 1][n - 1][o - 1];

      // if equal, then we store the value of the
      // function call
      if (X.charAt(m - 1) == Y.charAt(n - 1) && 
          Y.charAt(n - 1) == Z.charAt(o - 1)) {

          // store it in arr to avoid further repetitive work
          // in future function calls
          arr[m - 1][n - 1][o - 1] = 1 + lcs(X, Y, Z, m - 1,
                                              n - 1, o - 1);
          return arr[m - 1][n - 1][o - 1];
      }
      else
      {

          // store it in arr to avoid further repetitive work
          // in future function calls
          arr[m - 1][n - 1][o - 1] =
                                 max(lcs(X, Y, Z, m, n - 1, o),
                                   max(lcs(X, Y, Z, m - 1, n, o),
                                      lcs(X, Y, Z, m, n, o - 1)));
          return arr[m - 1][n - 1][o - 1];
      }
  }

  // Utility function to get max of 2 integers
  static int max(int a, int b)
  {
      return (a > b) ? a : b;
  }

  // Driver Code
  public static void main (String[] args)
  {  
    for(int i = 0; i < 100; i++) 
    {
      for(int j = 0; j < 100; j++) 
      {
        for(int k = 0; k < 100; k++)
        {
          arr[i][j][k] = -1;
        }
      }
    }
    
    String X = "geeks";
    String Y = "geeksfor";
    String Z = "geeksforgeeks";
    int m = X.length();
    int n = Y.length();
    int o = Z.length();
    System.out.print("Length of LCS is " + lcs(X, Y, Z, m, n, o));
  }
}
```