# **SCHEMA WITH TABLE DESCRIPTION**

**products :**

**TABLE**

| product_id | product_name | product_price | availability | rating | weight | category    |
| ---------- | ------------ | ------------- | ------------ | ------ | ------ | ----------- |
| 401        | Cake         | 350           | 3            |        | 3.5    | FOOD        |
| 402        | Laptop       | 60000         | 2            | 5      | 2      | ELECTRONICS |
| 403        | Icecream     | 200           | 10           | 5      | 1      | FOOD        |
| 404        | Shampoo      | 250           | 20           | 3      | 1.5    | COSMETICS   |
| 405        | Cellphone    | 20000         | 5            |        | 1      | ELECTRONICS |
| 406        | Cherry       | 150           | 6            | 2      | 1      | FOOD        |
| 407        | Jeans        | 890           | 10           |        | 2.1    | CLOTHING    |

**TABLE DESCRIPTION**

| Field         | Type        | Null | Key | Default | Extra |
| ------------- | ----------- | ---- | --- | ------- | ----- |
| product_id    | int         | NO   | PRI | NULL    |       |
| product_name  | varchar(15) | YES  |     | NULL    |       |
| product_price | int         | YES  |     | NULL    |       |
| availability  | int         | YES  |     | NULL    |       |
| rating        | int         | YES  |     | NULL    |       |
| weight        | float       | YES  |     | NULL    |       |
| category      | varchar(15) | YES  |     | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO products(product_id, product_name, product_price, availability, weight, category) values(401, "Cake", 350, 3, 3.5, "FOOD");
INSERT INTO products values(402, "Laptop", 60000, 2, 5, 2, "ELECTRONICS");
INSERT INTO products values(403, "Icecream", 200, 10, 5, 1, "FOOD");
INSERT INTO products values(404, "Shampoo", 250, 20, 3, 1.5, "COSMETICS");
INSERT INTO products(product_id, product_name, product_price, availability, weight, category) values(405, "Cellphone", 20000, 5, 1, "ELECTRONICS");
INSERT INTO products values(406, "Cherry", 150, 6, 2, 1, "FOOD");
INSERT INTO products(product_id, product_name, product_price, availability, weight, category) values(407, "Jeans", 890, 10, 2.1, "CLOTHING");
```

**rateProduct :**

**TABLE**

| review_id | product_id | customer_id | customer_rating | customer_review |
| --------- | ---------- | ----------- | --------------- | --------------- |
| 601       | 406        | 101         | 4               | Good            |
| 602       | 406        | 102         | 2               | Okay            |
| 603       | 402        | 102         | 5               | Excellent       |
| 604       | 403        | 103         | 5               | Great           |
| 605       | 405        | 103         | 3               | Good            |
| 606       | 405        | 101         | 5               | Great           |
| 607       | 405        | 102         | 1               | Worst           |

**TABLE DESCRIPTION**

| Field           | Type        | Null | Key | Default | Extra |
| --------------- | ----------- | ---- | --- | ------- | ----- |
| review_id       | int         | NO   | PRI | NULL    |       |
| product_id      | int         | YES  | MUL | NULL    |       |
| customer_id     | int         | YES  |     | NULL    |       |
| customer_rating | int         | YES  |     | NULL    |       |
| customer_review | varchar(20) | YES  |     | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO rateProduct values(601, 406, 101, 4, "Good");
INSERT INTO rateProduct values(602, 406, 102, 2, "Okay");
INSERT INTO rateProduct values(603, 402, 102, 5, "Excellent");
INSERT INTO rateProduct values(604, 403, 103, 5, "Great");
INSERT INTO rateProduct values(605, 405, 103, 3, "Good");
INSERT INTO rateProduct values(606, 405, 101, 5, "Great");
INSERT INTO rateProduct values(607, 405, 102, 1, "Worst");
```

# **QUESTIONS**

### **QUESTION 1**

Display product name, price and availability for products which have price greater than 1000 and product id not equal to 401 and rating is not null;

### **QUESTION 2**

Increment the price of for the products by 1000 for the products which are available and have a minimum rating of 3

### **QUESTION 3**

Remove the customer reviews for the products where product id is not equal to 401 or the product lies in the category of food or clothing

### **QUESTION 4**

Remove column customer review from the table rateproduct

### **QUESTION 5**

Display the average rating with the customer id for each customer in the descending order of the average rating
