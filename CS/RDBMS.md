#cs #database #mysql

# Introduction 
> 
> RDBMS stands for Relational Database Management System.
> it is a program used to maintain a relational database.

- RDBMS is it’s the basis system.
- RDBMS uses [[SQL queries]]  to access the data in the database.

# 組成
1.  資料庫 （Database） 
	由 Tables 組成。

1.  資料表（Table）
	資料表是 MySQL 中最基本的資料存儲結構，它用於存儲具有相同結構的資料。每個資料表都有一個名稱，並且包含了多個欄位和資料列。

2.  資料列（Row）
	資料列是資料表中的一條記錄，它包含了多個欄位的值。每個資料列都有一個唯一的識別符，稱為主鍵（Primary Key），用於區分不同的資料列。

3.  欄位（Column）
	欄位是資料表中的一個數據項，它代表了一個特定的資料類型。每個欄位都有一個名稱和資料類型，例如整數、字串、日期等等。在 MySQL 中，欄位還可以設置約束（Constraints），例如主鍵、外鍵等等，用於保護資料庫的完整性和一致性。

![[Pasted image 20220920230553.png]]
-   Table: Customers.
-   Column: The columns in Customers are CustomerID, CustomerName, ContactName…
-   Row: This table has 5 records(rows)

# What is a Relational Database?
EX
## Customers Table
![[Pasted image 20220920230759.png]]
## Orders Table
![[Pasted image 20220920230808.png]]
