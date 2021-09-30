# Tables

## BankCustomer

| CUSTOMER_ID | USER_ID | USER_NAME       | USER_PASSWORD | MOBILE_NUMBER | RATE_LIMIT | FIRST_NAME | LAST_NAME | EMAIL                   | ADDRESS                                                             |
| ----------- | ------- | --------------- | ------------- | ------------- | ---------- | ---------- | --------- | ----------------------- | ------------------------------------------------------------------- |
| 1           | 6       | Vishwajith      | vishwa1234    | 9087269921    | 100        | Vishwajith | V         | vishwajith567@gmail.com | Plot no 24 Ramalinga 1st StrretShanthi nekethan colony Thoraipakkam |
| 2           | 7       | Suresh Krishnaa | suresh1234    | 9940419139    | 120        | Suresh     | Krishnaa  | shyrams1346@gmail.com   | 4/20 YADAVAL STREET KADAPERI WEST TAMBARAM                          |
|             |

## BankAccount

| ACCOUNT_NUMBER  | CUSTOMER_ID | BRANCH_NAME | ACCOUNT_TYPE              | BALANCE | IS_TERMINATED |
| --------------- | ----------- | ----------- | ------------------------- | ------- | ------------- |
| SBICHNI23645792 | 1           | CHENNAI     | CURRENT_ACCOUNT           | 3300    | 0             |
| SBICHNI24617266 | 1           | CHENNAI     | FIXED_DEPOSIT_ACCOUNT     | 40000   | 0             |
| SBICHNI86978722 | 2           | CHROMPET    | HOME_LOAN_ACCOUNT         | 300000  | 0             |
| SBICHNI86978723 | 2           | CHENNAI     | EDUCATION_LOAN_ACCOUNT    | 120000  | 0             |
| SBICHNI86978756 | 1           | CHENNAI     | SAVINGS_ACCOUNT           | 3000    | 0             |
| SBICMPT16818246 | 1           | CHROMPET    | RECURRING_DEPOSIT_ACCOUNT | 0       | 0             |

## DebitCard

| CARD_NUMBER | ACCOUNT_NUMBER  | CARD_TYPE                  | PIN  | VALID_TILL | IS_ACTIVE | IS_BLOCKED |
| ----------- | --------------- | -------------------------- | ---- | ---------- | --------- | ---------- |
| 26352349    | SBICHNI23645792 | SBI_PLATINUM_INTERNATIONAL | 1285 | 2021-04-30 | 1         | 0          |
| 26352739    | SBICHNI86978756 | SBI_GLOBAL_INTERNATIONAL   | 4389 | 2021-08-23 | 1         | 0          |

# Description

## BankCustomer

| Field         | Type         | Null | Key | Default | Extra |
| ------------- | ------------ | ---- | --- | ------- | ----- |
| CUSTOMER_ID   | bigint(19)   | NO   | PRI | NULL    |       |
| USER_ID       | bigint(19)   | NO   | UNI | NULL    |       |
| USER_NAME     | varchar(40)  | NO   | UNI | NULL    |       |
| USER_PASSWORD | text         | NO   |     | NULL    |       |
| MOBILE_NUMBER | bigint(19)   | NO   | UNI | NULL    |       |
| RATE_LIMIT    | int(10)      | NO   |     | 100     |       |
| FIRST_NAME    | varchar(40)  | YES  |     | NULL    |       |
| LAST_NAME     | varchar(40)  | YES  |     | NULL    |       |
| EMAIL         | varchar(40)  | YES  | UNI | NULL    |       |
| ADDRESS       | varchar(150) | YES  |     | NULL    |       |

## BankAccount

| Field          | Type        | Null | Key | Default | Extra |
| -------------- | ----------- | ---- | --- | ------- | ----- |
| ACCOUNT_NUMBER | varchar(40) | NO   | PRI | NULL    |       |
| CUSTOMER_ID    | bigint(19)  | NO   | MUL | NULL    |       |
| BRANCH_NAME    | varchar(40) | NO   |     | NULL    |       |
| ACCOUNT_TYPE   | varchar(40) | NO   |     | NULL    |       |
| BALANCE        | double      | NO   |     | NULL    |       |
| IS_TERMINATED  | tinyint(1)  | YES  |     | 0       |       |

## DebitCard

| Field          | Type        | Null | Key | Default | Extra |
| -------------- | ----------- | ---- | --- | ------- | ----- |
| CARD_NUMBER    | bigint(19)  | NO   | PRI | NULL    |       |
| ACCOUNT_NUMBER | varchar(40) | NO   | MUL | NULL    |       |
| CARD_TYPE      | varchar(40) | NO   |     | NULL    |       |
| PIN            | int(10)     | NO   |     | NULL    |       |
| VALID_TILL     | date        | NO   |     | NULL    |       |
| IS_ACTIVE      | tinyint(1)  | YES  |     | 1       |       |
| IS_BLOCKED     | tinyint(1)  | YES  |     | 1       |       |

