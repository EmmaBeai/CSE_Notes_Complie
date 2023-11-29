# Binary Search Tree
## Definition:

> A **Binary Search Tree** is a tree where at every node, all keys to the *left* of that node is **smaller** than that key, and all keys to the *right* are **larger**. 

> The **Height** of a tree is the number of nodes on the longest path from the root to the bottom (*leaf*)
> > Best Case (shortest height): O($log(n$))
> > Worst Case (longest height): O($n^2$)

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

A broken `get` implementation:
```
  V get(Node<K,V> node, K key) {
	if (node == null) { // throw error }
	if (node.key.equals(key)){
		return node.value;
	}
	if (node.key > key){
		return get(node.left, key);
	}
	else{
		return get(node.right, key);
	} 
	return null;
  }
```
Some question related to this code:

1. Where is this `get` method broken? *the `>` does not match.*
2. How can we fix the method? *Use comparator or comparable (CompareTo())*
3. What error should be throw in above code? *NoSuchElementException()* *or* *ElementNotFoundException()*
4. What would the code that uses `get()` look like to prevent the program crashing if **the key is missing**? *a simple try_catch set up*





### How to `set` a Node from BST
```
private Node<K,V> set(Node<K,V> node, K key, V value){
	if(node == null) {
		size ++;
		return new Node<K,V>(key, value, null, null);
	}
	int comp = this.comparator.compare(node.key, key);
	if(comp < 0) {
	node.right = this.set(node.right, key, value);
	return node;
	} else if (comp > 0) {
		node.left = this.set(node.left, key, value);
		return node;
	}else {
		node.value = value;
		return node;
	}
}

public void set(K key, V value) throws IllegalArgumentException {
	if(key == null) {
		throw new IllegalArgumentException(emptyKey);
	}
	this.root = this.set(root, key, value);
}
```
The logistic for `set` function (with arguments) is

![image](https://github.com/EmmaBeai/CSE_Notes_Complie/assets/129473980/718f629f-4fd9-4fcf-9785-ff5398e54297)


# Heap





