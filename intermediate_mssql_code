-------------------------------------------------------------
--SQLserver Northwind Database Intermediate Practice Problems
--12 (20-31) problems in total-------------------------------
-------------------------------------------------------------

--Problem 20
--Categories, and the total products in each category
SELECT
	CategoryName,
	TotalProducts = count(*)
FROM
	Products
	JOIN Categories
		ON Products.CategoryID = Categories.CategoryID
GROUP BY
	CategoryName
ORDER BY
	TotalProducts DESC

--Problem 21
--Total customers per country/city
SELECT
	City,
	Country,
	TotalCustomers = count(*)
FROM
	Customers
GROUP BY
	Country,
	City
ORDER BY
	TotalCustomers DESC,
	Country ASC,
	City ASC

--Problem 22
--Products that need reordering
SELECT
	ProductID,
	ProductName,
	UnitsInStock,
	ReorderLevel
FROM
	Products
WHERE
	UnitsInStock <= ReorderLevel
ORDER BY
	ProductID

--Problem 23
--Products that need reordering, continued
SELECT
	ProductID,
	ProductName,
	UnitsInStock,
	UnitsOnOrder,
	ReorderLevel,
	Discontinued
FROM
	Products
WHERE
	UnitsInStock + UnitsOnOrder <= ReorderLevel
	AND Discontinued <> 1
ORDER BY
	ProductID

--Problem 24
--Customer list by region
SELECT
	CustomerID,
	CompanyName,
	Region
FROM
	Customers
ORDER BY
	CASE
		WHEN Region IS NULL THEN 1
		ELSE 0
	END,
	Region ASC,
	CustomerID ASC

--Problem 25
--High freight charges
SELECT
	TOP 3 ShipCountry,
	AVG(Freight) AS AverageFreight
FROM
	Orders
GROUP BY
	ShipCountry
ORDER BY
	AverageFreight DESC

--Problem 26
--High freight charges - 1996
SELECT
	TOP 3 ShipCountry,
	AVG(Freight) AS AverageFreight
FROM
	Orders
WHERE
	OrderDate LIKE '%1996%'
GROUP BY
	ShipCountry,
	OrderDate
ORDER BY
	AverageFreight DESC

--Problem 27
--High freight charges with between
SELECT
	TOP 3 ShipCountry,
	CAST(OrderDate AS Date) AS Date,
	AVG(Freight) AS AverageFreight
FROM
	Orders
WHERE
	OrderDate BETWEEN '1996-01-01' AND '1996-12-31'
GROUP BY
	ShipCountry,
	OrderDate
ORDER BY
	AverageFreight DESC

--Problem 28
--High freight charges - last year
SELECT
	TOP 3 ShipCountry,
	AVG(Freight) AS AverageFreight
FROM
	Orders
WHERE
	OrderDate >= DATEADD(yy, -1, 
	(SELECT MAX(OrderDate) 
	FROM Orders))
GROUP BY
	ShipCountry
ORDER BY
	AverageFreight DESC

--Problem 29
--Inventory List
SELECT
	Employees.EmployeeID,
	Employees.LastName,
	Orders.OrderID,
	Products.ProductName,
	[Order Details].Quantity
FROM
	Employees
	JOIN Orders
		ON Employees.EmployeeID = Orders.EmployeeID
		JOIN [Order Details] 
			ON Orders.OrderID = [Order Details].OrderID
		JOIN Products
			ON [Order Details].ProductID = Products.ProductID
ORDER BY
	Orders.OrderID,
	Products.ProductID

--Problem 30
--Customers with no orders
SELECT
	Customers.CustomerID,
	Orders.CustomerID
FROM
	Customers
	LEFT JOIN Orders
	ON Customers.CustomerID = Orders.CustomerID
WHERE
	Orders.CustomerID IS NULL

--Problem 31
--Customers with no orders from EmployeeID 4
SELECT
	Customers.CustomerID,
	Orders.CustomerID
FROM
	Customers
	LEFT JOIN Orders
	ON Customers.CustomerID = Orders.CustomerID
	AND Orders.EmployeeID = 4
WHERE
	Orders.CustomerID IS NULL