# Creation

## BankCustomer

```sql
create table BankCustomer (CUSTOMER_ID INT PRIMARY KEY, USER_ID INT NOT NULL UNIQUE, USER_NAME VARCHAR(40) UNIQUE NOT NULL, USER_PASSWORD VARCHAR(300), MOBILE_NUMBER BIGINT UNIQUE NOT NULL,  RATE_LIMIT INT NOT NULL DEFAULT 100, FIRST_NAME VARCHAR(40), LAST_NAME VARCHAR(40), EMAIL VARCHAR(40) UNIQUE NOT NULL, ADDRESS VARCHAR(150));
```

## BankAccount

```sql
create table BankAccount (ACCOUNT_NUMBER VARCHAR(40) PRIMARY KEY, CUSTOMER_ID INT, BRANCH_NAME VARCHAR(40), ACCOUNT_TYPE VARCHAR(40), BALANCE DOUBLE, IS_TERMINATED BIT(1) DEFAULT false, CONSTRAINT fk_account FOREIGN KEY (CUSTOMER_ID) REFERENCES BankCustomer(CUSTOMER_ID) ON DELETE SET NULL);
```

## DebitCard

```sql
create table DebitCard (CARD_NUMBER BIGINT PRIMARY KEY, ACCOUNT_NUMBER VARCHAR(40), CARD_TYPE,VARCHAR(40) NOT NULL, PIN INT, VALID_TILL DATE, IS_ACTIVE BIT(1), IS_BLOCKED BIT(1), CONSTRAINT fk_debit_card FOREIGN KEY (ACCOUNT_NUMBER) REFERENCES BankAccount(ACCOUNT_NUMBER));
```

# Insertion

## BankCustomer

```sql
insert into BankCustomer (CUSTOMER_ID, USER_ID, USER_NAME, USER_PASSWORD, MOBILE_NUMBER, RATE_LIMIT, FIRST_NAME, LAST_NAME, EMAIL, ADDRESS) values(1, 6, 'Vishwajith', 'vishwa1234', 9087269921, 100, 'Vishwajith', 'V', 'vishwajith567@gmail.com', 'Plot no 24 Ramalinga 1st StrretShanthi nekethan colony Thoraipakkam');
insert into BankCustomer (CUSTOMER_ID, USER_ID, USER_NAME, USER_PASSWORD, MOBILE_NUMBER, RATE_LIMIT, FIRST_NAME, LAST_NAME, EMAIL, ADDRESS) values(2, 7, 'Suresh Krishnaa', 'suresh1234', 9940419139, 120, 'Suresh', 'Krishnaa', 'shyrams1346@gmail.com', '4/20 YADAVAL STREET KADAPERI WEST TAMBARAM');
```

## BankAccount

```sql
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI23645792', 1, 'CHENNAI', 'CURRENT_ACCOUNT', 3300, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI24617266', 1, 'CHENNAI', 'FIXED_DEPOSIT_ACCOUNT', 40000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978722', 2, 'CHROMPET', 'HOME_LOAN_ACCOUNT', 300000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978723', 2, 'CHENNAI', 'EDUCATION_LOAN_ACCOUNT', 120000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978756' , 1, 'CHENNAI', 'SAVINGS_ACCOUNT', 3000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICMPT16818246', 1, 'CHROMPET', 'RECURRING_DEPOSIT_ACCOUNT', 0, 0);
```

## DebitCard

```sql
insert into DebitCard (CARD_NUMBER, ACCOUNT_NUMBER, CARD_TYPE, PIN, VALID_TILL, IS_ACTIVE, IS_BLOCKED) values(26352349, 'SBICHNI23645792', 'SBI_PLATINUM_INTERNATIONAL', 1285, '2021-04-30', 1, 0);
insert into DebitCard (CARD_NUMBER, ACCOUNT_NUMBER, CARD_TYPE, PIN, VALID_TILL, IS_ACTIVE, IS_BLOCKED) values( 26352739, 'SBICHNI86978756', 'SBI_GLOBAL_INTERNATIONAL', 4389, '2021-08-23', 1, 0);
```

### Difficulty Level : EASY

1. A customer would like to Block his lost Debit Card (CARD_NUMBER - 26352739 ), help the customer by writing a query to block his Debit Card by updating IS_BLOCKED to true.

2. A Customer would like to update his expired Debit Card’s Validity (CARD_NUMBER - 26352739 ), Write a query to update his Debit Cards validity (VALID_TILL) 10 years from his expired validity.

### Difficulty Level : MEDIUM

3. Create a Filter to search a Customer’s Info and Bank Accounts by matching the Customer’s USER_NAME

4. Write a Query for a Customer to fetch Bank Account Details of his Debit Card (CARD_NUMBER - 26352739 )

### Difficulty Level : TOUGH

5. A Customer's First Name needs to be updated but only his/her Bank Account Number is knowm, Construct a query updating FIRST_NAME of Customer with ACCOUNT_NUMBER = SBICHNI86978756
