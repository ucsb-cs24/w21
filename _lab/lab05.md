---
layout: lab
num: lab05
ready: true
desc: "Binary Search Tree"
assigned: 2021-03-04 9:00:00.00-8
due: 2021-03-10 23:59:00.00-8
---

# Goals for this lab

By the time you have completed this lab, you should be able to

* Know how to navigate a binary tree data structure
* Implement recursive functions for binary trees
* Implement binary search tree functions

# Step by Step

## Step 0: Getting Started

This lab may be done solo, or in pairs.
Before you begin working on the lab, please decide if you will work solo or with a partner.
As stated in previous labs, there are a few requirements you must follow if you decide to work with a partner. I will re-iterate them here:
* Your partner must be enrolled in the same lab section as you.
* You and your partner must agree to work together outside of the lab section in case you do not finish the lab during your lab section. You must agree to reserve at least two hours outside of the lab section to work together if needed. You are responsible for exchanging contact information in case you need to reach your partner.
* If you choose to work with a partner for a future lab where pair programming is allowed, then you must choose a partner you have not worked with before.
* You MUST add your partner on Gradescope when submitting your work EACH TIME you submit a file(s). After uploading your file(s) on Gradescope, there is a “Group Members” link at the bottom (or “Add Group Member” under “Groups”) where you can select the partner you are working with. Whoever uploaded the submission must make sure your partner is part of your Group. Click on “Group Members” -> “Add Member” and select your partner from the list.
* You must write your Name(s) and Perm number on each file submitted to Gradescope.
Once you and your partner are in agreement, choose an initial driver and navigator, and have the driver log into their account.

## Step 1: Copying some programs from my directory
Visit the following web link—you may want to use “right-click” (or “control-click” on Mac) to bring up a window where you can open this in a new window or tab:

