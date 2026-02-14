# goit-rdb-hw-02
# 📘 Database Design and Normalization (1NF, 2NF, 3NF)

## 📌 Project Overview

This project demonstrates the process of database normalization and Entity-Relationship (ER) modeling using MySQL Workbench.

The goal was to transform an initial denormalized table into a properly structured relational database that satisfies:

* First Normal Form (1NF)
* Second Normal Form (2NF)
* Third Normal Form (3NF)

The final result includes an ER diagram and physically created tables in MySQL.

---

## 📊 Initial Problem

The original table contained:

* Multiple products stored in a single column
* Redundant customer and address data
* Mixed entity information in one table

This structure caused data duplication and violated normalization principles.

---

## 🔹 Step 1 — First Normal Form (1NF)

To achieve 1NF:

* Repeating groups were removed
* Each product was stored in a separate row
* All attributes were made atomic

Result: One row per product per order.

---

## 🔹 Step 2 — Second Normal Form (2NF)

To achieve 2NF:

* Partial dependencies were eliminated
* Order information was separated from order items
* Functional dependencies were aligned with primary keys

Tables created:

* Orders
* OrderItem

---

## 🔹 Step 3 — Third Normal Form (3NF)

To achieve 3NF:

* Transitive dependencies were removed
* Customer data was separated into its own table
* Vendor data was separated from Product

Final tables:

* **Customer**
* **Order**
* **OrderItem**
* **Product**
* **Vendor**

The many-to-many relationship between Order and Product was resolved through the associative table **OrderItem** with a composite primary key:

```
PRIMARY KEY (order_id, product_id)
```

---

## 🗂 Final Database Structure

### Customer

* customer_id (PK)
* first_name
* last_name
* phone
* email
* address

### Order

* order_id (PK)
* order_date
* customer_id (FK)

### Product

* product_id (PK)
* product_name
* price DECIMAL(10,2)
* vendor_id (FK)

### Vendor

* vendor_id (PK)
* name
* phone
* email

### OrderItem

* order_id (FK)
* product_id (FK)
* quantity
* PRIMARY KEY (order_id, product_id)

---

## 🔗 Relationships

* One Customer → Many Orders
* One Order → Many OrderItems
* One Product → Many OrderItems
* One Vendor → Many Products

All foreign key constraints were implemented in MySQL.

---

## 🛠 Tools Used

* MySQL Workbench
* MySQL Server 8.0

---

## ✅ Result

The database:

* Fully satisfies 1NF, 2NF, and 3NF
* Eliminates redundancy
* Ensures referential integrity
* Implements proper primary and foreign keys
* Is physically created and verified in MySQL

---


