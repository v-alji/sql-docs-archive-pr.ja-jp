---
title: パフォーマンスの問題の特定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b42d780a8174ab57d00de72e8b00ef7af0abc17e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716289"
---
# <a name="isolate-performance-problems"></a><span data-ttu-id="791c1-102">パフォーマンスの問題の特定</span><span class="sxs-lookup"><span data-stu-id="791c1-102">Isolate Performance Problems</span></span>
  <span data-ttu-id="791c1-103">一般に、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または Microsoft Windows の複数のツールを併用した方が、ツールを 1 つずつ使用するよりも、データベースのパフォーマンスに関する問題を効率よく特定できます。</span><span class="sxs-lookup"><span data-stu-id="791c1-103">It is often more effective to use several [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Microsoft Windows tools together to isolate database performance problems than to use one tool at a time.</span></span> <span data-ttu-id="791c1-104">たとえば、グラフィカル実行プラン機能 (プラン表示) を使用すると、1 つのクエリ内のデッドロックをすばやく特定できます。</span><span class="sxs-lookup"><span data-stu-id="791c1-104">For example, the graphical Execution Plan feature, also called Showplan, helps you quickly recognize deadlocks in a single query.</span></span> <span data-ttu-id="791c1-105">さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の監視機能と Windows の監視機能を同時に使用すると、その他のパフォーマンス問題をより簡単に特定できます。</span><span class="sxs-lookup"><span data-stu-id="791c1-105">However, you can recognize some other performance problems more easily if you use the monitoring features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows together.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="791c1-106">を使用すると、Transact-SQL とアプリケーションに関連する問題を監視して、問題点を突き止めることができます。</span><span class="sxs-lookup"><span data-stu-id="791c1-106">can be used to monitor and troubleshoot Transact-SQL and application-related problems.</span></span> <span data-ttu-id="791c1-107">システム モニターを使用すると、ハードウェアとその他のシステムに関連する問題を監視できます。</span><span class="sxs-lookup"><span data-stu-id="791c1-107">System Monitor can be used to monitor hardware and other system-related problems.</span></span>  
  
 <span data-ttu-id="791c1-108">次の要素を監視することによって、問題のトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="791c1-108">You can monitor the following areas to troubleshoot problems:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="791c1-109">ストアド プロシージャまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのバッチ (ユーザー アプリケーションから送信されたもの)。</span><span class="sxs-lookup"><span data-stu-id="791c1-109">stored procedures or batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted by user applications.</span></span>  
  
-   <span data-ttu-id="791c1-110">ブロッキング ロックまたはデッドロックなどのユーザーの利用状況</span><span class="sxs-lookup"><span data-stu-id="791c1-110">User activity, such as blocking locks or deadlocks.</span></span>  
  
-   <span data-ttu-id="791c1-111">ディスクの使用量などのハードウェア利用状況</span><span class="sxs-lookup"><span data-stu-id="791c1-111">Hardware activity, such as disk usage.</span></span>  
  
 <span data-ttu-id="791c1-112">問題としては、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="791c1-112">Problems can include:</span></span>  
  
-   <span data-ttu-id="791c1-113">不適切に記述された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに関係するアプリケーション開発エラー</span><span class="sxs-lookup"><span data-stu-id="791c1-113">Application development errors involving incorrectly written [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="791c1-114">ディスクまたはネットワークに関連するエラーなどのハードウェア エラー</span><span class="sxs-lookup"><span data-stu-id="791c1-114">Hardware errors, such as disk- or network-related errors.</span></span>  
  
-   <span data-ttu-id="791c1-115">不適切に設計されたデータベースによる過剰なブロッキング</span><span class="sxs-lookup"><span data-stu-id="791c1-115">Excessive blocking due to an incorrectly designed database.</span></span>  
  
## <a name="tools-for-common-performance-problems"></a><span data-ttu-id="791c1-116">パフォーマンスの一般的な問題を解決するツール</span><span class="sxs-lookup"><span data-stu-id="791c1-116">Tools for Common Performance Problems</span></span>  
 <span data-ttu-id="791c1-117">各ツールでパフォーマンス問題を監視または調整する場合は、問題を慎重に選択することも重要になります。</span><span class="sxs-lookup"><span data-stu-id="791c1-117">Equally important is careful selection of the performance problem that you want each tool to monitor or tune.</span></span> <span data-ttu-id="791c1-118">ツールとユーティリティは、解決するパフォーマンス問題の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="791c1-118">The tool and the utility depend on the type of performance problem you want to resolve.</span></span>  
  
 <span data-ttu-id="791c1-119">監視および調整ツールの種類と特定可能な問題については、次のトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="791c1-119">The following topics describe a variety of monitoring and tuning tools and the problems they uncover.</span></span>  
  
 [<span data-ttu-id="791c1-120">ボトルネックの特定</span><span class="sxs-lookup"><span data-stu-id="791c1-120">Identify Bottlenecks</span></span>](identify-bottlenecks.md)  
  
 [<span data-ttu-id="791c1-121">メモリ使用率の監視</span><span class="sxs-lookup"><span data-stu-id="791c1-121">Monitor Memory Usage</span></span>](../performance-monitor/monitor-memory-usage.md)  
  
  
