# Binary Search Tree
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
you can ignore the toString() method here, but I still put it up as it is in the notes, we can see that there are four instance variables for binary search tree, which allows it to store a {key,value} pair
