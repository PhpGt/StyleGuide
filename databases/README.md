# Databases

## [Table collection hierarchies](table-collection-hierarchies.md)

+ Tables should be organised into a Table Collection Hierarchy.
+ Tables in the same collection should use an underscore to split the hierarchy.

## [Casing](casing.md)

+ Tables should use `UpperCamelCase`.
+ Columns should use `lowercase_underscored`.
+ Primary keys should follow `id_TableName`.

## [Naming](naming.md)

+ Columns can have optional descriptions to uniquely identify their purpose.
+ Foreign key column names should match their referenced column.
+ Foreign key constraint names should reference both tables and columns uniquely.