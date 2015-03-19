---
layout: post
title: Algorithm to return to the Beginning of Loop in (corrupt) LinkedList
---

####QUESTION:
 Given a circular linked list, implement an algorithm which returns node at the beginning of the loop.

**DEFINITION**
	Circular linked list: A (corrupt) linked list in which a node’s next pointer points to an earlier node, so as to make a loop in the linked list.         

**EXAMPLE**		
input: A -> B -> C -> D -> E -> C [the same C as earlier]      
output: C

**CODE** from [ctci](https://github.com/gaylemcd/ctci/blob/master/java/Chapter%202/Question2_6/Question.java)  
{% highlight java %}
public static LinkedListNode FindBeginning(LinkedListNode head) {
		LinkedListNode slow = head;
		LinkedListNode fast = head; 
		
		// Find meeting point
		while (fast != null && fast.next != null) { 
			slow = slow.next; 
			fast = fast.next.next;
			if (slow == fast) {
				break;
			}
		}

		// Error check - there is no meeting point, and therefore no loop
		if (fast == null || fast.next == null) {
			return null;
		}

		/* Move slow to Head. Keep fast at Meeting Point. Each are k steps
		/* from the Loop Start. If they move at the same pace, they must
		 * meet at Loop Start. */
		slow = head; 
		while (slow != fast) { 
			slow = slow.next; 
			fast = fast.next; 
		}
		
		// Both now point to the start of the loop.
		return fast;
	}
{% endhighlight %}

####ANALYSIS:

**Why is this working??**
let k be the num of steps from head to loopBeginNode.   
let s be the num of steps from loopBeginNode to Meeting node      
_slow_ has previously travelled k + s nodes                  
_fast_ been circulating the n circles in the ring (1 <= n).                   
let r be the loop length                 
then fast has travelled s + nr to meet the slow.                     
Hence meeting point = **(s + nr) = s** { due to the loop }                 
The total movement of fast from head is **k + s + nr**.                
so from meeting node fast needs to move k times to reach loopBeginNode.              
from head, k steps is needed to reach the loopBeginNode.          


Hope you enjoyed it. 

Happy Coding . :)

**Credits**: To my geeky friend [Santhosh](http://www.santhosh.info/)
