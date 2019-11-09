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
<br/>
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
\```
</details>

