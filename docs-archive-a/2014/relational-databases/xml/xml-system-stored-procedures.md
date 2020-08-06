---
title: XML システム ストアド プロシージャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
author: rothja
ms.author: jroth
ms.openlocfilehash: 2008294fe5bc532dfb6883656420b4189e4da7b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642634"
---
# <a name="xml-system-stored-procedures"></a><span data-ttu-id="60bb3-102">XML システム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="60bb3-102">XML System Stored Procedures</span></span>
  <span data-ttu-id="60bb3-103">SQL Server には、OPENXML と共に使用する、次のシステム ストアド プロシージャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="60bb3-103">SQL Server provides the following system stored procedures that are used together with OPENXML:</span></span>  
  
-   [<span data-ttu-id="60bb3-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="60bb3-104">sp_xml_preparedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql)  
  
-   [<span data-ttu-id="60bb3-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="60bb3-105">sp_xml_removedocument &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql)  
  
 <span data-ttu-id="60bb3-106">OPENXML を使用してクエリを作成するには、最初に **sp_xml_preparedocument**を呼び出して XML ドキュメントの内部表現を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60bb3-106">To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp_xml_preparedocument**.</span></span> <span data-ttu-id="60bb3-107">このストアド プロシージャは、XML ドキュメントの内部表現へのハンドルを返します。</span><span class="sxs-lookup"><span data-stu-id="60bb3-107">The stored procedure returns a handle to the internal representation of the XML document.</span></span> <span data-ttu-id="60bb3-108">その後、このハンドルは OPENXML に渡されます。</span><span class="sxs-lookup"><span data-stu-id="60bb3-108">This handle is then passed to OPENXML.</span></span> <span data-ttu-id="60bb3-109">OPENXML は、XPath を基にドキュメントの行セット ビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="60bb3-109">OPENXML provides rowset views of the document based on XPaths.</span></span> <span data-ttu-id="60bb3-110">具体的には、これは 1 つの行パターンと 1 つ以上の列パターンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="60bb3-110">Specifically, this is one row pattern and one or more column patterns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60bb3-111">**sp_xml_preparedocument** から返されたドキュメント ハンドルは、セッションが確立されている間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="60bb3-111">The document handle that is returned by **sp_xml_preparedocument** is valid for the duration of the session.</span></span>  
  
 <span data-ttu-id="60bb3-112">XML ドキュメントの内部表現は、 **sp_xml_removedocument** システム ストアド プロシージャを呼び出すことによってメモリから削除できます。</span><span class="sxs-lookup"><span data-stu-id="60bb3-112">The internal representation of an XML document can be removed from memory by calling the **sp_xml_removedocument** system stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bb3-113">参照</span><span class="sxs-lookup"><span data-stu-id="60bb3-113">See Also</span></span>  
 <span data-ttu-id="60bb3-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="60bb3-114">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="60bb3-115">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="60bb3-115">OPENXML &#40;SQL Server&#41;</span></span>](../xml/openxml-sql-server.md)  
  
  
