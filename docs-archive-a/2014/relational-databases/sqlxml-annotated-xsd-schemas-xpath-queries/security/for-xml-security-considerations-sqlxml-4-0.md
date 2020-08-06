---
title: FOR XML のセキュリティに関する考慮事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a64fa61848e4b5435b2aa944c53953a8c083ab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643741"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a><span data-ttu-id="f21ae-102">FOR XML のセキュリティに関する注意点 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f21ae-102">FOR XML Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="f21ae-103">FOR XML AUTO モードでは、XML 階層が生成され、要素名はテーブル名に、属性名は列名にマップされます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-103">The FOR XML AUTO mode generates an XML hierarchy in which element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="f21ae-104">この場合、データベースのテーブルと列の情報が公開されます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-104">This exposes the database table and column information.</span></span> <span data-ttu-id="f21ae-105">AUTO モード (サーバー側の書式設定) を使用する場合は、テーブルと列の別名をクエリで指定することで、データベース情報を隠すことができます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-105">You can hide the database information when you use AUTO mode (server-side formatting) by specifying table and column aliases in the query.</span></span> <span data-ttu-id="f21ae-106">これらの別名は、結果の XML ドキュメント内に要素名および属性名として返されます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-106">These aliases are returned in the resulting XML document as element and attribute names.</span></span>  
  
 <span data-ttu-id="f21ae-107">たとえば、次のクエリでは AUTO モードを指定しており、XML の書式設定はサーバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-107">For example, the following query specifies AUTO mode; therefore, the XML formatting is done on the server:</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="f21ae-108">結果の XML ドキュメントでは、要素名と属性名に別名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-108">In the resulting XML document, the aliases are used for element and attribute names:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 <span data-ttu-id="f21ae-109">NESTED モード (クライアント側の書式設定) を使用する場合、結果の XML ドキュメントでは、別名が属性にのみ返され、</span><span class="sxs-lookup"><span data-stu-id="f21ae-109">When you use NESTED mode (client-side formatting), aliases are returned only for attributes in the resulting XML document.</span></span> <span data-ttu-id="f21ae-110">ベース テーブルの名前が常に要素名として返されます。</span><span class="sxs-lookup"><span data-stu-id="f21ae-110">The names of the base tables are always returned as element names.</span></span> <span data-ttu-id="f21ae-111">たとえば、次のクエリでは NESTED モードを指定しています。</span><span class="sxs-lookup"><span data-stu-id="f21ae-111">For example, the following query specifies NESTED mode.</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="f21ae-112">結果の XML ドキュメントでは、ベース テーブルの名前が要素名として返され、テーブルの別名は使用されません。</span><span class="sxs-lookup"><span data-stu-id="f21ae-112">In the resulting XML document, the names of the base tables are returned as element names and table aliases are not used:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
