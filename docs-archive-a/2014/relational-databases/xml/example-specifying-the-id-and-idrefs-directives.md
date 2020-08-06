---
title: '例: ID ディレクティブと IDREFS ディレクティブの指定 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: rothja
ms.author: jroth
ms.openlocfilehash: c21ba1bd19691014f179801421322970a3dd6dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644354"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a><span data-ttu-id="20778-102">例:ID ディレクティブと IDREFS ディレクティブの指定</span><span class="sxs-lookup"><span data-stu-id="20778-102">Example: Specifying the ID and IDREFS Directives</span></span>
  <span data-ttu-id="20778-103">要素の属性は、`ID` 型の属性として指定することができます。さらに、この属性を参照する `IDREFS` 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="20778-103">An element attribute can be specified as an `ID` type attribute, and the `IDREFS` attribute can then be used to refer to it.</span></span> <span data-ttu-id="20778-104">これにより、ドキュメント内のリンク作成が可能になります。これは、リレーショナル データベースにおける主キーと外部キーのリレーションシップに似ています。</span><span class="sxs-lookup"><span data-stu-id="20778-104">This enables intra-document links and is similar to the primary key and foreign key relationships in relational databases.</span></span>  
  
 <span data-ttu-id="20778-105">この例では、`ID` ディレクティブと `IDREFS` ディレクティブを使用して、`ID` 型と `IDREFS` 型の属性を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="20778-105">This example illustrates how the `ID` and `IDREFS` directives can be used to create attributes of `ID` and `IDREFS` types.</span></span> <span data-ttu-id="20778-106">ID は整数値にできないので、この例では ID 値を変換します。</span><span class="sxs-lookup"><span data-stu-id="20778-106">Because IDs cannot be integer values, the ID values in this example are converted.</span></span> <span data-ttu-id="20778-107">つまり、型キャストを行っています。</span><span class="sxs-lookup"><span data-stu-id="20778-107">In other words, they are type casted.</span></span> <span data-ttu-id="20778-108">ID 値にはプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="20778-108">Prefixes are used for the ID values.</span></span>  
  
 <span data-ttu-id="20778-109">次のような XML を生成するとします。</span><span class="sxs-lookup"><span data-stu-id="20778-109">Assume that you want to construct XML as shown in the following:</span></span>  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 <span data-ttu-id="20778-110">< `SalesOrderIDList` > 要素の `Customer` 属性は、複数の値を指定できる属性であり、< `SalesOrderID` > 要素の `SalesOrder` 属性を参照しています。</span><span class="sxs-lookup"><span data-stu-id="20778-110">The `SalesOrderIDList` attribute of the < `Customer` > element is a multivalued attribute that refers to the `SalesOrderID` attribute of the < `SalesOrder` > element.</span></span> <span data-ttu-id="20778-111">このリンクを確立するには、`SalesOrderID` 属性を `ID` 型として宣言し、< `SalesOrderIDList`> 要素の `Customer` 属性を `IDREFS` 型として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20778-111">To establish this link, the `SalesOrderID` attribute must be declared of `ID` type, and the `SalesOrderIDList` attribute of the < `Customer`> element must be declared of `IDREFS` type.</span></span> <span data-ttu-id="20778-112">各顧客が複数の注文を発注することが考えられるので、 `IDREFS` 型を使用しています。</span><span class="sxs-lookup"><span data-stu-id="20778-112">Because a customer can request several orders, the `IDREFS` type is used.</span></span>  
  
 <span data-ttu-id="20778-113">`IDREFS` 型の要素も、複数の値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="20778-113">Elements of `IDREFS` type also have more than one value.</span></span> <span data-ttu-id="20778-114">このため、別の SELECT 句を使用して、同じタグ、親、およびキー列の情報を再利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20778-114">Therefore, you have to use a separate select clause that will reuse the same tag, parent, and key column information.</span></span> <span data-ttu-id="20778-115">さらに、`IDREFS` 値を構成する一連の行が、それぞれの親要素の直後にグループ化された状態で表示されるように、`ORDER BY` 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="20778-115">The `ORDER BY` then has to ensure that the sequence of rows that make up the `IDREFS` values appears grouped together under their parent element.</span></span>  
  
 <span data-ttu-id="20778-116">求める XML を生成するクエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="20778-116">This is the query that produces the XML you want.</span></span> <span data-ttu-id="20778-117">このクエリでは、 `ID` ディレクティブと `IDREFS` ディレクティブを使用して、指定した列名の型を上書きしています (`SalesOrder!2!SalesOrderID!ID`、 `Customer!1!SalesOrderIDList!IDREFS`)。</span><span class="sxs-lookup"><span data-stu-id="20778-117">The query uses the `ID` and `IDREFS` directives to overwrite the types in the column names (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a><span data-ttu-id="20778-118">参照</span><span class="sxs-lookup"><span data-stu-id="20778-118">See Also</span></span>  
 [<span data-ttu-id="20778-119">FOR XML での EXPLICIT モードの使用</span><span class="sxs-lookup"><span data-stu-id="20778-119">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
