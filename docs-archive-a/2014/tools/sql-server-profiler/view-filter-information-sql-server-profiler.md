---
title: フィルター情報の表示 (SQL Server プロファイラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 931b83f8087d446cfc7b08d9582cbad5b02cf671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634194"
---
# <a name="view-filter-information-sql-server-profiler"></a><span data-ttu-id="fe1e1-102">フィルター情報の表示 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-102">View Filter Information (SQL Server Profiler)</span></span>
  <span data-ttu-id="fe1e1-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してイベント クラスのデータ列のフィルターを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-103">This topic describes how to view filters on data columns for event classes by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-view-filter-information"></a><span data-ttu-id="fe1e1-104">フィルター情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="fe1e1-104">To view filter information</span></span>  
  
1.  <span data-ttu-id="fe1e1-105">トレース ファイル、トレース テーブル、または SQL スクリプトを開き、 **[ファイル]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-105">Open a trace file, trace table, or SQL script, and on the **File** menu, click **Properties**.</span></span> <span data-ttu-id="fe1e1-106">トレース テンプレートを編集している場合、または新しいトレースを作成している場合、この手順は省略します。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-106">If you are editing a trace template or creating a new trace, skip this step.</span></span>  
  
2.  <span data-ttu-id="fe1e1-107">**[イベントの選択]** タブで、フィルターを表示するデータ列の名前を右クリックし、 **[列フィルターの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-107">On the **Events Selection** tab, right-click the data column name for the filter you want to view, and click **Edit Column Filter**.</span></span>  
  
3.  <span data-ttu-id="fe1e1-108">**[フィルターの編集]** ダイアログ ボックスでフィルターの比較演算子を展開し、指定の条件に割り当てられている値を確認します。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-108">In the **Edit Filter** dialog box, expand the filter comparison operators to see the assigned value for the specified criterion.</span></span> <span data-ttu-id="fe1e1-109">フィルター情報を表示するすべての列に対し、手順 2. と 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-109">Repeat Steps 2 and 3 for all columns for which you want to view filter information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe1e1-110">値が割り当てられている比較演算子は太字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-110">Comparison operators with assigned values are formatted bold.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1e1-111">参照</span><span class="sxs-lookup"><span data-stu-id="fe1e1-111">See Also</span></span>  
 [<span data-ttu-id="fe1e1-112">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fe1e1-112">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
