# SQL

## Distance between two cities

```sql
drop table dist ;
create table dist (src varchar2(50), dest varchar2(50), distance number);

insert into dist values ('DEL','KOL',700);
insert into dist values ('KOL','DEL',700);
insert into dist values ('MUM','DEL',800);
insert into dist values ('DEL','MUM',800);
insert into dist values ('BAN','DEL',780);
```
### Remove duplicate distance two cities

<details>
<summary>Answer</summary>

```sql
Select
case when src < dest then src else dest end ,
case when src > dest then src else dest end
from 
dist 
group by 
case when src < dest then src else dest end ,
case when src > dest then src else dest end
having count(*) >1;
```
</details>

## Sequence of numbers

<details>
<summary>Answer</summary>
  
```sql
with t(n) as 
(select 1 as n from dual
union all
select n+1 as n from t where n < 25)
select * from t ;
```
</details>

## Employee timesheets

```sql
DROP TABLE TIMESHEETS;
CREATE TABLE TIMESHEETS(empid NUMBER , timestamps NUMBER , in_out VARCHAR2(50));

insert into timesheets values(1,830,'IN');
insert into timesheets values(2,900,'IN');
insert into timesheets values(3,930,'IN');
insert into timesheets values(1,945,'OUT');
insert into timesheets values(2,946,'OUT');
insert into timesheets values(4,1000,'IN');
```

<details>
<summary>Answer</summary>
  
```sql
select count(*) from 
(select dense_rank() over(partition by empid order by timestamps desc) rn , in_out from timesheets t)
where in_out='IN' and rn=1 ;
```
</details>
