# Binary Search Tree
## Definition:

> A **Binary Search Tree** is a tree where at every node, all keys to the *left* of that node is **smaller** than that key, and all keys to the *right* are **larger**. 

## Set up:
### Nodes for BST's:
```
class Node<K,V> {
  K key;
  V value;
  Node<K,V> left;
  Node<K,V> right;
  public Node(K key, V value, Node<K,V> left, Node<K,V> right) {
    this.key = key;
    this.value = value;
    this.left = left;
    this.right = right;
  }
  public String toString() {
    String children = "";
    if(left != null || right != null) {
      children = ", " + left + ", " + right;
    }
    return "(" + key + ": " + value + children + ")";
  }
}
```
you can ignore the `toString()` method here, but I still put it up as it is in the notes, we can see that there are four instance variables for binary search tree, which allows it to store a {key,value} pair and information of the nodes connected to it.

### How to `get` a Node from BST
```
  V get(Node<K,V> node, K key) {
	  if (node == null) { return null; }
	  
	  if (node.key.equals(key)) { return node.value; }
	  
	  V leftResult = get(node.left, key);
	  V rightResult = get(node.right, key);
	  
	  if (leftResult != null) { return leftResult; }
	  if (rightResult != null) { return rightResult; }
	  
	  return null;
  }

  V get(K key) {
	  return this.get(this.root, key);
  }
```
The logistic of this `get` function (with arguments) is 
![image](https://github.com/EmmaBeai/CSE_Notes_Complie/assets/129473980/48f375c1-2bc2-46df-9662-030da1b2463c)

### How to `set` a Node from BST


