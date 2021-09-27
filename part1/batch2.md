# **SCHEMA WITH TABLE DESCRIPTION**

**customers :**

**TABLE**

| customer_id | first_name | last_name | phone_number | email_address      | city       |
| ----------- | ---------- | --------- | ------------ | ------------------ | ---------- |
| 101         | Tony       | Stark     | 9022838221   | stark@gmail.com    | WASHINGTON |
| 102         | Steve      | Rogers    | 9822102291   |                    | NEW YORK   |
| 103         | Black      | Widow     |              | romanoff@gmail.com | CHICAGO    |
| 104         | Peter      | Parker    | 9217929222   | spider@gmail.com   | NEW YORK   |
| 105         | Banner     | Bruce     | 8291928221   |                    |            |

**TABLE DESCRIPTION**

| Field         | Type        | Null | Key | Default | Extra |
| ------------- | ----------- | ---- | --- | ------- | ----- |
| customer_id   | int         | NO   | PRI | NULL    |       |
| first_name    | varchar(15) | YES  |     | NULL    |       |
| last_name     | varchar(15) | YES  |     | NULL    |       |
| phone_number  | bigint      | YES  |     | NULL    |       |
| email_address | varchar(20) | YES  |     | NULL    |       |
| city          | varchar(30) | YES  |     | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO customers values(101, "Tony", "Stark", 9022838221, "stark@gmail.com", "WASHINGTON");
INSERT INTO customers(customer_id, first_name, last_name, phone_number, city) values(102, "Steve", "Rogers", 9822102291, "NEW YORK");
INSERT INTO customers(customer_id, first_name, last_name, email_address, city) values(103, "Black", "Widow", "romanoff@gmail.com", "CHICAGO");
INSERT INTO customers values(104, "Peter", "Parker", 9217929222, "spider@gmail.com", "NEW YORK");
INSERT INTO customers(customer_id, first_name, last_name, phone_number) values(105, "Banner", "Bruce", 8291928221);
```

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
| customer_id      | int         | YES  | MUL | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO orders values(301, '2021-09-29 12:00:00', 15000, 'true', 'SUCCESSFUL', 1, 101);
INSERT INTO orders values(302, '2021-09-30 12:00:00', 40000, 'false', 'SUCCESSFUL', 1, 102);
INSERT INTO orders values(303, '2021-10-01 12:00:00', 17000, 'true', 'CANCELED', 0, 101);
INSERT INTO orders values(304, '2021-04-30 12:00:00', 50000, 'true', 'SUCCESSFUL', 1, 103);
INSERT INTO orders values(305, '2021-06-30 12:00:00', 30000, 'false', 'CANCELED', 1, 105);
INSERT INTO orders values(306, '2021-09-28 12:00:00', 30000, 'false', 'SUCCESSFUL', 1, 104);
```

# **QUESTIONS**

### **QUESTION 1**

Find out the number of customers who have given details about both phone number and city but not email address

### **QUESTION 2**

Change the city as washington and phone number as 9281825621 for the user with customer id is 105

### **QUESTION 3**

Delete the orders which are placed before 2 months

### **QUESTION 4**

Change the show_to_user column in the orders table to type varchar with length 5

### **QUESTION 5**

Find out the customer id and maximum total cost of order placed by the customers in each city
