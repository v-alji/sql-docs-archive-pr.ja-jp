---
title: SQLColumnPrivileges |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: rothja
ms.author: jroth
ms.openlocfilehash: bf46fed47817ed94ea2382f2147df254f2986aec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633137"
---
# <a name="sqlcolumnprivileges"></a><span data-ttu-id="8e576-102">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="8e576-102">SQLColumnPrivileges</span></span>
  <span data-ttu-id="8e576-103">**Sqlcolumnprivileges**は、*CatalogName*、 *SchemaName*、 *TableName*、または*ColumnName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。</span><span class="sxs-lookup"><span data-stu-id="8e576-103">**SQLColumnPrivileges** returns SQL_SUCCESS whether or not values exist for the*CatalogName*, *SchemaName*, *TableName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="8e576-104">これらのパラメーターで無効な値が使用されている場合、 **Sqlfetch**は SQL_NO_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="8e576-104">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="8e576-105">**Sqlcolumnprivileges**は、静的サーバーカーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e576-105">**SQLColumnPrivileges** can be executed on a static server cursor.</span></span> <span data-ttu-id="8e576-106">更新可能なカーソル (動的カーソルまたはキーセットカーソル) に対して**Sqlcolumnprivileges**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="8e576-106">An attempt to execute **SQLColumnPrivileges** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="8e576-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="8e576-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e576-108">参照</span><span class="sxs-lookup"><span data-stu-id="8e576-108">See Also</span></span>  
 <span data-ttu-id="8e576-109">[SQLColumnPrivileges 関数](https://go.microsoft.com/fwlink/?LinkId=59335) </span><span class="sxs-lookup"><span data-stu-id="8e576-109">[SQLColumnPrivileges Function](https://go.microsoft.com/fwlink/?LinkId=59335) </span></span>  
 [<span data-ttu-id="8e576-110">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="8e576-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
