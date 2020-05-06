# TreeBinary
/*
   1. Only write your code in the methods that have the comment 'write your code here' or in the section 'write optional helper functions here'
   2. Do not modify anything else
   3. If your code cannot compile or fails the test cases in 'main()', you will not receive a response from us
*/
 
import java.util.*;
import java.util.regex.*;
 
public class TreeTest {
    public static void main(String... args) {
 
        /*
           Consider the following tree:
 
                 1
              /  |  \
             2   4   6
           / |  / \  |  \  
          3  9 5  7  11 12
              / \      / | \
             13 16    14 23 17
               / \
              24 32
 
 
          Assuming the numbers are the ids of each node, the tree can be written down as follows:
 
          1(2,4,6) 2(3,9) 4(5,7) 6(11,12) 5(13,16) 12(14,23,17) 16(24,32)
 
          In the example above, for the group 1(2,4,6), node 2, 4 and 6 are the child nodes of
          node 1. Note that extra whitespaces should be accepted. Assume ids are positive integers only.
        */
 
        Tree first = new Tree("1(2,4, 6) 2(3, 9) 4(5,7)  6(11,12 ) 5(13,16)   12(14, 23, 17) 16( 24,32 )");
        assertTrue(first.getDepthOfNodeWithId(1) == 1);
        assertTrue(first.getDepthOfNodeWithId(4) == 2);
        assertTrue(first.getDepthOfNodeWithId(5) == 3);
        assertTrue(first.getDepthOfNodeWithId(12) == 3);
        assertTrue(first.getDepthOfNodeWithId(16) == 4);
        assertTrue(first.getDepthOfNodeWithId(23) == 4);
        assertTrue(first.getDepthOfNodeWithId(32) == 5);
 
        /*
              2
           / | | \ 
          5  4 3  1
          |     \
          7      9
         / \   /  \
        12 10 11  14
            |
            13
           / | \
         16  8  15
        */
 
        Tree second = new Tree(" 2(5, 4, 3,1)  5(7)   3(9) 7(12, 10)   9(11, 14)  10(13) 13(16,8,15)");
        assertTrue(second.getDepthOfNodeWithId(2) == 1);
        assertTrue(second.getDepthOfNodeWithId(5) == 2);
        assertTrue(second.getDepthOfNodeWithId(3) == 2);
        assertTrue(second.getDepthOfNodeWithId(12) == 4);
        assertTrue(second.getDepthOfNodeWithId(11) == 4);
        assertTrue(second.getDepthOfNodeWithId(13) == 5);
        assertTrue(second.getDepthOfNodeWithId(8) == 6);
    }
 
    private static void assertTrue(boolean v) {
        if(!v) {
            Thread.dumpStack();
            System.exit(0);
        }
    }
}
 
class Tree {
    private Node root;
 
    public Tree(String treeData) {
        // write your code here
    }
 
    public int getDepthOfNodeWithId(int id) {
        // write your code here
        // if a node is not found, return a negative value
    }
 
    // write optional helper functions here
}
 
class Node {
    private Node parent;
    private List<Node> children;
    private int id;
 
    public Node(int id) {
        this.id = id;
        this.children = new ArrayList<Node>();
    }
 
    public Node(int id, Node parent) {
        this(id);
        this.parent = parent;
    }
 
    public void appendChild(Node child) {
        children.add(child);
    }
 
    public int getId() {
        return id;
    }
 
    public List<Node> getChildren() {
        return Collections.unmodifiableList(children);
    }
}