[Lab05 Files](https://github.com/ucsb-cs24-kozerawski-w21/lab05_data)

You should see a listing of several C++ files. Please copy those files into your local lab05 Github repo directory.

If so, you are ready to move on.


# Step 2: Understand the code in given files

Verify you got all the files and try to compile them as follows:
```
intbst.cpp  intbst.h  testbst.cpp
```

A binary search tree class for integers, class IntBST is defined in intbst.h - please study this file for details of the class's features:

The constructor, destructor, insert method and pre-order print method are already implemented in intbst.cpp. Notice the insert method will return false to indicate an attempt to insert a duplicate value; otherwise it inserts the value and returns true.
In Step 2, you will implement the other two print methods, in-order and post-order. In Step 3 you will implement the sum, count and contains methods. In Step 4, you will implement the predecessor, successor, and remove methods. Step 4 will likely take you the most time BY FAR, so plan accordingly.
The binary tree node structure is defined in the private area. The only instance variable is a node pointer, to point at the root node of the tree or at 0 if the tree is empty.
Several utility functions are declared in the private area too. These functions can be recursive (by virtue of their Node* parameters), and the public methods may choose to use them or not. See how the destructor uses clear, for example, and the insert method uses the overloaded version of insert, each by passing the root pointer to the corresponding utility function. Also take note of the definition of getNodeFor, which will be useful in several of the functions you need to implement. Consider implementing this function immediately after the print functions, and think about where you can reuse it.


# Step 3: Implement in-order and post-order binary tree printing

You should be able to run testbst now (assuming you compiled it in Step 2):
```
-bash-4.3$ ./testbst
Choice of tests:
  0. all tests
  1. just printInOrder
  2. just printPostOrder
  3. just sum
  4. just count
  5. just contains
Enter choice:
0
BST:
  pre-order: 64 8 4 32 16 128 512 256
  in-order:
  post-order:
  sum: 0
  count: 0
  contains 64? Y
  contains 4? Y
  contains 16? Y
  contains 128? Y
  contains 17? N
  contains 512? Y
  . . .
Empty BST:
  pre-order:
  in-order:
  post-order:
  sum: 0
  count: 0
  contains 16? N

```
Note that just the pre-order print is complete (and the sum, count and contains methods aren't working either).

Use an editor (e.g., emacs) to make the following changes to intbst.cpp - do not change any of the other files.

Fix the comment at the top to show your name(s) and the date.
Scroll to the print functions (starting line 60). See how the public method just passes the root pointer to the private function in each case. Implement the private functions, printInOrder and printPostOrder.
Save, and then test your print implementations: compile and execute testbst again, choosing either all tests or just one of your print functions to test.
Here are the correct results (abbreviated to show just the print orders):

BST:

  pre-order: 64 8 4 32 16 128 512 256

  in-order: 4 8 16 32 64 128 256 512

  post-order: 4 16 32 8 256 512 128 64

By the way, you should be able to draw the tree now, both by tracing the order of the inserts, or by interpreting the three orders above. Take a minute to try that now on a piece of scratch paper since it may be very helpful when implementing the remaining functions.


# Step 4: Implement three more binary search tree functions

You may do these tasks in any order. Check the results of each part as you complete it.

Implement the helper function for sum() - notice the public method just returns the result of the helper function. We suggest you use recursion to do so. Think about these questions before starting to code: What's the base case? What should be returned in the base case? What should be returned in the general (recursive) case?
Implement the helper function for count() - this is very similar to the sum() function.
Implement the public contains method, either recursively or iteratively - both are about the same level of difficulty in this case. If you decide to use recursion, you can use getNodeFor() in your implementation of contains(). You won't need this utility function to solve the problem iteratively. In either case, remember the tree is a binary search tree, and so your solution should run in O(log n) time.
Here are the results of all tests from our solution - you should verify that your results match:
```
BST:
  pre-order: 64 8 4 32 16 128 512 256
  in-order: 4 8 16 32 64 128 256 512
  post-order: 4 16 32 8 256 512 128 64
  sum: 1020
  count: 8
  contains 64? Y
  contains 4? Y
  contains 16? Y
  contains 128? Y
  contains 17? N
  contains 512? Y
  . . .
Empty BST:
  pre-order:
  in-order:
  post-order:
  sum: 0
  count: 0
  contains 16? N
```

Be aware, however, that more rigorous testing will be done when your work is submitted (a different program is used for testing your functions, some with random data).

# Step 5: Implement predecessor, successor, and remove

Your final task for this lab is to implement getPredecessor(), getSuccessor(), and remove(). The predecessor of a value is the next lowest value, while the successor is the next highest. Note that these functions should be implemented using the inherent structure of the binary tree, not by an exhaustive search for the next value. It will very likely be helpful to draw out the tree (the pre-order print can help you with this) when understanding how to implement getPredecessor() and getSuccessor(). If the element passed to the function is the first (for predecessor) or last (for successor) element in the tree, the function should return 0. It should also return 0 if the value is not present in the tree. Both of these functions will likely be harder to implement than any of the prior functions in this lab. However, correct implementations of getPredecessor() and getSuccessor look VERY similar, so you will likely be able to reuse a lot of your logic.

Finally, move on to remove(), which is likely the hardest algorithm you will be asked to implement this quarter. It is not excessively complicated in principle, but getting it completely right can take a while. Consider switching off pilot and navigator as you are debugging your implementation. You will probably find it helpful to use either getPredecessor() or getSuccessor() in remove(). You can also use remove() inside of itself, though it should NOT be a recursive function--the difference being that only one additional call of remove() should EVER occur. As with predecessors and successors, drawing the tree will be very helpful.

A correct implementation of all functions should produce the following output from testbst when selecting option 0:

```
BST:
  pre-order: 64 8 4 32 16 128 512 256
  in-order: 4 8 16 32 64 128 256 512
  post-order: 4 16 32 8 256 512 128 64
  sum: 1020
  count: 8
  contains 64? Y
  contains 4? Y
  contains 16? Y
  contains 128? Y
  contains 17? N
  contains 512? Y
  predecessor of 64 is: 32
  predecessor of 512 is: 256
  predecessor of 4 is: 0
  successor of 64 is: 128
  successor of 512 is: 0
  successor of 4 is: 8
  removing 4
  removing 64
  removing 128
  contains 64? N
  contains 4? N
  contains 16? Y
  contains 128? N
  contains 17? N
  contains 512? Y
  pre-order: 256 8 32 16 512
Empty BST:
  pre-order:
  in-order:
  post-order:
  sum: 0
  count: 0
  contains 16? N
```


# Step 6: Test Your Code and Upload to Gradescope

The Autograder will use some test cases to check if your implementations are correct. In order to verify them, you’ll need to write your own test code, which can be a ‘main’ function to print out the results, before the submission. Then, write a Makefile to link all dependencies to make and run your test. 
The lab assignment “Lab05” should appear in your Gradescope dashboard in CS 24. If you haven’t submitted anything for this assignment yet, Gradescope will prompt you to upload your files. **For this lab, you will only need to upload your modified files (i.e.intbst.h and intbst.cpp).** If you already submitted something on Gradescope, it will take you to their “Autograder Results” page. There is a “Resubmit” button on the bottom right that will allow you to update the files for your submission. For this lab, if everything is correct, you’ll see a successful submission passing all of the Autograder tests.

**Remember to add your partner to Groups Members for this submission on Gradescope if applicable. At this point, if you worked in a pair, it is a good idea for both partners to log into Gradescope and check if you can see the uploaded files for Lab05.**
