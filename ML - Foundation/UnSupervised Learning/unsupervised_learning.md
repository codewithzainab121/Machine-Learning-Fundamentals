# 📁 unsupervised_learning.md

## Introduction

“Unsupervised” = no labels (no answers given).

We have the data, but we do not predict anything directly.

Instead, the model tries to:

* find patterns
* group similar items
* detect hidden structures
* spot outliers

Common unsupervised learning tasks:

* Clustering
* Association Rule Mining
* Anomaly Detection

One of the most popular unsupervised learning techniques is clustering.

---

# 🔹 K-Means Clustering

## What is K-Means Clustering?

K-Means is an unsupervised learning algorithm that groups data into clusters based on similarity.

Think of it like:
👉 “Put similar things together.”

Example:
Customers with similar buying behavior can be grouped into the same cluster.

K-Means works through an iterative process of assigning and updating clusters.

---

## How K-Means Works

### Step 1: Choose K

You decide how many clusters you want.

Example:
K = 3

---

### Step 2: Random Centroids

The algorithm randomly picks K points called centroids.

Think:
📍 center of each cluster

---

### Step 3: Assign Points

Each data point goes to the nearest centroid.

Distance is usually calculated using Euclidean Distance.

---

### Step 4: Update Centroids

New centroid = average of all points in that cluster.

---

### Step 5: Repeat

Steps 3 and 4 repeat until centroids stop moving.

That means clusters are finalized.

To assign points to the nearest centroid, K-Means uses distance calculations.

---

## Distance Formula (Euclidean Distance)

genui{"math_block_widget_always_prefetch_v2":{"content":"d = \sqrt{(x_2-x_1)^2 + (y_2-y_1)^2}"}}

This measures distance between two points.

---

## Feature Scaling in K-Means

K-Means is distance-based.

If one feature dominates because of larger values,
clustering can become incorrect.

Example:

* Salary values = huge numbers
* Age values = small numbers

Salary may dominate clustering.

That’s why feature scaling is important.

Common scaling methods:

* StandardScaler
* MinMaxScaler

Because distance-based algorithms are sensitive to feature scales, normalization or standardization is important.

---

## Inertia

Inertia measures how tightly clusters are packed.

It is:
👉 the sum of squared distances between points and their cluster centroid.

### Good Clustering

Points are close to centroid
→ tight cluster
→ low inertia ✅

### Bad Clustering

Points are spread out
→ messy cluster
→ high inertia ❌

🔥 Important:
Lower inertia usually means better clustering.

BUT:

If K increases:

* inertia always decreases

Because:
more clusters = points closer to centroids

So lower inertia alone does not guarantee the best number of clusters.

That’s why we use the Elbow Method.

---

## Elbow Method

The Elbow Method helps choose the best value of K.

We plot:

* X-axis → number of clusters (K)
* Y-axis → inertia

We look for:
👉 the “bend” in the graph

That bend = optimal K

Example:

| K | Inertia |
| - | ------- |
| 1 | 10      |
| 2 | 1.8     |
| 3 | 1.2     |
| 4 | 1.0     |

K = 2 may be best because inertia drops sharply before slowing down.

Another way to evaluate clustering quality is by measuring how well-separated the clusters are.

---

## Silhouette Score

Silhouette Score measures:
How similar a point is to its own cluster compared to other clusters.

Range:

* +1 → excellent clustering
* 0 → overlapping clusters
* -1 → poor clustering

For each point:

* a = distance to its own cluster
* b = distance to nearest other cluster

Formula:

\frac{b-a}{\max(a,b)}

If:

* a ≪ b → score near 1 ✅
* a ≈ b → score near 0
* a > b → negative score ❌

---

## Cluster Labels

When clustering is complete,
each data point gets a cluster label.

Example output:

```python
[0, 0, 1, 2, 1, 0]
```

Meaning:
👉 which cluster each point belongs to.

---

# 🔹 Apriori Algorithm

## What is Apriori Algorithm?

The Apriori Algorithm is used to find patterns or relationships between items.

👉 In simple words:
“What things usually occur together?”

This is commonly used in:

* Market Basket Analysis
* Recommendation systems

Example:

* People who buy bread also buy butter
* People who buy milk also buy cereal

Apriori works by identifying frequent item combinations and generating association rules.

---

## Core Idea of Apriori

Apriori is based on one important rule:

If an itemset is frequent,
then all of its subsets must also be frequent.

Example:
If:
{bread, butter} is frequent

Then:
{bread} and {butter} must also be frequent.

---

## How Apriori Works

### Step 1: Set Minimum Support

Choose minimum support threshold.

This decides:
“How frequently an item should appear.”

---

### Step 2: Find Frequent Single Items

Find items that appear frequently.

Example:

* bread
* milk

---

### Step 3: Combine Items

Create combinations:

* bread + butter
* milk + cereal

---

### Step 4: Remove Weak Combinations

Remove combinations below support threshold.

---

### Step 5: Generate Association Rules

Generate rules using:

* support
* confidence
* lift

---

# 🔹 Key Metrics in Apriori

## Support

Support measures:
How often an item appears in the dataset.

Formula idea:
support(item) =
(item frequency) / (total transactions)

---

## Confidence

Confidence measures:
How reliable the relationship is.

Example:
If someone buys bread,
how often do they also buy butter?

Higher confidence
→ stronger rule.

---

## Lift

Lift measures:
Strength of relationship between items.

* Lift > 1 → strong association
* Lift = 1 → no special relationship
* Lift < 1 → weak relationship

---

## Why Apriori is Useful

Apriori helps businesses:

* increase sales
* bundle products
* recommend items
* design store layouts

Used in:

* e-commerce
* supermarkets
* recommendation systems

---

## Drawback of Apriori

Apriori can become slow on large datasets because:
👉 it creates too many combinations.

That’s why faster alternatives exist.

Example:

* FP-Growth algorithm 🚀
