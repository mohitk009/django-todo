---
title: "Recursion"
datePublished: Thu Dec 05 2019 20:33:47 GMT+0000 (Coordinated Universal Time)
cuid: cldva7ky200r9vonv1gyyf35z
slug: recursion-30a45d01acc4

---

In simple words, recursion means to breaking the complex problem into simpler parts to get the base case, which then returns values until final output is recieved.

Let us understand it with help of an example

> In this code we are finding powers of any natural number.

> public class Solution {

> public static int power(int x, int n) {  
>   
>  if(n==0){  
>  return 1;  
>  }  
>  int shortAns=power(x,n-1)\*x;  
>  return shortAns;  
>    
>  }  
> }

In the above code, we first first focus on finding simple problem, ie. shortAns

The main idea is if we want to solve x^n we should have result of it’s subproblem x^n-1. Let’s assume we know result of x^n-1

Then x^n=x\*(x^n-1)

We simply call function to calculate result of subproblem as we did in above code, power(x,n-1)\*x

If we run this, then it will keep on dividing the problem in simpler ones forever, ie. infinite loop

To prevent this, we need to have a base case from which it will reach simplest problem and return some value to calling (recursive )function. When recursive function calculates the final value it returns the output.