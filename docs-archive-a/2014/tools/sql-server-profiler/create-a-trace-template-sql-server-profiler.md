---
title: トレーステンプレートを作成する (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 355f97c7fecd8a9e31f10de881d1ae6df3b8f122
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711258"
---
# <a name="create-a-trace-template-sql-server-profiler"></a><span data-ttu-id="bb110-102">トレース テンプレートの作成 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bb110-102">Create a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="bb110-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して新しいトレース テンプレートを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb110-103">This topic describes how to create a new trace template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-trace-template"></a><span data-ttu-id="bb110-104">トレース テンプレートを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb110-104">To create a trace template</span></span>  
  
1.  <span data-ttu-id="bb110-105">**[ファイル]** メニューの **[テンプレート]** をポイントし、 **[新しいテンプレート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb110-105">On the **File** menu, point to **Templates**, and then click **New Template**.</span></span>  
  
2.  <span data-ttu-id="bb110-106">**[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[サーバーの種類の選択]** ボックスの一覧でサーバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb110-106">In the **Trace Template Properties** dialog box, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="bb110-107">**[新しいテンプレート名]** ボックスにテンプレート名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb110-107">In the **New template name** box, enter a template name.</span></span>  
  
4.  <span data-ttu-id="bb110-108">必要に応じて、 **[既存のテンプレートを基に新しいテンプレートを作成する]** をクリックし、一覧からテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb110-108">Optionally, click **Base new template on existing one**, and then select a template from the list.</span></span>  
  
     <span data-ttu-id="bb110-109">すべてのイベント、データ列、フィルターは、最初、選択したテンプレートで指定されたとおりに設定されています。</span><span class="sxs-lookup"><span data-stu-id="bb110-109">All events, data columns, and filters are initially set as specified in the selected template.</span></span>  
  
5.  <span data-ttu-id="bb110-110">必要に応じて、 **[選択したサーバーの種類に対する既定のテンプレートとして使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb110-110">Optionally, click **Use as a default template for selected server type**.</span></span>  
  
6.  <span data-ttu-id="bb110-111">**[イベントの選択]** タブで、イベント、データ列、またはフィルターの追加、削除、変更を行います。</span><span class="sxs-lookup"><span data-stu-id="bb110-111">On the **Events Selection** tab, add, remove, or modify events, data columns, or filters.</span></span>  
  
7.  <span data-ttu-id="bb110-112">**[イベントの選択]** タブで、グリッド コントロールを使用して、次のようにトレース ファイルに対するイベントとデータ列の追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="bb110-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows:</span></span>  
  
    -   <span data-ttu-id="bb110-113">イベントを追加するには、 **[イベント]** 列の適切なイベント カテゴリを展開し、イベント名を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb110-113">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="bb110-114">イベントを追加すると、関連するすべてのデータ列が既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb110-114">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="bb110-115">トレースからイベントのデータ列を削除するには、そのイベントのデータ列のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="bb110-115">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="bb110-116">フィルターを追加するには、データ列名をクリックし、 **[フィルターの編集]** ダイアログ ボックスにフィルターの条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb110-116">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="bb110-117">また、データ列名を右クリックし、 **[列フィルターの編集]** をクリックすることによっても **[フィルターの編集]** ダイアログ ボックスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="bb110-117">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="bb110-118">**[OK]** をクリックしてフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb110-118">Click **OK** to add the filter.</span></span>  
  
8.  <span data-ttu-id="bb110-119">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb110-119">Click **Save.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb110-120">参照</span><span class="sxs-lookup"><span data-stu-id="bb110-120">See Also</span></span>  
 <span data-ttu-id="bb110-121">[トレース ファイルに含めるイベントとデータ列の指定 &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bb110-121">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bb110-122">[実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bb110-122">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bb110-123">[トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="bb110-123">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="bb110-124">[SQL Server プロファイラーのテンプレートと権限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="bb110-124">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="bb110-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="bb110-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
