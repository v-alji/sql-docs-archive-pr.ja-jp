---
title: 開始 SQL Server プロファイラー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05743927420865a9b6341fc050ca999f494d64d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719154"
---
# <a name="start-sql-server-profiler"></a><span data-ttu-id="80c8f-102">SQL Server Profiler の起動</span><span class="sxs-lookup"><span data-stu-id="80c8f-102">Start SQL Server Profiler</span></span>
  <span data-ttu-id="80c8f-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、さまざまなシナリオでのトレース出力の収集をサポートするために、いくつかの異なる方法で起動することができます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-103">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in several different ways to support gathering trace output in a variety of scenarios.</span></span> <span data-ttu-id="80c8f-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、 **[スタート]** メニューや **チューニング アドバイザーの** [ツール] [!INCLUDE[ssDE](../../includes/ssde-md.md)] メニューから起動できるほか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-104">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] include from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, and from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="80c8f-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動し、 **[ファイル]** メニューの **[新しいトレース]** をクリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されるので、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-105">When you first start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select **New Trace** from the **File** menu, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a><span data-ttu-id="80c8f-106">[スタート] メニューから SQL Server Profiler を起動するには</span><span class="sxs-lookup"><span data-stu-id="80c8f-106">To start SQL Server Profiler from the Start menu</span></span>  
  
1.  <span data-ttu-id="80c8f-107">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **[パフォーマンス ツール]** の順にポイントして、 **[SQL Server Profiler]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-107">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a><span data-ttu-id="80c8f-108">データベース エンジン チューニング アドバイザーで SQL Server Profiler を起動するには</span><span class="sxs-lookup"><span data-stu-id="80c8f-108">To start SQL Server Profiler in Database Engine Tuning Advisor</span></span>  
  
1.  <span data-ttu-id="80c8f-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで、 **[ツール]** メニューの **[SQL Server Profiler]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-109">On the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a><span data-ttu-id="80c8f-110">Management Studio での SQL Server Profiler の起動</span><span class="sxs-lookup"><span data-stu-id="80c8f-110">Starting SQL Server Profiler in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="80c8f-111">は、それぞれのインスタンスで各プロファイラー セッションを開始します。このセッションは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]をシャットダウンしても実行が続きます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-111">starts each profiler session in its own instance and continues to run if you shutdown [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="80c8f-112">以降の各手順に示すように、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の複数の場所から起動できます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-112">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as illustrated in the following procedures.</span></span> <span data-ttu-id="80c8f-113">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動すると、その時点の接続コンテキスト、トレース テンプレート、およびフィルター コンテキストが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="80c8f-113">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] starts it loads the connection context, trace template, and filter context of its launch point.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a><span data-ttu-id="80c8f-114">[ツール] メニューから SQL Server Profiler を起動するには</span><span class="sxs-lookup"><span data-stu-id="80c8f-114">To start SQL Server Profiler from the Tools menu</span></span>  
  
1.  <span data-ttu-id="80c8f-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ツール]** メニューで、 **[SQL Server Profiler]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-115">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a><span data-ttu-id="80c8f-116">クエリ エディターから SQL Server Profiler を起動するには</span><span class="sxs-lookup"><span data-stu-id="80c8f-116">To start SQL Server Profiler from the Query Editor</span></span>  
  
1.  <span data-ttu-id="80c8f-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のメニュー バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-117">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] menu bar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="80c8f-118">クエリ エディター内で右クリックし、 **[SQL Server Profiler でクエリをトレース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="80c8f-118">In Query Editor, right-click and then select **Trace Query in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80c8f-119">接続コンテキストはエディター接続、トレース テンプレートは TSQL_SPs、適用されているフィルターは SPID = query window SPID です。</span><span class="sxs-lookup"><span data-stu-id="80c8f-119">The connection context is the editor connection, the trace template is TSQL_SPs, and the applied filter is SPID = query window SPID.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a><span data-ttu-id="80c8f-120">利用状況モニターから SQL Server Profiler を起動するには</span><span class="sxs-lookup"><span data-stu-id="80c8f-120">To start SQL Server Profiler from Activity Monitor</span></span>  
  
1.  <span data-ttu-id="80c8f-121">オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを右クリックし、 **[利用状況モニター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-121">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="80c8f-122">**プロセス** ペインをクリックし、プロファイルするプロセスを右クリックして **[SQL Server Profiler のトレース プロセス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="80c8f-122">Click the **Processes** pane, right-click the process that you want to profile, and then click **Trace Process in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80c8f-123">プロセスを選択したときに、利用状況モニターが開いていた場合、接続コンテキストはオブジェクト エクスプローラー接続になります。</span><span class="sxs-lookup"><span data-stu-id="80c8f-123">When a process is selected, the connection context is the Object Explorer connection when Activity Monitor was opened.</span></span> <span data-ttu-id="80c8f-124">トレース テンプレートはサーバーの種類に応じた既定値になります。SPID は、選択されたプロセスの SPID と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="80c8f-124">The trace template is the default based on the server type, and the SPID equals the SPID for the selected process.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="80c8f-125">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="80c8f-125">.NET Framework Security</span></span>  
 <span data-ttu-id="80c8f-126">Windows 認証モードでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行するユーザー アカウントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続する権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="80c8f-126">In Windows Authentication mode, the user account that runs [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="80c8f-127">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]でトレースを実行するには、ユーザーが ALTER TRACE 権限も持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="80c8f-127">To perform tracing with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], users must also have the ALTER TRACE permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c8f-128">参照</span><span class="sxs-lookup"><span data-stu-id="80c8f-128">See Also</span></span>  
 <span data-ttu-id="80c8f-129">[SQL Server プロファイラー](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80c8f-129">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80c8f-130">[SQL Server Management Studio の使用 [SQL Server]](../../database-engine/use-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="80c8f-130">[Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)</span></span>  
  
  
