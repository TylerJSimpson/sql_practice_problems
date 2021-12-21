---------------------------------------------------------
--SQLserver Northwind Database Beginner Practice Problems
--19 problems in total-----------------------------------
---------------------------------------------------------

--Problem 1
--Which shippers do we have?
SELECT
	*
FROM
	Shippers

--Problem 2
--Certain fields from Categories
SELECT
	CategoryName,
	Description
FROM
	Categories

--Problem 3
--Sales Representatives
SELECT
	FirstName,
	LastName,
	HireDate
FROM
	Employees
WHERE
	Title = 'Sales Representative'

--Problem 4
--Sales Representatives in the United States
SELECT
	FirstName,
	LastName,
	HireDate
FROM
	Employees
WHERE
	Title = 'Sales Representative'
AND
	Country = 'USA'

--Problem 5
--Orders placed by specific EmployeeID
SELECT
	OrderID,
	OrderDate
FROM
	Orders
WHERE
	EmployeeID = '5'

--Problem 6
--Suppliers and ContactTitles
SELECT
	SupplierID,
	ContactName,
	ContactTitle
FROM
	Suppliers
WHERE
	ContactTitle <> 'Marketing Manager'

--Problem 7
--Products with "queso" in ProductName
SELECT
	ProductID,
	ProductName
FROM
	Products
WHERE
	ProductName like '%queso%'

--Problem 8
--Orders shipping to France or Belgium
SELECT
	OrderID,
	CustomerID,
	ShipCountry
FROM
	Orders
WHERE
	ShipCountry = 'France'
OR
	ShipCountry = 'Belgium'

--Problem 9
--Orders shipping to any country in Latin America
SELECT
	OrderID,
	CustomerID,
	ShipCountry
FROM
	Orders
WHERE
	ShipCountry in ('Brazil', 'Mexico', 'Argentina', 'Venezuela')

--Problem 10
--Employees, in order of age
SELECT
	FirstName,
	LastName,
	Title,
	BirthDate
FROM
	Employees
ORDER BY
	BirthDate ASC

--Problem 11
--Showing only the Date with a DateTime field
SELECT
	FirstName,
	LastName,
	Title,
	CONVERT(date, BirthDate) AS BirthDate_Date
FROM
	Employees
ORDER BY
	BirthDate ASC

--Problem 12
--Employees full name
SELECT
	FirstName,
	LastName,
	CONCAT(FirstName,' ',LastName) AS FullName
FROM
	Employees

--Problem 13
--OrderDetails amount per line item
SELECT
	OrderID,
	ProductID,
	UnitPrice,
	Quantity,
	(Quantity * UnitPrice) AS TotalPrice
FROM
	OrderDetails
ORDER BY
	OrderID, ProductID

--Problem 14
--How many customers?
SELECT
	COUNT(DISTINCT(CustomerID)) AS TotalCustomers
FROM
	Customers

--Problem 15
--When was the first order?
SELECT
	MIN(CONVERT(date, OrderDate)) AS FirstOrderDate
FROM
	Orders

--Problem 16
--Countries where there are customers
SELECT
	DISTINCT(Country)
FROM
	Customers

--Problem 17
--Contact titles for customers
SELECT
	Count(*) as ContactTitleCount,
	ContactTitle
FROM
	Customers
GROUP BY
	ContactTitle
ORDER BY 1 ASC

--Problem 18
--Products with associated supplier names
SELECT
	ProductID,
	ProductName,
	CompanyName AS SupplierName
FROM
	Products Prod
		JOIN 
		Suppliers Supp
			ON Prod.SupplierID = Supp.SupplierID
ORDER BY
	ProductID

--Problem 19
--Orders and the Shipper that was used
SELECT
	OrderID,
	CONVERT(date, OrderDate) AS Dates,
	CompanyName AS ShipperName
FROM
	Orders Ord
		JOIN
		Shippers Ship
			ON Ord.ShipVia = Ship.ShipperID
WHERE
	OrderID < '10300'
ORDER BY
	OrderID ASC
