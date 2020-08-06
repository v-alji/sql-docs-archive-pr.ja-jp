---
title: トレースの再生に関する注意点 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c2f030a0191596e40ef1ee9e2b0b2d4da34c773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711282"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a><span data-ttu-id="36847-102">トレースの再生に関する注意点 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="36847-102">Considerations for Replaying Traces (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="36847-103">では、次の種類のトレースを再生できません。</span><span class="sxs-lookup"><span data-stu-id="36847-103">cannot replay the following kinds of traces:</span></span>  
  
-   <span data-ttu-id="36847-104">トランザクション レプリケーションや他のトランザクションのログ利用状況を含むトレース。</span><span class="sxs-lookup"><span data-stu-id="36847-104">Traces that contain transactional replication and other transaction log activity.</span></span> <span data-ttu-id="36847-105">このようなイベントはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="36847-105">These events are skipped.</span></span> <span data-ttu-id="36847-106">他の種類のレプリケーションではトランザクション ログが記録されないので、そのようなレプリケーションは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="36847-106">Other types of replication do not mark the transaction log so they are not affected.</span></span>  
  
-   <span data-ttu-id="36847-107">グローバル一意識別子 (GUID) を必要とする操作を含むトレース。</span><span class="sxs-lookup"><span data-stu-id="36847-107">Traces that contain operations that involve globally unique identifiers (GUID).</span></span> <span data-ttu-id="36847-108">このようなイベントはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="36847-108">These events will be skipped.</span></span>  
  
-   <span data-ttu-id="36847-109">**bcp**ユーティリティ、BULK INSERT、READTEXT、WRITETEXT、UPDATETEXT ステートメントを必要とする **text**列、 **ntext** 列、および **image** 列での操作やフルテキスト操作を含むトレース。</span><span class="sxs-lookup"><span data-stu-id="36847-109">Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations.</span></span> <span data-ttu-id="36847-110">このようなイベントはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="36847-110">These events are skipped.</span></span>  
  
-   <span data-ttu-id="36847-111">セッションをバインドする **sp_getbindtoken** および **sp_bindsession** システム ストアド プロシージャを含むトレース。</span><span class="sxs-lookup"><span data-stu-id="36847-111">Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span> <span data-ttu-id="36847-112">このようなイベントはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="36847-112">These events are skipped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36847-113">あらかじめ構成された再生テンプレート (**TSQL_Replay**) を使用せず、必要なすべてのデータをキャプチャしていないトレースは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では再生されません。</span><span class="sxs-lookup"><span data-stu-id="36847-113">If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] does not replay the trace.</span></span> <span data-ttu-id="36847-114">詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36847-114">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
 <span data-ttu-id="36847-115">トレースの再生に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36847-115">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36847-116">参照</span><span class="sxs-lookup"><span data-stu-id="36847-116">See Also</span></span>  
 <span data-ttu-id="36847-117">[bcp ユーティリティ](../bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="36847-117">[bcp Utility](../bcp-utility.md) </span></span>  
 <span data-ttu-id="36847-118">[SQL Server イベント クラスの参照](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="36847-118">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="36847-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36847-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span></span>  
 <span data-ttu-id="36847-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36847-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 <span data-ttu-id="36847-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36847-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="36847-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36847-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span></span>  
 <span data-ttu-id="36847-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="36847-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span></span>  
 [<span data-ttu-id="36847-124">UPDATETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="36847-124">UPDATETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
