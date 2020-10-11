# Linked-list

+ [Linked list cycle](#linked-list-cycle)
+ [Reverse linked list](#reverse-linked-list)
+ [Middle of the linked list](#middle-of-the-linked-list)
+ [Remove nth node from end of list](#remove-nth-node-from-end-of-list)

## Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

```python
class Solution:
    dct = {}
    def find(self, node):
        if node.next == None:
            return False
        else:
            if not node.next in self.dct:
                self.dct[node.next] = None
                return self.find(node.next)
                
            else:
                return True
    def hasCycle(self, head: listnode) -> bool:
        if not head:
            return False
        return self.find(head)
```

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```python
class Solution:
    
    def deep(self, node, prev):
        if node.next==None:
            node.next = prev
            return node
        else:
            temp = node.next
            node.next = prev
            return self.deep(temp, node)
            if node.next == None:
                return node
            
        
    def reverse(self, head: listnode) -> listnode:
        if not head:
            return None
        return self.deep(head,None)
```

## Middle of the Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```python
class Solution:
    length = 1
    
    def findmiddle(self, node):
        if(node.next == None):
            self.length//=2
            print(self.length)
        else:
            self.length += 1
            self.findmiddle(node.next)
    def inp(self, node):
        if self.length == 0:
            return node
        else:
            self.length-=1
            return self.inp(node.next)
    
    def middleNode(self, head: listnode) -> listnode:
        
        self.findmiddle(head)
        return self.inp(head)
```

## Remove Nth Node From End of List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```python
class Solution:
    i = 0
    def delete(self,node,ind):
        
        if node is None:
            self.i = ind
        else:
            self.delete(node.next,ind)
            if self.i != 0:
                self.i-=1
            else:
                node.next = node.next.next
                self.i-=1
    
    def removeFromEnd(self, head: listnode, n: int) -> listnode:
        if head.next is None:
            return None
        self.delete(head,n)
        if self.i == 0:
            head = head.next
        return head
```

