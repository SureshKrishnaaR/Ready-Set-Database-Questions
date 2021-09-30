# Tables

## CheckingAccountType

| CHECKING_ACCOUNT_TYPE_ID | ACCOUNT_TYPE              | MINIMUM_BALANCE |
| ------------------------ | ------------------------- | --------------- |
| 0                        | SAVINGS_ACCOUNT           | 3000            |
| 1                        | CURRENT_ACCOUNT           | 0               |
| 2                        | FIXED_DEPOSIT_ACCOUNT     | 5000            |
| 3                        | RECURRING_DEPOSIT_ACCOUNT | 0               |

## InterestMonth

| INTEREST_MONTH_ID | ACCOUNT_TYPE              | INTEREST_MONTHS |
| ----------------- | ------------------------- | --------------- |
| 0                 | FIXED_DEPOSIT_ACCOUNT     | 6               |
| 1                 | FIXED_DEPOSIT_ACCOUNT     | 12              |
| 2                 | FIXED_DEPOSIT_ACCOUNT     | 15              |
| 3                 | RECURRING_DEPOSIT_ACCOUNT | 6               |
| 4                 | RECURRING_DEPOSIT_ACCOUNT | 12              |
| 5                 | RECURRING_DEPOSIT_ACCOUNT | 24              |
| 6                 | HOME_LOAN_ACCOUNT         | 12              |
| 7                 | HOME_LOAN_ACCOUNT         | 18              |
| 8                 | HOME_LOAN_ACCOUNT         | 24              |
| 9                 | EDUCATION_LOAN_ACCOUNT    | 9               |
| 10                | EDUCATION_LOAN_ACCOUNT    | 12              |
| 11                | EDUCATION_LOAN_ACCOUNT    | 24              |
| 12                | PERSONAL_LOAN_ACCOUNT     | 6               |
| 13                | PERSONAL_LOAN_ACCOUNT     | 9               |
| 14                | PERSONAL_LOAN_ACCOUNT     | 12              |
| 15                | CAR_LOAN_ACCOUNT          | 6               |
| 16                | CAR_LOAN_ACCOUNT          | 9               |
| 17                | CAR_LOAN_ACCOUNT          | 12              |

## History

| HISTORY_ID | EVENT_TYPE     | TIME_STAMP          | CARD_NUMBER | ACCOUNT_NUMBER | TRANSACTION_TYPE           | TRANSACTION_COMMENT | AMOUNT |
| ---------- | -------------- | ------------------- | ----------- | -------------- | -------------------------- | ------------------- | ------ |
| 0          | DEPOSIT        | 2021-09-09 03:14:27 | 26352349    | NULL           | SBI_PLATINUM_INTERNATIONAL | DEPOSIT FEE         | 5000   |
| 1          | DEPOSIT        | 2021-09-13 02:23:34 | 26352349    | NULL           | SBI_PLATINUM_INTERNATIONAL | TEST DEPOSIT        | 20     |
| 2          | WITHDRAW       | 2021-09-20 09:23:17 | 26352349    | NULL           | SBI_PLATINUM_INTERNATIONAL | NULL                | 1000   |
| 3          | MONEY_TRANSFER | 2021-09-21 09:23:20 | 26352349    | NULL           | SBI_PLATINUM_INTERNATIONAL | FOOD PAYMENT        | 450    |

# Description

## CheckingAccountType

| Field                    | Type        | Null | Key | Default | Extra |
| ------------------------ | ----------- | ---- | --- | ------- | ----- |
| CHECKING_ACCOUNT_TYPE_ID | bigint(19)  | NO   | PRI | NULL    |       |
| ACCOUNT_TYPE             | varchar(40) | NO   | UNI | NULL    |       |
| MINIMUM_BALANCE          | double      | NO   |     | NULL    |       |

## InterestMonth

| Field             | Type        | Null | Key | Default | Extra |
| ----------------- | ----------- | ---- | --- | ------- | ----- |
| INTEREST_MONTH_ID | bigint(19)  | NO   | PRI | NULL    |       |
| ACCOUNT_TYPE      | varchar(40) | NO   | MUL | NULL    |       |
| INTEREST_MONTHS   | int(10)     | NO   |     | NULL    |       |

## History

| Field               | Type         | Null | Key | Default           | Extra |
| ------------------- | ------------ | ---- | --- | ----------------- | ----- |
| HISTORY_ID          | bigint(19)   | NO   | PRI | NULL              |       |
| EVENT_TYPE          | varchar(50)  | NO   |     | NULL              |       |
| TIME_STAMP          | timestamp    | NO   |     | CURRENT_TIMESTAMP |       |
| CARD_NUMBER         | bigint(19)   | YES  |     | NULL              |       |
| ACCOUNT_NUMBER      | varchar(40)  | YES  |     | NULL              |       |
| TRANSACTION_TYPE    | varchar(70)  | YES  |     | NULL              |       |
| TRANSACTION_COMMENT | varchar(100) | YES  |     | NULL              |       |
| AMOUNT              | double       | YES  |     | 0                 |       |

# Creation

## CheckingAccountType

```sql
create table CheckingAccountType(ACCOUNT_TYPE VARCHAR(40) NOT NULL UNIQUE, MINIMUM_BALANCE DOUBLE NOT NULL);
```

## InterestMonth

```sql
create table InterestMonth(INTEREST_MONTH_ID INT NOT NULL PRIMARY KEY, ACCOUNT_TYPE VARCHAR(40) NOT NULL, INTEREST_MONTHS INT NOT NULL, CONSTRAINT fk_interest_month FOREIGN KEY (ACCOUNT_TYPE) REFERENCES AccountType(ACCOUNT_TYPE));
```

