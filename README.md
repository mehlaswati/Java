# Java
import java.util.ArrayList;
import java.util.List;

public class IntuitSonali {



        /* function to find and print the longest common
           substring of X[0..m-1] and Y[0..n-1] */
        static void printLCSubStr(List<String> X, List<String> Y, int m, int n)
        {
            // Create a table to store lengths of longest common
            // suffixes of substrings.   Note that LCSuff[i][j]
            // contains length of longest common suffix of X[0..i-1]
            // and Y[0..j-1]. The first row and first column entries
            // have no logical meaning, they are used only for
            // simplicity of program
            int[][] LCSuff = new int[m + 1][n + 1];

            // To store length of the longest common substring
            int len = 0;

            // To store the index of the cell which contains the
            // maximum value. This cell's index helps in building
            // up the longest common substring from right to left.
            int row = 0, col = 0;

        /* Following steps build LCSuff[m+1][n+1] in bottom
           up fashion. */
            for (int i = 0; i <= m; i++) {
                for (int j = 0; j <= n; j++) {
                    if (i == 0 || j == 0)
                        LCSuff[i][j] = 0;

                    else if (X.get(i - 1) == Y.get(j - 1)) {
                        LCSuff[i][j] = LCSuff[i - 1][j - 1] + 1;
                        if (len < LCSuff[i][j]) {
                            len = LCSuff[i][j];
                            row = i;
                            col = j;
                        }
                    } else
                        LCSuff[i][j] = 0;
                }
            }

            // if true, then no common substring exists
            if (len == 0) {
                System.out.println("No Common Substring");
                return;
            }

            // allocate space for the longest common substring
            List<String> resultStr = new ArrayList<>();

            // traverse up diagonally form the (row, col) cell
            // until LCSuff[row][col] != 0
            while (LCSuff[row][col] != 0) {
                resultStr.add(0,X.get(row - 1));
//                = X.get(row - 1) + resultStr; // or Y[col-1]
                --len;

                // move diagonally up to previous cell

            }

            // required longest common substring
            System.out.println(resultStr);
        }

        /* Driver program to test above function */
        public static void main(String args[])
        {
            List<String> l1 = new ArrayList<>();

            l1.add("/nine.html");
            l1.add("/four.html");
            l1.add("/six.html");
            l1.add("/seven.html");
            l1.add("/one.html");
            System.out.println(l1);

            List<String> l2 = new ArrayList<>();

            l2.add("/nine.html");
            l2.add("/two.html");
            l2.add("/three.html");
            l2.add("/four.html");
            l2.add("/six.html");
            l2.add("/seven.html");



            int m = l1.size();
            int n = l2.size();

            printLCSubStr(l1, l2, m, n);
        }
    }



