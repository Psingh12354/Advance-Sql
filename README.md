<h1 align='center'>Advance-Sql</h1>

- Time [Refer](https://www.javatpoint.com/postgresql-time) or [Documentation](https://www.postgresql.org/docs/current/functions-datetime.html)
  - **Time-:** Contains time only
  - **Date-:** Contains date only 
  - **TIMESTAMP-:** Contain Date and Time
  - **TIMESTAMPTZ-:** Time stamp + Time Zone
  - **NOW-:** To return current time
  - **EXTRACT()-:** extract subcomponent like date from year
  
- Mathmetical Function [Refer](https://www.postgresql.org/docs/9.5/functions-math.html)

- String Functions & Operators [Refer](https://www.postgresql.org/docs/9.1/functions-string.html)

- SubQuery
```
Select x,y from test where y>(select avg(y) from test)
```

- Joins [Refer](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-joins/)

- Self join is a query to join the table in itself no special command only simple join required and on both side same table required.
``` 
select emp.name,report.name from employee as emp join employee as report on emp.emp_id = report.report_id
```

### Constraints
- Most commons are-:
  - Not Null
  - Unique
  - Primary Key
  - Foreign Key
  - Check(To check all values in a column satisfy certain condition)

### Create table
```
create table student(id SERIAL PRIMARY KEY,age SMALLINT NOT NULL);
```

### Check Constraints 
It is to put some condition like age>x
```
create table example(ex_id serial primary key, age smallint check(age>21));
```

### Case
- To apply condition similar to if else we have case is pgsql
```
select customer_id, 
CASE
when(customer_id<=100)_ then 'premimum'
when(customer_id between 100 and 200) then 'plus'
else 'Normal'
END
from customer;
```
- And can create a new class
```
select customer_id, 
CASE
when(customer_id<=100)_ then 'premimum'
when(customer_id between 100 and 200) then 'plus'
else 'Normal'
END as customer_class
from customer;
```

### Coalesce 
- When table contain null values it help to substitute it with another value.
``` 
# so here discount column contain 1 NULL values which make the final column row null so coalesce replace that null value and assign a new value 0 
select item,(price-coalesce(discount,0)) as final from table
```
