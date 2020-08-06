---
title: イベントの開始時刻に基づいたイベントのフィルター選択 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739025"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a><span data-ttu-id="bbed5-102">イベントの開始時刻に基づいたイベントのフィルター選択 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bbed5-102">Filter Events Based on the Event Start Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="bbed5-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース イベントをイベントの開始時刻に基づいてフィルター選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-103">This topic describes how to filter trace events based on the event start time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a><span data-ttu-id="bbed5-104">イベントの開始時刻に基づいてイベントをフィルター選択するには</span><span class="sxs-lookup"><span data-stu-id="bbed5-104">To filter an event based on the event start time</span></span>  
  
1.  <span data-ttu-id="bbed5-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="bbed5-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bbed5-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bbed5-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="bbed5-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="bbed5-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="bbed5-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="bbed5-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="bbed5-110">**[使用するテンプレート]** ボックスの一覧で、トレース テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="bbed5-111">必要に応じて、トレース結果の保存先を指定します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-111">Optionally specify a destination for the trace results.</span></span>  
  
5.  <span data-ttu-id="bbed5-112">**[イベントの選択]** タブで、 **[StartTime]** 列見出しをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbed5-112">On the **Events Selection**tab, click the **StartTime** column heading.</span></span> <span data-ttu-id="bbed5-113">また、この列見出しを右クリックし、 **[列フィルターの編集]** をクリックして **[フィルターの編集]** ダイアログ ボックスを開く方法もあります。</span><span class="sxs-lookup"><span data-stu-id="bbed5-113">You can also right-click the column heading, and then click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span>  
  
6.  <span data-ttu-id="bbed5-114">[次の値**より大きい**] または [**より小さい**] を展開し、 `datetime` 比較演算子の下に表示されるフィールドに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="bbed5-114">Expand **Greater than** or **Less than**, and then enter a `datetime` value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbed5-115">参照</span><span class="sxs-lookup"><span data-stu-id="bbed5-115">See Also</span></span>  
 [<span data-ttu-id="bbed5-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="bbed5-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
