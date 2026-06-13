# Chapter 2 — K-Nearest Neighbors

## 1. What is KNN?

KNN stands for **K-Nearest Neighbors**.

It is a simple classification method.

The idea is:

```text
To classify a new data point, look at the K closest known data points.
Then choose the class that appears most often among them.
```

KNN does not really learn a formula during training.

Instead, it keeps the training data and compares new data points with the old ones.

---

## 2. Example

Suppose we have two classes:

```text
Black points
White points
```

Now we receive a new unknown point.

To classify it using KNN, we check which labeled points are closest to it.

If most of the nearest neighbors are black, the new point is classified as black.

If most of the nearest neighbors are white, the new point is classified as white.

---

## 3. What does K mean?

K is the number of neighbors we check.

For example:

```text
K = 1
```

means:

```text
Look only at the closest neighbor.
The new point gets the same class as that neighbor.
```

But:

```text
K = 3
```

means:

```text
Look at the 3 closest neighbors.
The class with the majority vote wins.
```

---

## 4. Majority voting

In KNN classification, the final class is usually chosen by majority vote.

Example with K = 3:

```text
Neighbor 1: Black
Neighbor 2: Black
Neighbor 3: White
```

Result:

```text
Black
```

Because black appears 2 times and white appears 1 time.

---

## 5. Why changing K can change the answer

The value of K can affect the classification result.

Example:

```text
K = 1 → only the closest point matters
K = 3 → the three closest points matter
```

So a point may be classified as black when K = 1, but white when K = 3.

This is exactly the type of reasoning used in the exam.

---

## 6. Small K vs large K

### Small K

A small K, such as K = 1, is very sensitive to local points.

Advantage:

```text
It can capture detailed local patterns.
```

Disadvantage:

```text
It can be affected by noise or unusual points.
```

### Large K

A larger K looks at more neighbors.

Advantage:

```text
It is usually more stable.
```

Disadvantage:

```text
It may ignore small local patterns.
```

---

## 7. Distance

KNN needs a way to measure closeness.

The most common distance is Euclidean distance.

For two points:

```text
p = (p1, p2)
q = (q1, q2)
```

The Euclidean distance is:

```text
distance = sqrt((p1 - q1)^2 + (p2 - q2)^2)
```

In many exam questions, you may not need to calculate the exact distance.

You only need to visually identify the nearest points.

---

## 8. KNN and feature scale

KNN is very sensitive to feature scale.

Example:

```text
Feature 1: house price, maybe billions of tomans
Feature 2: number of rooms, maybe 1 to 5
```

If we use raw values, house price may dominate the distance calculation.

That is why normalization can be important.

Normalization puts features on a more comparable scale.

---

## 9. How to solve KNN exam questions

Use this method:

```text
1. Find the unknown point.
2. Identify the K closest labeled points.
3. Count the classes among those K points.
4. Choose the majority class.
5. Repeat separately for each value of K.
```

For example, if the question asks for K = 1 and K = 3, solve the problem twice.

Do not assume the answer will stay the same.

---

## 10. Common exam traps

### Trap 1: Forgetting to change K

Sometimes students solve for K = 1 and then use the same answer for K = 3.

This is wrong.

Each K must be checked separately.

### Trap 2: Looking at all points

KNN does not look at all points equally.

It only looks at the nearest K points.

### Trap 3: Ignoring majority vote

For K = 3, the closest single point may not decide the final answer.

The majority among the three nearest neighbors decides.

---

## 11. Quick self-check questions

### Question 1

In KNN, what does K represent?

Answer:

```text
The number of nearest neighbors used for prediction.
```

### Question 2

If K = 1, how is the class chosen?

Answer:

```text
The new point gets the class of its single closest neighbor.
```

### Question 3

If K = 3 and the nearest neighbors are black, white, and black, what is the predicted class?

Answer:

```text
Black
```

### Question 4

Why can KNN be affected by feature scale?

Answer:

```text
Because distance calculations can be dominated by features with larger numerical values.
```

### Question 5

Can changing K change the predicted class?

Answer:

```text
Yes. A point may receive different labels for different values of K.
```
