##### select
```
-- use database
use [sql intro];

exec sp_help;
exec sp_help people;
exec sp_help [car stock];

select * from dbo.People;
select [first name], [last name], [favorite color] from dbo.People;

select [favorite color] from dbo.People;
select distinct [favorite color] from dbo.People;

select distinct [favorite color] from dbo.People where [favorite color] is not null;

select [first name], [last name] from dbo.People where [favorite color] is null;
select [first name], [last name] from dbo.People where [favorite color] = 'WhiteSmoke';
select [favorite color] from dbo.People where [first name] = 'Sara' and [last name] = 'Abbott';

select count(*) from dbo.People where [favorite color] = 'WhiteSmoke';

select * from dbo.People where [favorite color] = 'gold';
select vin from dbo.[car stock] where color = 'gold';
select * from dbo.People cross join dbo.[car stock];
select * from dbo.People join dbo.[car stock] on dbo.People.[favorite color] = dbo.[car stock].color;
select dbo.People.[first name], dbo.People.[last name], dbo[car stock].vin from dbo.People join dbo.[car stock] on dbo.People.[favorite color] = dbo.[car stock].color;

```

##### insert
```
insert into people values ('clarabell', 'the clown', 'green');
insert into people([last name], [first name], [favorite color]) values ('clarabell', 'the clown', 'green');
insert into people values ('clarabell', 'the clown', default);

insert into people values 
('clarabell', 'test', default),
('clarabell', 'the clown', default);

--marx brothers table is not exist
select * into [marx brothers] from people where [last name] = 'marx';
select * from [marx brothers];

insert into [marx brothers] ([first name], [last name], [favorite color]) select [first name], [last name], [favorite color] from people where [last name] = 'kelly';
```

##### update
```
select * into people2 from people;
--change all to green
update people2 set [favorite color] = 'green';

update people3 set [favorite color] = 'puce' where [favorite color] = 'darkred';

--update single entity
update people3 set [favorite color] = 'green' where [first name] = 'roger' and [last name] = 'stevens';

update people2 set [favorite color] =
(
  select [favorite color] from people where
  people2.[first name] = people.[first name]
  and dbo.people2[last name] = people.[last name]
)
```

##### delete
```
--delete the content of the table
select * into people4 from people;
delete people4;

delete people5 where [first name] = 'toby';
delete people5 where [first name] = 'bud' and [last name] = 'abbott';
```

#####  create
```
create table points
(
[x coord] float,
[y coord] float
);

create table [points list]
(
[position] int identity primary key,
[x coord] float,
[y coord] float
);
insert into [points list] (position, [x coord], [y coord]) values (10, 2.3, 5.6);

create table People
(
[first name] varchar(40) not null,
[last name] varchar(40) not null,
[favorite color] varchar(15) null default 'willow blue',
constraint people_pk primary key ([first name], [last name])
);
```

##### alter table
```
alter table people add [favorite food] varchar(25) null default 'hot dog' with values;

drop table people;
```

##### 
```
重置自增长数
dbcc checkident([Asset],RESEED,0)
查询自增长数
dbcc checkident([表名],NORESEED)
```
