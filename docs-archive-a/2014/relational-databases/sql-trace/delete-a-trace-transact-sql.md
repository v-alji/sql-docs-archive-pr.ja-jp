---
title: トレースの削除 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3551cff36ef6e2c2e9cc6a4d9b7056ae44cb950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641568"
---
# <a name="delete-a-trace-transact-sql"></a><span data-ttu-id="08459-102">トレースの削除 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="08459-102">Delete a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="08459-103">このトピックでは、ストアド プロシージャを使用してトレースを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="08459-103">This topic describes how to use stored procedures to delete a trace.</span></span>  
  
 <span data-ttu-id="08459-104">トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08459-104">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).</span></span>  
  
### <a name="to-delete-a-trace"></a><span data-ttu-id="08459-105">トレースを削除するには</span><span class="sxs-lookup"><span data-stu-id="08459-105">To delete a trace</span></span>  
  
1.  <span data-ttu-id="08459-106">**@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。</span><span class="sxs-lookup"><span data-stu-id="08459-106">Execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="08459-107">**@status = 2** を指定して **sp_trace_setstatus** を実行し、トレースを閉じてトレースの情報をサーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="08459-107">Execute **sp_trace_setstatus** by specifying **@status = 2** to close the trace and delete its information from the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08459-108">トレースを閉じるには、最初にそのトレースを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08459-108">A trace must be stopped first before it can be closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08459-109">参照</span><span class="sxs-lookup"><span data-stu-id="08459-109">See Also</span></span>  
 <span data-ttu-id="08459-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08459-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="08459-111">[システム ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="08459-111">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="08459-112">SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08459-112">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
