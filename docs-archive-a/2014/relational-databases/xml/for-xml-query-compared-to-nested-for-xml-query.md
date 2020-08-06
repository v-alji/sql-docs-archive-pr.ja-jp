---
title: FOR XML クエリと入れ子になった FOR XML クエリの比較 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], comparing query types
ms.assetid: 19225b4a-ee3f-47cf-8bcc-52699eeda32c
author: rothja
ms.author: jroth
ms.openlocfilehash: ca10060702d0c7e50f2be79310c55e177dca358d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743101"
---
# <a name="for-xml-query-compared-to-nested-for-xml-query"></a><span data-ttu-id="c6ba2-102">FOR XML クエリと入れ子になった FOR XML クエリの比較</span><span class="sxs-lookup"><span data-stu-id="c6ba2-102">FOR XML Query Compared to Nested FOR XML Query</span></span>
  <span data-ttu-id="c6ba2-103">ここでは、単一レベルの FOR XML クエリと入れ子になった FOR XML クエリを比較します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-103">This topic compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="c6ba2-104">入れ子になった FOR XML クエリを使用すると、たとえば、属性中心の XML と要素中心の XML の組み合わせをクエリの結果に指定できるなどの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-104">One of the benefits of using nested FOR XML queries is that you can specify a combination of attribute-centric and element-centric XML for query results.</span></span> <span data-ttu-id="c6ba2-105">次の例はこのことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-105">The example demonstrates this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ba2-106">例</span><span class="sxs-lookup"><span data-stu-id="c6ba2-106">Example</span></span>  
 <span data-ttu-id="c6ba2-107">次の `SELECT` クエリでは、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの製品カテゴリとサブカテゴリの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-107">The following `SELECT` query retrieves product category and subcategory information in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="c6ba2-108">このクエリには入れ子になった FOR XML はありません。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-108">There is no nested FOR XML in the query.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductCategory.ProductCategoryID,   
         ProductCategory.Name as CategoryName,  
         ProductSubCategory.ProductSubCategoryID,   
         ProductSubCategory.Name  
FROM     Production.ProductCategory, Production.ProductSubCategory  
WHERE    ProductCategory.ProductCategoryID = ProductSubCategory.ProductCategoryID  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="c6ba2-109">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-109">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory ProductSubCategoryID="1" Name="Mountain Bike"/>  
  <ProductSubCategory ProductSubCategoryID="2" Name="Road Bike"/>  
  <ProductSubCategory ProductSubCategoryID="3" Name="Touring Bike"/>  
</ProductCategory>  
...  
```  
  
 <span data-ttu-id="c6ba2-110">クエリに `ELEMENTS` ディレクティブを指定すると、次のフラグメントに示すように、要素中心の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-110">If you specify the `ELEMENTS` directive in the query, you receive an element-centric result, as shown in the following result fragment:</span></span>  
  
```  
<ProductCategory>  
  <ProductCategoryID>1</ProductCategoryID>  
  <CategoryName>Bike</CategoryName>  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <Name>Mountain Bike</Name>  
  </ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  </ProductSubCategory>  
