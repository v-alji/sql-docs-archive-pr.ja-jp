---
title: フィルターの変更 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a7bab18952820a3dc49c9479797a411521f8e71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639846"
---
# <a name="modify-a-filter-sql-server-profiler"></a><span data-ttu-id="ef920-102">フィルターの変更 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="ef920-102">Modify a Filter (SQL Server Profiler)</span></span>
  <span data-ttu-id="ef920-103">トレース定義を保持するトレース テンプレートにフィルターを追加して、トレースで収集するイベントの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="ef920-103">You add filters to trace templates, which contain the trace definitions, to limit the number of events that are gathered by a trace.</span></span> <span data-ttu-id="ef920-104">収集するイベントの数を制限すると、トレースによるパフォーマンスの影響を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="ef920-104">Limiting the number of events gathered can reduce the performance effects of tracing.</span></span> <span data-ttu-id="ef920-105">トレース テンプレートにフィルターを設定していても、そのトレースで必要な種類の情報が収集されていないことが判明した場合は、そのフィルターを編集できます。</span><span class="sxs-lookup"><span data-stu-id="ef920-105">If you set filters for a trace template and find that the trace is not gathering the kind of information that you need, you can edit the filter.</span></span>  
  
### <a name="to-modify-a-filter"></a><span data-ttu-id="ef920-106">フィルターを変更するには</span><span class="sxs-lookup"><span data-stu-id="ef920-106">To modify a filter</span></span>  
  
1.  <span data-ttu-id="ef920-107">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で、変更するトレース フィルターのテンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="ef920-107">In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], open the template for the trace filter that you want to modify.</span></span> <span data-ttu-id="ef920-108">**[ファイル]** メニューの **[テンプレート]** をポイントし、 **[テンプレートの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef920-108">On the **File** menu, click **Templates**, and then choose **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="ef920-109">**[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[全般]** タブで、 **[テンプレート名の選択]** ボックスの一覧からテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="ef920-109">In the **General** tab of the **Trace Template Properties** dialog, select a template from the **Select template name** list.</span></span>  
  
3.  <span data-ttu-id="ef920-110">**[イベントの選択]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef920-110">Click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="ef920-111">**[イベントの選択]** タブにはグリッド コントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="ef920-111">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="ef920-112">グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="ef920-112">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="ef920-113">このテーブルには、各イベント クラスが 1 行で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef920-113">The table contains one row for each event class.</span></span> <span data-ttu-id="ef920-114">イベント クラスは、接続先のサーバーの種類やバージョンによって多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ef920-114">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="ef920-115">イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。</span><span class="sxs-lookup"><span data-stu-id="ef920-115">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="ef920-116">残りの列には、各イベント クラスに対応するデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef920-116">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
4.  <span data-ttu-id="ef920-117">**[列フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef920-117">Click **Column Filters**.</span></span>  
  
5.  <span data-ttu-id="ef920-118">**[フィルターの編集]** ダイアログ ボックスで、編集する比較演算子に対応した値をクリックし、新しい値を入力するか、既存の値を削除します。</span><span class="sxs-lookup"><span data-stu-id="ef920-118">In the **Edit Filter** dialog box, click the value next to the comparison operator that you want to edit, and type the new value or delete a value.</span></span> <span data-ttu-id="ef920-119">また、新しいフィルターを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef920-119">You can also add additional filters.</span></span>  
  
6.  <span data-ttu-id="ef920-120">**[OK]** をクリックしてテンプレートを保存します。</span><span class="sxs-lookup"><span data-stu-id="ef920-120">Click **OK** and save the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef920-121">参照</span><span class="sxs-lookup"><span data-stu-id="ef920-121">See Also</span></span>  
 [<span data-ttu-id="ef920-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ef920-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
