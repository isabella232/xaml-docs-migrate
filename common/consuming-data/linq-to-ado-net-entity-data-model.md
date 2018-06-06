---
title: Using LINQ to ADO.NET Entity Data Model
page_title: Using LINQ to ADO.NET Entity Data Model
description: Using LINQ to ADO.NET Entity Data Model
slug: consuming-data-linq-to-ado-net-entity-data-model
tags: using,linq,to,ado.net,entity,data,model
published: True
position: 10
---

# Using LINQ to ADO.NET Entity Data Model

The purpose of this article is to show you how to use __LINQ__ against __ADO.NET Entity Data Model__. It will cover how to:

* [Create the ADO.NET Entity Data Model](#create-the-adonet-entity-data-model)

* [Query an entity from the database](#query-an-entity-from-the-database)

* [Update an entity in the database](#update-an-entity-in-the-database)

* [Insert a new record(s) in the database](#insert-a-new-records-in-the-database)

* [Delete a record from the database](#delete-a-record-from-the-database)

* [Retrieve a record with Server Side Paging](#retrieve-a-record-with-server-side-paging)

>tipThis tutorial uses the __Northwind__ database, which can be downloaded from [here](https://northwinddatabase.codeplex.com/).

## Create the ADO.NET Entity Data Model

You can take advantage of the **Visual Studio Entity Data Model Wizard** to generate an Entity Data Model from the Northwind database automatically.

To do so, follow these steps:

1. Right-click on your project in the Solution Explorer window and select the menu option **Add -> New Item**.
2. In the **Add New Item** dialog, select the **Data** category.
3. Select the **ADO.NET Entity Data Model** template, give the Entity Data Model the name Northwind.edmx, and click the **Add** button. Clicking the **Add** button launches the **Data Model Wizard**.
4. In the **Choose Model Contents** step, choose the **EF Designer from Database** option and click the Next button.
5. In the **Choose Your Data Connection** step, select the Northwind.mdf database connection, enter the entities connection settings name NorthwindEntities, and click the Next button.
6. In the **Choose Your Database Objects and Settings** step, select the desired database tables, specify the model namespace and click the **Finish** button.

## Query an Entity from the Database

The code in __Example 1__ shows how to use LINQ query syntax to retrieve an __IEnumerable__ sequence of __Product__ objects.

#### __[C#] Example 1: Query Product by CategoryName__

{{region consuming-data-linq-to-ado-net-entity-data-model_0}}
	NorthwindEntities dbContext = new NorthwindEntities();
	var query = from p in dbContext.Products
				where p.Category.CategoryName == "Seafood"
				select p;
	IEnumerable<Product> products = query.ToList();
{{endregion}}

#### __[VB] Example 1: Query Product by CategoryName__

{{region consuming-data-linq-to-ado-net-entity-data-model_1}}
	Dim dbContext As New NorthwindEntities()
	Dim query = From p In dbContext.Products
		Where p.Category.CategoryName = "Seafood"
		Select p
	Dim products As IEnumerable(Of Product) = query.ToList()
{{endregion}}

## Update an Entity in the Database

The code in __Example 2__ demonstrates how to grab a single __Product__ object from the database, update its price, and then save the changes back to the database.

#### __[C#] Example 2: Update UnitPrice of Product__

{{region consuming-data-linq-to-ado-net-entity-data-model_2}}
	NorthwindEntities dbContext = new NorthwindEntities();
	Product product = dbContext.Products.First(p => p.ProductName == "Aniseed Syrup");
	product.UnitPrice = 1000;
	dbContext.SaveChanges();
{{endregion}}

#### __[VB] Example 2: Update UnitPrice of Product__

{{region consuming-data-linq-to-ado-net-entity-data-model_3}}
	Dim dbContext As New NorthwindEntities()
	Dim product As Product = dbContext.Products.First(Function(p) p.ProductName = "Aniseed Syrup")
	product.UnitPrice = 1000
	dbContext.SaveChanges()
{{endregion}}

## Insert a New Record(s) in the Database

The code in __Example 3__ shows you how to create a new __Category__ object. Then, it shows how to create two new __Products__ and associate them with the __Category__. Finally, all three objects are saved in the database.
        
#### __[C#] Example 3: Insert Products with new Category__

{{region consuming-data-linq-to-ado-net-entity-data-model_4}}
	NorthwindEntities dbContext = new NorthwindEntities();
	
	Category category = new Category();
	category.CategoryName = "Test Category";
	
	Product firstProduct = new Product();
	firstProduct.ProductName = "Test Product 1";
	
	Product secondProduct = new Product();
	secondProduct.ProductName = "Test Product 2";
	
	category.Products.Add( firstProduct );
	category.Products.Add( secondProduct );
	
	dbContext.Categories.Add(category);
	dbContext.SaveChanges();
{{endregion}}

#### __[VB] Example 3: Insert Products with new Category__

{{region consuming-data-linq-to-ado-net-entity-data-model_5}}
	Dim dbContext As New NorthwindEntities()
	
	Dim category As New Category()
	category.CategoryName = "Test Category"
	
	Dim firstProduct As New Product()
	firstProduct.ProductName = "Test Product 1"
	
	Dim secondProduct As New Product()
	secondProduct.ProductName = "Test Product 2"
	
	category.Products.Add(firstProduct)
	category.Products.Add(secondProduct)
	
	dbContext.Categories.Add(category)
	dbContext.SaveChanges()
{{endregion}}

## Delete a Record from the Database

__Example 4__ demonstrates you how to delete all 'Test' products from the database.

#### __[C#] Example 4: Delete a record based on a condition__

{{region consuming-data-linq-to-ado-net-entity-data-model_6}}
	NorthwindEntities dbContext = new NorthwindEntities();
	var query = from p in dbContext.Products
				where p.ProductName.Contains("Test")
				select p;
	foreach (Product p in query)
	{
		dbContext.Products.Remove(p);
	}
	dbContext.SaveChanges();
{{endregion}}

#### __[VB] Example 4: Delete a record based on a condition__

{{region consuming-data-linq-to-ado-net-entity-data-model_7}}
	Dim dbContext As New NorthwindEntities()
	Dim query = From p In dbContext.Products
				Where p.ProductName.Contains("Test")
				Select p
	For Each p As Product In query
		dbContext.Products.Remove(p)
	Next p
	dbContext.SaveChanges()
{{endregion}}

## Retrieve a Record with Server-side Paging

__Example 5__ shows you how to implement efficient server-side database paging. By using the __Skip()__ and __Take()__ methods, you will return 15 rows from the database - starting with row 300.

#### __[C#] Example 5:Server-side Paging__

{{region consuming-data-linq-to-ado-net-entity-data-model_8}}
	NorthwindEntities dbContext = new NorthwindEntities();
	var query = (from p in dbContext.Products
				where p.Category.CategoryName == "Aniseed Syrup"
				select p).Skip(300).Take(15);
	IEnumerable<Product> products = query.ToList();
{{endregion}}

#### __[VB] Example 5:Server-side Paging__

{{region consuming-data-linq-to-ado-net-entity-data-model_9}}
	Dim dbContext As New NorthwindEntities()
	Dim query = (From p In dbContext.Products
				Where p.Category.CategoryName = "Aniseed Syrup"
				Select p).Skip(300).Take(15)
	Dim products As IEnumerable(Of Product) = query.ToList()
{{endregion}}

## See Also  
{% if site.site_name == 'WPF' %}
 * [Consuming WCF Service]({%slug consuming-data-wcf-service%})
{% endif %}
 * [Consuming WCF Data Service]({%slug consuming-data-ado-net-data-service%})
{% if site.site_name == 'Silverlight' %} 
 * [Consuming Web (asmx) Service]({%slug consuming-data-web-asmx-service%})
{% endif %}
