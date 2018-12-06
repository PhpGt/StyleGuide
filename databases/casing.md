# Casing

## Tables should use `snake_case`

Snake case allows for tables to clearly identify their relationship within the [[query collection hierarchies]].

When naming junction tables, the use of underscores separates the table names from the relationship, as in `student_in_class` and `product_in_category`.

## Columns should use `camelCase`

When columns are referenced in PHP using model classes, they are done so using object properties, so using camel case is consistent with how object properties are written and accessed across other repositories.

## Primary keys should be called `id`

Most tables will use a single identifying column as the primary key. In this case, they should simple be named `id`, rather than other commonly used patterns such as `id_customer`, or `customerId`.

Database columns should be named using the same conventions as object properties, as when the database is loaded into PHP it will inevitably be represented by object properties.
