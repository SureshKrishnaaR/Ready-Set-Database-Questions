# **SCHEMA WITH TABLE DESCRIPTION**

**customers :**

**TABLE**

| customer_id | first_name | last_name | phone_number | email_address      | city        |
| ----------- | ---------- | --------- | ------------ | ------------------ | ----------- |
| 101         | Tony       | Stark     | 9022838221   | stark@gmail.com    | WASHINGTON  |
| 102         | Steve      | Rogers    | 9822102291   | rogers@gmail.com   | NEW YORK    |
| 103         | Black      | Widow     | 8291028119   | romanoff@gmail.com | CHICAGO     |
| 104         | Peter      | Parker    | 9217929222   | spider@gmail.com   | NEW YORK    |
| 105         | Banner     | Bruce     | 8291928221   | hulk@gmail.com     | HOUSTON     |
| 106         |            |           | 8291919191   | none@gmail.com     | LOS ANGELES |
| 107         | Strange    |           | 6271818181   | strange@gmail.com  | LOS ANGELES |

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
INSERT INTO customers values(102, "Steve", "Rogers", 9822102291, "rogers@gmail.com", "NEW YORK");
INSERT INTO customers values(103, "Black", "Widow", 8291028119, "romanoff@gmail.com", "CHICAGO");
INSERT INTO customers values(104, "Peter", "Parker", 9217929222, "spider@gmail.com", "NEW YORK");
INSERT INTO customers values(105, "Banner", "Bruce", 8291928221, "hulk@gmail.com", "HOUSTON");
INSERT INTO customers(customer_id, phone_number, email_address, city) values(106, 8291919191, "none@gmail.com", "LOS ANGELES");
INSERT INTO customers(customer_id, first_name, phone_number, email_address, city) values(107, "Strange", 6271818181, "strange@gmail.com", "LOS ANGELES");
```

**customerCards :**

**TABLE**

| card_id | card_number      | card_holder_name | expiry_date | customer_id |
| ------- | ---------------- | ---------------- | ----------- | ----------- |
| 201     | 3892918191331234 | Tony Stark       | 07/22       | 101         |
| 202     | 1838292191922919 | Black Widow      | 01/25       | 103         |
| 203     | 7281828292828228 | Bruce Banner     | 06/30       | 105         |

**TABLE DESCRIPTION**

| Field            | Type        | Null | Key | Default | Extra |
| ---------------- | ----------- | ---- | --- | ------- | ----- |
| card_id          | int         | NO   | PRI | NULL    |       |
| card_number      | bigint      | YES  |     | NULL    |       |
| card_holder_name | varchar(20) | YES  |     | NULL    |       |
| expiry_date      | varchar(10) | YES  |     | NULL    |       |
| customer_id      | int         | YES  | MUL | NULL    |       |

**INSERT QUERIES**

```sql
INSERT INTO customerCards values(201, 3892918191331234, "Tony Stark", "07/22", 101);
INSERT INTO customerCards values(202, 1838292191922919, "Black Widow", "01/25", 103);
INSERT INTO customerCards values(203, 7281828292828228, "Bruce Banner", "06/30", 105);
```

# **QUESTIONS**

### **QUESTION 1 - EASY**

From the customers table, find out the customers(display customer full name with the header as full_name - first name + last name seperated by space) who reside in CHENNAI and MUMBAI

### **QUESTION 2 - MEDIUM**

Change the expiry date as 06/25 for the customers whose first name starts with the letter B and is more than 5 characters in length

### **QUESTION 3 - EASY**

Delete the customers for whom both first name and last name are not present

### **QUESTION 4 - EASY**

Add a column called wifi_enabled of type boolean in the customercards table

### **QUESTION 5 - EASY**

Find out the number of customers from each city for all the cities except Houston(display city and customer count)
