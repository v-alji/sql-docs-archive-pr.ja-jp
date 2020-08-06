---
title: 保存されているトレースの表示 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b67760d575b651b089a6936adc945d74a1c62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743142"
---
# <a name="view-a-saved-trace-transact-sql"></a><span data-ttu-id="51354-102">保存されているトレースの表示 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="51354-102">View a Saved Trace (Transact-SQL)</span></span>
  <span data-ttu-id="51354-103">このトピックでは、組み込み関数を使用して、保存されているトレースを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51354-103">This topic describes how to use built-in functions to view a saved trace.</span></span>  
  
### <a name="to-view-a-specific-trace"></a><span data-ttu-id="51354-104">特定のトレースを表示するには</span><span class="sxs-lookup"><span data-stu-id="51354-104">To view a specific trace</span></span>  
  
1.  <span data-ttu-id="51354-105">情報が必要なトレースの ID を指定して **fn_trace_getinfo** を実行します。</span><span class="sxs-lookup"><span data-stu-id="51354-105">Execute **fn_trace_getinfo** by specifying the ID of the trace about which information is needed.</span></span> <span data-ttu-id="51354-106">この関数は、トレース、トレースのプロパティ、およびそのプロパティに関する情報を一覧にしたテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="51354-106">This function returns a table that lists the trace, trace property, and information about the property.</span></span>  
  
     <span data-ttu-id="51354-107">この関数を呼び出すには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="51354-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a><span data-ttu-id="51354-108">既存のトレースをすべて表示するには</span><span class="sxs-lookup"><span data-stu-id="51354-108">To view all existing traces</span></span>  
  
1.  <span data-ttu-id="51354-109">**または** を指定して `0` fn_trace_getinfo `default`を実行します。</span><span class="sxs-lookup"><span data-stu-id="51354-109">Execute **fn_trace_getinfo** by specifying `0` or `default`.</span></span> <span data-ttu-id="51354-110">この関数は、すべてのトレース、そのプロパティ、およびプロパティに関する情報を一覧にしたテーブルを返します。</span><span class="sxs-lookup"><span data-stu-id="51354-110">This function returns a table that lists all the traces, their properties, and information about these properties.</span></span>  
  
     <span data-ttu-id="51354-111">この関数を呼び出すには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="51354-111">Invoke the function as follows:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a><span data-ttu-id="51354-112">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="51354-112">.NET Framework Security</span></span>  
 <span data-ttu-id="51354-113">組み込み関数 **fn_trace_getinfo**を実行するには、ユーザーに次の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="51354-113">To run the built-in function **fn_trace_getinfo**, the user needs the following permission:</span></span>  
  
 <span data-ttu-id="51354-114">サーバーの ALTER TRACE</span><span class="sxs-lookup"><span data-stu-id="51354-114">ALTER TRACE on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51354-115">参照</span><span class="sxs-lookup"><span data-stu-id="51354-115">See Also</span></span>  
 <span data-ttu-id="51354-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51354-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 [<span data-ttu-id="51354-117">SQL Server Profiler を使用したトレースの表示と分析</span><span class="sxs-lookup"><span data-stu-id="51354-117">View and Analyze Traces with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
