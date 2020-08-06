---
title: トレース結果のテーブルへの保存 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08acfb4e7136f8b28d1c990d508b8578f96a57b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737188"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a><span data-ttu-id="19e35-102">トレース結果のテーブルへの保存 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="19e35-102">Save Trace Results to a Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="19e35-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース結果をデータベース テーブルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19e35-103">This topic describes how to save trace results to a database table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-table"></a><span data-ttu-id="19e35-104">トレース結果をテーブルに保存するには</span><span class="sxs-lookup"><span data-stu-id="19e35-104">To save trace results to a table</span></span>  
  
1.  <span data-ttu-id="19e35-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="19e35-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="19e35-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19e35-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="19e35-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="19e35-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="19e35-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="19e35-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="19e35-109">**[トレース名]** ボックスにトレースの名前を入力し、 **[テーブルに保存]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="19e35-109">In the **Trace name** box, type a name for the trace, and then click **Save to table**.</span></span>  
  
3.  <span data-ttu-id="19e35-110">**[サーバーへの接続]** ダイアログ ボックスで、トレース テーブルを格納する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="19e35-110">In the **Connect to server** dialog box, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the trace table.</span></span>  
  
4.  <span data-ttu-id="19e35-111">**[キャプチャ先テーブル]** ダイアログ ボックスで、 **[データベース]** ボックスの一覧からデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="19e35-111">In the **Destination Table** dialog box, select a database from the **Database**list.</span></span>  
  
5.  <span data-ttu-id="19e35-112">**[所有者]** ボックスの一覧で、トレースの所有者を選択します。</span><span class="sxs-lookup"><span data-stu-id="19e35-112">In the **Owner** list, select the owner for the trace.</span></span>  
  
6.  <span data-ttu-id="19e35-113">**[テーブル]** ボックスの一覧で、トレース結果用のテーブルの名前を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="19e35-113">In the **Table** list, type or select the table name for the trace results.</span></span> <span data-ttu-id="19e35-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19e35-114">Click **OK.**</span></span>  
  
7.  <span data-ttu-id="19e35-115">[**トレースのプロパティ**] ダイアログボックスで、[**最大行数の設定 (1000 行単位)** ] チェックボックスをオンにして、保存する最大行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="19e35-115">In the **Trace Properties** dialog box, select the **Set maximum rows (in thousands)** check box to specify the maximum number of rows to save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e35-116">参照</span><span class="sxs-lookup"><span data-stu-id="19e35-116">See Also</span></span>  
 [<span data-ttu-id="19e35-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="19e35-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
