# Description

PostgreSQL is a flavour of SQL.

# Resources

- [Data Types](https://www.postgresql.org/docs/8.1/datatype.html)
- [PostgreSQL](https://www.postgresql.org/)
- [Manual](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-char-varchar-text/)
- [Rust with SQL](https://www.youtube.com/watch?v=TCERYbgvbq0)

# Notes

## Referential Integrity

You want to make sure that no one can insert rows in the `weather` table that do not have a matching entry in the `cities` table. This is called maintaining the *referential integrity* of your data.

## Create View

Making liberal use of views is a key aspect of good SQL database design. Views allow you to encapsulate the details of the structure of your tables, which might change as your application evolves, behind consistent interfaces.

## Transactions

A transaction is said to be _atomic_: from the point of view of other transactions, it either happens completely or not at all. If, partway through the transaction, we decide we do not want to commit (perhaps we just noticed that Alice's balance went negative), we can issue the command `ROLLBACK` instead of `COMMIT`, and all our updates so far will be cancelled. It's possible to control the statements in a transaction in a more granular fashion through the use of _savepoints_.

## Window Functions

A _window function_ performs a calculation across a set of table rows that are somehow related to the current row.

# Data Types

`INT2` is a  signed two-byte integer which means it can be a value between -32,768 to 32,767.