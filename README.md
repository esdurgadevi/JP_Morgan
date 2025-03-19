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
