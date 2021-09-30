# Tables

## BankAccount

| ACCOUNT_NUMBER  | CUSTOMER_ID | BRANCH_NAME | ACCOUNT_TYPE              | BALANCE | IS_TERMINATED |
| --------------- | ----------- | ----------- | ------------------------- | ------- | ------------- |
| SBICHNI23645792 | 1           | CHENNAI     | CURRENT_ACCOUNT           | 3300    | 0             |
| SBICHNI24617266 | 1           | CHENNAI     | FIXED_DEPOSIT_ACCOUNT     | 40000   | 0             |
| SBICHNI86978722 | 2           | CHROMPET    | HOME_LOAN_ACCOUNT         | 300000  | 0             |
| SBICHNI86978723 | 2           | CHENNAI     | EDUCATION_LOAN_ACCOUNT    | 120000  | 0             |
| SBICHNI86978756 | 1           | CHENNAI     | SAVINGS_ACCOUNT           | 3000    | 0             |
| SBICMPT16818246 | 1           | CHROMPET    | RECURRING_DEPOSIT_ACCOUNT | 0       | 0             |

## DepositDetail

| ACCOUNT_NUMBER  | PRIMARY_ACCOUNT_NUMBER | DEPOSIT_DATE | MATURITY_DATE | INTEREST_MONTHS | INTEREST | IS_MATURITY_INTEREST_DEPOSITED |
| --------------- | ---------------------- | ------------ | ------------- | --------------- | -------- | ------------------------------ |
| SBICHNI24617266 | SBICHNI86978756        | 2021-08-30   | 2022-02-28    | 6               | 12.3     | 0                              |
| SBICMPT16818246 | SBICHNI86978756        | 2021-08-30   | 2022-08-30    | 12              | 11.45    | 0                              |

## BankAuth

| SECRET                               | USER_ID |
| ------------------------------------ | ------- |
| 2f9c538b-fc9b-42c8-a45c-25f1bfa766bb | 0       |
| 41c1d7b6-21aa-424a-a360-f35aefa2c040 | 6       |
| a700a33a-3b75-40b8-867f-c80988981a15 | 6       |
| ae37eb83-7223-4461-960f-7bae02ea4503 | 6       |
| b9ed47b1-4a60-4abe-92ff-0b87c7ce580a | 6       |
| ba8bfdf7-4d23-45e1-b9a7-a05e86088adc | 6       |

# Description

## BankAccount

| Field          | Type        | Null | Key | Default | Extra |
| -------------- | ----------- | ---- | --- | ------- | ----- |
| ACCOUNT_NUMBER | varchar(40) | NO   | PRI | NULL    |       |
| CUSTOMER_ID    | bigint(19)  | NO   |     | NULL    |       |
| BRANCH_NAME    | varchar(40) | NO   |     | NULL    |       |
| ACCOUNT_TYPE   | varchar(40) | NO   |     | NULL    |       |
| BALANCE        | double      | NO   |     | NULL    |       |
| IS_TERMINATED  | tinyint(1)  | YES  |     | 0       |       |

## DepositDetail

| Field                          | Type        | Null | Key | Default | Extra |
| ------------------------------ | ----------- | ---- | --- | ------- | ----- |
| ACCOUNT_NUMBER                 | varchar(40) | NO   | PRI | NULL    |       |
| PRIMARY_ACCOUNT_NUMBER         | varchar(40) | NO   | MUL | NULL    |       |
| DEPOSIT_DATE                   | date        | NO   |     | NULL    |       |
| MATURITY_DATE                  | date        | NO   |     | NULL    |       |
| INTEREST_MONTHS                | int(10)     | YES  |     | 0       |       |
| INTEREST                       | float       | YES  |     | 0       |       |
| IS_MATURITY_INTEREST_DEPOSITED | tinyint(1)  | YES  |     | 0       |       |

## BankAuth

| Field   | Type        | Null | Key | Default | Extra |
| ------- | ----------- | ---- | --- | ------- | ----- |
| SECRET  | varchar(60) | NO   | PRI | NULL    |       |
| USER_ID | bigint(19)  | NO   |     | NULL    |       |

# Creation

## BankAccount

```sql
create table BankAccount (ACCOUNT_NUMBER VARCHAR(40) PRIMARY KEY, CUSTOMER_ID INT, BRANCH_NAME VARCHAR(40), ACCOUNT_TYPE VARCHAR(40), BALANCE DOUBLE, IS_TERMINATED BIT(1) DEFAULT false);
```

