# **SCHEMA WITH TABLE DESCRIPTION**

**orders :**

**TABLE**

| order_id | order_time_stamp    | total_cost | pay_on_delivery | order_status | show_to_user | customer_id |
| -------- | ------------------- | ---------- | --------------- | ------------ | ------------ | ----------- |
| 301      | 2021-09-29 12:00:00 | 15000      | true            | SUCCESSFUL   | 1            | 101         |
| 302      | 2021-09-30 12:00:00 | 40000      | false           | SUCCESSFUL   | 1            | 102         |
| 303      | 2021-10-01 12:00:00 | 17000      | true            | CANCELED     | 0            | 101         |
| 304      | 2021-04-30 12:00:00 | 50000      | true            | SUCCESSFUL   | 1            | 103         |
| 305      | 2021-06-30 12:00:00 | 30000      | false           | CANCELED     | 1            | 105         |
| 306      | 2021-09-28 12:00:00 | 30000      | false           | SUCCESSFUL   | 1            | 104         |

**TABLE DESCRIPTION**

| Field            | Type        | Null | Key | Default | Extra |
| ---------------- | ----------- | ---- | --- | ------- | ----- |
| order_id         | int         | NO   | PRI | NULL    |       |
| order_time_stamp | timestamp   | YES  |     | NULL    |       |
| total_cost       | int         | YES  |     | NULL    |       |
| pay_on_delivery  | varchar(5)  | YES  |     | NULL    |       |
| order_status     | varchar(15) | YES  |     | NULL    |       |
| show_to_user     | bit(1)      | YES  |     | NULL    |       |
| customer_id      | int         | YES  |     | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO orders values(301, '2021-09-29 12:00:00', 15000, 'true', 'SUCCESSFUL', 1, 101);
INSERT INTO orders values(302, '2021-09-30 12:00:00', 40000, 'false', 'SUCCESSFUL', 1, 102);
INSERT INTO orders values(303, '2021-10-01 12:00:00', 17000, 'true', 'CANCELED', 0, 101);
INSERT INTO orders values(304, '2021-04-30 12:00:00', 50000, 'true', 'SUCCESSFUL', 1, 103);
INSERT INTO orders values(305, '2021-06-30 12:00:00', 30000, 'false', 'CANCELED', 1, 105);
INSERT INTO orders values(306, '2021-09-28 12:00:00', 30000, 'false', 'SUCCESSFUL', 1, 104);
```

**orderedProducts :**

**TABLE**

| product_id | order_id | quantity |
| ---------- | -------- | -------- |
| 401        | 301      | 3        |
| 401        | 302      | 2        |
| 402        | 302      | 6        |
| 403        | 301      | 15       |
| 404        | 303      | 1        |
| 404        | 304      | 8        |
| 405        | 301      | 10       |

**TABLE DESCRIPTION**

| Field      | Type | Null | Key | Default | Extra |
| ---------- | ---- | ---- | --- | ------- | ----- |
| product_id | int  | NO   | PRI | NULL    |       |
| order_id   | int  | NO   | PRI | NULL    |       |
| quantity   | int  | YES  |     | 0       |       |

**INSERT QUERIES**

```sql
INSERT INTO orderedProducts values(401, 301, 3);
INSERT INTO orderedProducts values(405, 301, 10);
INSERT INTO orderedProducts values(403, 301, 15);
INSERT INTO orderedProducts values(401, 302, 2);
INSERT INTO orderedProducts values(404, 303, 1);
INSERT INTO orderedProducts values(402, 302, 6);
INSERT INTO orderedProducts values(404, 304, 8);
```

# **QUESTIONS**

### **QUESTION 1**

Display all the details in orders table in the descending order of total_cost, if two orders have the same total_cost then sort them in the ascending order of order_time_stamp

### **QUESTION 2**

Change the total cost as zero for the customers who have canceled the order or have already paid for it(the one who doesn't pay on delivery)

### **QUESTION 3**

Delete the products from orderedProducts table for the orders which are canceled

### **QUESTION 4**

Set default value for quantity as 0 in the ordered products table

### **QUESTION 5**

Find the total number of items purchased with the order id in each order
