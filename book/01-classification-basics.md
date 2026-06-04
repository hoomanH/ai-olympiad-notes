# Chapter 1 — Classification Basics

## 1. What is classification?

Classification is a machine learning task where the model receives an input and assigns it to one of several possible categories.

For example:

| Input                   | Possible output             |
| ----------------------- | --------------------------- |
| Image of a lung CT scan | Sick / Healthy              |
| House information       | Sold / Not sold             |
| Movie information       | Comedy / Action / Drama     |
| Student behavior data   | Group 1 / Group 2 / Group 3 |

In classification, the answer is usually a **class label**.

Examples of labels:

```text
Positive / Negative
Black / White
Spam / Not spam
Sick / Healthy
Class 1 / Class 2 / Class 3
```

---

## 2. Features and labels

A machine learning model learns from data.

Each data point usually has:

1. **Features**
2. **Label**

Features are the input information.

Label is the correct answer.

Example:

| House price     | Area  | City? | Label    |
| --------------- | ----- | ----- | -------- |
| 5 billion toman | 80 m² | 1     | Sold     |
| 2 billion toman | 60 m² | 0     | Not sold |

Here:

```text
Features: price, area, city/rural status
Label: sold or not sold
```

The model tries to learn a rule that maps features to labels.

---

## 3. Binary classification

Binary classification means there are only two possible classes.

Examples:

```text
Cancer / No cancer
Sold / Not sold
Spam / Not spam
Positive / Negative
```

A binary classifier often outputs a probability.

Example:

```text
p = 0.83
```

This may mean:

```text
The model thinks there is an 83% chance that the input belongs to the positive class.
```

Then we choose a threshold.

For example, if the threshold is 0.5:

```text
If p >= 0.5 → Positive
If p < 0.5 → Negative
```

---

## 4. Multi-class classification

Multi-class classification means there are more than two possible classes, but each input belongs to only one class.

Example:

```text
Classifying an image as:
Cat / Dog / Bird / Fish
```

Only one answer is correct.

In AI Olympiad-style questions, this can appear as:

```text
A 5-class classification problem
```

If we are only allowed to use binary classifiers, we may need to combine several binary classifiers.

Two common strategies are:

### One-vs-rest

For each class, train one classifier that separates that class from all other classes.

For 5 classes:

```text
Classifier 1: Class 1 vs others
Classifier 2: Class 2 vs others
Classifier 3: Class 3 vs others
Classifier 4: Class 4 vs others
Classifier 5: Class 5 vs others
```

This usually needs 5 binary classifiers.

### One-vs-one

Train one binary classifier for each pair of classes.

For 5 classes, the number of pairs is:

```text
5 × 4 / 2 = 10
```

So one-vs-one needs 10 binary classifiers.

---

## 5. Multi-label classification

Multi-label classification is different from multi-class classification.

In multi-label classification, one input can have several labels at the same time.

Example:

```text
A movie can be:
Comedy + Action + Adventure
```

So the output is not just one class.

For K possible labels, we can represent the answer with a vector of zeros and ones.

Example with 5 genres:

```text
[1, 0, 1, 0, 1]
```

This means the movie has labels 1, 3, and 5.

Important idea:

```text
Multi-class: exactly one class is correct.
Multi-label: several labels can be correct at the same time.
```

This difference is very important when choosing between **softmax** and **sigmoid**.

---

## 6. Decision boundary

A decision boundary is the border that separates classes.

For example, in a two-dimensional space with features x1 and x2, a classifier may separate the data using a line.

One side of the line is class A.

The other side is class B.

Example:

```text
w1x1 + w2x2 + b = 0
```

This equation represents a line in two dimensions.

The classifier can work like this:

```text
If w1x1 + w2x2 + b >= 0 → Positive
If w1x1 + w2x2 + b < 0 → Negative
```

---

## 7. Linear classifier

A linear classifier separates data using a line, plane, or hyperplane.

In two dimensions, it uses a line.

In three dimensions, it uses a plane.

In higher dimensions, it uses a hyperplane.

The general form is:

```text
w1x1 + w2x2 + ... + wnxn + b = 0
```

Where:

```text
x1, x2, ..., xn = features
w1, w2, ..., wn = weights
b = bias
```

The weights decide how important each feature is.

The bias shifts the decision boundary.

---

## 8. Linearly separable data

Data is linearly separable if we can separate the classes perfectly using a linear boundary.

In two dimensions, this means one line can separate the classes.

Example:

```text
All positive points are on one side.
All negative points are on the other side.
```

If no single line can separate the classes perfectly, the data is not linearly separable.

---

## 9. Why this matters for the exam

The uploaded exam contains several questions where you must understand:

```text
What classification is
What features and labels are
How binary and multi-class classification differ
What a linear classifier is
What linearly separable means
How to use binary classifiers for multi-class problems
Why multi-label classification is different from multi-class classification
```

These ideas are the foundation for later chapters:

```text
KNN
Decision trees
Logistic regression
Softmax
Cross-entropy
ROC and AUC
Neural networks
```

---

## 10. Quick self-check questions

### Question 1

A model predicts whether an email is spam or not spam.

What type of classification is this?

Answer:

```text
Binary classification
```

### Question 2

A model predicts whether an image is a cat, dog, bird, or fish.

What type of classification is this?

Answer:

```text
Multi-class classification
```

### Question 3

A movie can be action, comedy, and adventure at the same time.

What type of classification is this?

Answer:

```text
Multi-label classification
```

### Question 4

What is a decision boundary?

Answer:

```text
A border that separates different classes.
```

### Question 5

What does linearly separable mean?

Answer:

```text
The classes can be separated perfectly using a line, plane, or hyperplane.
```
