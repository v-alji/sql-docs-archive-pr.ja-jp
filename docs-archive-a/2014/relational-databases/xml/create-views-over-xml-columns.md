---
title: XML 列でのビューの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: rothja
ms.author: jroth
ms.openlocfilehash: bf06f1107cbf4875eb63fe6747775b5c5c04810c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738077"
---
# <a name="create-views-over-xml-columns"></a><span data-ttu-id="c8de9-102">XML 列でのビューの作成</span><span class="sxs-lookup"><span data-stu-id="c8de9-102">Create Views over XML Columns</span></span>
  <span data-ttu-id="c8de9-103">`xml` 型の列を使用して、ビューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8de9-103">You can use an `xml` type column to create views.</span></span> <span data-ttu-id="c8de9-104">次の例では、`xml` データ型の `value()` メソッドを使用して `xml` 型の列の値を取得するビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8de9-104">The following example creates a view in which the value from an `xml` type column is retrieved using the `value()` method of the `xml` data type.</span></span>  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 <span data-ttu-id="c8de9-105">このビューに対し、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c8de9-105">Execute the following query against the view:</span></span>  
  
```  
SELECT *   
FROM   MyView  
```  
  
 <span data-ttu-id="c8de9-106">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c8de9-106">This is the result:</span></span>  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 <span data-ttu-id="c8de9-107">`xml` データ型を使用してビューを作成する際には次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8de9-107">Note the following points about using the `xml` data type to create views:</span></span>  
  
-   <span data-ttu-id="c8de9-108">xml データ型は、具体化されたビュー内に作成できます。</span><span class="sxs-lookup"><span data-stu-id="c8de9-108">The xml data type can be created in a materialized view.</span></span> <span data-ttu-id="c8de9-109">具体化されたビューは、xml データ型のメソッドに基づくことはできません。</span><span class="sxs-lookup"><span data-stu-id="c8de9-109">The materialized view cannot be based on an xml data type method.</span></span> <span data-ttu-id="c8de9-110">ただし、ベース テーブルの xml 型の列とは異なる XML スキーマ コレクションにキャストできます。</span><span class="sxs-lookup"><span data-stu-id="c8de9-110">However, it can be cast to an XML schema collection that is different from the xml type column in the base table.</span></span>  
  
-   <span data-ttu-id="c8de9-111">分散パーティション ビューには `xml` データ型を使用できません。</span><span class="sxs-lookup"><span data-stu-id="c8de9-111">The `xml` data type cannot be used in Distributed Partitioned Views.</span></span>  
  
-   <span data-ttu-id="c8de9-112">ビューに対して実行される SQL 述語は、ビュー定義の XQuery には組み込まれません。</span><span class="sxs-lookup"><span data-stu-id="c8de9-112">SQL predicates running against the view will not be pushed into the XQuery of the view definition.</span></span>  
  
-   <span data-ttu-id="c8de9-113">ビューの XML データ型メソッドは更新できません。</span><span class="sxs-lookup"><span data-stu-id="c8de9-113">XML data type methods in a view are not updatable.</span></span>  
  
  
