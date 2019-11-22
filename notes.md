--insert into geese (name) values ('Ben Aflack');
--create view Sales as
--select Employee.FirstName, Employee.LastName, Employee.Title, [Order].*
--from [Order]
--join Employee on [Order].EmployeeId = Employee.Id;


--list of products including the Product Category Name
--select c.CategoryName, p.ProductName as Product
--from [Product] as p --considered left for left join
--join Category as c on p.CategoryId = c.Id; --considered right

--list of customers & orders if there are any 16,789
--Select *
--from Customer as c
--join [Order] as o on c.iD = o.CustomerId
--order by c.Id;

--list of customers without orders
--Select *
--from Customer as c
--left join [Order] as o on c.iD = o.CustomerId
--order by c.Id;

--delete from [Order] where CustomerId = 'ALFKI'
--select * from [Order]
--delete from [Order]
--where CustomerId= 'ALFKI';

-- pretend the extra data is there
-- a join is the default "inner join"
-- list of orders including who sold it
--create view Sales as 
select Employee.FirstName, Employee.LastName, Employee.Title, [Order].*
from [Order]
join Employee on [Order].EmployeeId = Employee.Id;

-- list of products including the Product name and Category Name
select c.CategoryName as Category, p.ProductName as Product
from [Product] as p
join Category as c on p.CategoryId = c.Id;

-- delete orders to have the left join example work
select * from [Order]
--delete from [Order] 
where CustomerId = 'ALFKI';

-- list of customers and their orders if they have any (16,589)
select * 
from Customer as c
join [Order] as o on c.Id = o.CustomerId
order by c.Id;

-- list of customers that have no orders (16,590)
select * 
from Customer as c
left join [Order] as o on c.Id = o.CustomerId
order by c.Id;

/*GROUPING & AGGREGATE */
--Group first then aggregate an operation each group

--How many orders have been processed
select count(*) as [Total Orders] from [Order];

--grouping products by Category
select c.CategoryName as Category, count(*) as Products 
from [Product] as p
join Category as c on p.CategoryId = c.Id
group by c.CategoryName
order by c.CategoryName;

--what's cheapest product
select c.CategoryName as Category, min(p.UnitPrice) as Cheapest--p.UnitPrice is a column
from [Product] as p
join Category as c on p.CategoryId = c.Id
group by c.CategoryName
order by c.CategoryName;

--what's most expensive
select c.CategoryName as Category, max(p.UnitPrice) as Most_Expensive--p.UnitPrice is a column
from [Product] as p
join Category as c on p.CategoryId = c.Id
group by c.CategoryName
order by c.CategoryName;

--combined
select c.CategoryName as Category
    , count(*) as TotalProducts
    , max(p.UnitPrice) as Apple
    , min(p.UnitPrice) as Cheapest
from [Product] as p
join Category as c on p.CategoryId = c.Id
group by c.CategoryName
order by c.CategoryName;


--delete from users;
--delete from posts;

select * from  users;
select * from posts;

--find users posts

select p.contents as Message, u.username as PostedBy 
from users as u
join posts as p on u.id = p.user_id;

select p.contents as Message, u.username as PostedBy 
from users as u
join posts as p on u.id = p.user.id


