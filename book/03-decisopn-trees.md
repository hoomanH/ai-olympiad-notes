Chapter 3 — Decision Trees
1. What is a decision tree?

A decision tree is a machine learning model that makes predictions by asking a sequence of questions.

Each question splits the data into smaller parts.

At the end, the model reaches a final decision.

Example:

Is x1 < 5?
    Yes → Class A
    No  → Is x2 < 3?
              Yes → Class B
              No  → Class A

A decision tree is similar to a flowchart.

2. Nodes, branches, and leaves

A decision tree has three important parts:

Node   = a place where the model asks a question
Branch = the answer path after the question
Leaf   = the final prediction

Example:

Question node: Is price < 2 billion?
Branch 1: Yes
Branch 2: No
Leaf: Sold / Not sold

The final class is written in the leaf.

3. Decision tree conditions

In many exam questions, each node checks a condition like:

x1 < C

or:

x2 < C

Here:

x1, x2 = features
C = a fixed number

For example:

x1 < 4

means:

Is feature x1 smaller than 4?

If yes, the data goes to one branch.

If no, it goes to the other branch.

4. Decision trees in 2D space

Suppose each data point has two features:

x1
x2

A condition like:

x1 < 4

splits the plane using a vertical line.

A condition like:

x2 < 3

splits the plane using a horizontal line.

So, basic decision trees split the space using horizontal and vertical cuts.

This is very important.

5. Axis-aligned splits

A split is called axis-aligned when it is parallel to one of the coordinate axes.

Example:

x1 < C

creates a vertical split.

Example:

x2 < C

creates a horizontal split.

Decision trees that use conditions like x1 < C and x2 < C make axis-aligned splits.

They usually do not directly create diagonal boundaries.

6. Tree complexity

In the uploaded exam, tree complexity is defined as the number of nodes in the tree.

A smaller tree is simpler.

A larger tree is more complex.

Example:

Tree A: 3 nodes
Tree B: 9 nodes

Tree B is more complex.

The exam may ask whether a transformation makes the required tree simpler or more complex.

Example of a simpler tree:

Suppose the classes are separated by a diagonal boundary:

Class A: x2 < x1
Class B: x2 >= x1

Because a basic decision tree uses only horizontal and vertical splits, it may need many nodes to approximate this diagonal boundary.

If we rotate the data (turn the coordinate system so the points are viewed from a different angle) so that the diagonal boundary becomes vertical, the tree may classify the data with only one or two splits.

In this case, the transformation makes the tree simpler.

Example of a more complex tree:

Suppose the classes are separated by a vertical boundary:

If x1 < 3 → Class A
If x1 >= 3 → Class B

A decision tree can solve this with a single split.

If we rotate the data by 45 degrees, the boundary becomes diagonal.

Now the tree may need several horizontal and vertical splits to approximate the same boundary.

In this case, the transformation makes the tree more complex.

Why does complexity matter?

A simpler tree:

Uses fewer nodes
Is easier to understand
Trains faster
Often generalizes better

A more complex tree:

Uses more nodes
Is harder to interpret
Requires more computation
Has a higher risk of overfitting

Therefore, transformations that align class boundaries with the coordinate axes can reduce tree complexity, while transformations that create diagonal boundaries can increase it.

7. Normalization and decision trees

Normalization usually changes the scale of features.

For example, it may transform data so that each feature has:

Mean = 0
→ After normalization, the average value of the feature becomes 0. Values larger than the original average become positive, and values smaller than the original average become negative.

Variance = 1
→ Variance measures how spread out the values are around the mean. A small variance means most values are close to the mean, while a large variance means the values are more widely spread. After normalization, the feature is scaled so that its variance equals 1, making different features easier to compare.

For many decision trees, normalization does not fundamentally change the shape of the classification problem.

Why?

Because a condition like:

x1 < C

can still be replaced by another condition after normalization.

The threshold number changes, but the ordering of points along the same feature usually stays the same.

So if the tree only depends on comparisons along x1 or x2, normalization often does not make the tree essentially simpler or harder.

8. Rotation and decision trees

Rotation is different from normalization.

If we rotate the data by 45 degrees, the position of the data changes relative to the x1 and x2 axes.

This can strongly affect decision trees.

Why?

Because decision trees with conditions like:

x1 < C
x2 < C

can only make horizontal and vertical splits.

If the original classification boundary was diagonal, rotating the data may make it horizontal or vertical.

Then the tree can become simpler.

But the opposite can also happen.

If the original boundary was horizontal or vertical, rotation may make it diagonal.

Then the tree may need more nodes.

So rotation can make the tree simpler or more complex depending on the data.

9. Important comparison: normalization vs rotation

Normalization changes scale.

Rotation changes direction.

This is the key difference.

Normalization:
Usually stretches or compresses axes.

Rotation:
Turns the whole coordinate system.

Decision trees are usually more sensitive to rotation than to normalization because their splits are axis-aligned.

10. Example idea

Suppose the class boundary is already vertical.

Example:

If x1 < 3 → Class A
If x1 >= 3 → Class B

A decision tree can solve this with one simple split.

But if we rotate the data, that vertical boundary may become diagonal.

Now a basic decision tree cannot represent the diagonal boundary with one split.

It may need several horizontal and vertical cuts.

So the tree becomes more complex.

11. Opposite example

Suppose the class boundary is diagonal.

A decision tree may need several horizontal and vertical cuts to approximate it.

But if we rotate the data so the diagonal boundary becomes vertical or horizontal, the tree may become much simpler.

So rotation can sometimes reduce complexity.

This is why we usually cannot say rotation always increases or always decreases decision tree complexity.

It depends on the geometry of the data.

12. Decision trees and overfitting

A very deep decision tree can memorize training data.

This may give very good training performance but bad performance on new data.

This is called overfitting.

A simpler tree may generalize better.

Common ways to control tree complexity include:

Limit the maximum depth
Require a minimum number of samples in each leaf
Prune unnecessary branches
13. How to solve decision tree exam questions

Use this checklist:

1. Identify the features: x1, x2, ...
2. Identify the allowed conditions, such as x1 < C.
3. Ask: are the splits axis-aligned?
4. Check whether the transformation preserves axis directions or changes them.
5. For normalization, think about scale and ordering.
6. For rotation, think about whether boundaries become easier or harder for horizontal/vertical cuts.
7. Compare the number of required nodes.
14. Common exam traps
Trap 1: Thinking normalization always helps

Normalization is very useful for many models, but it does not always reduce decision tree complexity.

For decision trees, the ordering of values often matters more than the exact scale.

Trap 2: Forgetting that decision tree splits are axis-aligned

If the tree only uses questions like x1 < C, then it cannot directly make arbitrary diagonal splits.

Trap 3: Saying rotation always helps

Rotation may help or hurt.

It depends on the original arrangement of the data.

15. Quick self-check questions
Question 1

What is a node in a decision tree?

Answer:

A place where the tree asks a question or checks a condition.
Question 2

What is a leaf?

Answer:

The final prediction point of the tree.
Question 3

What kind of split does x1 < C create in two dimensions?

Answer:

A vertical axis-aligned split.
Question 4

What kind of split does x2 < C create in two dimensions?

Answer:

A horizontal axis-aligned split.
Question 5

Why can rotation strongly affect a decision tree?

Answer:

Because decision tree splits are usually axis-aligned, and rotation changes the direction of the data relative to the axes.
Question 6

Does normalization always make a decision tree simpler?

Answer:

No. It may change the scale and thresholds, but it does not necessarily reduce tree complexity.
