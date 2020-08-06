---
title: データベース エンジン チューニング アドバイザーの起動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server]
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: 4abc0e10-96fd-4e46-93d6-d7ee03eec844
author: stevestein
ms.author: sstein
ms.openlocfilehash: ad8a594873e581d116acd50a336652f27002112d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719220"
---
# <a name="launching-database-engine-tuning-advisor"></a><span data-ttu-id="70e29-102">データベース エンジン チューニング アドバイザーの起動</span><span class="sxs-lookup"><span data-stu-id="70e29-102">Launching Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="70e29-103">まず、データベース エンジン チューニング アドバイザーのグラフィカル ユーザー インターフェイス (GUI) を開きます。</span><span class="sxs-lookup"><span data-stu-id="70e29-103">To begin, open the Database Engine Tuning Advisor graphical user interface (GUI).</span></span> <span data-ttu-id="70e29-104">初回起動時には、 **sysadmin** 固定サーバー ロールのメンバーがデータベース エンジン チューニング アドバイザーを起動し、アプリケーションを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70e29-104">On first use, a member of the **sysadmin** fixed server role must launch Database Engine Tuning Advisor to initialize the application.</span></span> <span data-ttu-id="70e29-105">初期化が完了すると、 **db_owner** 固定データベース ロールのメンバーがデータベース エンジン チューニング アドバイザーを使用し、所有するデータベースをチューニングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="70e29-105">After initialization, members of the **db_owner** fixed database role can use Database Engine Tuning Advisor to tune databases that they own.</span></span> <span data-ttu-id="70e29-106">データベース エンジン チューニング アドバイザーの初期化の詳細については、「 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70e29-106">For more information about initializing Database Engine Tuning Advisor, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
### <a name="open-the-database-engine-tuning-advisor-gui"></a><span data-ttu-id="70e29-107">データベース エンジン チューニング アドバイザーの GUI を開く</span><span class="sxs-lookup"><span data-stu-id="70e29-107">Open the Database Engine Tuning Advisor GUI</span></span>  
  
