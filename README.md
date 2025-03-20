# JP_Morgan
### Copycat

Ashish was copying from Rahit in the exam. So, Rahit told him to change the answers a little bit so that the examiner cannot find the fraud. But silly Ashish in the way started to change all the answers that were needed. He shuffled the letters in each word in a way where the maximum number of letters were misplaced. For a given word, find the maximum difference that Ashish can generate between his answer and Rahit’s answer. Suppose Rahit wrote “car” for an answer, Ashish can write “acr” with difference 2, or “arc” with differnece 3. Note That: The letters are all in lowercase.

Input Format:
First line containing an integer n, number of words.
Then, n numbers of lines as the query words.

Output:
N number of lines with an integer each denoting possible maximum difference.

Sample Input:
4
abababa
bbj
kj
kk

Sample Output:
6
2
2
0

```java
import java.util.*;
class Main {
    public static void find(String s,int[] arr1,List<String> ans,List<Character> arr)
    {
        if(arr.size()>=s.length())
        {
            StringBuilder str = new StringBuilder();
            for(char x:arr) str.append(x);
            ans.add(str.toString());
            return;
        }
        for(int i=0;i<s.length();i++)
        {
            if(arr1[i]!=-1)
            {
                arr1[i]=-1;
                arr.add(s.charAt(i));
                find(s,arr1,ans,arr);
                arr.remove(arr.size()-1);
                arr1[i]=0;
            }
        }
    }
    public static int get(String s)
    {
        List<Character> arr = new ArrayList<>();
        List<String> ans = new ArrayList<>();
        int[] arr1 = new int[s.length()];
        find(s,arr1,ans,arr);
        int max = 0;
        for(String x:ans)
        {
            int c = 0;
            for(int i=0;i<x.length();i++)
            {
                if(x.charAt(i)!=s.charAt(i)) c++;
            }
            max = Math.max(max,c);
        }
        return max;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();
        sc.nextLine();
        String[] str = new String[n];
        for(int i=0;i<n;i++) str[i] = sc.nextLine();
        int[] res= new int[n];

        for(int i=0;i<n;i++)
        {
            res[i] = get(str[i]);
        }
        System.out.println("Answer");
        for(int i=0;i<n;i++) System.out.println(res[i]);
    }
}
```

### New Number System
Here is about to introduce a new kind of number system. Where instead of 10 digits there is 20, from a to t, all in small. Now a means 1, b means 2 and t means 20, thenn aa means 21. Now for  a new number you have to print the decimal form it. Note that the letters in the input string will be lower case and from a to t. 

Input Format:
Single line containing the string of new number system’s number

Output Format:
Single line denoting the integer with the same decimal value as the input string

Sample input 1: e
Sample Output: 5

Sample  Input 2: ac
Sample Output: 23

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int ans = 0;
        
        String str = sc.nextLine();
        for(int i=0;i<str.length();i++)
        {
            ans = (ans*20)+((str.charAt(i)-'a')+1);
        }
        System.out.print("Answer : "+ans);
    }
}
```
### 121. Best Time to Buy and Sell Stock
[Leetcode link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
<br>
You are given an array prices where prices[i] is the price of a given stock on the ith day.
You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example 1:
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

Example 2:
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.

Constraints:
1 <= prices.length <= 105
0 <= prices[i] <= 104

```java
class Solution {
    public int maxProfit(int[] prices) {
        int ans = 0;
        int max1 = Integer.MIN_VALUE;
        int min = Integer.MAX_VALUE;
        int[] max = new int[prices.length];
        for(int i=prices.length-1;i>=0;i--) 
        {
            max1 = Math.max(max1,prices[i]);
            max[i] = max1;
        }
        for(int i=0;i<prices.length;i++) 
        {
            min = Math.min(min,prices[i]);
            ans = Math.max(ans,(max[i]-min));
        }
        return ans;
    }
}
```

