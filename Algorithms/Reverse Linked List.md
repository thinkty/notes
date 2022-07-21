# Reverse Linked List
To reverse a given linked list, one can use recursive or iterative methods. I personally find recursive method to be more easy to understand.

###### Implementation
- Recursive
```
ListNode * reverse(ListNode * node) {
	// Base case: head is NULL or current node is tail
	if (node == NULL || node->next == NULL) {
		return head;
	}
	
	ListNode * newHead = reverse(node->next);
	node->next->next = node;
	node->next = NULL;
	
	return newHead;
}
```

The first condition `node == NULL` is only used when the given linked list is empty.
The next condition `node->next == NULL` is the usual base case where the current node is the tail of the given linked list.

```
	ListNode * newHead = reverse(node->next);
```
With the return value from the recursive call, the tail will be the head of the reversed linked list.

```
	node->next->next = node;
```
Next, make the current node to point to itself.
This part is basically appending the current node to the reversed linked list.

```
	node->next = NULL;
```
However, the reversed linked list (newHead) will have a cycle.
Therefore, make the current node point to nothing since it is appended to the reversed linked list and it is now the tail of the list.

Below is an example to better understand the procedure.
Suppose the given linked list is as follows :
```
	[1 → 2 → 3 → 4 → 5]
```

Following the recursive steps, the method will traverse to the end until it hits the base case which is the last element `[5]`.

When the given node is `[4 → 5]`, the return value from `reverse(node->next)` will be `[5]`.
After appending the current node `[4 → 5]` to the new head `[5]`, the new head `[5 → 4 → 5 → 4 ...]` will have a cycle.
To get rid of the cycle, `node->next = NULL` is used and returns the new head `[5 → 4]`.

Next, the current node will be `[3 → 4]`.
Same as before, append the current node to the new head `[5 → 4 → 3 → 4 → 3 ...]` and get rid of the cycle by setting the current node's next to point to nothing.
After getting rid of the cycle and following the same steps multiple times, the new head `[5 → 4 → 3]` will eventually have a perfect reversed linked list.

- Iterative
```
ListNode * reverse(ListNode * head) {
	if (head == NULL || head->next == NULL) {
		return head;
	}
	
	ListNode* iter = head->next;
	ListNode* prev = head;
	
	while (iter) {
		prev->next = iter->next;
		iter->next = head;
		head = iter;
		iter = prev->next;
	}
	
	return head;
}
```

The `iter` variable is used as an iterator to go through the linked list and the `prev` variable is used to keep track of the previous variable while going through the linked list.

In the loop, when the `iter` is `NULL`, it means that it has reached the end of the linked list.
Inside the loop, the idea is to prepend the current iterating element to the head and update the head value.

For me, it's quite hard to understand the instructions inside the loop just by looking at it, so here is an example.
```
Example linked list : 1 → 2 → 3 → 4 → 5
```

Before going into the loop, the variables will look like this:
```
linked list : 1 → 2 → 3 → 4 → 5
       head : 1
       iter : 2
       prev : 1
```

By making the previous element's next element will be the next element of the currently iterating element `prev->next = iter->next`, below are the current states.
```
linked list : 1 → 3 → 4 → 5 , 2 → 3 → 4 → 5
       head : 1
       iter : 2
       prev : 1
```
Elements with value 1 `prev` and 2 `iter` both points to the same element.

In order to prepend the currently iterating element to the head, the currently iterating element's next element will be the head `iter->next = head`.
```
linked list : 2 → 1 → 3 → 4 → 5
       head : 1
       iter : 2
       prev : 1
```

After prepending the element, the next two instructions are for preparing the next step of the loop.
First, update the `head` to the currently iterating element `head = iter` since it has been prepended to the head making it the new head.
Next, update the currently iterating element `iter` to the next element to iterate `iter = prev->next`.
```
linked list : 2 → 1 → 3 → 4 → 5
       head : 2
       iter : 3
       prev : 1
```

Notice that the previous element `prev` isn't updated because it already points to the previous element of the currently iterating element.

After repeating the steps a few more times, we get to the last iteration with the array looking like below,
```
linked list : 4 → 3 → 2 → 1 → 5
       head : 4
       iter : 5
       prev : 1
```

Since the currently iterating element `iter` is the last element that points to nothing, the previous element `prev` and `iter` will both point to nothing
```
linked list : 4 → 3 → 2 → 1 , 5
       head : 4
       iter : 5
       prev : 1
```

Prepend the currently iterating item to the head and update the `head`.
```
linked list : 5 → 4 → 3 → 2 → 1
       head : 5
       iter : 5
       prev : 1
```

Since there are no elements to iterate, the loop will exit and return the head of the reversed linked list.
