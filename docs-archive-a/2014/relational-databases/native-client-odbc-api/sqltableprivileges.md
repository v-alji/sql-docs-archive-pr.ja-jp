---
title: SQLTablePrivileges |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: rothja
ms.author: jroth
ms.openlocfilehash: 63298330d3f0ebf707dbb42c337553c1f363deab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640920"
---
# <a name="sqltableprivileges"></a><span data-ttu-id="41171-102">SQLTablePrivileges</span><span class="sxs-lookup"><span data-stu-id="41171-102">SQLTablePrivileges</span></span>
  <span data-ttu-id="41171-103">**Sqltableprivileges**は、静的カーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="41171-103">**SQLTablePrivileges** can be executed on a static cursor.</span></span> <span data-ttu-id="41171-104">更新可能な (キーセットドリブンまたは動的) に対して**Sqltableprivileges**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="41171-104">An attempt to execute **SQLTablePrivileges** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="41171-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="41171-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41171-106">参照</span><span class="sxs-lookup"><span data-stu-id="41171-106">See Also</span></span>  
 [<span data-ttu-id="41171-107">SQLTablePrivileges 関数</span><span class="sxs-lookup"><span data-stu-id="41171-107">SQLTablePrivileges Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [<span data-ttu-id="41171-108">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="41171-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
