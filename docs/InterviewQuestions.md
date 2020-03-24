# Data Engineer Interview Questions

[Sequence of numbers](#sequence-of-numbers)

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
### Duplicate Cities 

```sql
select  d1.src, d1.dest 
from dist d1 left outer join dist d2 
               on d1.src = d2.dest 
              and d1.dest = d2.src
where d1.src <= d2.src;
```

### Distinct Cities

```sql
select  d1.src, d1.dest 
from dist d1 left outer join dist d2 
               on d1.src = d2.dest 
              and d1.dest = d2.src
where d1.src <= NVL(d2.src, d1.src);
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
<summary>Answer 1</summary>
  
```sql
select count(*) from 
(select dense_rank() over(partition by empid order by timestamps desc) rn , in_out from timesheets t)
where in_out='IN' and rn=1 ;
```
</details>

<details>
<summary>Answer 2</summary>
  
```sql
select sum(time_diff), empid 
from
(select 
lead(timestamps) over(partition by empid order by timestamps) - timestamps time_diff , empid , in_out from timesheets)
where in_out='IN'
group by empid ;
```
</details>

## Batsman Outscoring Himself

```sql
drop table ipl_batsman_score ;
create table ipl_batsman_score
(batsman_id number , match_id number, score number);

insert all
into ipl_batsman_score values (1,1,10)
into ipl_batsman_score values (1,2,15)
into ipl_batsman_score values (1,3,100)
into ipl_batsman_score values (2,1,101)
into ipl_batsman_score values (2,2,115)
into ipl_batsman_score values (2,3,90)
into ipl_batsman_score values (1,4,45)
into ipl_batsman_score values (1,5,155)
into ipl_batsman_score values (1,6,60)
into ipl_batsman_score values (2,4,10)
into ipl_batsman_score values (2,5,20)
into ipl_batsman_score values (2,6,100)
select 1 from dual;
```

<details>
<summary>Answer</summary>
  
```sql
select * from ipl_batsman_score ibs1 where ibs1.score > ALL(select ibs2.score from ipl_batsman_score ibs2 where ibs1.batsman_id=ibs2.batsman_id and ibs1.match_id > ibs2.match_id);
```

```sql
select batsman_id, count(*)
from
(select batsman_id, match_id, score , rank() over (partition by batsman_id order by score) rn
from ipl_batsman_score i1 
where i1.score > ALL( select i2.score from ipl_batsman_score i2 
                      where i1.batsman_id  = i2.batsman_id 
                      and i1.match_id  > i2.match_id  )
)where rn <> 1
group by batsman_id;
```

```sql
with t as 
(
select 
distinct 
case when ibs1.score > ibs2.score then 'Y' else 'N' end val_comp , 
ibs1.batsman_id,
ibs1.match_id 
from 
ipl_batsman_Score  ibs1
left outer join 
ipl_batsman_Score  ibs2
on ibs1.batsman_id=ibs2.batsman_id 
AND ibs1.match_id > ibs2.match_id)
select 
t1.*
from t t1 
left outer join t t2 
on t1.batsman_id = t2.batsman_id 
and t1.match_id=t2.match_id 
and t1.val_comp <> t2.val_comp 
where t2.batsman_id is null and t1.val_comp = 'Y';

```
</details>


## Begin and End Price 

```sql
drop table price ;
create table price ( product_id varchar2(50), price number , effective_date date);

insert into price values (1,400,to_Date('01-Jan-2019','DD-MON-YYYY'));
insert into price values (2,300,to_Date('01-Jan-2019','DD-MON-YYYY'));
insert into price values (1,400,to_Date('02-Jan-2019','DD-MON-YYYY'));
insert into price values (2,300,to_Date('02-Jan-2019','DD-MON-YYYY'));
insert into price values (1,500,to_Date('03-Jan-2019','DD-MON-YYYY'));
insert into price values (2,300,to_Date('03-Jan-2019','DD-MON-YYYY'));
insert into price values (1,500,to_Date('04-Jan-2019','DD-MON-YYYY'));
insert into price values (2,300,to_Date('04-Jan-2019','DD-MON-YYYY'));
insert into price values (1,600,to_Date('05-Jan-2019','DD-MON-YYYY'));
insert into price values (2,400,to_Date('05-Jan-2019','DD-MON-YYYY'));
insert into price values (1,600,to_Date('06-Jan-2019','DD-MON-YYYY'));
insert into price values (2,400,to_Date('06-Jan-2019','DD-MON-YYYY'));
```

<details>
<summary>Answer</summary>
  
```sql
select distinct product_id , price ,ranges , first_value(effective_Date) over(partition by ranges , product_id order by effective_Date rows between unbounded preceding and UNBOUNDED FOLLOWING ) begin_dt , 
last_value(effective_Date) over(partition by ranges, product_id order by effective_Date rows between unbounded preceding and UNBOUNDED FOLLOWING ) end_dt from(
select product_id , price , sum(case when price <> lag then 1 else 0 end)  over(partition by product_id order by effective_date) ranges , effective_Date from (
select product_id , price , lag(price) over(partition by product_id order by effective_date) lag, effective_Date from price )) order by 3;

select min(effective_date) begin_dt , max(effective_Date) end_dt , price , product_id  from(
select 
sum(case when lag_price <> price then 1 else 0 end) over(partition by product_id order by effective_Date ) rng , product_id , effective_Date, price
from
(select lag(price) over(partition by product_id order by effective_Date)  lag_price , price , effective_Date, product_id  from price ))
group by price , product_id , rng;
```
</details>

## Sort in Python
#### Input arr=[8,6,10,4,1]

<details>
<summary>Answer</summary>
  
```python
def heapify(arr,n,i):
    largest = i
    l=2*i+1
    r=2*i+2
    if l < n and arr[largest] < arr[l]:
        largest=l
    if r < n and arr[largest] < arr[r]:
        largest=r
    if largest != i:
        arr[i],arr[largest]=arr[largest],arr[i]
        heapify(arr,n,largest)
def heapsort(arr):
    n=len(arr)
    for i in range(n,-1,-1):
        heapify(arr,n,i)
    for i in range(n-1,0,-1):
        arr[i],arr[0]=arr[0],arr[i]
        heapify(arr,i,0)
```
</details>

<details>
<summary>Answer</summary>
  
```python
def merge(arr,p,q,r):
    n1=q-p+1
    n2=r-q
    L,R=[None]*(n1+1),[None]*(n2+1)
    for i in range(0,n1):
        L[i]=arr[p+i]
    for j in range(0,n2):
        R[j]=arr[q+j+1]
    L[n1],R[n2]=math.inf,math.inf
    i,j=0,0
    for k in range(p,r+1):
        if L[i] <= R[j]:
            arr[k]=L[i]
            i=i+1
        else:
            arr[k]=R[j]
            j=j+1
In [25]: def merge(arr,p,q,r): 
    ...:     L=arr[p:q+1] 
    ...:     R=arr[q+1:r+1] 
    ...:     L.append(math.inf) 
    ...:     R.append(math.inf) 
    ...:     i,j=0,0 
    ...:     for k in range(p,r+1): 
    ...:         if L[i] <= R[j]: 
    ...:             arr[k]=L[i] 
    ...:             i=i+1 
    ...:         else: 
    ...:             arr[k]=R[j] 
    ...:             j=j+1 
def merge_sort(A,p,r):
    if p < r:
        q=(p+r)//2
        merge_sort(A,p,q)
        merge_sort(A,q+1,r)
        merge(A,p,q,r)
        
def median(arr):
    heapsort(arr)
    if len(arr) % 2 == 0:
        n=len(arr)//2
        return (arr[n]+arr[n-1])/2
    else:
        n=len(arr)//2
        return arr[n]

```
</details>

## Execute commands on all servers and return if timeout occurs

<details>
<summary>Answer</summary>
  
```bash
ssh user1@server1 timeout 5 date
```
</details>

## Consecutive winning streak

```sql
create table MATCH_RESULTS
(
MATCH_ID NUMBER GENERATED ALWAYS AS IDENTITY,
TEAMA VARCHAR2(255),
TEAMB VARCHAR2(255),
WINNER VARCHAR2(255)
);

insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('IND','WI','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('SA','WI','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('IND','AUS','IND');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('WI','ENG','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('PAK','WI','PAK');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('IND','SA','IND');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('SA','ENG','ENG');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('ENG','AUS','AUS');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('AUS','PAK','AUS');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('PAK','WI','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('WI','IND','IND');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('IND','ENG','IND');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('IND','PAK','IND');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('WI','AUS','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('ENG','WI','WI');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('ENG','SA','ENG');
insert into MATCH_RESULTS (TEAMA, TEAMB, WINNER) VALUES('ENG','IND','ENG');
```

<details>
<summary>Answer</summary>
  
```sql
select 
team ,
lag_winner,
sum(case when winner <> team or winner <> lag_winner then 1 else 0 end) over(partition by team order by match_id rows unbounded preceding) cond ,
match_id,
winner 
from (
with teams as
(select teama team from match_results mr1  
union 
select teamb team from match_results mr2 )
select 
team ,
lag(mr.winner) over(partition by team order by match_id) lag_winner,
--sum(case when mr.winner <> team  or mr.winner <> lag(mr.winner) over(partition by team order by match_id)  then 1 else 0 end) over(partition by team order by match_id rows unbounded preceding) cond ,
match_id,
mr.winner 
from teams t cross join match_results mr 
where t.team = mr.teama or t.team=mr.teamb 
)
order by 1,match_id;
```
</details>

## Users were active in the month of January.

```sql
create table user_details 
( user_id NUMBER GENERATED ALWAYS AS IDENTITY,
start_dt DATE , 
end_dt DATE );

insert into user_Details(start_dt,end_dt) values ('01-Jul-2019','01-Aug-2019');
insert into user_Details(start_dt,end_dt) values ('01-Jul-2019','01-Jan-2020');
insert into user_Details(start_dt,end_dt) values ('01-Jan-2020','31-Jan-2020');
insert into user_Details(start_dt,end_dt) values ('15-Jan-2020','01-Feb-2020');
insert into user_Details(start_dt,end_dt) values ('01-Feb-2020','10-Feb-2020');
insert into user_Details(start_dt,end_dt) values ('01-Jul-2019','10-Feb-2020');
```

<details>
<summary>Answer</summary>
  
```sql
select * from user_details where end_dt >= '01-Jan-2020' and start_dt <='31-Jan-2020' ; 
```
</details>

## Worst case and Best case with joins 

```sql
DROP TABLE tb1;
DROP TABLE tb2;
CREATE TABLE TB1(
pk NUMBER);

CREATE TABLE TB2(
pk NUMBER);

insert into tb1 values(1);
insert into tb1 values(1);
insert into tb1 values(1);
insert into tb1 values(2);
insert into tb1 values(3);

insert into tb2 values(1);
insert into tb2 values(1);
insert into tb2 values(3);
insert into tb2 values(4);

select * from tb1 inner join tb2 using(pk) ;
select * from tb1 left outer join tb2 using(pk) ;
select * from tb1 right outer join tb2 using(pk) ;
select * from tb1 full outer join tb2 using(pk) ;
select * from tb1 cross join tb2 ;
```
<details>
<summary>Answer</summary>
7, 8, 8, 9, 20
</details>

## Find a file and archive it 

<details>
<summary>Answer</summary>
 
```bash
find <Path_To_Old_Files> -type f -mtime +30 | xargs rm -f
```
</details>

## Incremental data load

<details>
<summary>Answer</summary>
 
Use audit dimension or hash values to compare data.

</details>

## Difference between range and xrange.

<details>
<summary>Answer</summary>
 
range returns list and xrange returns generator objects.

</details>

## Use awk to divide the file between even and odd number of lines


<details>
<summary>Answer</summary>
 
```bash
awk '{ if ( NR % 2 == 0 ) print $0 >> "even.txt";if ( NR % 2 == 1 ) print $0 >> "odd.txt" }' traceexecution.py
awk '{ if ( NR % 2 == 0 ) print $0 >> "even.txt" ;else print $0 >> "odd.txt" }' traceexecution.py
```

</details>

## Delete empty records in a file

<details>
<summary>Answer</summary>
 
```bash
sed '/^$/d' even.txt
```

</details>

## Three consecutive seats availability in theatres.

```sql
create table seats(
seat_id NUMBER GENERATED ALWAYS AS IDENTITY,
AVAILABILITY VARCHAR2(1)
);

insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('N');
insert into seats(availability) values('Y');
insert into seats(availability) values('N');
insert into seats(availability) values('N');
insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('N');
insert into seats(availability) values('N');
insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('Y');
insert into seats(availability) values('N');
```

<details>
<summary>Answer</summary>
 
```sql
select * from seats s1 where  s1.availability ='Y' and 'Y'= ALL(select s2.availability from seats s2 where s2.seat_id between s1.seat_id and s1.seat_id + 2 ) order by 1 ;
```

</details>

## Create all combinations of teams from one table.

```sql
create table teams(
team varchar2(10)
);

insert into teams values('IND');
insert into teams values('SA');
insert into teams values('ENG');
insert into teams values('AUS');
```
<details>
<summary>Answer</summary>
 
```sql
select t1.team, t2.team from teams t1 cross join teams t2 where t1.team < t2.team ;
```

</details>

## How to handle late arriving dimensions ?

<details>
<summary>Answer</summary>
Derive dimensional context and then load fact table and then later update when dimensional data comes. 
</details>

## How to reload corrupt data as quickly as possible ?

<details>
<summary>Answer</summary>
By using audit dimension and delete them .
</details>

## Frequently brought products in a table.

```sql
create table order_line
(
order_id number ,
order_line_id number,
product varchar2(1)
);

insert into order_line values(1, 1, 'A');
insert into order_line values(1, 2, 'B');
insert into order_line values(1, 3, 'C');
insert into order_line values(1, 4, 'D');

insert into order_line values(2, 1, 'B');
insert into order_line values(2, 2, 'C');

insert into order_line values(3, 1, 'D');
insert into order_line values(3, 2, 'A');

insert into order_line values(4, 1, 'B');
insert into order_line values(4, 2, 'A');

insert into order_line values(5, 1, 'C');
insert into order_line values(5, 2, 'A');

insert into order_line values(6, 1, 'C');
insert into order_line values(6, 2, 'A');
insert into order_line values(6, 3, 'B');

insert into order_line values(7, 1, 'A');
insert into order_line values(7, 2, 'C');
insert into order_line values(7, 3, 'D');
```
<details>
<summary>Answer</summary>
  
```sql
select 
case when ol1.product < ol2.product then ol1.product else ol2.product end prodA , 
case when ol1.product < ol2.product then ol2.product else ol1.product end prodB,
count(*)  from order_line ol1 inner join  order_line ol2 
on ol1.order_id=ol2.order_id where ol1.order_line_id<ol2.order_line_id 
group by 
case when ol1.product < ol2.product then ol1.product else ol2.product end , 
case when ol1.product < ol2.product then ol2.product else ol1.product end ;
```
</details>

## Design a movie booking system

<details>
<summary>Answer</summary>
  
```sql
create table movie(
movie_id number,
movie_name varchar2(255),
movie_language varchar2(100));

create table auditorium(
auditorium_id number,
theatre_id number);

create table theatre(
theatre_id number,
theatre_name varchar2(100));

create table seats(
seat_id number,
row_number number,
column_no varchar2(1),
auditorium_id number);

create table screening(
screening_id number,
auditorium_id number,
movie_id number,
starttime date);

create table reservation(
reservation_id number,
customer_id number,
payment_type number 
);

create table seat_booking(
seat_id number,
screening_id number,
reservation_id number);

```
</details>

## Create a data model for IPL considering we have to calculate how many batsman have scored more than 15% runs as compared to last year.

<details>
<summary>Answer</summary>
  
```sql
select 
batsmen_id,
year
from(
select 
batsmen_id, 
year, 
(lag(sum_run) over(partition by batsmen_id, year) - sum_run)/sum_run *100 inc_pct
(
select sum(runs) sum_run , batsmen_id, year  from runs 
group by batsmen_id, year )) where inc_pct > 15;

```
</details>

## Check which department has more combined salary than 500000.

<details>
<summary>Answer</summary>
  
```sql
select d.department_id from 
employees e 
join departments d 
on e.department_id=d.department_id
group by d.department
having sum(e.salary) > 500000;
```
</details>

## Student class and schools.

<details>
<summary>Answer</summary>
Preaggregate class and school attendance.
</details>

## Role Playing Dimensions.

<details>
<summary>Answer</summary>
One dimension which can be used in multiple ways just like Date dimension.
</details>

## Compare current week’s data to previous year’s  corresponding week’s data.

<details>
<summary>Answer</summary>
  
```sql
select (next_day(trunc(sysdate+10),'MONDAY') - next_day(trunc(sysdate,'YYYY')- 7 , 'MONDAY'))/7 from dual;
```
</details>

## SQL for Merge SCD2 Type

```sql

create table stg_dim(
natural_key varchar2(100),
col1 varchar2(100),
col2 varchar2(100));

create table dim(
dim_key number,
natural_key varchar2(100),
col1 varchar2(100),
col2 varchar2(100),
eff_dt date ,
exp_dt date default to_date('99991231','YYYYMMDD') NOT NULL);

drop table dim ;
drop table stg_dim ;

insert into stg_dim values ('ABC','a','b');
insert into stg_dim values ('XYZ','g','r');
insert into stg_dim values ('YUI','d','o');

insert into dim values(1,'ABC','a','c',to_date('20190701','YYYYMMDD'),to_date('20190708','YYYYMMDD'));
insert into dim values(2,'ABC','a','d',to_date('20190709','YYYYMMDD'),to_date('99991231','YYYYMMDD'));
insert into dim values(3,'XYZ','g','s',to_date('20190706','YYYYMMDD'),to_date('99991231','YYYYMMDD'));

```

<details>
<summary>Answer</summary>
  
```sql

merge into dim d using(
select sd1.* , 'U' upd_ind , d1.dim_key from 
stg_dim sd1
left join 
dim d1 on d1.natural_key=sd1.natural_key and d1.exp_dt=to_date('99991231','YYYYMMDD') 
union all
select sd2.* ,'I' upd_ind , null dim_key from stg_dim sd2) s
on (s.dim_key=d.dim_key )
when matched  then
update set d.exp_dt=sysdate - 1 where upd_ind='U'
when not matched  then
insert values ( 1,s.natural_key,s.col1,s.col2,trunc(sysdate),to_date('99991231','YYYYMMDD'))
where upd_ind='I';

select * from dim ;
```

</details>
  
## Hotel reservation data model

<details>
<summary>Answer</summary>

```sql
create table hotel_tables(
hotel_table_id number,
hotel_table_capacity number);

select * 
from 
hotel_tables 
left outer join 
booking 
on ht.hotel_table_id=b.hotel_table_id
and b.date=:date
and b.time between :time-15 and :time+15
where 
b.hotel_table_id is null
and ht.hotel_table_capacity = :capacity;
```

</details>

## Last 3 orders of a customer

<details>
<summary>Answer</summary>

```sql
create table orders(
order_id number,
customer_id number,
order_date date,
order_time timestamp(6),
order_amount number);

create table order_line(
order_id number,
order_line_id number,
product_id number,
delivery_address_id number);

create table deliver_address(
delivery_address_id number,
address_line_1 varchar2(50),
address_line_2 varchar2(50),
address_line_3 varchar2(50),
pin number,
state varchar2(50));

select * from 
orders join
order_line  using(order_id)
join 
deliver_address using(delivery_address_id)
where customer_id= :customer_id ;

```
</details>

## Top five views per year and increase consistent views per year

<details>
<summary>Answer</summary>

```sql
create table song_dim (
song_id number,
song_name varchar2(255));

create table views_fact(
song_id number,
views number,
eff_dt date)

create table date_dim(
eff_dt date,
eff_year number
);


select song_id , eff_year , song_pop from(
select song_id , eff_year , dense_rank() over(partition by song_id, eff_year order by song_pop desc) rnk, song_pop from(
select 
vf.song_id , dd.eff_year , count(vf.views) song_pop
from views_fact vf
join date_dim dd
using(eff_dt)
-- join song_dim sd
-- using(song_id)
group by vf.song_id , dd.eff_year)) where rnk >= 5;

with t as (
select 
vf.song_id , dd.eff_year , count(vf.views) song_pop
from views_fact vf
join date_dim dd
using(eff_dt)
-- join song_dim sd
-- using(song_id)
group by vf.song_id , dd.eff_year))
select song_id , eff_year , song_pop 
from t t1 where t1.song_pop >=ALL(select t2.song_pop from t t2 where t1.song_id=t2.song_id AND t2.eff_year between t1.eff_year -2 and t1.eff_year );

```

</details>

## Pivot without using pivot function

<details>
<summary>Answer</summary>
  
```sql
with t as (
select 
sum(case when d.deptno=30 then e.sal end) sum_30, 
sum(case when d.deptno=10 then e.sal end) sum_10,
sum(case when d.deptno=20 then e.sal end) sum_20
from 
scott.emp e join 
scott.dept d 
on e.deptno=d.deptno 
group by d.deptno )
select max(sum_30) sum_30, max(sum_10) sum_10, max(sum_20) sum_20 from t;
```
</details>

## Apply lag function without using lag function

Order_day| Processing_Day | Quantity| Order_id

```sql
create table 
orders (
Order_day date ,  Processing_Day date ,  Quantity NUMBER , Order_id NUMBER);

insert into orders values('12-FEB-2020','13-FEB-2020', 2, 1); 
insert into orders values('12-FEB-2020','15-FEB-2020', 4, 1);
insert into orders values('12-FEB-2020','16-FEB-2020', 5, 1);
insert into orders values('12-FEB-2020','18-FEB-2020', 3, 1);
insert into orders values('11-FEB-2020','19-FEB-2020', 2, 3);
insert into orders values('11-FEB-2020','22-FEB-2020', 10, 3);
insert into orders values('11-FEB-2020','21-FEB-2020', 8, 3);
insert into orders values('11-FEB-2020','27-FEB-2020', 17, 3);
```

Processing_Day | Order_day | Order_id | change_in_quantity

<details>
<summary>Answer</summary>

```sql
select 
* 
from
orders o1 
left outer join 
orders o2 
on o1.order_day=o2.order_Day and o1.order_id=o2.order_id
and o2.processing_day = (select max(o3.processing_Day) from  orders o3 where o1.order_day=o3.order_day and o1.order_id=o3.order_id and o3.processing_day < o1.processing_Day); 

```
</details>

## Count how many employee id are under a manager table. 

Empid | Manager_id

<details>
<summary>Answer</summary>

```sql
select e1.ename  from scott.emp e1 
left outer join 
(select e.mgr emp from scott.emp e group by mgr having count(*) > 3) e2
on e1.empno=e2.emp;

```
</details>

## Total value for a seller on a day

| Seller_id  | Start_Date | end_Date | Seller_name |
Order_id | Order_day | Seller_id | Price|Quantity

<details>
<summary>Answer</summary>

```sql

select 
s.seller_id , sum(price*quantity) 
from 
seller s 
left outer join 
order o
on s.seller_id=o.seller_id and o.order_day between s.start_Date and s.end_Date
group by s.seller_id ;

```

</details>

## Complex Problem 

Situation

1. Migrate legacy data warehouse to new data warehouse/data model of approx. 10 TB containing data from 2007 till present.
2. Legacy datawarehouse had normalization and poor data model which created problem in developing and maintaining reports. 
3. Migrating for 3 months in lower environments took 2 days , extrapolating gives (12/3)*(2019-2007)*2 = 96 days

Task

1. Reduce time for migration. 
2. Keep CPU , RAM in check.

Action

1. Create partitions of 7 days.
2. Use Python Multi-threading to process 7 days chunk in one thread. 
3. Maintain 4-6 threads at a time to keep CPU , RAM in check. 
4. Use CTAS in place of conventional INSERT.

Result

3 months data took only 5 mins ultimately on prod day it got completed in 240 mins or 6 hours hence saving almost 90 days of effort and consumption. 

## How Uber can enhance their app?

1. Option to chat within the app with Customer support .
2. Ability to select your driver.
3. Analysis of Review via graph
4. System through which destination of customer is shared with driver.

## Uber system design 

1. Supply and demand service

2. Every car sends lat and long after every 5 secs.

3. DISPATCH Optimization
  a) Uber uses Google S2 which divides earth into small cells with unique cell id.
  b) S2 can give a coverage of a shape for example a circle of radius 1 km etc.
  c) Cell id is used as a sharding key to find data more quickly. 
  d) As per sharding key, Uber calculates distance by road system and sort it for better supply.

4. Scaling of dispatch system is done via Node.js with ringpop.

5. Apache Kafka's API's are used to send geo data to datacentre.

6. Historical time is used to calculate ETA's. 

7. Use either AI or Djisktra Algorithm to calculate ETA's.

8. Intersections are nodes and roads are edges.

9. Djisktra's algorithm is impractical for millions of nodes so use Contraction hierarchies where shortcuts , highways and other inputs can be given for pre-processing. Roads changes rarely so this pre-processing even if it takes hours can be afforded. 

10. Logging is done again via Kafka.

## Netflix system design 

1. Other than serving video everything is handled by AWS. 

2. Serving video is done by Open Connect ( A custom Content delivery Network).

3. Files are transcoded for different speed and devices.

4. Movie recommendations logging and all other things are done in AWS.

## Movie Reviewer Data Model

```sql
create table movie 
(
movie_id number,
movie_name varchar2(255)
);

create table reviewer
(
reviewer_id number,
reviewer_name varchar2(255)
);

create table rating
(
rating_id number,
movie_id number,
reviewer_id number,
rating_date date,
ratings number
);

insert into movie values (1,'A');
insert into movie values (2,'B');
insert into movie values (3,'C');
insert into movie values (4,'D');
insert into movie values (5,'E');

insert into reviewer values (1,'aa');
insert into reviewer values (2,'bb');
insert into reviewer values (3,'cc');
insert into reviewer values (4,'dd');
insert into reviewer values (5,'ee');
insert into reviewer values (6,'ff');

insert into rating values(1,1,2,to_date('20170201','YYYYMMDD'),3.1);
insert into rating values(2,4,4,to_date('20180301','YYYYMMDD'),4.2);
insert into rating values(3,1,5,to_date('20190401','YYYYMMDD'),5);
insert into rating values(4,3,1,to_date('20170501','YYYYMMDD'),3.3);
insert into rating values(5,6,3,to_date('20180601','YYYYMMDD'),4.4);
insert into rating values(6,2,2,to_date('20190701','YYYYMMDD'),5);
insert into rating values(7,5,1,to_date('20200801','YYYYMMDD'),3.6);
insert into rating values(8,2,3,to_date('20170901','YYYYMMDD'),4.5);
insert into rating values(9,1,4,to_date('20181001','YYYYMMDD'),5);
insert into rating values(10,5,1,to_date('20170201','YYYYMMDD'),3.7);
insert into rating values(11,2,5,to_date('20170201','YYYYMMDD'),4.5);
insert into rating values(12,3,6,to_date('20170201','YYYYMMDD'),3.5);
insert into rating values(13,2,3,to_date('20180201','YYYYMMDD'),4.7);
insert into rating values(14,1,4,to_date('20180301','YYYYMMDD'),4);
insert into rating values(15,5,1,to_date('20180401','YYYYMMDD'),3.8);
insert into rating values(16,2,5,to_date('20180501','YYYYMMDD'),3.9);
insert into rating values(17,3,6,to_date('20180601','YYYYMMDD'),4.5);

```

### Those who reviewed movie better than first time.(with and without analytical functions)

<details>
<summary>Answer</summary>

```sql

select re.reviewer_name from (
select 
reviewer_id , 
ratings,
lag(ratings) over(partition by movie_id, reviewer_id order by rating_date ) lag_rating
from rating 
) r 
left outer join reviewer re on  r.reviewer_id=re.reviewer_id
where ratings > lag_rating ;

select 
re.reviewer_name
from 
reviewer re
left outer join (
select 
ra1.*,
ra2.ratings lag_ratings
from 
rating ra1 
left outer join 
rating ra2
on ra1.movie_id=ra2.movie_id and ra1.reviewer_id=ra2.reviewer_id 
where ra2.rating_date = (select max(rating_date) from rating ra3 where ra3.reviewer_id=ra1.reviewer_id and ra3.movie_id=ra1.movie_id and ra3.rating_date < ra1.rating_date 
)) r 
on re.reviewer_id = r.reviewer_id 
where ratings > lag_ratings  ;

```
</details>

### Create a report with reviewername|2017|2018|2019

<details>
<summary>Answer</summary>
  
```sql
select 
re.reviewer_name , 
sum_rating."2017",
sum_rating."2018",
sum_rating."2019"
from 
reviewer re 
left outer join
(
select 
sum(case when to_char(rating_date,'YYYY') = '2017' then 1 else 0 end) as "2017" ,
sum(case when to_char(rating_date,'YYYY') = '2018' then 1 else 0 end) as "2018" ,
sum(case when to_char(rating_date,'YYYY') = '2019' then 1 else 0 end) as "2019" ,
reviewer_id 
from
rating ra 
group by reviewer_id) sum_rating
on sum_rating.reviewer_id = re.reviewer_id
;
```
</details>

### Reviewer name whose have not given rating date.

<details>
<summary>Answer</summary>

```sql
select 
distinct r.reviewer_name
from 
reviewer r 
left outer join
rating ra
on r.reviewer_id=ra.reviewer_id
where rating_date is null;

```
</details>

## Print dept and emp with max salary(analytical fns , group by IN clause, joins)

<details>
<summary>Answer</summary>

```sql
select 
e1.* 
from scott.emp e1 
join (
select 
max(sal) max_sal,
deptno
from
scott.emp 
group by deptno ) e2 
on e1.sal=e2.max_sal and e1.deptno=e2.deptno;

```
</details>

## Find batsman who scored 3 consecutive dots. 

Innid|Overid|Ball_num|Batsman|Bowler|Runs_scored|Is_wide|Is_noball|Is_freehit

<details>
<summary>Answer</summary>

```sql

select 
sum(case when lag_run_Scored <> runs_scored then 1 else 0 end)
over(partition by innid,batsman order by over_id,ball_num) lag_run_scored, 
batsman,
runs_scored
from(
select 
lag(runs_scored) over(partition by innid,batsman order by over_id,ball_num) lag_run_scored, 
batsman,
runs_scored
from match_details md
where is_wide='N' and is_noball='N' ) 

```

</details>
  
## All combination with NULL and joins

```sql
CREATE TABLE TB1(
pk NUMBER);

CREATE TABLE TB2(
pk NUMBER);

insert into tb1 values(1);
insert into tb1 values(1);
insert into tb1 values(1);
insert into tb1 values(2);
insert into tb1 values(3);
insert into tb1 values(null);

insert into tb2 values(1);
insert into tb2 values(1);
insert into tb2 values(3);
insert into tb2 values(4);
insert into tb2 values(null);

select * from tb1 inner join tb2 using(pk) ;
select * from tb1 left outer join tb2 using(pk) ;
select * from tb1 right outer join tb2 using(pk) ;
select * from tb1 full outer join tb2 using(pk) ;
select * from tb1 cross join tb2 ;
```

<details><summary>Answer</summary>

7,9,9,11,30
  
</details>  

## Find minimum number of changes in a string to convert it into Pallindrome.

<details>
<summary>Answer</summary>

```python

In [36]: def pallindrome(string): 
    ...:     cnt_steps=0 
    ...:     for i in range(len(string)//2): 
    ...:         if string[i] != string[(i+1)*-1]: 
    ...:             cnt_steps=cnt_steps + 1 
    ...:     return cnt_steps 
    ...:      
    ...:   

```
</details>

## Find files which has been updated in last hour.

<details>
  <summary>Answer</summary>

```bash

find . -mtime -1

```

</details>

## Find all files in a directory with last name as .pyc (in python and UNIX)

<details>
  <summary>Answer</summary>
  
```python
 import os
 for path, dirs, files in os.walk('.'):
     for file in files :
         if file.endswith('.pyc'):
             print(file)

```

```bash

find . -name "*.pyc"

```
</details>

## Ticket table , Audit Table Id
TID|Impact|CreateTime|
AID|TID|CreateTime|Team

Tickets count Group per week basis on Team, Impact

<details>
<summary>Answer</summary>
  
```sql

select
to_week(createtime) , team,impact,count(*)
from(
select 
distinct t.* , a.team
from 
ticket t
join
audit a 
on t.tid=a.tid)
group by to_week(createtime) , team,impact

```

</details>

## Backfill data like files missing on 12th process date after 10 days.   

<details>
  <summary>Answer</summary>
  
1. Insert those records which are received only on 12th process date
2. Update those records for which latest was received on 12th only.

</details>


## Explain when you disagree with someone.

<details>
  <summary>Answer</summary>
  
  1. Disagreed regarding tuning for performance issues. 
  2. Created a demo and a technical documentation.
  3. Gave a 5 min presentation with clear benefits quantitatively. 
  4. Approached senior management as well with clear and crisp problem statement and solution. 
  
  </details>

## Explain when you helped someone. 

<details><summary>Answer</summary>
  
  1. Testers needed to reconcile data between two databases. 
  2. Created utility extracting difference between two datasets.
  3. Using multithreading to speed up its performance. 
  
  </details>
  
## How to motivate someone who is not motivated ?

<details><summary>Answer</summary>

1. Informal catchup with the guy everyday for 2-3 weeks asking about skills he is interested in and his opinion of projects.
2. Made sure to bring to everyone's notice how good of a work he is doing. 
3. Asked what technology he is most interested in and then arranged for his inclusion even if it meant putting in some extra hours. 

</details>  

## Select all customer id and its latest version.

```sql
create table customer_hist(
customer_id number,
customer_prev_id number,
customer_succ_id number);

insert into customer_hist values(100,95,102);
insert into customer_hist values(101,96,105);
insert into customer_hist values(102,100,104);
insert into customer_hist values(103,99,106);
insert into customer_hist values(107,88,111);
```

<details>
<summary>Answer</summary>

```sql
with tab1 as (
select customer_prev_id cust_id , customer_id cust_prev_id from customer_hist
union
select customer_id cust_id , customer_succ_id cust_prev_id from customer_hist)
, t1 as (select cust_id, cust_prev_id  , level lvl , CONNECT_BY_ROOT cust_prev_id cust_latest_id
from tab1
CONNECT BY PRIOR cust_id = cust_prev_id )
select cust_id, cust_latest_id from(
select cust_id, cust_latest_id , dense_rank() over(partition by cust_id order by lvl desc) rn , lvl from t1)
where rn =1 order by 1;
```
</details>

## Difference in salary with current employee and minimum salary greater than his/her.

<details>
<summary>Answer</summary>
  
```sql  
select employeeid , salary, lead(salary) over(order by salary) - salary as diff_salary   from Employee_Yearly_Salary;
```

</details>

## Printing all combinations with employees.

<details>
  <summary>Answer</summary>
  
```sql
with rec_table(empno,mgr,path) as
(
select empno , null as mgr , to_char(empno) path from scott.emp where mgr is null
union all
select e.empno , e.mgr , r.path || ',' || e.empno path from rec_table r join scott.emp e on e.mgr=r.empno )
select * from rec_table ;

```
</details>

## Find all products sold in november 2018

<details>
  <summary>Answer</summary>

```sql
select 
p.product_name
from
(select 
distinct ol.product_id  
from orders o
left outer join 
order_line on o.order_id=ol.order_id
left outer join date d on d.day=o.order_day
where d.month='November' and d.year=2018
) tbl
inner join products p 
on p.product_id=tbl.product_id
```
</details>

## Sales rep who sold most amount of products as per amount 

<details>
  <summary>Answer</summary>

```sql
select 
r.repr_name , sum(ol.amt)
from
orders o 
left join 
order_line ol
on o.order_id=ol.order_id
left join 
representative r 
on r.repr_id=o.repr_id 
group by r.repr_name 

```
</details>

## Each student with maximum marks and students

```sql
CREATE TABLE STUDENTS
(
student_id NUMBER ,
subject VARCHAR2(100),
marks NUMBER
);

insert into students values(1,'ENG',90);
insert into students values(1,'HIN',93);
insert into students values(1,'MATHS',92);
insert into students values(11,'ENG',97);
insert into students values(11,'HIN',93);
insert into students values(11,'MATHS',92);

```

<details>
  <summary>Answer</summary>
  
  ```sql
  
  select * from students where (student_id,marks) IN (
select student_id , max(marks) from students group by student_id );

select s1.* from students s1 inner join  (
select student_id , max(marks) as marks from students group by student_id ) s2
on s1.student_id=s2.student_id and s1.marks=s2.marks;

select student_id,marks,subject from
(select 
s1.student_id, s1.marks,s1.subject , dense_rank() over(partition by  student_id order by marks desc) rn 
from 
students s1) t
where rn=1;
  
  ```
</details>

## Running sum of customer data

```sql

CREATE TABLE customers 
(
customer_id NUMBER , 
month_id NUMBER ,
amount NUMBER
);

insert into customers values (1,1,100);
insert into customers values (1,2,200);
insert into customers values (1,4,150);
insert into customers values (2,5,100);
insert into customers values (2,12,200);
insert into customers values (2,7,200);

```

<details>
  <summary>Answer</summary>
  
  ```sql
  
  select 
c.*,
sum(amount) over(partition by customer_id order by month_id) running_sum
from customers c
  
  ```  
</details>

## Knapsack Problem

```sql
create table items 
(
id number , 
item_weight number , 
item_profit number 
);

insert into items values (1, 3, 10);
insert into items values (2, 4, 20);
insert into items values (3, 5, 30);
insert into items values (4,6 , 40);

```

<details>
<summary>Answer</summary>

```sql  
WITH rsf (nxt_id, lev, tot_weight, tot_profit, path) AS (
SELECT id nxt_id, 0 lev, item_weight tot_weight, item_profit tot_profit, To_Char (id) path
  FROM items
 UNION ALL
SELECT n.id, 
       r.lev + 1, 
       r.tot_weight + n.item_weight,
       r.tot_profit + n.item_profit,
       r.path || ',' || To_Char (n.id)
  FROM rsf r
  JOIN items n
    ON n.id > r.nxt_id
   AND r.tot_weight + n.item_weight <= 9
) SEARCH DEPTH FIRST BY nxt_id SET line_no 
SELECT LPad (To_Char(nxt_id), lev + 1, '*') node,tot_weight, tot_profit,
       CASE WHEN lev >= Lead (lev, 1, lev) OVER (ORDER BY line_no) THEN 'Y' END is_leaf,
       path
  FROM rsf
 ORDER BY line_no
 
``` 
</details> 
  
  
