---
layout: post
title: "What is Linked List?"
ref: ds-linked-list
date: 2020-05-09 07:50:00 +0900
published: false
categories:
 - "Data Structure"
lang: ko
---

# Linked List
연결 리스트는 배열과 같은 선형 자료구조이지만 자료들이 메모시상에 순차적으로 저장되지 않고 
노드라는 것들로 서로 연결되어 있습니다.

Linked List is a linear data structure like arrays where data are not stored
contiguously in the memory like arrays. The elements in a linked list are linked using pointers.

연결 리스트의 장점으로는 데이터의 삽입과 삭제가 O(1)에 가능하다는 점이고, 단점으로는 배열처럼 
리스트 중간에 바로 접근 할 수 없다는 것입니다. 무조건 첫 번째 노드에서 부터 순차적으로 접근을 해야
하므로 접근에는 O(n)의 시간이 걸립니다. 추가적인 메모리가 소모된다는 것 또한 연결 리스트의 
단점입니다.

<div class="divider"></div>

## Linked List vs. Array
Arrays are used to store linear data of same types, but they have the following limitations:
1. The size of the arrays is fixed.
2. Inserting and deleting an element is expensive because we first need to create a room for the 
new element, and then shift all elements.

For example, let say we have a sorted list of IDs<br>
`id[] = [1000, 1010, 1050, 2000, 2040]`.

To insert a new id `1001` in a **sorted list**, we need to shift every elements after `id[0]` to
the right to maintain its order. 

| Operations| Array | Linked List|
|:---:|:---:|:---:|
|**Access**| O(1) | O(n) |
|**Search**| O(n) | O(n) |
|**Insert**| O(n) | O(1) |
|**Delete**| O(n) | O(1) |

## Advantages of Linked List
1. Unlike the arrays, the size of the linked lists is dynamic. You can insert or delete elements
without resizing or shiftin.
2. Linked lists have faster insert and delete operations.

## Drawbacks
1. Random access is not allowed. We have to access elements sequentially starting from the 
first node.
2. Every time we create a new node to link, we're using that much more memory space.
3. Linked Lists are not cache friendly. Array elements are located contiguously in a memory, 
so there's locality of reference.

## Representation
A linked list is represented by a pointer to the first node or the linked list, which is called 
the `head` node. `head` is `nil` if the list is empty.

Each node consists of at least two parts: `value`, which is the data stored in the node and `next` which is a pointer/reference to the next node.

## Simple Linked List Example
```rb
class Node
  attr_accessor :data, :next
  
  def initialize(data)
    @data = data
    @next = nil
  end
end

head = Node.new(1)    # [head,   1] -> nil
second = Node.new(2)  # [second, 2] -> nil
third = Node.new(3)   # [third , 3] -> nil

head.next = second    # [head, 1] -> [second, 2] -> nil
second.next = third   # [head, 1] -> [second, 2] -> [third, 3]
```

## Traversal
```rb
def print_list(node)
  while node != nil
    print "#{node.data} "
    node = node.next
  end
  puts
end

head = Node.new(1)             # 1 -> nil
head.next = Node.new(2)        # 1 -> 2 -> nil
head.next.next = Node.new(3)   # 1 -> 2 -> 3 -> nil

print_list(head)
# 1 2 3
```
