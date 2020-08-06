---
title: SQL Server プロファイラーソーステーブル-データベースエンジンチューニングアドバイザーワークロードテーブルの選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d10899c01df8e7fbc7ee45d108841a18d3248500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639629"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a><span data-ttu-id="99273-102">SQL Server プロファイラーソーステーブル-データベースエンジンチューニングアドバイザーワークロードテーブルの選択</span><span class="sxs-lookup"><span data-stu-id="99273-102">SQL Server Profiler - Source Table-Database Engine Tuning Advisor - Select Workload Table</span></span>
  <span data-ttu-id="99273-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] および[!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザーでは、このダイアログ ボックスを使用してテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="99273-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] and [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor use this dialog box to select tables.</span></span>  
  
 <span data-ttu-id="99273-104">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] では、**[基になるテーブル]** ダイアログ ボックスを使用して、トレース テーブルの基になるテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="99273-104">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use the **Source Table** dialog box to specify a source table for a trace table.</span></span> <span data-ttu-id="99273-105">This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.</span><span class="sxs-lookup"><span data-stu-id="99273-105">This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.</span></span>  
  
 <span data-ttu-id="99273-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザーでは、**[ワークロード テーブルの選択]** ダイアログ ボックスを使用して、チューニング ワークロードとして使用する [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] のトレース情報が格納されているデータベース テーブルを選択したり、チューニング分析を開始する前にテーブルの内容をプレビューしたりします。</span><span class="sxs-lookup"><span data-stu-id="99273-106">In [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor, use the **Select Workload Table** dialog box to select a database table that contains [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information to use as a tuning workload, or to preview the table contents before starting tuning analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="99273-107">Options</span><span class="sxs-lookup"><span data-stu-id="99273-107">Options</span></span>  
 <span data-ttu-id="99273-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="99273-108">**SQL Server**</span></span>  
 <span data-ttu-id="99273-109">現在接続されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="99273-109">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] currently connected.</span></span> <span data-ttu-id="99273-110">このフィールドには自動的に値が入力され、更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="99273-110">This field is populated automatically and cannot be updated.</span></span>  
  
 <span data-ttu-id="99273-111">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="99273-111">**Database**</span></span>  
 <span data-ttu-id="99273-112">トレース テーブルがあるデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="99273-112">Specify the database where the trace table is located.</span></span>  
  
 <span data-ttu-id="99273-113">**所有者**</span><span class="sxs-lookup"><span data-stu-id="99273-113">**Owner**</span></span>  
 <span data-ttu-id="99273-114">Specifies the owner of the trace table.</span><span class="sxs-lookup"><span data-stu-id="99273-114">Specifies the owner of the trace table.</span></span> <span data-ttu-id="99273-115">このフィールドは、 **dbo**として自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="99273-115">This field is populated automatically as **dbo**.</span></span>  
  
 <span data-ttu-id="99273-116">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="99273-116">**Table**</span></span>  
 <span data-ttu-id="99273-117">トレースの読み込み元のトレース テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="99273-117">Specify the name of the trace table from which the trace should be read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99273-118">参照</span><span class="sxs-lookup"><span data-stu-id="99273-118">See Also</span></span>  
 <span data-ttu-id="99273-119">[トレース結果のテーブルへの保存 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="99273-119">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="99273-120">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="99273-120">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="99273-121">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="99273-121">Database Engine Tuning Advisor</span></span>](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
