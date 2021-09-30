# **SCHEMA WITH TABLE DESCRIPTION**

**products :**

**TABLE**

| product_id | product_name | product_price | availability | rating | weight | category    |
| ---------- | ------------ | ------------- | ------------ | ------ | ------ | ----------- |
| 401        | Cake         | 350           | 3            |        | 3.5    | FOOD        |
| 402        | Laptop       | 56000         | 2            | 5      | 2      | ELECTRONICS |
| 403        | Icecream     | 200           | 10           | 5      | 1      | FOOD        |
| 404        | Shampoo      | 250           | 20           |        | 1.5    | COSMETICS   |
| 405        | Cellphone    | 20000         | 5            | 4      | 1      | ELECTRONICS |
| 406        | Cherry       | 150           | 6            | 2      | 1      | FOOD        |
| 407        | Jeans        | 890           | 10           | 3      | 2.1    | CLOTHING    |

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
INSERT INTO products values(402, "Laptop", 56000, 2, 5, 2, "ELECTRONICS");
INSERT INTO products values(403, "Icecream", 200, 10, 5, 1, "FOOD");
INSERT INTO products(product_id, product_name, product_price, availability, weight, category) values(404, "Shampoo", 250, 20, 1.5, "COSMETICS");
INSERT INTO products values(405, "Cellphone", 20000, 5, 4, 1, "ELECTRONICS");
INSERT INTO products values(406, "Cherry", 150, 6, 2, 1, "FOOD");
INSERT INTO products values(407, "Jeans", 890, 10, 3, 2.1, "CLOTHING");
```

**productOffers :**

**TABLE**

| offer_id | product_id |
| -------- | ---------- |
| 502      | 401        |
| 501      | 402        |
| 502      | 405        |
| 503      | 405        |

**TABLE DESCRIPTION**

| Field      | Type | Null | Key | Default | Extra |
| ---------- | ---- | ---- | --- | ------- | ----- |
| offer_id   | int  | NO   | PRI | NULL    |       |
| product_id | int  | NO   | PRI | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO productOffers values(501, 402);
INSERT INTO productOffers values(502, 401);
INSERT INTO productOffers values(503, 405);
INSERT INTO productOffers values(502, 405);
```

# **QUESTIONS**

### **QUESTION 1 - MEDIUM**

Display the products(all product details) for which an offer is available

### **QUESTION 2 - EASY**

Increase the product price by 2000 for the products in which the name starts with C and ends with e and rating is not null

### **QUESTION 3 - EASY**

Remove the products in the price range of 100 and 300(both including) and with the maximum rating of 3

### **QUESTION 4 - EASY**

Rename the weight column of the products table to product_weight

### **QUESTION 5 - EASY**

Maximum rating of each category for categories which has it's 3rd letter as 'O'
