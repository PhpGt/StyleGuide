# Naming

## Column names should be treated exactly as object properties are

When queries are executed in PHP, the rows are mapped to an object and columns are represented by object properties. This imposes certain limitations to the name of column within a database.

For instance, it is technically possible to name a column `something-like-this`, `Or even this`, but having hyphens or spaces is not sensible in an object property and will cause confusion.

Columns, as with object properties, should be named to describe what they represent.

## Foreign key column names do not need special identification

As with all variable naming, special notation should not be used to identify different types of variables. This also applies to database column names; a foreign key does not need to be named in a way to identify that it is a foreign key.

Common bad examples include column names such as `fk_user`, but a better name would be `userId`, assuming the foreign key matches a user's id.

## Foreign key constraint names should reference both tables and columns uniquely

Given example tables called `customer` and `user`, both of which have an `id` column, if a customer column `userId` refers to the user table's id column, a foreign key can be named `customer__user__id`, or a similar naming convention should be used consistently.
