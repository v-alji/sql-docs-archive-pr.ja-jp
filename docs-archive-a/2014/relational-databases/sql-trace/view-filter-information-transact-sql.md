---
title: フィルター情報の表示 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d94a7b4a73c264c1fb3a950aa1c9615a73db956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743138"
---
# <a name="view-filter-information-transact-sql"></a><span data-ttu-id="7f619-102">フィルター情報の表示 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7f619-102">View Filter Information (Transact-SQL)</span></span>
  <span data-ttu-id="7f619-103">このトピックでは、組み込み関数を使用してトレース フィルター情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f619-103">This topic describes how to use built-in functions to view trace filter information.</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="7f619-104">フィルター情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="7f619-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="7f619-105">フィルター情報が必要なトレースの ID を指定して、 **fn_trace_getfilterinfo** を実行します。</span><span class="sxs-lookup"><span data-stu-id="7f619-105">Execute **fn_trace_getfilterinfo** by specifying the ID of the trace about which filter information is needed.</span></span> <span data-ttu-id="7f619-106">この関数は、フィルター、フィルターが適用されている列、およびフィルターで使用している値の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="7f619-106">This function returns a table that lists the filters, the columns on which the filters are applied, and the values on which the filter is applied.</span></span>  
  
     <span data-ttu-id="7f619-107">この関数を呼び出すには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f619-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7f619-108">参照</span><span class="sxs-lookup"><span data-stu-id="7f619-108">See Also</span></span>  
 <span data-ttu-id="7f619-109">[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f619-109">[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql) </span></span>  
 <span data-ttu-id="7f619-110">[システム ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f619-110">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="7f619-111">SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7f619-111">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
