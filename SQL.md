##### command
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
