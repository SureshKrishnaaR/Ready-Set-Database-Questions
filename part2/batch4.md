# Tables

## AccountType

| ACCOUNT_TYPE              | INTEREST |
| ------------------------- | -------- |
| CAR_LOAN_ACCOUNT          | 12.65    |
| CURRENT_ACCOUNT           | 0        |
| EDUCATION_LOAN_ACCOUNT    | 7.8      |
| FIXED_DEPOSIT_ACCOUNT     | 12.3     |
| HOME_LOAN_ACCOUNT         | 13.2     |
| PERSONAL_LOAN_ACCOUNT     | 13.44    |
| RECURRING_DEPOSIT_ACCOUNT | 11.45    |
| SAVINGS_ACCOUNT           | 2.7      |

## LoanAccountType

| LOAN_ACCOUNT_TYPE_ID | ACCOUNT_TYPE           | MAX_LOAN_AMOUNT |
| -------------------- | ---------------------- | --------------- |
| 0                    | HOME_LOAN_ACCOUNT      | 700000          |
| 1                    | EDUCATION_LOAN_ACCOUNT | 200000          |
| 2                    | CAR_LOAN_ACCOUNT       | 100000          |
| 3                    | PERSONAL_LOAN_ACCOUNT  | 80000           |

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

# Description

## AccountType

| Field        | Type        | Null | Key | Default | Extra |
| ------------ | ----------- | ---- | --- | ------- | ----- |
| ACCOUNT_TYPE | varchar(40) | NO   | PRI | NULL    |       |
| INTEREST     | float       | NO   |     | NULL    |       |

## LoanAccountType

| Field                | Type        | Null | Key | Default | Extra |
| -------------------- | ----------- | ---- | --- | ------- | ----- |
| LOAN_ACCOUNT_TYPE_ID | bigint(19)  | NO   | PRI | NULL    |       |
| ACCOUNT_TYPE         | varchar(40) | NO   | UNI | NULL    |       |
| MAX_LOAN_AMOUNT      | double      | NO   |     | NULL    |       |

## InterestMonth

| Field             | Type        | Null | Key | Default | Extra |
| ----------------- | ----------- | ---- | --- | ------- | ----- |
| INTEREST_MONTH_ID | bigint(19)  | NO   | PRI | NULL    |       |
| ACCOUNT_TYPE      | varchar(40) | NO   | MUL | NULL    |       |
| INTEREST_MONTHS   | int(10)     | NO   |     | NULL    |       |

# Creation

## AccountType

```sql
create table AccountType(ACCOUNT_TYPE VARCHAR(40) NOT NULL PRIMARY KEY, INTEREST FLOAT NOT NULL);
```

## LoanAccountType

```sql
create table LoanAccountType(LOAN_ACCOUNT_TYPE_ID BIGINT PRIMARY KEY, ACCOUNT_TYPE VARCHAR(40) NOT NULL UNIQUE, MAX_LOAN_AMOUNT DOUBLE NOT NULL, CONSTRAINT fk_loan_account_type FOREIGN KEY (ACCOUNT_TYPE) REFERENCES AccountType(ACCOUNT_TYPE));
```

## InterestMonth

```sql
create table InterestMonth(INTEREST_MONTH_ID INT NOT NULL PRIMARY KEY, ACCOUNT_TYPE VARCHAR(40) NOT NULL, INTEREST_MONTHS INT NOT NULL, CONSTRAINT fk_interest_month FOREIGN KEY (ACCOUNT_TYPE) REFERENCES AccountType(ACCOUNT_TYPE));
```

# Insertion

## AccountType

```sql
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('CAR_LOAN_ACCOUNT', 12.65);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('CURRENT_ACCOUNT', 0);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('EDUCATION_LOAN_ACCOUNT', 7.8);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('FIXED_DEPOSIT_ACCOUNT', 12.3);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('HOME_LOAN_ACCOUNT', 13.2);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('PERSONAL_LOAN_ACCOUNT', 13.44);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('RECURRING_DEPOSIT_ACCOUNT', 11.45);
insert into AccountType (ACCOUNT_TYPE, INTEREST) values('SAVINGS_ACCOUNT', 2.7);
```

## LoanAccountType

```sql
insert into LoanAccountType (LOAN_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MAX_LOAN_AMOUNT) values(0, 'HOME_LOAN_ACCOUNT', 700000);
insert into LoanAccountType (LOAN_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MAX_LOAN_AMOUNT) values(1, 'EDUCATION_LOAN_ACCOUNT', 200000);
insert into LoanAccountType (LOAN_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MAX_LOAN_AMOUNT) values(2, 'CAR_LOAN_ACCOUNT', 100000);
insert into LoanAccountType (LOAN_ACCOUNT_TYPE_ID, ACCOUNT_TYPE, MAX_LOAN_AMOUNT) values(2, 'CAR_LOAN_ACCOUNT', 100000);
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

### Difficulty Level : EASY

1. A Super Admin tries to update Interest Rate for RECURRING_DEPOSIT_ACCOUNT with 12.45, Construct a query updating INTEREST Column in AccountType Table.

2.

### Difficulty Level : MEDIUM

3.

4.

### Difficulty Level : TOUGH

5. Join Tables AccountType, LoanAccountType, InterestMonth to fetch AccountType Information for CAR_LOAN_ACCOUNT from the above tables based on the ACCOUNT_TYPE Column, also sort the resultant table based on ACCOUNT_TYPE and INTEREST_MONTHS.