## DepositDetail

```sql
create table DepositDetail (ACCOUNT_NUMBER VARCHAR(40) PRIMARY KEY, PRIMARY_ACCOUNT_NUMBER VARCHAR(40), DEPOSIT_DATE DATE, MATURITY_DATE DATE, INTEREST_MONTHS INT DEFAULT 0, INTEREST FLOAT DEFAULT 0,  IS_MATURITY_INTEREST_DEPOSITED BIT(1), CONSTRAINT fk_deposit_account FOREIGN KEY (PRIMARY_ACCOUNT_NUMBER) REFERENCES BankAccount(ACCOUNT_NUMBER));
```

## BankAuth

```sql
create table BankAuth (SECRET VARCHAR(60) NOT NULL PRIMARY KEY, USER_ID INT NOT NULL);
```

## Insertion

## BankAccount

```sql
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI23645792', 1, 'CHENNAI', 'CURRENT_ACCOUNT', 3300, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI24617266', 1, 'CHENNAI', 'FIXED_DEPOSIT_ACCOUNT', 40000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978722', 2, 'CHROMPET', 'HOME_LOAN_ACCOUNT', 300000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978723', 2, 'CHENNAI', 'EDUCATION_LOAN_ACCOUNT', 120000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICHNI86978756' , 1, 'CHENNAI', 'SAVINGS_ACCOUNT', 3000, 0);
insert into BankAccount (ACCOUNT_NUMBER, CUSTOMER_ID, BRANCH_NAME, ACCOUNT_TYPE, BALANCE, IS_TERMINATED) values('SBICMPT16818246', 1, 'CHROMPET', 'RECURRING_DEPOSIT_ACCOUNT', 0, 0);
```

## DepositDetail

```sql
insert into DepositDetail (ACCOUNT_NUMBER, PRIMARY_ACCOUNT_NUMBER, DEPOSIT_DATE, MATURITY_DATE, INTEREST_MONTHS, INTEREST, IS_MATURITY_INTEREST_DEPOSITED) values('SBICHNI24617266', 'SBICHNI86978756', '2021-08-30', '2022-02-28', 6, 12.3, 0);
insert into DepositDetail (ACCOUNT_NUMBER, PRIMARY_ACCOUNT_NUMBER, DEPOSIT_DATE, MATURITY_DATE, INTEREST_MONTHS, INTEREST, IS_MATURITY_INTEREST_DEPOSITED) values('SBICMPT16818246', 'SBICHNI86978756', '2021-08-30', '2022-08-30', 12, 11.45, 0);
```

## BankAuth

```sql
insert into BankAuth (SECRET, USER_ID) values('2f9c538b-fc9b-42c8-a45c-25f1bfa766bb', 0 );
insert into BankAuth (SECRET, USER_ID) values('41c1d7b6-21aa-424a-a360-f35aefa2c040', 6 );
insert into BankAuth (SECRET, USER_ID) values('a700a33a-3b75-40b8-867f-c80988981a15', 6 );
insert into BankAuth (SECRET, USER_ID) values('ae37eb83-7223-4461-960f-7bae02ea4503', 6 );
insert into BankAuth (SECRET, USER_ID) values('b9ed47b1-4a60-4abe-92ff-0b87c7ce580a', 6 );
insert into BankAuth (SECRET, USER_ID) values('ba8bfdf7-4d23-45e1-b9a7-a05e86088adc', 6 );
```

### Difficulty Level : EASY

1.  Construct a query identifying session's secret from BankAuth Table with USER_ID = 6

2.  A Customer Deposit's Rupees 100 to his/her Bank Account, Construct a query Updating ₹ 100 from the previous BALANCE for a customer with ACCOUNT_NUMBER = SBICHNI86978756;

### Difficulty Level : MEDIUM

3. Construct a Query for fetching Deposit Account’s Information (BankAccount) for a Customer with CUSTOMER_ID = 1.

4. A Customer wants to fetch Deposit Accounts linked to his primary savings account SBICHNI86978756

Note: You can Identify the linked accounts with the PRIMARY_ACCOUNT_NUMBER Column in Deposit Detail Table

### Difficulty Level : TOUGH

5. A customer wants to terminate his Savings Account (ACCOUNT_NUMBER - SBICHNI86978756) and associated Deposit Accounts.

Note: You can track the Deposit Accounts linked to the Savings Account with the PRIMARY_ACCOUNT_NUMBER Column.
