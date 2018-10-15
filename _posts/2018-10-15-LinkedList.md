#LinkedList and Recursion I
*using python 2*
###### Why LinkedList?
- model the linked based relationship directly
- versatility and flexibility: dynamically resizing array
```
class ListNode(object):
  def __init__(self, value, next = None): 
    self.next = next
    self.val = value
    #default value give alternative parameters
```
######Tranverse:
- tranverse all the nodes inside a singly linked list and print their value accorfdingly to teh screen
```
#iteratively
def print_all_nodes(head):
  curr = head
  while curr:
    print curr.val
    curr = curr.next

#recursively
def print_all_nodes(head):
  if not head:
    return
  print head.val
  print_all_nodes(head.next)
```
######Search:
- given a linked list and an index/ value, find the node

```
def search_by_index(head, index):
  if not head or index < 0
    return None
  for move_times in xrange(index):
    head = head.next
    if not head:
      return None
  return head
#python2: xrange() uses one memory a in loop, yet range() creates an list
#python 3 only has range(), using loop
```
######Equality:
 ```
def __eq__(self, other):
  return isinstance(other, ListNode) and self.value == other.value
```
######Add:
- a -> b -> c add f to index 1
0     1     2   result: a->f->b->c
```
def add_to_index(head, index, val):
  fake_head = ListNode(None)
  fake_head.next = head
  insert_place = search_by_index(fake_head, index)
  if insert_place is None:
    return
  new_node = ListNode(val)
  insert_place.next, new_node.next = new_node, insert_place.next
  return fake_head.next
```
###Difference between Python list and singly linked list:
| | Python list | Singly linked list |
|-----------------|---------------|-----------------------|
|access item by index|O(1)| O(n)|
|add/ remove head| O(n) |O(1)|
|add/ remove end|O(1)|O(n) find the tail + insert it|
|add/ remove others|O(n)|O(n)|

######Homework Leetcode 707, 876, 237, 203, 83, 82, 19