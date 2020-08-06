---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: rothja
ms.author: jroth
ms.openlocfilehash: e37f15841a36eb95c1e9263d137ba2734d622367
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645022"
---
# <a name="sqlprocedures"></a><span data-ttu-id="60efb-102">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="60efb-102">SQLProcedures</span></span>
  <span data-ttu-id="60efb-103">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは値を返します。</span><span class="sxs-lookup"><span data-stu-id="60efb-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return a value.</span></span> <span data-ttu-id="60efb-104">**Sqlprocedures**は、結果セット列 PROCEDURE_TYPE の SQL_PT_FUNCTION を報告します。</span><span class="sxs-lookup"><span data-stu-id="60efb-104">**SQLProcedures** reports SQL_PT_FUNCTION for the result set column PROCEDURE_TYPE.</span></span>  
  
 <span data-ttu-id="60efb-105">**Sqlprocedures**は *、CatalogName、SchemaName、* または*ProcName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。</span><span class="sxs-lookup"><span data-stu-id="60efb-105">**SQLProcedures** returns SQL_SUCCESS whether or not values exist for *CatalogName, SchemaName,* or *ProcName* parameters.</span></span> <span data-ttu-id="60efb-106">これらのパラメーターで無効な値が使用されている場合、 **Sqlfetch**は SQL_NO_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="60efb-106">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="60efb-107">**Sqlprocedures**は、静的サーバーカーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="60efb-107">**SQLProcedures** can be executed on a static server cursor.</span></span> <span data-ttu-id="60efb-108">更新可能なカーソル (動的カーソルまたはキーセットカーソル) で**Sqlprocedures**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="60efb-108">An attempt to execute **SQLProcedures** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO, indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="60efb-109">**Sqlprocedures**は、名前が*ProcName*に一致し、現在のユーザーが実行できる、または現在のユーザーが VIEW DEFINITION 権限を許可されているプロシージャに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="60efb-109">**SQLProcedures** returns information about any procedures whose names match *ProcName* and can be executed by the current user, or for which the current user has been granted VIEW DEFINITION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60efb-110">参照</span><span class="sxs-lookup"><span data-stu-id="60efb-110">See Also</span></span>  
 <span data-ttu-id="60efb-111">[SQLProcedures 関数](https://go.microsoft.com/fwlink/?LinkId=59364) </span><span class="sxs-lookup"><span data-stu-id="60efb-111">[SQLProcedures Function](https://go.microsoft.com/fwlink/?LinkId=59364) </span></span>  
 [<span data-ttu-id="60efb-112">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="60efb-112">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
