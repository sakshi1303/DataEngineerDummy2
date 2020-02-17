## 4 Step dimensional process

1. Gather business requirement
2. Declare grain
3. Declare facts
4. Declare dimensions.

## Basic fact table techniques

1. Fact table contains numeric data to be measured.
2. Additive can be summed across all records , semi-additive is which can be summed across partially for example account balance and non-additive which cannot be summed such as ratios etc.
3. NULLS must be avoided in fact table rather a surrogate key needs to be generated for dimension keys with attributes as unknown. 
4. Conformed facts so that they are identically named. 
5. Transaction fact table contains rows only if a transaction takes place hence they are sparse. They contain exact details like time stamps etc.
6. Periodic snapshot are records on periodic interval such as days, week, month and year.
7. Accumulating snapshot fact table consists of steps at a pipeline and after completion of each step records gets updated.
8. Factless fact tables are there to capture events such as promotion coverage because they wont be available in sales table. This type of table also has dummy value of 1 for easy calculation.
9. Aggregated fact tables are rollups of numeric fact data so accelerate performance at UI level , also known as aggregate navigation. 
They also contain foreign keys for shrunken dimensions.
10. Consolidated facts are those to merge those facts with same grain. 

## Basic Dimension table techniques

1. Every dimension table has a unique primary key and contains descriptive columns in dimension table with its associated primary key in fact table as foreign key.
2. Dimension surrogate keys are created because for one natural key there will be more than one record as we keep track of history. Also since natural key can be created by more than one source system they may be poorly administered.
3. Natural keys can be changed hence to identify a particular dimension DW/BI sytem can have their own durable key which never changes.
4. Drilling down means adding more column in GROUP BY clause so that additional details are gained.

