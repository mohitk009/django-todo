---
title: "How to easily find midpoint of any given Linked List"
datePublished: Sun Apr 26 2020 13:05:18 GMT+0000 (Coordinated Universal Time)
cuid: cldva7f9z00r8vonvg0ec5dxj
slug: how-to-easily-find-midpoint-of-any-given-linked-list-5d1a8380bf95
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675837207384/46ca26a9-c076-45f6-8d95-c6e654f4eb27.png

---

So we are given an linked list

1 -> 4 -> 7 -> 3-> 6 -> 8

Now we want to find the mid element of this list without calculating the length

For this purpose we will use two pointers fast and slow and the concept that if fast moves the double speed of the slow then the slow pointer will be at midpoint.

So, let’s start the adventure.

Here is given class **solution** in which we have a method **midpointLL** in which we take **head** node in argument, also return type is of **LinkedListNode** while using **<Integer>** as generics

> public class Solution {

> public static LinkedListNode<Integer> midpointLL(LinkedListNode<Integer> head) {  
>  // write your code here  
>  if(head==null || head.next==null){  
>  return head;  
>  }  
>  LinkedListNode<Integer> temp=head,slow=head,fast=head;  
>  while**(fast.next!=null && fast.next.next!=null)**{  
>  slow=slow.next;  
>  fast=fast.next.next;  
>  }

> }

> }

1.  We have a head pointer currently pointing at first element of LL. We initialize two more pointers **slow** and **fast** as discussed before.
2.  **Basic check:** If there is no element in LL (head==null) or only one element in LL (head.next==null) then we return that element (head)
3.  We initialize fast and slow pointers pointing them to head, because everyone starts from first element( head).
4.  Imagine, all three pointers, **fast, slow, head** pointing at first element ie. 1 Now, we move slow to next element using condition (slow=slow.next) at 1x speed and fast (fast=fast.next.next) at 2x speed.
5.  Now, we want to decide condition of termination of while loop. What should we do?

Obviously, it is related to **fast pointer only** because **slow will be our midpoint** pointer.

6\. So for determine condition of while loop we need to determine when will fast pointer turns null so that we can come out of loop

Let’s assume there are even elements in list then there will be 2 mid elements, if we need to find first mid we can put while(fast.next.next!=null) and slow will automatically pointing at mid element.

even elements case for midpoint of Linked List

Again, let’s assume there are odd elements in list then there will be just 1 mid element, if we need to find first mid we can put while(fast.next!=null) and slow will be pointing at mid element.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675837204849/2de8352a-9076-4242-80f4-b9d79b8aca85.png)

odd elements case for midpoint of Linked List

We obviously need **&& condition** to satisfy both odd and even element condition but be careful if you are thinking to put **fast.next.next!=null** and then fast.next!=null because, if you see again at diagram of odd elements, **fast.next** is turning out to be **null** which is enough to give null pointer exception.

So, if we check fast.next in advance (put it before 2nd condition) then if turns out to be null, according to operator precedence it will not check 2nd condtion and will exit loop.

Hence, understand and follow what’s written in above code.

7\. Finally, we will written **slow pointer/referance** which will be pointing to our mid-element.