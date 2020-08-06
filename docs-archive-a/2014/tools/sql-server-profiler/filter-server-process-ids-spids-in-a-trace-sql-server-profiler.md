---
title: トレースでのサーバー プロセス ID (SPID) のフィルター選択 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99ae7eac6f19bd942a04f97b0a7da580eadc9dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739019"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a><span data-ttu-id="2b294-102">トレースでのサーバー プロセス ID (SPID) のフィルター選択 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2b294-102">Filter Server Process IDs (SPIDs) in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="2b294-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレースでサーバー プロセス ID (SPID) をフィルター選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b294-103">This topic describes how to filter server process identifiers (SPIDs) in a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-system-ids-in-a-trace"></a><span data-ttu-id="2b294-104">トレースでシステム ID をフィルター選択するには</span><span class="sxs-lookup"><span data-stu-id="2b294-104">To filter system IDs in a trace</span></span>  
  
1.  <span data-ttu-id="2b294-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2b294-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="2b294-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b294-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b294-107">[**接続の確立直後に**トレースを開始する] を選択すると、[**トレースのプロパティ**] ダイアログボックスが表示されず、トレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="2b294-107">if **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="2b294-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2b294-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="2b294-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2b294-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="2b294-110">**[使用するテンプレート]** ボックスの一覧で、トレース テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b294-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="2b294-111">必要に応じて、トレース結果の保存先ファイルまたは保存先テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="2b294-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="2b294-112">**[イベントの選択]** タブで、 **[SPID]** 列見出しをクリックして **[フィルターの編集]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="2b294-112">On the **Events Selection**tab, click the **SPID**column heading to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="2b294-113">このダイアログ ボックスは、列見出しを右クリックして **[列フィルターの編集]** をクリックしても表示することができます。</span><span class="sxs-lookup"><span data-stu-id="2b294-113">You can also right-click the column heading and choose **Edit Column Filter**.</span></span> <span data-ttu-id="2b294-114">**[SPID]** 列が表示されていない場合は、 **[すべての列を表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2b294-114">If the **SPID** column does not appear, check the **Show all columns** box.</span></span>  
  
6.  <span data-ttu-id="2b294-115">**[フィルターの編集]** ダイアログ ボックスで適切な比較演算子を展開し、比較の値として SPID を入力します。</span><span class="sxs-lookup"><span data-stu-id="2b294-115">In the **Edit Filter** dialog box, expand the appropriate comparison operator, and enter a SPID as a value for the comparison.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b294-116">参照</span><span class="sxs-lookup"><span data-stu-id="2b294-116">See Also</span></span>  
 [<span data-ttu-id="2b294-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2b294-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
