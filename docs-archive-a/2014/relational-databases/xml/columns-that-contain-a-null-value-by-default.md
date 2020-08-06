---
title: NULL 値が含まれる列の既定動作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ea51101f73695be2075a1b41deb62ca021f496
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631692"
---
# <a name="columns-that-contain-a-null-value-by-default"></a><span data-ttu-id="60363-102">NULL 値が含まれる列の既定動作</span><span class="sxs-lookup"><span data-stu-id="60363-102">Columns that Contain a Null Value By Default</span></span>
  <span data-ttu-id="60363-103">既定で、列内の NULL 値は、属性、ノード、または要素がない状態にマップされます。</span><span class="sxs-lookup"><span data-stu-id="60363-103">By default, a null value in a column maps to the absence of the attribute, node, or element.</span></span> <span data-ttu-id="60363-104">この既定動作を変更するには、次のクエリに示すように、ELEMENTS ディレクティブで要素中心の XML を要求し、NULL 値に対しても要素の追加を要求する XSINIL を指定します。</span><span class="sxs-lookup"><span data-stu-id="60363-104">This default behavior can be overwritten by requesting element-centric XML using the ELEMENTS directive and specifying XSINIL to request adding elements for NULL values, as shown in the following query:</span></span>  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="60363-105">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="60363-105">The following shows the result.</span></span> <span data-ttu-id="60363-106">XSINIL を指定しないと、<`Middle`> 要素は出力されません。</span><span class="sxs-lookup"><span data-stu-id="60363-106">Note that if XSINIL is not specified, the <`Middle`> element will be absent.</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60363-107">参照</span><span class="sxs-lookup"><span data-stu-id="60363-107">See Also</span></span>  
 [<span data-ttu-id="60363-108">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="60363-108">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
