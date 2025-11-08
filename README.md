# MarketBasedAnalysis

## 🧺 Market Basket Analysis with Apriori Algorithm

This project demonstrates Market Basket Analysis using the Apriori Algorithm to find frequently purchased itemsets and generate association rules for cross-selling opportunities in retail.

## 📌 Overview

Market Basket Analysis is a data mining technique used by retailers to understand customer purchasing behavior. By analyzing transaction data, we can identify which items are frequently bought together. This insight helps businesses to:

Suggest complementary products to customers (cross-selling)

Optimize product placement in stores

Design promotions, bundles, or discounts

Increase revenue by targeting potential buyers for related products

### Example:

If a customer buys bread, they are likely to buy butter.

If a customer buys diaper, they might also buy beer.

These insights allow businesses to recommend additional products, either at checkout, via email, or through in-store promotions.

## ⚙️ Features

Transaction Encoding
Converts a list of transactions into a True/False matrix using TransactionEncoder from mlxtend.

Frequent Itemset Mining
Uses the Apriori algorithm to find itemsets that appear in at least a specified fraction of transactions (min_support).

Association Rule Generation
Generates rules of the form X → Y, meaning if a customer buys X, they are likely to buy Y. Rules are filtered by confidence and lift.

Top Recommendations
Sorts association rules to show the strongest cross-selling opportunities.

## 🛠️ Libraries Used

pandas – for data manipulation

mlxtend.preprocessing.TransactionEncoder – for transaction encoding

mlxtend.frequent_patterns.apriori – for frequent itemset mining

mlxtend.frequent_patterns.association_rules – for generating association rules

## 📝 Example Dataset
```python
dataset = [
    ['milk', 'bread', 'butter'],
    ['bread', 'diaper', 'beer', 'eggs'],
    ['milk', 'diaper', 'beer', 'cola'],
    ['bread', 'milk', 'diaper', 'beer'],
    ['bread', 'milk', 'diaper', 'cola']
]
```

## 💡 How It Works

### 1. Encode transactions into a True/False matrix:
```python
    beer  bread  butter   cola  diaper   eggs   milk
0  False   True    True  False   False  False   True
1   True   True   False  False    True   True  False
2   True  False   False   True    True  False   True
3   True   True   False  False    True  False   True
4  False   True   False   True    True  False   True
```

### 2. Generate frequent itemsets:
```python
support               itemsets
0       0.6                 (beer)
1       0.8                (bread)
2       0.4                 (cola)
3       0.8               (diaper)
4       0.8                 (milk)
5       0.4          (bread, beer)
6       0.6         (diaper, beer)
7       0.4           (milk, beer)
8       0.6        (diaper, bread)
9       0.6          (milk, bread)
10      0.4         (diaper, cola)
11      0.4           (milk, cola)
12      0.6         (diaper, milk)
13      0.4  (diaper, bread, beer)
14      0.4   (diaper, milk, beer)
15      0.4  (diaper, bread, milk)
16      0.4   (diaper, cola, milk)
```

### 3. Generate association rules:
```python
antecedents      consequents  support  confidence      lift
0          (diaper)           (beer)      0.6    0.750000  1.250000
1            (beer)         (diaper)      0.6    1.000000  1.250000
2          (diaper)           (cola)      0.4    0.500000  1.250000
3            (cola)         (diaper)      0.4    1.000000  1.250000
4            (milk)           (cola)      0.4    0.500000  1.250000
5            (cola)           (milk)      0.4    1.000000  1.250000
6   (diaper, bread)           (beer)      0.4    0.666667  1.111111
7     (bread, beer)         (diaper)      0.4    1.000000  1.250000
8          (diaper)    (bread, beer)      0.4    0.500000  1.250000
9            (beer)  (diaper, bread)      0.4    0.666667  1.111111
10   (diaper, milk)           (beer)      0.4    0.666667  1.111111
11     (milk, beer)         (diaper)      0.4    1.000000  1.250000
12         (diaper)     (milk, beer)      0.4    0.500000  1.250000
13           (beer)   (diaper, milk)      0.4    0.666667  1.111111
14   (diaper, cola)           (milk)      0.4    1.000000  1.250000
15   (diaper, milk)           (cola)      0.4    0.666667  1.666667
16     (milk, cola)         (diaper)      0.4    1.000000  1.250000
17         (diaper)     (milk, cola)      0.4    0.500000  1.250000
18           (cola)   (diaper, milk)      0.4    1.000000  1.666667
19           (milk)   (diaper, cola)      0.4    0.500000  1.250000
```

## 🏪 Use in Cross-Selling Strategy

Market Basket Analysis directly supports cross-selling:

Example 1: If a customer buys milk and bread, recommend butter.

Example 2: Group items often bought together into promotional bundles (e.g., cola + chips for snack promotions).

By targeting products customers are likely to buy together, businesses can increase average order value and enhance customer satisfaction.

## 📈 Practical Business Benefits

E-commerce & Retail: Personalized product recommendations at checkout.

Supermarkets: Optimized shelf placement for frequently bought-together items.

Promotional Offers: Design bundle offers that maximize sales.

Inventory Management: Stock complementary items together to reduce stockouts.

## 🏃 How to Run

1. Clone the repository

2. Open market_basket_analysis.py in VS Code or Jupyter Notebook

3. Run the script

4. Check the output:

- Encoded transactions

- Frequent itemsets

- Association rules

- Top cross-selling recommendations

## 🔗 References

mlxtend documentation

Apriori algorithm on Wikipedia
