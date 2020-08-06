---
title: イベントの終了時刻に基づいたフィルターでのイベントの選択 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25d8e1adbd95f48d88fd1516c48dcc0f8374a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741490"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a><span data-ttu-id="70fe2-102">イベントの終了時刻に基づいたフィルターでのイベントの選択 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="70fe2-102">Filter Events Based on the Event End Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="70fe2-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、イベントの終了時刻に基づいてフィルターでトレース イベントを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-103">This topic describes how to filter trace events based on the event ending time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a><span data-ttu-id="70fe2-104">イベントの終了時刻に基づいてフィルターでイベントを選択するには</span><span class="sxs-lookup"><span data-stu-id="70fe2-104">To filter events based on the event end time</span></span>  
  
1.  <span data-ttu-id="70fe2-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="70fe2-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70fe2-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70fe2-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="70fe2-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="70fe2-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="70fe2-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="70fe2-109">**[トレースのプロパティ]** ダイアログ ボックスで、 **[全般]** タブをクリックして、 **[トレース名]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-109">In the **Trace Properties** dialog box, make sure the **General** tab is selected, and enter a name in the **TraceName** text box.</span></span>  
  
3.  <span data-ttu-id="70fe2-110">**[使用するテンプレート]** の一覧からトレース テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-110">From the **Use the template**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="70fe2-111">必要に応じて、トレース結果の保存先ファイルまたは保存先テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="70fe2-112">**[イベントの選択]** タブで、 **[EndTime]** データ列をクリックして **[フィルターの編集]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-112">On the **Events Selection**tab, click the **EndTime** data column to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="70fe2-113">このダイアログ ボックスは、列見出しを右クリックして **[列フィルターの編集]** をクリックしても表示することができます。</span><span class="sxs-lookup"><span data-stu-id="70fe2-113">You can also right-click the column heading, and select **Edit Column Filter**.</span></span>  
  
6.  <span data-ttu-id="70fe2-114">[より**大きい**] または [**より小さい**] を展開し、 `datetime` 比較演算子の下に表示されるフィールドに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="70fe2-114">Expand **Greater than** or **Less than**, and enter a `datetime`value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70fe2-115">参照</span><span class="sxs-lookup"><span data-stu-id="70fe2-115">See Also</span></span>  
 <span data-ttu-id="70fe2-116">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="70fe2-116">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="70fe2-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="70fe2-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
