---
title: トレース結果のファイルへの保存 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 644fc812bbb4863c336ff2f53f5b2d67ee0a4d5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632297"
---
# <a name="save-trace-results-to-a-file"></a><span data-ttu-id="ce029-102">トレース結果のファイルへの保存</span><span class="sxs-lookup"><span data-stu-id="ce029-102">Save Trace Results to a File</span></span>
  <span data-ttu-id="ce029-103">トレース結果をファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="ce029-103">You can save trace results to a file.</span></span> <span data-ttu-id="ce029-104">トレース ファイルは、トレース結果が書き込まれるファイルです。</span><span class="sxs-lookup"><span data-stu-id="ce029-104">A trace file is a file where the trace results are written.</span></span> <span data-ttu-id="ce029-105">トレース ファイルは、ローカル ディレクトリ (C:\\*foldername*\\*filename.trc*など) またはネットワーク ディレクトリ ( \\\computername\sharename\filename.trc など) に配置できます。</span><span class="sxs-lookup"><span data-stu-id="ce029-105">A trace file can be located either in a local directory (such as C:\\*foldername*\\*filename.trc*) or a network directory (such as \\\computername\sharename\filename.trc).</span></span>  
  
 <span data-ttu-id="ce029-106">トレース ファイルを使用して、次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="ce029-106">You can use the trace files to do the following:</span></span>  
  
-   <span data-ttu-id="ce029-107">トレースの再生</span><span class="sxs-lookup"><span data-stu-id="ce029-107">Replay traces</span></span>  
  
-   <span data-ttu-id="ce029-108">監査 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce029-108">Audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="ce029-109">パフォーマンス分析の実行</span><span class="sxs-lookup"><span data-stu-id="ce029-109">Conduct performance analysis</span></span>  
  
-   <span data-ttu-id="ce029-110">トレース イベントとパフォーマンス カウンターの相互関係による問題の検出の向上</span><span class="sxs-lookup"><span data-stu-id="ce029-110">Correlate trace events with performance counters to enhance problem detection</span></span>  
  
-   <span data-ttu-id="ce029-111">データベース エンジン チューニング アドバイザー分析の実行</span><span class="sxs-lookup"><span data-stu-id="ce029-111">Perform Database Engine Tuning Advisor analysis</span></span>  
  
-   <span data-ttu-id="ce029-112">クエリの最適化の実行</span><span class="sxs-lookup"><span data-stu-id="ce029-112">Carry out query optimization</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ce029-113">**@tracefile**ストアドプロシージャ**sp_trace_create**の引数にパスとファイル名が指定されている場合に、トレース結果をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="ce029-113">saves trace results to a file when a path and file name are specified for the **@tracefile** argument of the stored procedure **sp_trace_create**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce029-114">トレース ファイルの保存用に、 **sp_trace_create** ストアド プロシージャにパスを指定する場合は、サーバーからそのディレクトリにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce029-114">If a path is specified to the **sp_trace_create** stored procedure for saving the trace file, the directory must be accessible to the server.</span></span> <span data-ttu-id="ce029-115">また、 **sp_trace_create**にローカル ディレクトリを指定すると、サーバー コンピューターのローカル ディレクトリを指定したことになるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce029-115">Also be aware that if a local directory is specified to **sp_trace_create**, it is a local directory on the server computer.</span></span>  
  
 <span data-ttu-id="ce029-116">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用している場合は、トレース結果をファイルまたはテーブルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="ce029-116">If [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is used, it allows you to save trace results to a file or to a table.</span></span> <span data-ttu-id="ce029-117">テーブルにトレース結果を保存すると、ファイルにトレースを保存する場合と同じアクセスが可能になります。そのうえ、そのテーブルにクエリして、特定のイベントを検索できます。</span><span class="sxs-lookup"><span data-stu-id="ce029-117">Saving trace results to a table allows the same access as saving the trace to a file plus you can query the table to search for specific events.</span></span>  
  
 <span data-ttu-id="ce029-118">トレース結果の保存の詳細については、「[トレース結果のテーブルへの保存 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)」および「[トレース結果のファイルへの保存 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce029-118">For more information about saving trace results, see [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) and [Save Trace Results to a File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce029-119">参照</span><span class="sxs-lookup"><span data-stu-id="ce029-119">See Also</span></span>  
 <span data-ttu-id="ce029-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce029-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="ce029-121">[トレースの作成 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="ce029-121">[Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span></span>  
 [<span data-ttu-id="ce029-122">トレースの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="ce029-122">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