</ProductCategory>  
```  
  
 <span data-ttu-id="c6ba2-111">次に示すように、生成する XML 階層が属性中心の XML と要素中心の XML の組み合わせだとします。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-111">Next, assume that you want to generate an XML hierarchy that is a combination of attribute-centric and element-centric XML, as shown in the following fragment:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="c6ba2-112">上のフラグメントに示した結果で、カテゴリ ID やカテゴリ名などの製品カテゴリの情報は属性です。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-112">In the previous fragment, product category information such as category ID and category name are attributes.</span></span> <span data-ttu-id="c6ba2-113">ただし、サブカテゴリの情報は要素中心です。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-113">However, the subcategory information is element-centric.</span></span> <span data-ttu-id="c6ba2-114"><`ProductCategory`> 要素を構築するには、次に示すような `FOR XML` クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-114">To construct the <`ProductCategory`> element, you can write a `FOR XML` query as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName  
FROM Production.ProductCategory ProdCat  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="c6ba2-115">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-115">This is the result:</span></span>  
  
```  
< ProdCat ProductCategoryID="1" CategoryName="Bikes" />  
< ProdCat ProductCategoryID="2" CategoryName="Components" />  
< ProdCat ProductCategoryID="3" CategoryName="Clothing" />  
< ProdCat ProductCategoryID="4" CategoryName="Accessories" />  
```  
  
 <span data-ttu-id="c6ba2-116">XML 内に入れ子構造の <`ProductSubCategory`> 要素を構築するには、次に示すような入れ子構造の `FOR XML` クエリを追加します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-116">To construct the nested <`ProductSubCategory`> elements in the XML you want, you then add a nested `FOR XML` query, as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName  
        FROM   Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="c6ba2-117">上のクエリに関して、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-117">Note the following in the previous query:</span></span>  
  
-   <span data-ttu-id="c6ba2-118">内側の `FOR XML` クエリは、製品サブカテゴリの情報を取得しています。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-118">The inner `FOR XML` query retrieves product subcategory information.</span></span> <span data-ttu-id="c6ba2-119">要素中心の XML を生成するために、内側の `ELEMENTS` に `FOR XML` ディレクティブを追加しています。ここで生成した XML は外側のクエリで生成される XML に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-119">The `ELEMENTS` directive is added in the inner `FOR XML` to generate element-centric XML that is added to the XML generated by the outer query.</span></span> <span data-ttu-id="c6ba2-120">既定では、外側のクエリで属性中心の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-120">By default, the outer query generates attribute-centric XML.</span></span>  
  
-   <span data-ttu-id="c6ba2-121">結果を `TYPE` xml **型にするために、内側のクエリに** ディレクティブを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-121">In the inner query, the `TYPE` directive is specified so the result is of **xml** type.</span></span> <span data-ttu-id="c6ba2-122">`TYPE` ディレクティブを指定しないと、結果は `nvarchar(max)` 型で返され、XML データはエンティティ化されます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-122">If `TYPE` is not specified, the result is returned as `nvarchar(max)` type and the XML data is returned as entities.</span></span>  
  
-   <span data-ttu-id="c6ba2-123">外側のクエリでも `TYPE` ディレクティブを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-123">The outer query also specifies the `TYPE` directive.</span></span> <span data-ttu-id="c6ba2-124">そのため、このクエリの結果は **xml** 型でクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-124">Therefore, the result of this query is returned to the client as **xml** type.</span></span>  
  
 <span data-ttu-id="c6ba2-125">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-125">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="c6ba2-126">次のクエリは単に上記のクエリを拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-126">The following query is just an extension of the previous query.</span></span> <span data-ttu-id="c6ba2-127">これによって、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに格納されている完全な製品階層が示されます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-127">It shows the full product hierarchy in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="c6ba2-128">これには、次の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-128">This includes the following:</span></span>  
  
-   <span data-ttu-id="c6ba2-129">製品カテゴリ</span><span class="sxs-lookup"><span data-stu-id="c6ba2-129">Product categories</span></span>  
  
-   <span data-ttu-id="c6ba2-130">各カテゴリの製品サブカテゴリ</span><span class="sxs-lookup"><span data-stu-id="c6ba2-130">Product subcategories in each category</span></span>  
  
-   <span data-ttu-id="c6ba2-131">各サブカテゴリの製品モデル</span><span class="sxs-lookup"><span data-stu-id="c6ba2-131">Product models in each subcategory</span></span>  
  
-   <span data-ttu-id="c6ba2-132">各モデルの製品</span><span class="sxs-lookup"><span data-stu-id="c6ba2-132">Products in each model</span></span>  
  
 <span data-ttu-id="c6ba2-133">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを理解するために、次のクエリが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-133">You might find the following query useful in understanding the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName,  
               (SELECT ProductModel.ProductModelID,   
                       ProductModel.Name as ModelName,  
                       (SELECT ProductID, Name as ProductName, Color  
                        FROM   Production.Product  
                        WHERE  Product.ProductModelID =   
                               ProductModel.ProductModelID  
                        FOR XML AUTO, TYPE)  
                FROM   (SELECT distinct ProductModel.ProductModelID,   
                               ProductModel.Name  
                        FROM   Production.ProductModel,   
                               Production.Product  
                        WHERE  ProductModel.ProductModelID =   
                               Product.ProductModelID  
                        AND    Product.ProductSubCategoryID =   
                               ProductSubCategory.ProductSubCategoryID)   
                                  ProductModel  
                FOR XML AUTO, type  
               )  
        FROM Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="c6ba2-134">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-134">This is the partial result:</span></span>  
  
```  
<Production.ProductCategory ProductCategoryID="1" CategoryName="Bikes">  
  <Production.ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bikes</SubCategoryName>  
    <ProductModel ProductModelID="19" ModelName="Mountain-100">  
      <Production.Product ProductID="771"   
                ProductName="Mountain-100 Silver, 38" Color="Silver" />  
      <Production.Product ProductID="772"   
                ProductName="Mountain-100 Silver, 42" Color="Silver" />  
      <Production.Product ProductID="773"   
                ProductName="Mountain-100 Silver, 44" Color="Silver" />  
        ...  
    </ProductModel>  
     ...  
```  
  
 <span data-ttu-id="c6ba2-135">製品サブカテゴリを生成している入れ子構造の `ELEMENTS` クエリから `FOR XML` ディレクティブを削除すると、結果全体が属性中心になります。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-135">If you remove the `ELEMENTS` directive from the nested `FOR XML` query that generates product subcategories, the whole result is attribute-centric.</span></span> <span data-ttu-id="c6ba2-136">このクエリは入れ子にしないでも記述できます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-136">You can then write this query without nesting.</span></span> <span data-ttu-id="c6ba2-137">`ELEMENTS` を追加することで、結果として一部が属性中心で、一部が要素中心の XML が得られます。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-137">The addition of `ELEMENTS` results in an XML that is partly attribute-centric and partly element-centric.</span></span> <span data-ttu-id="c6ba2-138">この結果は単一レベルの FOR XML クエリでは生成できません。</span><span class="sxs-lookup"><span data-stu-id="c6ba2-138">This result cannot be generated by a single-level, FOR XML query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ba2-139">参照</span><span class="sxs-lookup"><span data-stu-id="c6ba2-139">See Also</span></span>  
 [<span data-ttu-id="c6ba2-140">入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="c6ba2-140">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
