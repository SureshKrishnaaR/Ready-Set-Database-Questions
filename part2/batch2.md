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

## LoanDetail

| ACCOUNT_NUMBER  | PRIMARY_ACCOUNT_NUMBER | LOAN_ISSUE_DATE | EMI  | INTEREST_PAID | MONTHS | INTEREST | LOAN_AMOUNT |
| --------------- | ---------------------- | --------------- | ---- | ------------- | ------ | -------- | ----------- |
| SBICHNI86978722 | SBICHNI86978756        | 2021-04-05      | 6000 | 0             | 24     | 13.2     | 430000      |
| SBICHNI86978723 | SBICHNI86978756        | 2021-08-02      | 3000 | 2300          | 12     | 7.8      | 130000      |

## DebitCard

| CARD_NUMBER | ACCOUNT_NUMBER  | CARD_TYPE                  | PIN  | VALID_TILL | IS_ACTIVE | IS_BLOCKED |
| ----------- | --------------- | -------------------------- | ---- | ---------- | --------- | ---------- |
| 26352349    | SBICHNI23645792 | SBI_PLATINUM_INTERNATIONAL | 1285 | 2021-04-30 | 1         | 0          |
| 26352739    | SBICHNI86978756 | SBI_GLOBAL_INTERNATIONAL   | 4389 | 2021-08-23 | 1         | 0          |

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

## LoanDetail

| Field                  | Type        | Null | Key | Default | Extra |
| ---------------------- | ----------- | ---- | --- | ------- | ----- |
| ACCOUNT_NUMBER         | varchar(40) | NO   | PRI | NULL    |       |
| PRIMARY_ACCOUNT_NUMBER | varchar(40) | NO   | MUL | NULL    |       |
| LOAN_ISSUE_DATE        | date        | NO   |     | NULL    |       |
| EMI                    | double      | NO   |     | NULL    |       |
| INTEREST_PAID          | double      | NO   |     | 0       |       |
| MONTHS                 | int(10)     | YES  |     | 0       |       |
| INTEREST               | float       | YES  |     | 0       |       |
| LOAN_AMOUNT            | double      | YES  |     | NULL    |       |

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

## BankAccount

```sql
create table BankAccount (ACCOUNT_NUMBER VARCHAR(40) PRIMARY KEY, CUSTOMER_ID INT, BRANCH_NAME VARCHAR(40), ACCOUNT_TYPE VARCHAR(40), BALANCE DOUBLE, IS_TERMINATED BIT(1) DEFAULT false);
```

## LoanDetail

```sql
create table LoanDetail (ACCOUNT_NUMBER VARCHAR(40) PRIMARY KEY, PRIMARY_ACCOUNT_NUMBER VARCHAR(40), LOAN_ISSUE_DATE DATE, EMI DOUBLE NOT NULL, INTEREST_PAID DOUBLE NOT NULL DEFAULT 0, MONTHS INT DEFAULT 0, INTEREST FLOAT DEFAULT 0, LOAN_AMOUNT DOUBLE, CONSTRAINT fk_loan_account FOREIGN KEY (PRIMARY_ACCOUNT_NUMBER) REFERENCES BankAccount(ACCOUNT_NUMBER));
```

## DebitCard

```sql
create table DebitCard (CARD_NUMBER BIGINT PRIMARY KEY, ACCOUNT_NUMBER VARCHAR(40), CARD_TYPE,VARCHAR(40) NOT NULL, PIN INT, VALID_TILL DATE, IS_ACTIVE BIT(1), IS_BLOCKED BIT(1), CONSTRAINT fk_debit_card FOREIGN KEY (ACCOUNT_NUMBER) REFERENCES BankAccount(ACCOUNT_NUMBER));
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

## LoanDetail

```sql
insert into LoanDetail (ACCOUNT_NUMBER, PRIMARY_ACCOUNT_NUMBER, LOAN_ISSUE_DATE, EMI, INTEREST_PAID, MONTHS, INTEREST, LOAN_AMOUNT) values('SBICHNI86978722', 'SBICHNI86978756', '2021-04-05', 6000, 0, 24, 13.2, 430000);
insert into LoanDetail (ACCOUNT_NUMBER, PRIMARY_ACCOUNT_NUMBER, LOAN_ISSUE_DATE, EMI, INTEREST_PAID, MONTHS, INTEREST, LOAN_AMOUNT) values('SBICHNI86978723', 'SBICHNI86978756', '2021-08-02', 3000, 2300, 12, 7.8, 130000);
```

## DebitCard

```sql
insert into LoanDetail (CARD_NUMBER, ACCOUNT_NUMBER, CARD_TYPE, PIN, VALID_TILL, IS_ACTIVE, IS_BLOCKED) values(26352349, 'SBICHNI23645792', 'SBI_PLATINUM_INTERNATIONAL', 1285, '2021-04-30', 1, 0);
insert into LoanDetail (CARD_NUMBER, ACCOUNT_NUMBER, CARD_TYPE, PIN, VALID_TILL, IS_ACTIVE, IS_BLOCKED) values(26352739, 'SBICHNI86978756', 'SBI_GLOBAL_INTERNATIONAL', 4389, '2021-08-23', 1, 0);
```

### Difficulty Level : EASY

1. Construct a Query for fetching Loan Account’s Information from BankAccount Table for a Customer with CUSTOMER_ID = 2.

2. Update Customer's Debit Card PIN with CARD_NUMBER = 26352349;

### Difficulty Level : MEDIUM

3. A customer wants to receive his Debit Card’s Branch Name, construct a query to get BRANCH_NAME for his Debit Card (CARD_NUMBER - 26352739 )

4. A Customer with [ CUSTOMER_ID = 2 ] would like to list all his Loan Accounts, Help the customer to fetch Loan Account Details with his CUSTOMER_ID.

### Difficulty Level : TOUGH

5. A customer wants to terminate his Savings Account (ACCOUNT_NUMBER - SBICHNI86978756) and associated Loan Accounts.

Note: You can track the Loan Accounts linked to the Savings Account with the PRIMARY_ACCOUNT_NUMBER Column.
