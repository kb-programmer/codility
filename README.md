# codility
My solutions to codility.com problems

Equillibrium index (Got 58%) https://codility.com/demo/results/demoU43H7Y-2Z4/
```java
class Solution {
    
    public int solution(int[] A) {
        
        
        int right = 0;
        int left = 0;
        
        for (int i = 0;i < A.length; i ++) {
            right += A[i];
        }
        for (int i = 0; i < A.length; i ++) {
            
            right -= A[i];
            
            if (i == 0) {
                left += 0;
            } else if (i == A.length -1) {
                
                if (left == 0) {
                    return i;
                }
            } else {
                left += A[i -1];
            }
            
            if (left == right) {
                return i;
            }
        }
        return -1;
    }
}
```
TapeEqullibrium (83%) https://codility.com/demo/results/trainingPNNFJ4-B3Y/
```java
import java.util.*;
class Solution {
    
    public int solution(int[] A) {
        
        int right = 0;
        int left = 0;
        int[] num = new int[A.length];
        
        for (int i = 0; i < A.length; i ++) {
            right += A[i];
        }
        for (int i = 0; i < A.length; i ++) {
            right -= A[i];
            left += A[i];
            num[i] = Math.abs(right - left);
        }
        Arrays.sort(num);
        return num[0];
    }
}
```
MissingInteger

Find the minimal positive integer not occurring in a given sequence.
https://codility.com/demo/results/trainingG9PW7P-MJ7 Passed with 100%

```java
public class Solution {

	public static void main(String[] args) {
		int[] A = new int[]{2,3,1,5};
		System.out.println(solution(A));
	}
	
	public static int solution(int[] A) {
		int[] counters = new int[A.length+2];
		for (int i = 0; i < A.length; i++) {
			counters[A[i]] = 1;
		}
		for (int i = 1; i < counters.length; i++) {
			if (counters[i] == 0)
				return i;
		}
		//no element is missing
		return -1;
	}
}
```
PermCheck


Check whether array A is a permutation (100%). https://codility.com/demo/results/trainingNGSJA5-DCD/

```java
import java.util.*;
class Solution {
    public int solution(int[] A) {
        
        Hashtable<Integer, Boolean> table = new Hashtable<>();
        
        for (int i = 0; i < A.length; i ++) {
           
            if (table.containsKey(A[i]) || A[i] > A.length) {
                return 0; // is not a perm since A[i] exists more than once
            } else {
                table.put(A[i], true);
            }
        }
        return 1;
    }
}
```
MissingInteger (100% score)
Find the minimal positive integer not occurring in a given sequence.
```java
public class Solution {
    public int solution(int[] A) {
        int positiveCount = 0;        
        for(int i=0; i< A.length; i++) {
            positiveCount++;
        }
        
        int[] B = new int[positiveCount];
        
        for(int i=0; i<A.length; i++) {
            if(A[i]<=A.length && A[i]>0) {
                B[A[i]-1]=1;
            }
        }
        
        int min = B.length+1;
        
        for(int i=0; i<B.length; i++) {
            if(B[i]==0) {
                // min = B[i]+1;
                min = i+1;
                break;
            }
        }
        
        return min;
    }
}
```
CountDiv: Compute number of integers divisible by k in range [a..b]. (50% score)
https://codility.com/demo/results/trainingF4QJ7X-DDW/ (Scored 62%)

```java
class Solution {
    public int solution(int A, int B, int K) {
        return (B/K) - ((A - 1)/K);
    }
}
```
PassingCars
Count the number of passing cars on the road.
https://codility.com/demo/results/trainingQBRC5T-UWU/ (70%)

```java
class Solution {
    
    public int solution(int[] A) {
        
        int passing = 0;
        int zerosBefore = 0;
        
        for (int i = 0; i < A.length; i ++) {
            
            if (A[i] == 1) {
                passing += zerosBefore;;
            } else {
                zerosBefore += 1;
            }
        }
        return passing > Integer.MAX_VALUE ? -1 : passing;
    }
}
```
Distinct
Compute number of distinct values in an array. (100% score)
```java
import java.util.*;

class Solution {
    
    public int solution(int[] A) {
        if (A.length == 0) {
            return 0;
        }
        Arrays.sort(A);
        int distinct = 1;
        
        for (int i = 1; i < A.length; i ++) {
            
            if (A[i] != A[i - 1]) {
                distinct ++;
            }
        }
        return distinct;
    }
}

```

MaxProductOfThree
Maximize A[P] * A[Q] * A[R] for any triplet (P, Q, R). (44%)
```java
import java.util.*;

class Solution {
    public int solution(int[] A) {
        Arrays.sort(A);
        int left = A[0] * A[1] * A[2];
        int right = A[A.length - 1] * A[A.length - 2] * A[A.length - 3];
        return left > right? left : right;
    }
}
```
GenomicRangeQuery solution https://codility.com/demo/results/trainingVEBDN7-VCT/ (62% score)
```java
import java.util.*;
class Solution {
    public int[] solution(String S, int[] P, int[] Q) {
        
        Hashtable<String, Integer> factors = new Hashtable<>();
        factors.put("A", 1);
        factors.put("C", 2);
        factors.put("G", 3);
        factors.put("T", 4);
        // int min = 0;
        int[] ans = new int[P.length];
        
        for (int i = 0; i < P.length; i ++) {
            String sub = S.substring(P[i], Q[i] + 1);
            // System.out.println(sub);
            int min = 10;
            
            for (String str : sub.split("")) {
                
                if (factors.get(str) < min) {
                    min = factors.get(str);
                }
            }
            ans[i] = min;
        }
        return ans;
    }
}

```
https://codility.com/demo/results/trainingA8MF5W-7K5/

// you can also use imports, for example:
import java.util.*;

// you can write to stdout for debugging purposes, e.g.
// System.out.println("this is a debug message");

https://codility.com/demo/results/training6XE7HV-TA3/ Passed with 86%
```java
class Solution {
    
    public int solution(String S) {
        
        Stack<String> stack = new Stack<>();
        
        for (String str : S.split("")) {
            
            if (isOpening(str)) {
                stack.add(str);
            } 
            else {
                
                if (stack.isEmpty() || !getOpening(str).equals(stack.peek())) {
                    return 0;
                }
                stack.pop();
            }
        }
        return stack.isEmpty()? 1 : 0;
    }
    
    private boolean isOpening(String s) {
        
         if (s.equals("(") || s.equals("{") || s.equals("[")) {
             return true;
         }
         return false;
    }
    private String getOpening(String s) {
        
        if (s.equals(")")) {
            return "(";
        }
        if (s.equals("}")) {
            return "{";
        }
        if (s.equals("]")) {
            return "[";
        }
        return "";
    }
}
```
