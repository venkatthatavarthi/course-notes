# LINQ

# LINQ

Let's progress our learning slightly

LINQ is a special language generated by Microsoft to read databases.

LINQ has 2 types

    from c in customers 
    where c.City="Berlin"
    select c
    
    customers.Where(c=>c.City=="Berlin");

# Getting Started

Microsoft have their own test database
1) Northwind ==> Business database with customers
2) Adventure Works