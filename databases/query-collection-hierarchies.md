# Query collection hierarchies

## Queries should be organised into a Query Collection Hierarchy

In real world systems, one single query will not always only read from or write to an individual table, but there will always be a main intent behind all queries.

To promote clean database organisation, queries should be hierarchically organised within named "collection" directories in accordance to the area of the database their main intent affects. 

A query collection will typically be the name of a table within the database -- for example, if there is a `Customer` table and a `Product` table, it makes sense to have a "customer" and "product" query collection for when select, insert, update or delete queries mainly affect those tables. If a query interacts with more than one table, through a join or subselect for example, it should be organised within the collection which represents its main _intent_.

An example query directory:

```
.
├── query
   ├── customer
   │   ├── getAll.sql
   │   └── getById.sql
   └── product
       ├── getById.sql
       └── getAllForCustomer.sql
```

In the above simple example, the query `product/getAllForCustomer` will refer to both _customer_ and _product_ tables, but because its main intent is to return a _product_ list, it is organised within the product _query_ collection.

## Tables within the same collection can use an underscore to indicate their hierarchy

Tables can be organised within the same named collections by using underscores to indicate which table is used for the main responsibility. For example, there may be tables called `product`, `product_category`, `product_offer` within the "product" collection, and `customer`, `customer_address`, and `customer_payment` within the "customer" collection.

## Related tables should use underscored words to indicate their relationship

When two or more tables are tightly related in a system, for instance when a junction table is required to create a many-to-many relationship, underscored words should be used to indicate the relationship between the tables.

A set of predefined "relationship" words can be used to increase readability, such as "has", "owns", "can", etc.

In our customer-product example, a common relationship would be the list of product orders that a customer has made, which can be recorded in a `customer_has_product` or `customer_ordered_product` junction table. From the name of the table, and the use of the predefined relationship word, it is obvious as to what the purpose of the table is without needing to see the columns or code that uses it.