1.  <span data-ttu-id="70e29-108">Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントします。次に、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] をポイントし、 **[パフォーマンス ツール]** をポイントして、 **[データベース エンジン チューニング アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70e29-108">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="70e29-109">**[サーバーへの接続]** ダイアログ ボックスで既定の設定を確認し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70e29-109">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="70e29-110">既定では、次の図に示す構成でデータベース エンジン チューニング アドバイザーが開きます。</span><span class="sxs-lookup"><span data-stu-id="70e29-110">By default, Database Engine Tuning Advisor opens to the configuration in the following illustration:</span></span>  
  
 <span data-ttu-id="70e29-111">![データベース エンジン チューニング アドバイザーの既定のウィンドウ](media/defaultdtagui.gif "データベース エンジン チューニング アドバイザーの既定のウィンドウ")</span><span class="sxs-lookup"><span data-stu-id="70e29-111">![Database Engine Tuning Advisor default window](media/defaultdtagui.gif "Database Engine Tuning Advisor default window")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70e29-112">[タブと**セッション名**] ボックスには、コンピューターの名前と接続先のインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-112">The tab and **Session Name** box display the name of your computer and the instance you are connected to.</span></span> <span data-ttu-id="70e29-113">タブおよびボックスには、現在の日付と時刻も表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-113">The tab and box also display the current date and time.</span></span>  
  
 <span data-ttu-id="70e29-114">データベース エンジン チューニング アドバイザーの GUI を初めて開くと、2 つのメイン ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-114">Two main panes are displayed in the Database Engine Tuning Advisor GUI when it is first opened.</span></span>  
  
-   <span data-ttu-id="70e29-115">左側のウィンドウには、このインスタンスで実行されたすべてのチューニングセッションを一覧表示するセッションモニターが表示され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="70e29-115">The left pane contains the Session Monitor, which lists all tuning sessions that have been performed on this [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="70e29-116">データベース エンジン チューニング アドバイザーを開くと、セッション モニターの最上部に新しいセッションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-116">When you open Database Engine Tuning Advisor, it displays a new session at the top of the pane.</span></span> <span data-ttu-id="70e29-117">隣のペインで、このセッションに名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="70e29-117">You can name this session in the adjacent pane.</span></span> <span data-ttu-id="70e29-118">初期状態では既定のセッションのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-118">Initially, only a default session is listed.</span></span> <span data-ttu-id="70e29-119">このセッションは、データベース エンジン チューニング アドバイザーが自動的に作成する既定のセッションです。</span><span class="sxs-lookup"><span data-stu-id="70e29-119">This is the default session that Database Engine Tuning Advisor automatically creates for you.</span></span> <span data-ttu-id="70e29-120">データベースのチューニングが完了すると、接続している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで実行されたすべてのチューニング セッションが、新しいセッションの下に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-120">After you have tuned databases, all tuning sessions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you are connected are listed below the new session.</span></span> <span data-ttu-id="70e29-121">セッション名を変更する、セッションを閉じる、削除する、またはクローンを作成するときは、チューニング セッションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="70e29-121">You can right-click a tuning session to rename it, close it, delete it, or clone it.</span></span> <span data-ttu-id="70e29-122">リスト内で右クリックすると、名前順、状態順、または作成時間順にセッションを並べ替えることができます。新しいセッションも作成できます。</span><span class="sxs-lookup"><span data-stu-id="70e29-122">If you right-click in the list you can sort the sessions by name, status, or creation time, or create a new session.</span></span> <span data-ttu-id="70e29-123">このペインの下部には、選択したチューニング セッションの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-123">In the bottom section of this pane, details of the selected tuning session are displayed.</span></span> <span data-ttu-id="70e29-124">**[項目別]** ボタンをクリックすると、詳細情報がカテゴリ別に分類され、表示されます。 **[アルファベット順]** ボタンをクリックすると、詳細情報がアルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-124">You can choose to display the details organized into categories with the **Categorized** button, or you can display them in an alphabetized list by using the **Alphabetical** button.</span></span> <span data-ttu-id="70e29-125">このペインの右側の境界を左方向にドラッグすることで、セッション モニターを非表示にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="70e29-125">You can also hide Session Monitor by dragging the right pane border to the left side of the window.</span></span> <span data-ttu-id="70e29-126">再度表示するには、ペインの境界を右方向にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="70e29-126">To view it again, drag the pane border back to the right.</span></span> <span data-ttu-id="70e29-127">セッション モニターは以前のチューニング セッションを表示できるほか、似ている定義を使用して新しいセッションを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="70e29-127">Session Monitor enables you to view previous tuning sessions, or to use them to create new sessions with similar definitions.</span></span> <span data-ttu-id="70e29-128">また、セッション モニターを使用してチューニング推奨設定を評価することもできます。</span><span class="sxs-lookup"><span data-stu-id="70e29-128">You can also use Session Monitor to evaluate tuning recommendations.</span></span> <span data-ttu-id="70e29-129">詳細については、「 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70e29-129">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="70e29-130">このチュートリアルに戻るには、ブラウザーの **[戻る]** ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="70e29-130">Use the **Back** button on your browser to return to this tutorial.</span></span>  
  
-   <span data-ttu-id="70e29-131">右側のペインには、 **[全般]** タブと **[チューニング オプション]** タブがあります。</span><span class="sxs-lookup"><span data-stu-id="70e29-131">The right pane contains the **General** and the **Tuning Options** tabs.</span></span> <span data-ttu-id="70e29-132">これらのタブでデータベース エンジン チューニング セッションを定義します。</span><span class="sxs-lookup"><span data-stu-id="70e29-132">This is where you can define your Database Engine Tuning session.</span></span> <span data-ttu-id="70e29-133">**[全般]** タブでは、チューニング セッション名の入力、使用するワークロード ファイルまたはテーブルの指定、およびこのセッションでチューニングするデータベースとテーブルの選択を行います。</span><span class="sxs-lookup"><span data-stu-id="70e29-133">In the **General** tab, you type the name for your tuning session, specify the workload file or table to use, and select the databases and tables you want to tune in this session.</span></span> <span data-ttu-id="70e29-134">ワークロードとは、チューニングするデータベースに対して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットです。</span><span class="sxs-lookup"><span data-stu-id="70e29-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="70e29-135">データベースをチューニングする際には、トレース ファイル、トレース テーブル、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、または XML ファイルがワークロード入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="70e29-135">Database Engine Tuning Advisor uses trace files, trace tables, [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, or XML files as workload input when tuning databases.</span></span> <span data-ttu-id="70e29-136">**[チューニング オプション]** タブでは、物理データベース設計構造 (インデックスまたはインデックス付きビュー) を選択し、その分析時に適用するパーティション分割方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="70e29-136">On the **Tuning Options** tab, you can select the physical database design structures (indexes or indexed views) and the partitioning strategy that you want Database Engine Tuning Advisor to consider during its analysis.</span></span> <span data-ttu-id="70e29-137">また、ワークロードのチューニングにあてる最大時間を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="70e29-137">On this tab you also can specify the maximum time that Database Engine Tuning Advisor takes to tune a workload.</span></span> <span data-ttu-id="70e29-138">既定のワークロード チューニング時間は 1 時間です。</span><span class="sxs-lookup"><span data-stu-id="70e29-138">By default, Database Engine Tuning Advisor will tune a workload for one hour.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70e29-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディターから [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] スクリプトをインポートする場合、XML ファイルからスクリプトを取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="70e29-139">Database Engine Tuning Advisor can take XML files as input when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is imported from [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span> <span data-ttu-id="70e29-140">詳細については、「 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] データベース エンジン チューニング アドバイザーからの出力の表示および操作 [」の](../../relational-databases/performance/database-engine-tuning-advisor.md)クエリ エディターからデータベース エンジン チューニング アドバイザーを起動する方法に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70e29-140">For more information, see the section on launching Database Engine Tuning Advisor from the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor in [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="70e29-141">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="70e29-141">Next Task in Lesson</span></span>  
 [<span data-ttu-id="70e29-142">ツール オプションとレイアウトの設定</span><span class="sxs-lookup"><span data-stu-id="70e29-142">Setting Tool Options and Layout</span></span>](lesson-1-2-setting-tool-options-and-layout.md)  
  
  