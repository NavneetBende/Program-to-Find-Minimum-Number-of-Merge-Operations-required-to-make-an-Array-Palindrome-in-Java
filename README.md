Minimum number of merge operations required to make an array palindrome in Java
Here, in this page we will discuss the program to find Minimum number of merge operations required to make an array palindrome in  Java programming language. We are given with an array and we need to print an integer value denoting the number of operations required.

Minimum Number of Merge Operations
Method Discussed :
Method 1 : Using Iteration
Method 2 : Using Recursion
Let’s discuss them one by one in brief,

Method 1:
Simple approach is to calculate the factorial of the number then, track its unit digit until the non-zero digit found.

Create a recursive function say fact(int n) to calculate the factorial,
Base condition: if(n<=1) return 1
Otherwise return n*fact(n-1).
After getting the factorial, and store it in variable say factorial.
Run a loop till (factorial % 10 != 0)
After that, print(factorial % 10)
Method 1 : Code in Java
Run
class Main
{
    static int findMinOps(int[] arr, int n)
    {
        int ans = 0; 
 
        for (int i=0,j=n-1; i<=j;)
        {
            if (arr[i] == arr[j])
            {
                i++;
                j--;
            }
 
            else if (arr[i] > arr[j])
            {
                j--;
                arr[j] += arr[j+1] ;
                ans++;
            }
 
            else
            {
                i++;
                arr[i] += arr[i-1];
                ans++;
            }
        }
 
        return ans;
    }
 
    public static void main(String[] args)
    {
        int arr[] = new int[]{1, 4, 5, 9, 1} ;
        System.out.println("Minimum Operations is "+ findMinOps(arr, arr.length));
     
    }
}
Output :
Minimum Operations is 1
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2:
Create a recursive function say, fun() pass arr and two values 0 and n-1.
In the fun(), return 0, if(i==j or i>j)
Otherwise, check if (arr[i]==arr[j]), then return(1+fun(arr, i+1, j-1))
Else check if (arr[i]>arr[j]), then set arr[j-1] = arr[j-1]+arr[j] and return(1+fun(arr, i, j-1))
Else set, arr[i+1] = arr[i]+arr[i+1] and return(1+fun(arr, i+1, j)).
 
Method 2 : Code in Java
Run
class Main
{
    static int fun(int []arr, int i, int j){

    if( i==j || i>j )
         return 0;

    if(arr[i]==arr[j])
         return fun(arr, i+1, j-1);

    else if(arr[i]>arr[j]){
          arr[j-1] = arr[j]+arr[j-1];
          return (1+fun( arr, i, j-1));
     }
     else{
          arr[i+1] = arr[i]+arr[i+1];
          return (1+fun( arr, i+1, j)); 
     }

}
 
    public static void main(String[] args)
    {
        int arr[] = new int[]{1, 4, 5, 9, 1} ;
        System.out.println("Minimum Operations is "+ fun(arr,0, arr.length-1));
     
    }
}
Output :
Minimum Operations is 1
