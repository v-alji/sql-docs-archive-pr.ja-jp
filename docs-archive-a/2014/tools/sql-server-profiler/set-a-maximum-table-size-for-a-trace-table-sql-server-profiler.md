---
title: トレース テーブルの最大テーブル サイズの設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f48efbe02e300e06faf857ed0fb36ae340ad979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711238"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a><span data-ttu-id="ad4c8-102">トレース テーブルの最大テーブル サイズの設定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="ad4c8-102">Set a Maximum Table Size for a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="ad4c8-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース テーブルの最大テーブル サイズを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-103">This topic describes how to set a maximum table size for trace tables by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a><span data-ttu-id="ad4c8-104">トレース テーブルの最大テーブル サイズを設定するには</span><span class="sxs-lookup"><span data-stu-id="ad4c8-104">To set a maximum table size for a trace table</span></span>  
  
1.  <span data-ttu-id="ad4c8-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="ad4c8-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad4c8-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="ad4c8-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="ad4c8-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="ad4c8-110">**[テンプレート名]** ボックスの一覧で、トレース テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="ad4c8-111">**[テーブルに保存]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-111">Select the **Save to table**check box.</span></span>  
  
5.  <span data-ttu-id="ad4c8-112">トレースを格納するサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-112">Connect to the server on which you want the trace to be stored.</span></span>  
  
     <span data-ttu-id="ad4c8-113">**[キャプチャ先テーブル]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-113">The **Destination Table** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="ad4c8-114">**[データベース]** ボックスの一覧から、トレースするデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-114">Select a database for the trace from the **Database** list.</span></span>  
  
7.  <span data-ttu-id="ad4c8-115">**[テーブル]** ボックスで、テーブル名を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-115">In the **Table** box, type or select a table name.</span></span>  
  
8.  <span data-ttu-id="ad4c8-116">**[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、トレース テーブルの最大行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-116">Select the **Set maximum rows** check box, and specify a maximum number of rows for the trace table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad4c8-117">テーブル内の行数が、指定した最大数を超えると、トレース イベントは記録されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-117">When the number of rows in the table exceeds the maximum that you have specified, the trace events are no longer recorded.</span></span> <span data-ttu-id="ad4c8-118">ただし、トレースは続行されます。</span><span class="sxs-lookup"><span data-stu-id="ad4c8-118">However, tracing continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4c8-119">参照</span><span class="sxs-lookup"><span data-stu-id="ad4c8-119">See Also</span></span>  
 <span data-ttu-id="ad4c8-120">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ad4c8-120">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="ad4c8-121">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ad4c8-121">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
