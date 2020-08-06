---
title: トレーステンプレートの変更 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- modifying traces
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2a93baedb1875ac740e74065ae7188f9b576e083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632648"
---
# <a name="modify-a-trace-template-sql-server-profiler"></a><span data-ttu-id="91af6-102">トレース テンプレートの変更 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="91af6-102">Modify a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="91af6-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]を使用してトレース テンプレートを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91af6-103">This topic describes how to modify a trace template by using [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-modify-a-trace-template"></a><span data-ttu-id="91af6-104">トレース テンプレートを変更するには</span><span class="sxs-lookup"><span data-stu-id="91af6-104">To modify a trace template</span></span>  
  
1.  <span data-ttu-id="91af6-105">**[ファイル]** メニューの **[テンプレート]** をポイントし、 **[テンプレートのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="91af6-105">On the **File** menu, point to **Templates**, and then click **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="91af6-106">**[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[全般]** タブで、サーバーの種類とテンプレート名を変更するか、そのサーバーの種類の既定のテンプレートを使用することを選択します。</span><span class="sxs-lookup"><span data-stu-id="91af6-106">In the **Trace Template Properties** dialog box, on the **General** tab, you can modify the server type and template name, or choose to use a default template for the server type.</span></span>  
  
3.  <span data-ttu-id="91af6-107">[**イベントの選択**] タブで、次のように、グリッドコントロールを使用してトレースファイルのイベントとデータ列を追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="91af6-107">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows.</span></span>  
  
    -   <span data-ttu-id="91af6-108">イベントを追加するには、 **[イベント]** 列の適切なイベント カテゴリを展開し、イベント名を選択します。</span><span class="sxs-lookup"><span data-stu-id="91af6-108">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="91af6-109">イベントを追加すると、関連するすべてのデータ列が既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="91af6-109">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="91af6-110">トレースからイベントのデータ列を削除するには、そのイベントのデータ列のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="91af6-110">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="91af6-111">フィルターを追加するには、データ列名をクリックし、 **[フィルターの編集]** ダイアログ ボックスにフィルターの条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="91af6-111">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="91af6-112">また、データ列名を右クリックし、 **[列フィルターの編集]** をクリックすることによっても **[フィルターの編集]** ダイアログ ボックスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="91af6-112">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="91af6-113">**[OK]** をクリックしてフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="91af6-113">Click **OK** to add the filter.</span></span>  
  
4.  <span data-ttu-id="91af6-114">**[保存]** をクリックするか、 **[名前を付けて保存]** をクリックして別の名前でトレース テンプレートを保存します。</span><span class="sxs-lookup"><span data-stu-id="91af6-114">Click **Save**, or click **Save As**to save the trace template under another name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91af6-115">参照</span><span class="sxs-lookup"><span data-stu-id="91af6-115">See Also</span></span>  
 <span data-ttu-id="91af6-116">[トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="91af6-116">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="91af6-117">[実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="91af6-117">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="91af6-118">[トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="91af6-118">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="91af6-119">[SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="91af6-119">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="91af6-120">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="91af6-120">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