## History

```sql
create table History (HISTORY_ID INT NOT NULL PRIMARY KEY, EVENT_TYPE VARCHAR(50), TIME_STAMP TIMESTAMP,  CARD_NUMBER BIGINT, ACCOUNT_NUMBER VARCHAR(40), TRANSACTION_TYPE VARCHAR(70),  TRANSACTION_COMMENT VARCHAR(100), AMOUNT DOUBLE);
```

# Insertion

## CheckingAccountType

```sql
insert into CheckingAccountType (CHECKING_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MINIMUM_BALANCE) values(0, 'SAVINGS_ACCOUNT', 3000);
insert into CheckingAccountType (CHECKING_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MINIMUM_BALANCE) values(1, 'CURRENT_ACCOUNT', 0);
insert into CheckingAccountType (CHECKING_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MINIMUM_BALANCE) values(2, 'FIXED_DEPOSIT_ACCOUNT', 5000);
insert into CheckingAccountType (CHECKING_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MINIMUM_BALANCE) values(3, 'RECURRING_DEPOSIT_ACCOUNT', 0);
```

## InterestMonth

```sql
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(0, 'FIXED_DEPOSIT_ACCOUNT', 6);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(1, 'FIXED_DEPOSIT_ACCOUNT', 12);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(2, 'FIXED_DEPOSIT_ACCOUNT', 15);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(3, 'RECURRING_DEPOSIT_ACCOUNT', 6);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(4, 'RECURRING_DEPOSIT_ACCOUNT', 12);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(5, 'RECURRING_DEPOSIT_ACCOUNT', 24);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(6, 'HOME_LOAN_ACCOUNT', 12);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(7, 'HOME_LOAN_ACCOUNT', 18);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(8, 'HOME_LOAN_ACCOUNT', 24);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(9, 'EDUCATION_LOAN_ACCOUNT', 9);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(10, 'EDUCATION_LOAN_ACCOUNT', 12);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(11, 'EDUCATION_LOAN_ACCOUNT', 24);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(12, 'PERSONAL_LOAN_ACCOUNT', 6);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(13, 'PERSONAL_LOAN_ACCOUNT', 9);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(14, 'PERSONAL_LOAN_ACCOUNT', 12);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(15, 'CAR_LOAN_ACCOUNT', 6);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(16, 'CAR_LOAN_ACCOUNT', 9);
insert into InterestMonth (INTEREST_MONTH_ID, ACCOUNT_TYPE, INTEREST_MONTHS) values(17, 'CAR_LOAN_ACCOUNT', 12);
```

## History

```sql
insert into History (HISTORY_ID, EVENT_TYPE, TIME_STAMP, CARD_NUMBER, ACCOUNT_NUMBER, TRANSACTION_TYPE, TRANSACTION_COMMENT, AMOUNT) values( 0, 'DEPOSIT', '2021-09-09 03:14:27', 26352349, NULL, 'SBI_PLATINUM_INTERNATIONAL', 'DEPOSIT FEE', 5000);
insert into History (HISTORY_ID, EVENT_TYPE, TIME_STAMP, CARD_NUMBER, ACCOUNT_NUMBER, TRANSACTION_TYPE, TRANSACTION_COMMENT, AMOUNT) values(  1, 'DEPOSIT', '2021-09-13 02:23:34', 26352349, NULL, 'SBI_PLATINUM_INTERNATIONAL', 'TEST DEPOSIT', 20 );
insert into History (HISTORY_ID, EVENT_TYPE, TIME_STAMP, CARD_NUMBER, ACCOUNT_NUMBER, TRANSACTION_TYPE, TRANSACTION_COMMENT, AMOUNT) values( 2, 'WITHDRAW', '2021-09-20 09:23:17', 26352349, NULL, 'SBI_PLATINUM_INTERNATIONAL', NULL, 1000);
insert into History (HISTORY_ID, EVENT_TYPE, TIME_STAMP, CARD_NUMBER, ACCOUNT_NUMBER, TRANSACTION_TYPE, TRANSACTION_COMMENT, AMOUNT) values( 3, 'MONEY_TRANSFER', '2021-09-21 09:23:20', 26352349, NULL, 'SBI_PLATINUM_INTERNATIONAL', 'FOOD PAYMENT', 450);
```

# Queries & Solutions

### Difficulty Level : EASY

1. Help a Customer to Get his Debit Cards History Logs between the given dates 13 September 2021 (Inclusive of Limits) till 31 September 2021 in Descending Order.

Note: CARD_NUMBER - 26352349

2. Suresh transfers money to a Shop Keeper through his Debit Card, In order to confirm the successful transaction, he expects 10 recent transactions made through his Debit Card, Construct a query to get 10 recent transactions with his Debit Card (CARD_NUMBER - 26352739)

### Difficulty Level : MEDIUM

3. A Customer wants to view past 1-month transaction history from the current date, construct a query to fetch past 1-month transaction history.

4. Join CheckingAccountType, Interestmonth table by selecting MINIMUM_BALANCE, INTEREST_MONTHS, ACCOUNT_TYPE Column using inner join and sort by ACCOUNT_TYPE, INTEREST_MONTHS.

### Difficulty Level : TOUGH

5. Delete [ INTEREST_MONTHS = 12 ] with [ CHECKING_ACCOUNT_TYPE_ID = 2 ]
