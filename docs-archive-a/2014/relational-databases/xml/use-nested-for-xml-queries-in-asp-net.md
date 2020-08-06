---
title: ASP.NET における入れ子になった FOR XML クエリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], ASP.NET and
- nested FOR XML queries in ASP.NET
- ASP.NET [SQL Server]
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
author: rothja
ms.author: jroth
ms.openlocfilehash: 1218b4ad46f0d21d42ba480d68b29d7c39b03ea2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633008"
---
# <a name="use-nested-for-xml-queries-in-aspnet"></a><span data-ttu-id="c39da-102">ASP.NET における入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="c39da-102">Use Nested FOR XML Queries in ASP.NET</span></span>
  <span data-ttu-id="c39da-103">この例では、ASP.NET アプリケーションで SQL Server のストアド プロシージャを実行してブラウザーに XML を返します。</span><span class="sxs-lookup"><span data-stu-id="c39da-103">In this example, an ASP.NET application returns XML to a browser by executing a stored procedure in SQL Server.</span></span> <span data-ttu-id="c39da-104">このストアド プロシージャは、入れ子になったクエリを使用して XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="c39da-104">The stored procedure generates XML using nested queries.</span></span> <span data-ttu-id="c39da-105">同様の SELECT ステートメントは、「 [入れ子構造で AUTO モードのクエリを使用した兄弟の生成](generate-siblings-with-a-nested-auto-mode-query.md)」でも見ることができます。</span><span class="sxs-lookup"><span data-stu-id="c39da-105">A similar SELECT statement is shown in the topic [Generating Siblings by Using a Nested AUTO Mode Query](generate-siblings-with-a-nested-auto-mode-query.md).</span></span> <span data-ttu-id="c39da-106">この例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で入れ子になった FOR XML クエリを使用して要素中心の XML を生成する方法の一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="c39da-106">This example demonstrates one way to use nested FOR XML queries to generate element-centric XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="c39da-107">例</span><span class="sxs-lookup"><span data-stu-id="c39da-107">Example</span></span>  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="c39da-108">次に .aspx アプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="c39da-108">This is the .aspx application.</span></span> <span data-ttu-id="c39da-109">これによってストアド プロシージャが実行され、XML がブラウザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="c39da-109">It executes the stored procedure and returns XML in the browser:</span></span>  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### <a name="to-test-the-application"></a><span data-ttu-id="c39da-110">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="c39da-110">To test the application</span></span>  
  
1.  <span data-ttu-id="c39da-111">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="c39da-111">Create the stored procedure in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="c39da-112">.aspx アプリケーションを c:\inetpub\wwwroot directory に保存します (GetSalesOrderInfo.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c39da-112">Save the .aspx application in the c:\inetpub\wwwroot directory (GetSalesOrderInfo.aspx).</span></span>  
  
3.  <span data-ttu-id="c39da-113">アプリケーションを実行します (「」を実行 http://server/GetSalesOrderInfo.aspx) します。</span><span class="sxs-lookup"><span data-stu-id="c39da-113">Execute the application (http://server/GetSalesOrderInfo.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39da-114">参照</span><span class="sxs-lookup"><span data-stu-id="c39da-114">See Also</span></span>  
 [<span data-ttu-id="c39da-115">入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="c39da-115">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
