---
title: データベース エンジン チューニング アドバイザーの起動および使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.dta.advancedtuningoptions.f1
- sql12.dta.general.f1
- sql12.dta.tuningoptions.f1
- sql12.dta.workload.f1
- sql12.dta.progress.f1
- sql12.dta.options.f1
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: a4e3226a-3917-4ec8-bdf0-472879d231c9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46f8e49de657d7021d846c7e57022a580b877f8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716285"
---
# <a name="start-and-use-the-database-engine-tuning-advisor"></a><span data-ttu-id="d721e-102">データベース エンジン チューニング アドバイザーの起動および使用</span><span class="sxs-lookup"><span data-stu-id="d721e-102">Start and Use the Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="d721e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でデータベース エンジン チューニング アドバイザーを起動して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d721e-103">This topic describes how to start and use Database Engine Tuning Advisor in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d721e-104">データベースをチューニングした後で結果を表示および操作する方法については、「 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-104">For information about how to view and work with the results after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
##  <a name="initialize-the-database-engine-tuning-advisor"></a><a name="Initialize"></a> <span data-ttu-id="d721e-105">データベース エンジン チューニング アドバイザーを初期化する</span><span class="sxs-lookup"><span data-stu-id="d721e-105">Initialize the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="d721e-106">初回起動時に、 **sysadmin** 固定サーバー ロールのメンバーであるユーザーがデータベース エンジン チューニング アドバイザーを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-106">On first use, a user who is member of the **sysadmin** fixed server role must initialize the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="d721e-107">これは、チューニング操作をサポートするには、いくつかのシステム テーブルを `msdb` データベースに作成する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="d721e-107">This is because several system tables must be created in the `msdb` database to support tuning operations.</span></span> <span data-ttu-id="d721e-108">また、初期化によって、 **db_owner** 固定データベース ロールのメンバーであるユーザーも自分の所有するデータベースにあるテーブルのワークロードをチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-108">Initialization also enables users that are members of the **db_owner** fixed database role to tune workloads on tables in databases that they own.</span></span>  
  
 <span data-ttu-id="d721e-109">システム管理者権限を持つユーザーは、次の操作のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-109">A user that has system administrator permissions must perform either of the following actions:</span></span>  
  
-   <span data-ttu-id="d721e-110">データベース エンジン チューニング アドバイザーのグラフィカル ユーザー インターフェイスを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d721e-110">Use the Database Engine Tuning Advisor graphical user interface to connect to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d721e-111">詳細については、このトピックの「 [データベース エンジン チューニング アドバイザーを起動する](#Start) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-111">For more information, see [Start the Database Engine Tuning Advisor](#Start) later in this topic.</span></span>  
  
-   <span data-ttu-id="d721e-112">**dta** ユーティリティを使用して最初のワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="d721e-112">Use the **dta** utility to tune the first workload.</span></span> <span data-ttu-id="d721e-113">詳細については、このトピックの「 [dta ユーティリティを使用する](#dta) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-113">For more information, see [Use the dta Utility](#dta) later in this topic.</span></span>  
  
##  <a name="start-the-database-engine-tuning-advisor"></a><a name="Start"></a> <span data-ttu-id="d721e-114">データベース エンジン チューニング アドバイザーを起動する</span><span class="sxs-lookup"><span data-stu-id="d721e-114">Start the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="d721e-115">データベース エンジン チューニング アドバイザーのグラフィカル インターフェイス (GUI) は、さまざまなシナリオでのデータベース チューニングに対応するために、いくつかの異なる方法で起動することができます。</span><span class="sxs-lookup"><span data-stu-id="d721e-115">You can start the Database Engine Tuning Advisor graphical user interface (GUI) in several different ways to support database tuning in a variety of scenarios.</span></span> <span data-ttu-id="d721e-116">データベース エンジン チューニング アドバイザーを起動する方法としては、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[スタート]** メニューからの操作、 **[ツール]** メニューからの操作、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターからの操作、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の **[ツール]** メニューからの操作があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-116">The different ways to start Database Engine Tuning Advisor include: from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and from the **Tools** menu in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="d721e-117">データベース エンジン チューニング アドバイザーを初めて起動すると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。このダイアログ ボックスで接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-117">When you first start Database Engine Tuning Advisor, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d721e-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をシングル ユーザー モードで実行している場合は、データベース エンジン チューニング アドバイザーを起動しないでください。</span><span class="sxs-lookup"><span data-stu-id="d721e-118">Do not start Database Engine Tuning Advisor when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in single-user mode.</span></span> <span data-ttu-id="d721e-119">サーバーをシングル ユーザー モードで実行しているときにデータベース エンジン チューニング アドバイザーを起動しようとしても、エラーが返されて、データベース エンジン チューニング アドバイザーは起動しません。</span><span class="sxs-lookup"><span data-stu-id="d721e-119">If you attempt to start it while the server is in single-user mode, an error will be returned and Database Engine Tuning Advisor will not start.</span></span> <span data-ttu-id="d721e-120">シングル ユーザー モードの詳細については、「 [シングル ユーザー モードでの SQL Server の起動](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-120">For more information about single-user mode, see [Start SQL Server in Single-User Mode](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).</span></span>  
  
#### <a name="to-start-database-engine-tuning-advisor-from-the-windows-start-menu"></a><span data-ttu-id="d721e-121">Windows の [スタート] メニューからデータベース エンジン チューニング アドバイザーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d721e-121">To start Database Engine Tuning Advisor from the Windows Start menu</span></span>  
  
1.  <span data-ttu-id="d721e-122">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[パフォーマンス ツール]** の順にポイントし、 **[データベース エンジン チューニング アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-122">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-management-studio"></a><span data-ttu-id="d721e-123">SQL Server Management Studio からデータベース エンジン チューニング アドバイザーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d721e-123">To start the Database Engine Tuning Advisor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d721e-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ツール]** メニューで、 **[データベース エンジン チューニング アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-124">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-from-the-sql-server-management-studio-query-editor"></a><span data-ttu-id="d721e-125">SQL Server Management Studio のクエリ エディターからデータベース エンジン チューニング アドバイザーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d721e-125">To start the Database Engine Tuning Advisor from the SQL Server Management Studio Query Editor</span></span>  
  
1.  <span data-ttu-id="d721e-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]スクリプト ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d721e-126">Open a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d721e-127">詳細については、「[クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-127">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="d721e-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト内のクエリを選択するか、スクリプト全体を選択します。選択範囲を右クリックし、 **[データベース エンジン チューニング アドバイザーでのクエリの分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-128">Select a query in the [!INCLUDE[tsql](../../includes/tsql-md.md)] script, or select the entire script, right-click the selection, and choose **Analyze Query in Database Engine Tuning Advisor**.</span></span> <span data-ttu-id="d721e-129">データベース エンジン チューニング アドバイザー GUI が表示され、そのスクリプトが XML ファイル ワークロードとしてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="d721e-129">The Database Engine Tuning Advisor GUI opens and imports the script as an XML file workload.</span></span> <span data-ttu-id="d721e-130">セッション名とチューニング オプションを指定して、選択した [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを自分のワークロードとしてチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-130">You can specify a session name and tuning options to tune the selected [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as your workload.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-profiler"></a><span data-ttu-id="d721e-131">SQL Server Profiler からデータベース エンジン チューニング アドバイザーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d721e-131">To start the Database Engine Tuning Advisor in SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="d721e-132">SQL Server Profiler の **[ツール]** メニューの **[データベース エンジン チューニング アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-132">On the SQL Server Profiler **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
##  <a name="create-a-workload"></a><a name="Create"></a> <span data-ttu-id="d721e-133">ワークロードを作成する</span><span class="sxs-lookup"><span data-stu-id="d721e-133">Create a Workload</span></span>  
 <span data-ttu-id="d721e-134">ワークロードとは、チューニングするデータベースに対して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのセットです。</span><span class="sxs-lookup"><span data-stu-id="d721e-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="d721e-135">データベース エンジン チューニング アドバイザーでは、サーバーのクエリ パフォーマンスを向上させるインデックスやパーティション分割ストラテジを推奨するために、これらのワークロードが分析されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-135">Database Engine Tuning Advisor analyzes these workloads to recommend indexes or partitioning strategies that will improve your server's query performance.</span></span>  
  
 <span data-ttu-id="d721e-136">ワークロードを作成するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="d721e-136">You can create a workload by using one of the following methods.</span></span>  
  
-   <span data-ttu-id="d721e-137">プラン キャッシュをワークロードとして指定する。</span><span class="sxs-lookup"><span data-stu-id="d721e-137">Use the plan cache as a workload.</span></span> <span data-ttu-id="d721e-138">このようにすることでワークロードを手動で作成する手間が省けます。</span><span class="sxs-lookup"><span data-stu-id="d721e-138">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="d721e-139">詳細については、このトピックの「 [データベースをチューニングする](#Tune) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-139">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
-   <span data-ttu-id="d721e-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディター、または使い慣れたテキスト エディターを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを手動で作成できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-140">Use the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or your favorite text editor to manually create [!INCLUDE[tsql](../../includes/tsql-md.md)] script workloads.</span></span>  
  
-   <span data-ttu-id="d721e-141">トレース ファイルまたはトレース テーブル ワークロードを作成するには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="d721e-141">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create trace file or trace table workloads</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d721e-142">ワークロードとしてトレース テーブルを使用する場合、そのテーブルは、データベース エンジン チューニング アドバイザーがチューニングを実行するサーバーと同じサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-142">When using a trace table as a workload, that table must exist on the same server where Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="d721e-143">別のサーバーにトレース テーブルを作成した場合は、データベース エンジン チューニング アドバイザーでチューニングされているサーバーに移動します。</span><span class="sxs-lookup"><span data-stu-id="d721e-143">If you create the trace table on a different server, then move it to the server where Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="d721e-144">ワークロードは XML 入力ファイルにも埋め込むことができます。XML 入力ファイルでは、各イベントの重みも指定できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-144">Workloads can also be embedded in an XML input file, where you can also specify a weight for each event.</span></span> <span data-ttu-id="d721e-145">埋め込まれたワークロードを指定する方法については、このトピックの「 [XML 入力ファイルを作成する](#XMLInput) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-145">For more information about specifying embedded workloads, see [Create an XML Input File](#XMLInput) later in this topic.</span></span>  
  
###  <a name="to-create-transact-sql-script-workloads"></a><a name="SSMS"></a> <span data-ttu-id="d721e-146">Transact-SQL スクリプトのワークロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="d721e-146">To create Transact-SQL script workloads</span></span>  
  
1.  <span data-ttu-id="d721e-147">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でクエリ エディターを起動します。</span><span class="sxs-lookup"><span data-stu-id="d721e-147">Launch the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d721e-148">詳細については、「[クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-148">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="d721e-149">クエリ エディターに [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-149">Type your [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor.</span></span> <span data-ttu-id="d721e-150">このスクリプトには、チューニングする 1 つ以上のデータベースに対して実行する一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-150">This script should contain a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against the database or databases that you want to tune.</span></span>  
  
3.  <span data-ttu-id="d721e-151">**.sql** 拡張子を付けて、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d721e-151">Save the file with a **.sql** extension.</span></span> <span data-ttu-id="d721e-152">データベース エンジン チューニング アドバイザーの GUI および **dta** コマンド ライン ユーティリティで、この [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをワークロードとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-152">The Database Engine Tuning Advisor GUI and the command-line **dta** utility can use this [!INCLUDE[tsql](../../includes/tsql-md.md)] script as a workload.</span></span>  
  
###  <a name="to-create-trace-file-and-trace-table-workloads"></a><a name="Profiler"></a> <span data-ttu-id="d721e-153">トレース ファイル ワークロードおよびトレース テーブル ワークロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="d721e-153">To create trace file and trace table workloads</span></span>  
  
1.  <span data-ttu-id="d721e-154">次の方法のいずれかを使用して、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="d721e-154">Launch [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="d721e-155">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[パフォーマンス ツール]** の順にポイントして、 **[SQL Server Profiler]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-155">On the **Start** menu, point to **All Programs**, **Microsoft SQL Server**, **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
    -   <span data-ttu-id="d721e-156">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で **[ツール]** メニューをクリックし、次に **[SQL Server Profiler]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-156">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click the **Tools** menu, and then click **SQL Server Profiler**.</span></span>  
  
2.  <span data-ttu-id="d721e-157">次の手順では、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** テンプレートを使用して、トレース ファイルまたはトレース テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-157">Create a trace file or table as described in the following procedures that uses the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** template:</span></span>  
  
    -   [<span data-ttu-id="d721e-158">トレースの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d721e-158">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
    -   [<span data-ttu-id="d721e-159">トレース結果のファイルへの保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d721e-159">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
         <span data-ttu-id="d721e-160">データベース エンジン チューニング アドバイザーでは、ワークロード トレース ファイルはロールオーバー ファイルと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d721e-160">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="d721e-161">ロールオーバー ファイルの詳細については、「 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-161">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
    -   [<span data-ttu-id="d721e-162">トレース結果のテーブルへの保存 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d721e-162">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
         <span data-ttu-id="d721e-163">トレース テーブルをワークロードとして使用する前に、トレースが停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d721e-163">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
 <span data-ttu-id="d721e-164">データベース エンジン チューニング アドバイザー用のワークロードをキャプチャするには、SQL Server Profiler の Tuning テンプレートを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d721e-164">We recommend that you use the SQL Server Profiler Tuning template for capturing workloads for Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="d721e-165">独自のテンプレートを使用する場合、次のトレース イベントがキャプチャされるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d721e-165">If you want to use your own template, ensure that the following trace events are captured:</span></span>  
  
-   <span data-ttu-id="d721e-166">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="d721e-166">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="d721e-167">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="d721e-167">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="d721e-168">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="d721e-168">**SP:StmtCompleted**</span></span>  
  
 <span data-ttu-id="d721e-169">これらのトレース イベントの **Starting** バージョンを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-169">You can also use the **Starting** versions of these trace events.</span></span> <span data-ttu-id="d721e-170">たとえば、 **SQL:BatchStarting**などです。</span><span class="sxs-lookup"><span data-stu-id="d721e-170">For example, **SQL:BatchStarting**.</span></span> <span data-ttu-id="d721e-171">ただし、これらのトレース イベントの **Completed** バージョンには、 **Duration** 列が含まれているので、データベース エンジン チューニング アドバイザーは、より効率的にワークロードのチューニングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d721e-171">However, the **Completed** versions of these trace events include the **Duration** column, which allows Database Engine Tuning Advisor to more effectively tune the workload.</span></span> <span data-ttu-id="d721e-172">データベース エンジン チューニング アドバイザーは、他の種類のトレース イベントのチューニングは行いません。</span><span class="sxs-lookup"><span data-stu-id="d721e-172">Database Engine Tuning Advisor does not tune other types of trace events.</span></span> <span data-ttu-id="d721e-173">これらのトレース イベントの詳細については、「 [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) 」および「 [TSQL Event Category](../event-classes/tsql-event-category.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-173">For more information about these trace events, see [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) and [TSQL Event Category](../event-classes/tsql-event-category.md).</span></span> <span data-ttu-id="d721e-174">SQL トレース ストアド プロシージャを使用したトレース ファイル ワークロードの作成の詳細については、「[トレースの作成 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-174">For information about using the SQL Trace stored procedures to create a trace file workload, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
### <a name="trace-file-or-trace-table-workloads-that-contain-the-loginname-data-column"></a><span data-ttu-id="d721e-175">LoginName データ列を含んでいるトレース ファイル ワークロードまたはトレース テーブル ワークロード</span><span class="sxs-lookup"><span data-stu-id="d721e-175">Trace File or Trace Table Workloads That Contain the LoginName Data Column</span></span>  
 <span data-ttu-id="d721e-176">データベース エンジン チューニング アドバイザーは、チューニング処理の一環としてプラン表示要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="d721e-176">Database Engine Tuning Advisor submits Showplan requests as part of the tuning process.</span></span> <span data-ttu-id="d721e-177">**LoginName** データ列が含まれているトレース テーブルまたはトレース ファイルをワークロードとして使用する場合、データベース エンジン チューニング アドバイザーは、 **LoginName**に指定されているユーザーの権限を借用します。</span><span class="sxs-lookup"><span data-stu-id="d721e-177">When a trace table or file that contains the **LoginName** data column is consumed as a workload, Database Engine Tuning Advisor impersonates the user specified in **LoginName**.</span></span> <span data-ttu-id="d721e-178">トレースに含まれているステートメントに対してプラン表示を実行し生成するための SHOWPLAN 権限がそのユーザーに許可されていない場合、そのステートメントのチューニングは行われません。</span><span class="sxs-lookup"><span data-stu-id="d721e-178">If this user has not been granted the SHOWPLAN permission, which enables the user to execute and produce Showplans for the statements contained in the trace, Database Engine Tuning Advisor will not tune those statements.</span></span>  
  
##### <a name="to-avoid-granting-the-showplan-permission-to-each-user-specified-in-the-loginname-column-of-the-trace"></a><span data-ttu-id="d721e-179">トレースの LoginName 列に指定された各ユーザーに SHOWPLAN 権限を許可しないようにするには</span><span class="sxs-lookup"><span data-stu-id="d721e-179">To avoid granting the SHOWPLAN permission to each user specified in the LoginName column of the trace</span></span>  
  
1.  <span data-ttu-id="d721e-180">トレース ファイル ワークロードまたはトレース テーブル ワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="d721e-180">Tune the trace file or table workload.</span></span> <span data-ttu-id="d721e-181">詳細については、このトピックの「 [データベースをチューニングする](#Tune) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-181">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
2.  <span data-ttu-id="d721e-182">権限が不適切だったためにチューニングされなかったステートメントがないかどうか、チューニング ログを確認します。</span><span class="sxs-lookup"><span data-stu-id="d721e-182">Check the tuning log for statements that were not tuned due to inadequate permissions.</span></span> <span data-ttu-id="d721e-183">詳細については、「 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-183">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="d721e-184">チューニングされなかったイベントから **LoginName** 列を削除することで、新しいワークロードを作成します。チューニングされなかったイベントのみを新しいトレース ファイルまたは新しいトレース テーブルに保存します。</span><span class="sxs-lookup"><span data-stu-id="d721e-184">Create a new workload by deleting the **LoginName** column from the events that were not tuned, and then save only the untuned events in a new trace file or table.</span></span> <span data-ttu-id="d721e-185">トレースからデータ列を削除する方法の詳細については、「[トレース ファイルに含めるイベントとデータ列の指定 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)」または「[既存のトレースの変更 &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-185">For more information about deleting data columns from a trace, see [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) or [Modify an Existing Trace &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md).</span></span>  
  
4.  <span data-ttu-id="d721e-186">**LoginName** 列が含まれていない新しいワークロードをデータベース エンジン チューニング アドバイザーに再送信します。</span><span class="sxs-lookup"><span data-stu-id="d721e-186">Resubmit the new workload without the **LoginName** column to Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="d721e-187">トレースでログイン情報が指定されていないので、データベース エンジン チューニング アドバイザーはこの新しいワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="d721e-187">Database Engine Tuning Advisor will tune the new workload because login information is not specified in the trace.</span></span> <span data-ttu-id="d721e-188">ステートメントに **LoginName** が含まれていない場合、データベース エンジン チューニング アドバイザーは、チューニング セッションを開始したユーザー ( **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのいずれかのメンバー) の権限を借用してステートメントをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="d721e-188">If the **LoginName** does not exist for a statement, Database Engine Tuning Advisor tunes that statement by impersonating the user who started the tuning session (a member of either the **sysadmin** fixed server role or the **db_owner** fixed database role).</span></span>  
  
##  <a name="tune-a-database"></a><a name="Tune"></a> <span data-ttu-id="d721e-189">データベースをチューニングする</span><span class="sxs-lookup"><span data-stu-id="d721e-189">Tune a Database</span></span>  
 <span data-ttu-id="d721e-190">データベースをチューニングするには、データベース エンジン チューニング アドバイザーの GUI または **dta** ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-190">To tune a database, you can use the Database Engine Tuning Advisor GUI or the **dta** utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d721e-191">データベース エンジン チューニング アドバイザーのワークロードとしてトレース テーブルを使用する前に、トレースが停止していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-191">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="d721e-192">データベース エンジン チューニング アドバイザーでは、トレース イベントをワークロードとして書き込み中のトレース テーブルには使用できません。</span><span class="sxs-lookup"><span data-stu-id="d721e-192">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
### <a name="use-the-database-engine-tuning-advisor-graphical-user-interface"></a><span data-ttu-id="d721e-193">データベース エンジン チューニング アドバイザーのグラフィカル ユーザー インターフェイスを使用する</span><span class="sxs-lookup"><span data-stu-id="d721e-193">Use the Database Engine Tuning Advisor Graphical User Interface</span></span>  
 <span data-ttu-id="d721e-194">データベース エンジン チューニング アドバイザーの GUI で、プラン キャッシュ、ワークロード ファイル、またはワークロード テーブルを使用してデータベースをチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-194">On the Database Engine Tuning Advisor GUI, you can tune a database by using the plan cache, workload files, or workload tables.</span></span> <span data-ttu-id="d721e-195">データベース エンジン チューニング アドバイザーの GUI を使用して、現在のチューニング セッションの結果および以前のチューニング セッションの結果を簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-195">You can use the Database Engine Tuning Advisor GUI to easily view the results of your current tuning session and results of previous tuning sessions.</span></span> <span data-ttu-id="d721e-196">ユーザー インターフェイス オプションの詳細については、後の「 [ユーザー インターフェイスの説明](#UI) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-196">For information about user interface options, see [User Interface Descriptions](#UI) later in this topic.</span></span> <span data-ttu-id="d721e-197">データベースのチューニング後の出力を操作する方法については、「 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-197">For more information about working with the output after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
####  <a name="to-tune-a-database-by-using-the-plan-cache"></a><a name="PlanCache"></a> <span data-ttu-id="d721e-198">プラン キャッシュを使用してデータベースをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-198">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="d721e-199">データベース エンジン チューニング アドバイザーを起動し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにログインします。</span><span class="sxs-lookup"><span data-stu-id="d721e-199">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d721e-200">詳細については、このトピックの「 [データベース エンジン チューニング アドバイザーを起動する](#Start) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-200">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="d721e-201">**[全般]** タブで **[セッション名]** ボックスに名前を入力して、新しいチューニング セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-201">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span> <span data-ttu-id="d721e-202">セッションのチューニングを始める前に、 **[全般]** タブのフィールドを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-202">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="d721e-203">**[チューニング オプション]** タブの設定は、チューニング セッションを開始する前に変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d721e-203">It is not necessary to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
3.  <span data-ttu-id="d721e-204">ワークロード オプションとして **[プラン キャッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-204">Select **Plan Cache** as the workload option.</span></span> <span data-ttu-id="d721e-205">データベース エンジン チューニング アドバイザーによって、分析に使用される上位 1,000 件のイベントがプラン キャッシュから選択されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-205">Database Engine Tuning Advisor selects the top 1,000 events from the plan cache to use for analysis.</span></span>  
  
4.  <span data-ttu-id="d721e-206">チューニングする必要のあるデータベースを選択し、必要に応じて、 **[選択したテーブル]** から、各データベースのテーブル (複数可) を選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-206">Select the database or databases that you want to tune, and optionally from **Selected Tables**, choose one or more tables from each database.</span></span> <span data-ttu-id="d721e-207">すべてのデータベースのキャッシュ エントリを含めるには、 **[チューニング オプション]** の **[詳細設定オプション]** をクリックし、 **[すべてのデータベースのプラン キャッシュ イベントを含める]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-207">To include cache entries for all databases, from **Tuning Options**, click **Advanced Options** and then check **Include plan cache events from all databases**.</span></span>  
  
5.  <span data-ttu-id="d721e-208">チューニング ログを保存するには、 **[チューニング ログを保存する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-208">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="d721e-209">チューニング ログのコピーを保存しない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-209">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="d721e-210">セッションを開いて **[進行状況]** タブを選択すると、分析後にチューニング ログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-210">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
6.  <span data-ttu-id="d721e-211">**[チューニング オプション]** タブをクリックし、必要なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-211">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
7.  <span data-ttu-id="d721e-212">**[分析の開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-212">Click **Start Analysis**.</span></span>  
  
     <span data-ttu-id="d721e-213">チューニング セッションの開始後にセッションを停止する場合、 **[アクション]** メニューにある次のオプションから 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-213">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="d721e-214">**[分析の停止 (推奨設定を使用)]** を選択すると、チューニング セッションが停止され、この時点までに実行された分析に基づいて、データベース エンジン チューニング アドバイザーで推奨設定を生成するかどうかを決定するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-214">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="d721e-215">**[分析の停止]** を選択すると、推奨設定を生成せずにチューニング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="d721e-215">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d721e-216">データベース エンジン チューニング アドバイザーの一時停止はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d721e-216">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="d721e-217">ツールバーの **[分析の停止]** または **[分析の停止 (推奨設定を使用)]** のいずれかをクリックしてからツールバーの **[分析の開始]** をクリックすると、データベース エンジン チューニング アドバイザーは新しいチューニング セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="d721e-217">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
##### <a name="to-tune-a-database-using-a-workload-file-or-table-as-input"></a><span data-ttu-id="d721e-218">ワークロード ファイルまたはテーブルを入力として使用してデータベースをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-218">To tune a database using a workload file or table as input</span></span>  
  
1.  <span data-ttu-id="d721e-219">解析時に、データベース エンジン チューニング アドバイザーによって追加、削除、または保有を検討するデータベースの機能 (インデックス、インデックス付きビュー、パーティション分割) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-219">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="d721e-220">ワークロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-220">Create a workload.</span></span> <span data-ttu-id="d721e-221">詳細については、このトピックの「 [ワークロードを作成する](#Create) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-221">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="d721e-222">データベース エンジン チューニング アドバイザーを起動し、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインします。</span><span class="sxs-lookup"><span data-stu-id="d721e-222">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d721e-223">詳細については、このトピックの「 [データベース エンジン チューニング アドバイザーを起動する](#Start) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-223">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
4.  <span data-ttu-id="d721e-224">**[全般]** タブで **[セッション名]** ボックスに名前を入力して、新しいチューニング セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-224">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span>  
  
5.  <span data-ttu-id="d721e-225">**[ワークロード]** で **[ファイル]** または [テーブル] を選択し、該当するボックスにファイルのパスまたはテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-225">Choose either a **Workload File** or **Table** and type either the path to the file, or the name of the table in the adjacent text box.</span></span>  
  
     <span data-ttu-id="d721e-226">テーブルは次の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-226">The format for specifying a table is</span></span>  
  
    ```  
  
    database_name.schema_name.table_name  
    ```  
  
     <span data-ttu-id="d721e-227">ワークロード ファイルまたはテーブルを検索するには、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-227">To search for a workload file or table, click **Browse**.</span></span> <span data-ttu-id="d721e-228">データベース エンジン チューニング アドバイザーでは、ワークロード ファイルがロールオーバー ファイルであることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="d721e-228">Database Engine Tuning Advisor assumes that workload files are rollover files.</span></span> <span data-ttu-id="d721e-229">ロールオーバー ファイルの詳細については、「 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-229">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
     <span data-ttu-id="d721e-230">ワークロードとしてトレース テーブルを使用する場合、そのテーブルは、データベース エンジン チューニング アドバイザーがチューニングを実行するサーバーと同じサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-230">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="d721e-231">異なるサーバー上でトレース テーブルを作成した場合は、そのテーブルをワークロードとして使用する前に、データベース エンジン チューニング アドバイザーがチューニングを実行するサーバーに移す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-231">If you create the trace table on a different server, move it to the server that Database Engine Tuning Advisor is tuning before using it as your workload.</span></span>  
  
6.  <span data-ttu-id="d721e-232">手順 5. で選択したワークロードを実行するデータベースとテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-232">Select the databases and tables against which you wish to run the workload that you selected in step 5.</span></span> <span data-ttu-id="d721e-233">テーブルを選択するには、 **[選択したテーブル]** 列の矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-233">To select the tables, click the **Selected Tables** arrow.</span></span>  
  
7.  <span data-ttu-id="d721e-234">チューニング ログを保存するには、 **[チューニング ログを保存する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-234">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="d721e-235">チューニング ログのコピーを保存しない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-235">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="d721e-236">セッションを開いて **[進行状況]** タブを選択すると、分析後にチューニング ログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-236">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
8.  <span data-ttu-id="d721e-237">**[チューニング オプション]** タブをクリックし、必要なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-237">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
9. <span data-ttu-id="d721e-238">ツール バーの **[分析の開始]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-238">Click the **Start Analysis** button in the toolbar.</span></span>  
  
     <span data-ttu-id="d721e-239">チューニング セッションの開始後にセッションを停止する場合、 **[アクション]** メニューにある次のオプションから 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-239">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="d721e-240">**[分析の停止 (推奨設定を使用)]** を選択すると、チューニング セッションが停止され、この時点までに実行された分析に基づいて、データベース エンジン チューニング アドバイザーで推奨設定を生成するかどうかを決定するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-240">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="d721e-241">**[分析の停止]** を選択すると、推奨設定を生成せずにチューニング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="d721e-241">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d721e-242">データベース エンジン チューニング アドバイザーの一時停止はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d721e-242">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="d721e-243">ツールバーの **[分析の停止]** または **[分析の停止 (推奨設定を使用)]** のいずれかをクリックしてからツールバーの **[分析の開始]** をクリックすると、データベース エンジン チューニング アドバイザーは新しいチューニング セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="d721e-243">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
###  <a name="use-the-dta-utility"></a><a name="dta"></a> <span data-ttu-id="d721e-244">dta ユーティリティを使用する</span><span class="sxs-lookup"><span data-stu-id="d721e-244">Use the dta Utility</span></span>  
 <span data-ttu-id="d721e-245">[dta ユーティリティ](../../tools/dta/dta-utility.md) には、データベースのチューニングに使用できるコマンド プロンプト実行可能ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d721e-245">The [dta utility](../../tools/dta/dta-utility.md) provides a command prompt executable file that you can use to tune databases.</span></span> <span data-ttu-id="d721e-246">このファイルにより、バッチ ファイルやスクリプトでデータベース エンジン チューニング アドバイザー機能を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d721e-246">It enables you to use Database Engine Tuning Advisor functionality in batch files and scripts.</span></span> <span data-ttu-id="d721e-247">**dta** ユーティリティでは、ワークロードとして、プラン キャッシュ エントリ、トレース ファイル、トレース テーブル、および [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-247">The **dta** utility takes plan cache entries, trace files, trace tables, and [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts as workloads.</span></span> <span data-ttu-id="d721e-248">また、データベース エンジン チューニング アドバイザー XML スキーマに準拠する XML 入力も使用されます。このスキーマは、この [Microsoft Web サイト](https://go.microsoft.com/fwlink/?linkid=43100)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-248">It also takes XML input that conforms to the Database Engine Tuning Advisor XML schema, which is available at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="d721e-249">**dta** ユーティリティを使用してワークロードのチューニングを開始する前に、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-249">Consider the following before you begin tuning a workload with the **dta** utility:</span></span>  
  
-   <span data-ttu-id="d721e-250">ワークロードとしてトレース テーブルを使用する場合、そのテーブルは、データベース エンジン チューニング アドバイザーがチューニングを実行するサーバーと同じサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-250">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="d721e-251">他のサーバーにトレース テーブルを作成した場合は、トレース テーブルをデータベース エンジン チューニング アドバイザーでチューニングするサーバーに移動してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-251">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="d721e-252">データベース エンジン チューニング アドバイザーのワークロードとしてトレース テーブルを使用する前に、トレースが停止していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-252">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="d721e-253">データベース エンジン チューニング アドバイザーでは、トレース イベントをワークロードとして書き込み中のトレース テーブルには使用できません。</span><span class="sxs-lookup"><span data-stu-id="d721e-253">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
-   <span data-ttu-id="d721e-254">チューニング セッションの実行が予想よりも長く続いている場合、Ctrl キーを押しながら C キーを押してチューニング セッションを停止し、その時点までに **dta** で完了した分析に基づいて推奨設定を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-254">If a tuning session continues running longer than you had anticipated it would run, you can press CTRL+C to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="d721e-255">推奨設定を生成するかどうかの確認が要求されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-255">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="d721e-256">Ctrl</localizedText> + <localizedText>C</localizedText> キーをもう一度押すと、推奨設定を生成せずにチューニング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="d721e-256">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
 <span data-ttu-id="d721e-257">**dta** ユーティリティの構文と例の詳細については、「 [dta Utility](../../tools/dta/dta-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-257">For more information about **dta** utility syntax and examples, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##### <a name="to-tune-a-database-by-using-the-plan-cache"></a><span data-ttu-id="d721e-258">プラン キャッシュを使用してデータベースをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-258">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="d721e-259">**-ip** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-259">Specify the **-ip** option.</span></span> <span data-ttu-id="d721e-260">選択したデータベースの上位 1,000 個のプラン キャッシュ イベントが分析されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-260">The top 1,000 plan cache events for the selected databases are analyzed.</span></span>  
  
     <span data-ttu-id="d721e-261">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-261">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -s SessionName  
    ```  
  
2.  <span data-ttu-id="d721e-262">分析に使用するイベントの数を変更するには、 **-n** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-262">To modify the number of events to use for analysis, specify the **-n** option.</span></span> <span data-ttu-id="d721e-263">次の例では、キャッシュ エントリの数を 2,000 に増やします。</span><span class="sxs-lookup"><span data-stu-id="d721e-263">The following example increases the number of cache entries to 2,000.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -n 2000-s SessionName1  
    ```  
  
3.  <span data-ttu-id="d721e-264">インスタンスのすべてのデータベースのイベントを分析するには、 **-ipf** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-264">To analyze events for all databases in the instance, specify the **-ipf** option.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -ipf -n 2000 -s SessionName2  
    ```  
  
##### <a name="to-tune-a-database-by-using-a-workload-and-dta-utility-default-settings"></a><span data-ttu-id="d721e-265">ワークロードと dta ユーティリティの既定の設定を使用してデータベースをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-265">To tune a database by using a workload and dta utility default settings</span></span>  
  
1.  <span data-ttu-id="d721e-266">解析時に、データベース エンジン チューニング アドバイザーによって追加、削除、または保有を検討するデータベースの機能 (インデックス、インデックス付きビュー、パーティション分割) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-266">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="d721e-267">ワークロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-267">Create a workload.</span></span> <span data-ttu-id="d721e-268">詳細については、このトピックの「 [ワークロードを作成する](#Create) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-268">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="d721e-269">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-269">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -if WorkloadFile -s SessionName  
    ```  
  
     <span data-ttu-id="d721e-270">このコマンドの `-E` はチューニング セッションで (ログイン ID とパスワードではなく) 信頼関係接続を使用することを指定し、 `-D` はチューニングするデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-270">where `-E` specifies that your tuning session uses a trusted connection (instead of a login ID and password), `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="d721e-271">既定では、ユーティリティは、ローカル コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d721e-271">By default, the utility connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="d721e-272">(リモート データベースを指定したり、名前付きインスタンスを指定したりするには、次の手順で示すように `-S` オプションを使用します)。 `-if` オプションは、ワークロード ファイル ( [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトまたはトレース ファイルが使用可能) の名前とファイル パスを指定し、 `-s` はチューニング セッションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-272">(Use the `-S` option to specify a remote database as shown in the following procedure, or to specify a named instance.) The `-if` option specifies the name and path to a workload file (which can be a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or a trace file), and `-s` specifies a name for your tuning session.</span></span>  
  
     <span data-ttu-id="d721e-273">ここで示した 4 つのオプション (データベース名、ワークロード、接続の種類、およびセッション名) は必ず指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-273">The four options shown here (database name, workload, connection type, and session name) are mandatory.</span></span>  
  
##### <a name="to-tune-a-remote-database-or-a-named-instance-for-a-specific-duration"></a><span data-ttu-id="d721e-274">リモート データベースまたは名前付きインスタンスを一定時間チューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-274">To tune a remote database or a named instance for a specific duration</span></span>  
  
1.  <span data-ttu-id="d721e-275">解析時に、データベース エンジン チューニング アドバイザーによって追加、削除、または保有を検討するデータベースの機能 (インデックス、インデックス付きビュー、パーティション分割) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-275">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="d721e-276">ワークロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-276">Create a workload.</span></span> <span data-ttu-id="d721e-277">詳細については、このトピックの「 [ワークロードを作成する](#Create) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-277">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="d721e-278">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-278">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -S ServerName\Instance -D DatabaseName -it WorkloadTableName   
    -U LoginID -P Password -s SessionName -A TuningTimeInMinutes  
    ```  
  
     <span data-ttu-id="d721e-279">このコマンドの `-S` はリモート サーバー名とインスタンス (またはローカル サーバー上の名前付きインスタンス) を指定し、 `-D` はチューニングするデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-279">where `-S` specifies a remote server name and instance (or a named instance on the local server) and `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="d721e-280">`-it` オプションはワークロード テーブル名を指定し、 `-U` および `-P` はリモート データベースに対するログイン ID とパスワードを指定します。また、 `-s` はチューニング セッション名を指定し、 `-A` はチューニング セッションの継続時間を分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-280">The `-it` option specifies the name of the workload table, `-U` and `-P` specify the login ID and password to the remote database, `-s` specifies the tuning session name, and `-A` specifies the tuning session duration in minutes.</span></span> <span data-ttu-id="d721e-281">既定では、 **dta** ユーティリティのチューニング時間は 8 時間に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d721e-281">By default, the **dta** utility uses an 8-hour tuning duration.</span></span> <span data-ttu-id="d721e-282">データベース エンジン チューニング アドバイザーによるワークロードのチューニング時間を無制限にする場合は、 **オプションを使用して** 0 `-A` (ゼロ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-282">If you would like Database Engine Tuning Advisor to tune a workload for an unlimited amount of time, specify **0** (zero) with the `-A` option.</span></span>  
  
##### <a name="to-tune-a-database-using-an-xml-input-file"></a><span data-ttu-id="d721e-283">XML 入力ファイルを使用してデータベースをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-283">To tune a database using an XML input file</span></span>  
  
1.  <span data-ttu-id="d721e-284">解析時に、データベース エンジン チューニング アドバイザーによって追加、削除、または保有を検討するデータベースの機能 (インデックス、インデックス付きビュー、パーティション分割) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-284">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="d721e-285">ワークロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-285">Create a workload.</span></span> <span data-ttu-id="d721e-286">詳細については、このトピックの「 [ワークロードを作成する](#Create) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-286">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="d721e-287">XML 入力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-287">Create an XML input file.</span></span> <span data-ttu-id="d721e-288">詳細については、このトピックの「 [XML 入力ファイルを作成する](#XMLInput) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-288">For more information, see [Create XML Input Files](#XMLInput) later in this topic.</span></span>  
  
4.  <span data-ttu-id="d721e-289">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-289">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -S ServerName\Instance -s SessionName -ix PathToXMLInputFile  
    ```  
  
     <span data-ttu-id="d721e-290">このコマンドの `-E` は信頼関係接続を指定し、 `-S` はリモート サーバーとインスタンス、またはローカル サーバー上の名前付きインスタンスを指定します。また、 `-s` はチューニング セッション名を指定し、 `-ix` はチューニング セッションで使用する XML 入力ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-290">where `-E` specifies a trusted connection, `-S` specifies a remote server and instance, or a named instance on the local server, `-s` specifies a tuning session name, and `-ix` specifies the XML input file to use for the tuning session.</span></span>  
  
5.  <span data-ttu-id="d721e-291">ユーティリティによるワークロードのチューニングが完了した後、データベース エンジン チューニング アドバイザーの GUI を使用して、チューニング セッションの結果を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-291">After the utility finishes tuning the workload, you can view the results of tuning sessions with the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="d721e-292">また、代替手段として、 **-ox** オプションを使用してチューニングの推奨設定を XML ファイルに書き込むように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-292">As an alternative, you can also specify that the tuning recommendations be written to an XML file with the **-ox** option.</span></span> <span data-ttu-id="d721e-293">詳細については、「 [dta Utility](../../tools/dta/dta-utility.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="d721e-293">For more information, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##  <a name="create-an-xml-input-file"></a><a name="XMLInput"></a> <span data-ttu-id="d721e-294">XML 入力ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="d721e-294">Create an XML Input File</span></span>  
 <span data-ttu-id="d721e-295">経験豊かな XML 開発者の場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで使用できる XML 形式のファイルを作成して、ワークロードをチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="d721e-295">If you are an experienced XML developer, you can create XML-formatted files that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use to tune workloads.</span></span> <span data-ttu-id="d721e-296">このような XML ファイルを作成するには、使い慣れた XML ツールを使用してサンプル ファイルを編集するか、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマからインスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-296">To create these XML files, use your favorite XML tools to edit a sample file or to generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
 <span data-ttu-id="d721e-297">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールの次の場所から入手できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-297">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is available in your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in the following location:</span></span>  
  
 <span data-ttu-id="d721e-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span><span class="sxs-lookup"><span data-stu-id="d721e-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span></span>  
  
 <span data-ttu-id="d721e-299">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマは、この [Microsoft Web サイト](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)からもオンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-299">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is also available online at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="d721e-300">この URL から、多くの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML スキーマを入手できるページに移動できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-300">This URL takes you to a page where many [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML schemas are available.</span></span> <span data-ttu-id="d721e-301">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの行までページを下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="d721e-301">Scroll down the page until you reach the row for [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span>  
  
#### <a name="to-create-an-xml-input-file-to-tune-workloads"></a><span data-ttu-id="d721e-302">XML 入力ファイルを作成してワークロードをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="d721e-302">To create an XML input file to tune workloads</span></span>  
  
1.  <span data-ttu-id="d721e-303">ワークロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-303">Create a workload.</span></span> <span data-ttu-id="d721e-304">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の Tuning テンプレートを使用してトレース ファイルまたはトレース テーブルを使用できます。または、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の代表的なワークロードを再現する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-304">You can use a trace file or table by using the tuning template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], or create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script that reproduces a representative workload for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d721e-305">詳細については、このトピックの「 [ワークロードを作成する](#Create) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-305">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="d721e-306">次のいずれかの方法で、XML 入力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-306">Create an XML input file by one of the following methods:</span></span>  
  
    -   <span data-ttu-id="d721e-307">「[XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md)」の 1 つをコピーし、使い慣れた XML エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d721e-307">Copy and paste one of the [XML Input File Samples &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md) into your favorite XML editor.</span></span> <span data-ttu-id="d721e-308">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールに適切な引数を指定するために値を変更し、XML ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d721e-308">Change the values to specify the appropriate arguments for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, and save the XML file.</span></span>  
  
    -   <span data-ttu-id="d721e-309">使い慣れた XML ツールを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマからインスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-309">Using your favorite XML tool, generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
3.  <span data-ttu-id="d721e-310">XML 入力ファイルを作成した後、その XML 入力ファイルを **dta** コマンド ライン ユーティリティへの入力として使用して、ワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="d721e-310">After creating the XML input file, use it as input to the **dta** command-line utility to tune the workload.</span></span> <span data-ttu-id="d721e-311">このツールでの XML 入力ファイルの使用については、このトピックの「 [dta ユーティリティを使用する](#dta) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-311">For information about using XML input files with this utility, see the section [Use the dta Utililty](#dta) earlier in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d721e-312">XML 入力ファイル内で直接指定されるワークロードであるインライン ワークロードを使用する場合、サンプル「[インライン ワークロードを使用した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="d721e-312">If you want to use an inline workload, which is a workload that is specified directly in the XML input file, use the sample [XML Input File Sample with Inline Workload &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
##  <a name="user-interface-descriptions"></a><a name="UI"></a> <span data-ttu-id="d721e-313">ユーザー インターフェイスの説明</span><span class="sxs-lookup"><span data-stu-id="d721e-313">User Interface Descriptions</span></span>  
  
### <a name="tools-menuoptions-page"></a><span data-ttu-id="d721e-314">[ツール] メニュー/[オプション] ページ</span><span class="sxs-lookup"><span data-stu-id="d721e-314">Tools Menu/Options Page</span></span>  
 <span data-ttu-id="d721e-315">このダイアログ ボックスを使用すると、データベース エンジン チューニング アドバイザーの全般的な構成パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-315">Use this dialog box to specify general configuration parameters for the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="d721e-316">**[スタートアップ時]**</span><span class="sxs-lookup"><span data-stu-id="d721e-316">**On startup**</span></span>  
 <span data-ttu-id="d721e-317">データベース エンジン チューニング アドバイザーの開始時に実行する操作を指定します。指定できる操作は、データベース接続を行わずに開く、 **[新しい接続]** ダイアログ ボックスを表示する、新しいセッションを表示する、前回読み込んだセッションを読み込む、のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="d721e-317">Specify what Database Engine Tuning Advisor should do when it is started: open without a database connection, show a **New Connection** dialog box, show a new session, or load the last loaded session.</span></span>  
  
 <span data-ttu-id="d721e-318">**[フォント変更]**</span><span class="sxs-lookup"><span data-stu-id="d721e-318">**Change font**</span></span>  
 <span data-ttu-id="d721e-319">データベース エンジン チューニング アドバイザーの表で使用される表示フォントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-319">Specify the display font used by Database Engine Tuning Advisor tables.</span></span>  
  
 <span data-ttu-id="d721e-320">**[最近使用した項目の一覧に表示する項目数]**</span><span class="sxs-lookup"><span data-stu-id="d721e-320">**Number of items in most recently used lists**</span></span>  
 <span data-ttu-id="d721e-321">**[ファイル]** メニューの **[最新のセッション]** または **[最近使ったファイル]** で表示されるセッションやファイルの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-321">Specify the number of sessions or files to display under **Recent Sessions** or **Recent Files** in the **File** menu.</span></span>  
  
 <span data-ttu-id="d721e-322">**[最後のチューニング オプションを保存する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-322">**Remember my last tuning options**</span></span>  
 <span data-ttu-id="d721e-323">セッションとセッションの間でチューニング オプションを保持します。</span><span class="sxs-lookup"><span data-stu-id="d721e-323">Retain tuning options between sessions.</span></span> <span data-ttu-id="d721e-324">既定で選択されています。</span><span class="sxs-lookup"><span data-stu-id="d721e-324">Selected by default.</span></span> <span data-ttu-id="d721e-325">このチェック ボックスをオフにすると、データベース チューニング アドバイザーは常に既定のオプションで起動します。</span><span class="sxs-lookup"><span data-stu-id="d721e-325">Clear this check box to always start with the Database Engine Tuning Advisor defaults.</span></span>  
  
 <span data-ttu-id="d721e-326">**[完全にセッションを削除する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-326">**Ask before permanently deleting sessions**</span></span>  
 <span data-ttu-id="d721e-327">セッションを削除する前に、確認のダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d721e-327">Display a confirmation dialog box before deleting sessions.</span></span>  
  
 <span data-ttu-id="d721e-328">**[セッションの分析を停止する前に確認する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-328">**Ask before stopping session analysis**</span></span>  
 <span data-ttu-id="d721e-329">ワークロードの分析を停止する前に、確認ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d721e-329">Display a confirmation dialog box before stopping analysis of a workload.</span></span>  
  
#### <a name="general-tab-options"></a><span data-ttu-id="d721e-330">[全般] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="d721e-330">General Tab Options</span></span>  
 <span data-ttu-id="d721e-331">セッションのチューニングを始める前に、 **[全般]** タブのフィールドを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-331">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="d721e-332">**[チューニング オプション]** タブの設定は、チューニング セッションを開始する前に変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d721e-332">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="d721e-333">**[セッション名]**</span><span class="sxs-lookup"><span data-stu-id="d721e-333">**Session name**</span></span>  
 <span data-ttu-id="d721e-334">セッションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-334">Specify a name for the session.</span></span> <span data-ttu-id="d721e-335">これによって、チューニングするセッションに名前が関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d721e-335">The session name associates a name with a tuning session.</span></span> <span data-ttu-id="d721e-336">後でこの名前を参照することで、チューニングするセッションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-336">You can refer to this name to review the tuning session later.</span></span>  
  
 <span data-ttu-id="d721e-337">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="d721e-337">**File**</span></span>  
 <span data-ttu-id="d721e-338">ワークロードとなる .sql スクリプトまたはトレース ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-338">Specify a .sql script or trace file for a workload.</span></span> <span data-ttu-id="d721e-339">対応するテキスト ボックスにパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-339">Specify the path and filename in the associated text box.</span></span> <span data-ttu-id="d721e-340">データベース エンジン チューニング アドバイザーでは、ワークロード トレース ファイルはロールオーバー ファイルと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d721e-340">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="d721e-341">ロールオーバー ファイルの詳細については、「 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-341">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
 <span data-ttu-id="d721e-342">**Table**</span><span class="sxs-lookup"><span data-stu-id="d721e-342">**Table**</span></span>  
 <span data-ttu-id="d721e-343">ワークロードのトレース テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-343">Specify a trace table for a workload.</span></span> <span data-ttu-id="d721e-344">次のように、対応するテキスト ボックスにトレース テーブルの完全修飾名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-344">Specify the fully qualified name of the trace table in the associated text box as follows:</span></span>  
  
```  
database_name.owner_name.table_name  
```  
  
-   <span data-ttu-id="d721e-345">トレース テーブルをワークロードとして使用する前に、トレースが停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d721e-345">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
-   <span data-ttu-id="d721e-346">トレース テーブルは、データベース エンジン チューニング アドバイザーでチューニングするサーバーと同じサーバーに置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="d721e-346">The trace table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="d721e-347">他のサーバーにトレース テーブルを作成した場合は、トレース テーブルをデータベース エンジン チューニング アドバイザーでチューニングするサーバーに移動してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-347">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
 <span data-ttu-id="d721e-348">**[プラン キャッシュ]**</span><span class="sxs-lookup"><span data-stu-id="d721e-348">**Plan Cache**</span></span>  
 <span data-ttu-id="d721e-349">プラン キャッシュをワークロードとして指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-349">Specify the plan cache as a workload.</span></span> <span data-ttu-id="d721e-350">このようにすることでワークロードを手動で作成する手間が省けます。</span><span class="sxs-lookup"><span data-stu-id="d721e-350">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="d721e-351">データベース エンジン チューニング アドバイザーによって、分析に使用される上位 1,000 件のイベントが選択されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-351">Database Engine Tuning Advisor selects the top 1,000 events to use for analysis.</span></span>  
  
 <span data-ttu-id="d721e-352">**Xml**</span><span class="sxs-lookup"><span data-stu-id="d721e-352">**Xml**</span></span>  
 <span data-ttu-id="d721e-353">これは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からワークロードをインポートしない限り表示されません。</span><span class="sxs-lookup"><span data-stu-id="d721e-353">This does not appear unless you import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d721e-354">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からワークロード クエリをインポートするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d721e-354">To import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
1.  <span data-ttu-id="d721e-355">クエリ エディターにクエリを入力し、選択して強調表示します。</span><span class="sxs-lookup"><span data-stu-id="d721e-355">Type a query into Query Editor and highlight it.</span></span>  
  
2.  <span data-ttu-id="d721e-356">強調表示したクエリを右クリックして、 **[データベース エンジン チューニング アドバイザーでのクエリの分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-356">Right-click the highlighted query and click **Analyze Query in Database Engine Tuning Advisor**.</span></span>  
  
 <span data-ttu-id="d721e-357">**[ワークロード ファイルを参照します。]/[ワークロード テーブルを参照します。]**</span><span class="sxs-lookup"><span data-stu-id="d721e-357">**Browse for a workload [file or table]**</span></span>  
 <span data-ttu-id="d721e-358">ワークロードのソースとして **[ファイル]** または **[テーブル]** を選択している場合に、この参照ボタンを使用して対象を選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-358">When **File** or **Table** is selected as the workload source, use this browse button to select the target.</span></span>  
  
 <span data-ttu-id="d721e-359">**[XML ワークロードをプレビューします。]**</span><span class="sxs-lookup"><span data-stu-id="d721e-359">**Preview the XML workload**</span></span>  
 <span data-ttu-id="d721e-360">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からインポートされた XML 形式のワークロードを表示します。</span><span class="sxs-lookup"><span data-stu-id="d721e-360">View an XML-formatted workload that has been imported from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d721e-361">**[ワークロード分析用のデータベース]**</span><span class="sxs-lookup"><span data-stu-id="d721e-361">**Database for workload analysis**</span></span>  
 <span data-ttu-id="d721e-362">データベース エンジン チューニング アドバイザーがワークロードのチューニング時に最初に接続するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-362">Specify the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="d721e-363">チューニングの開始後に、データベース チューニング アドバイザーは、ワークロードに含まれる `USE DATABASE` ステートメントで指定されたデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="d721e-363">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
 <span data-ttu-id="d721e-364">**[チューニングするデータベースとテーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="d721e-364">**Select databases and tables to tune**</span></span>  
 <span data-ttu-id="d721e-365">チューニングするデータベースとテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-365">Specify the databases and tables to be tuned.</span></span> <span data-ttu-id="d721e-366">すべてのデータベースを指定するには、 **[名前]** 列ヘッダーのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-366">To specify all of the databases, select the check box in the **Name** column heading.</span></span> <span data-ttu-id="d721e-367">特定のデータベースを指定するには、そのデータベース名の横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-367">To specify certain databases, select the check box next to the database name.</span></span> <span data-ttu-id="d721e-368">既定では、選択したデータベースのすべてのテーブルが自動的にチューニング対象のセッションに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-368">By default, all of the tables for selected databases are automatically included in the tuning session.</span></span> <span data-ttu-id="d721e-369">テーブルを除外するには、 **[選択したテーブル]** 列の矢印をクリックした後、チューニングの対象にしないテーブルの横にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d721e-369">To exclude tables, click the arrow in the **Selected Tables** column, and then clear the check boxes next to the tables that you do not want to tune.</span></span>  
  
 <span data-ttu-id="d721e-370">**[選択したテーブル]** の下向き矢印</span><span class="sxs-lookup"><span data-stu-id="d721e-370">**Selected Tables** down arrow</span></span>  
 <span data-ttu-id="d721e-371">テーブルの一覧を展開して、チューニングするテーブルを個別に選択できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-371">Expand the tables list to allow selecting individual tables for tuning.</span></span>  
  
 <span data-ttu-id="d721e-372">**[チューニング ログを保存する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-372">**Save tuning log**</span></span>  
 <span data-ttu-id="d721e-373">セッション中のログを作成し、エラーを記録します。</span><span class="sxs-lookup"><span data-stu-id="d721e-373">Create a log and record errors during the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d721e-374">データベース エンジン チューニング アドバイザーの **[全般]** タブに表示されるテーブルの行情報は、自動的に更新されません。この情報はデータベースのメタデータに依存しています。</span><span class="sxs-lookup"><span data-stu-id="d721e-374">Database Engine Tuning Advisor does not automatically update the rows information for the tables displayed on the **General** tab. Instead it relies upon the metadata in the database.</span></span> <span data-ttu-id="d721e-375">行の情報が古くなっていると感じた場合は、対応するオブジェクトに対して DBCC UPDATEUSAGE コマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="d721e-375">If you suspect that the rows information is outdated, run the DBCC UPDATEUSAGE command for the relevant objects.</span></span>  
  
##### <a name="tuning-tab-options"></a><span data-ttu-id="d721e-376">[チューニング オプション] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="d721e-376">Tuning Tab Options</span></span>  
 <span data-ttu-id="d721e-377">**[チューニング オプション]** タブを使用すると、全般的なチューニング オプションの既定の設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-377">Use the **Tuning Options** tab to modify default settings of general tuning options.</span></span> <span data-ttu-id="d721e-378">**[チューニング オプション]** タブの設定は、チューニング セッションを開始する前に変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d721e-378">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="d721e-379">**[チューニング時間を制限する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-379">**Limit tuning time**</span></span>  
 <span data-ttu-id="d721e-380">現在のチューニング セッションの時間を制限します。</span><span class="sxs-lookup"><span data-stu-id="d721e-380">Limits the time for the current tuning session.</span></span> <span data-ttu-id="d721e-381">チューニングの時間を増やすことにより、推奨設定の品質が向上します。</span><span class="sxs-lookup"><span data-stu-id="d721e-381">Providing more time for turning improves the quality of the recommendations.</span></span> <span data-ttu-id="d721e-382">推奨設定で最良の結果を得るためには、このオプションをオンにしないでください。</span><span class="sxs-lookup"><span data-stu-id="d721e-382">To ensure the best recommendations, do not select this option.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="d721e-383">チューニング アドバイザーは、分析中にシステム リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="d721e-383">Tuning Advisor consumes system resources during analysis.</span></span> <span data-ttu-id="d721e-384">**[チューニング時間を制限する]** を使用すると、チューニング対象サーバーでワークロードの増大が予想される期間の前にチューニングを停止できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-384">Use **Limit tuning time** to stop tuning before periods of anticipated heavy workload on the server being tuned.</span></span>  
  
 <span data-ttu-id="d721e-385">**[詳細設定オプション]**</span><span class="sxs-lookup"><span data-stu-id="d721e-385">**Advanced Options**</span></span>  
 <span data-ttu-id="d721e-386">**[チューニング オプションの詳細設定]** ダイアログ ボックスを使用すると、最大領域、最大キー列数、およびオンライン推奨インデックスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-386">Use the **Advanced Tuning Options** dialog box to configure the maximum space, maximum key columns, and online index recommendations.</span></span>  
  
 <span data-ttu-id="d721e-387">**[推奨インデックス用の最大領域を定義する (MB)]**</span><span class="sxs-lookup"><span data-stu-id="d721e-387">**Define max. space for recommendations (MB)**</span></span>  
 <span data-ttu-id="d721e-388">物理デザイン構造が使用する最大領域として、データベース エンジン チューニング アドバイザーによる推奨値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d721e-388">Type the maximum amount of space to be used by physical design structures recommended by Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="d721e-389">値を入力しない場合は、データベース エンジン チューニング アドバイザーは、次の領域制限より小さい値を想定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-389">If no value is entered here, Database Engine Tuning Advisor assumes the smaller of the following space limits:</span></span>  
  
-   <span data-ttu-id="d721e-390">現在の生データ サイズの 3 倍。このサイズには、データベース内のテーブルのヒープとクラスター化インデックスの合計サイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-390">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="d721e-391">アタッチ先のすべてのディスク ドライブの空き容量に生データのサイズを加算した値</span><span class="sxs-lookup"><span data-stu-id="d721e-391">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="d721e-392">**[すべてのデータベースのプラン キャッシュ イベントを含める]**</span><span class="sxs-lookup"><span data-stu-id="d721e-392">**Include plan cache events from all databases**</span></span>  
 <span data-ttu-id="d721e-393">すべてのデータベースのプラン キャッシュ イベントが分析されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-393">Specify that plan cache events from all databases are analyzed.</span></span>  
  
 <span data-ttu-id="d721e-394">**[インデックスごとの最大列数]**</span><span class="sxs-lookup"><span data-stu-id="d721e-394">**Max. columns per index**</span></span>  
 <span data-ttu-id="d721e-395">任意のインデックスに含める最大列数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-395">Specify the maximum number of columns to include in any index.</span></span> <span data-ttu-id="d721e-396">既定値は 1023 です。</span><span class="sxs-lookup"><span data-stu-id="d721e-396">The default is 1023.</span></span>  
  
 <span data-ttu-id="d721e-397">**[すべての推奨インデックスをオフラインにする]**</span><span class="sxs-lookup"><span data-stu-id="d721e-397">**All recommendations are offline**</span></span>  
 <span data-ttu-id="d721e-398">可能な限り最良の推奨が生成されますが、物理デザイン構造をオンラインで作成することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="d721e-398">Generate the best recommendations possible, but do not recommend that any physical design structures be created online.</span></span>  
  
 <span data-ttu-id="d721e-399">**[可能な限りオンラインの推奨インデックスを生成する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-399">**Generate online recommendations where possible**</span></span>  
 <span data-ttu-id="d721e-400">推奨を実装する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成するときに、より速いオフライン メソッドが利用可能な場合でも、サーバー オンラインで実装できるメソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-400">When creating [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to implement the recommendations, choose methods that can be implemented with the server online, even if a faster offline method is available.</span></span>  
  
 <span data-ttu-id="d721e-401">**[オンラインの推奨インデックスのみ生成する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-401">**Generate only online recommendations**</span></span>  
 <span data-ttu-id="d721e-402">サーバーでオンライン状態を維持できる推奨インデックスのみ生成します。</span><span class="sxs-lookup"><span data-stu-id="d721e-402">Only make recommendations that allow the server to stay online.</span></span>  
  
 <span data-ttu-id="d721e-403">**[停止時刻]**</span><span class="sxs-lookup"><span data-stu-id="d721e-403">**Stop at**</span></span>  
 <span data-ttu-id="d721e-404">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーを停止する日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="d721e-404">Provide the date and time when [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor should stop.</span></span>  
  
 <span data-ttu-id="d721e-405">**[インデックスおよびインデックス付きビュー]**</span><span class="sxs-lookup"><span data-stu-id="d721e-405">**Indexes and indexed views**</span></span>  
 <span data-ttu-id="d721e-406">このオプションをオンにすると、クラスター化インデックス、非クラスター化インデックス、およびインデックス付きビューを追加するための推奨設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-406">Check this box to include recommendations for adding clustered indexes, nonclustered indexes, and indexed views.</span></span>  
  
 <span data-ttu-id="d721e-407">**インデックス付きビュー**</span><span class="sxs-lookup"><span data-stu-id="d721e-407">**Indexed views**</span></span>  
 <span data-ttu-id="d721e-408">インデックス付きビューを追加するための推奨設定のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-408">Only include recommendations for adding indexed views.</span></span> <span data-ttu-id="d721e-409">クラスター化インデックスおよび非クラスター化インデックスは、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d721e-409">Clustered and nonclustered indexes will not be recommended.</span></span>  
  
 <span data-ttu-id="d721e-410">**フィルター選択されたインデックスを含める**</span><span class="sxs-lookup"><span data-stu-id="d721e-410">**Include filtered indexes**</span></span>  
 <span data-ttu-id="d721e-411">フィルター選択されたインデックスを追加するための推奨設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-411">Include recommendations for adding filtered indexes.</span></span> <span data-ttu-id="d721e-412">このオプションは、 **[インデックスおよびインデックス付きビュー]** 、 **[インデックス]** 、または **[非クラスター化インデックス]** のいずれかの物理デザイン構造を選択した場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="d721e-412">This option is available if you select one of these physical design structures: **Indexes and indexed views**, **Indexes**, or **Nonclustered indexes**.</span></span>  
  
 <span data-ttu-id="d721e-413">**インデックス**</span><span class="sxs-lookup"><span data-stu-id="d721e-413">**Indexes**</span></span>  
 <span data-ttu-id="d721e-414">クラスター化インデックスおよび非クラスター化インデックスを追加するための推奨設定のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-414">Only include recommendations for adding clustered and nonclustered indexes.</span></span> <span data-ttu-id="d721e-415">インデックス付きビューは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d721e-415">Indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="d721e-416">**[非クラスター化インデックス]**</span><span class="sxs-lookup"><span data-stu-id="d721e-416">**Nonclustered indexes**</span></span>  
 <span data-ttu-id="d721e-417">非クラスター化インデックスだけの推奨設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d721e-417">Include recommendations for only nonclustered indexes.</span></span> <span data-ttu-id="d721e-418">クラスター化インデックスおよびインデックス付きビューは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d721e-418">Clustered indexes and indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="d721e-419">**[既存の PDS のみ使用を評価する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-419">**Evaluate utilization of existing PDS only**</span></span>  
 <span data-ttu-id="d721e-420">現在のインデックスの効果を評価しますが、追加のインデックスまたはインデックス付きビューは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d721e-420">Evaluate the effectiveness of the current indexes but do not recommend additional indexes or indexed views.</span></span>  
  
 <span data-ttu-id="d721e-421">**パーティション分割しない。**</span><span class="sxs-lookup"><span data-stu-id="d721e-421">**No partitioning**</span></span>  
 <span data-ttu-id="d721e-422">パーティション分割を推奨しません。</span><span class="sxs-lookup"><span data-stu-id="d721e-422">Do not recommend partitioning.</span></span>  
  
 <span data-ttu-id="d721e-423">**[完全パーティション分割]**</span><span class="sxs-lookup"><span data-stu-id="d721e-423">**Full partitioning**</span></span>  
 <span data-ttu-id="d721e-424">パーティション分割の推奨設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="d721e-424">Include recommendations for partitioning.</span></span>  
  
 <span data-ttu-id="d721e-425">**[固定パーティション分割]**</span><span class="sxs-lookup"><span data-stu-id="d721e-425">**Aligned partitioning**</span></span>  
 <span data-ttu-id="d721e-426">パーティション分割を簡単に維持できるように、新しく推奨されたパーティションが固定されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-426">New recommended partitions will be aligned to make partitions easy to maintain.</span></span>  
  
 <span data-ttu-id="d721e-427">**[既存の PDS を保持しない]**</span><span class="sxs-lookup"><span data-stu-id="d721e-427">**Do not keep any existing PDS**</span></span>  
 <span data-ttu-id="d721e-428">不要な既存のインデックス、ビュー、およびパーティション分割の削除を推奨します。</span><span class="sxs-lookup"><span data-stu-id="d721e-428">Recommend dropping unnecessary existing indexes, views, and partitioning.</span></span> <span data-ttu-id="d721e-429">既存の物理デザイン構造 (PDS) がワークロードに対して有用である場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーは削除を推奨しません。</span><span class="sxs-lookup"><span data-stu-id="d721e-429">If an existing physical design structure (PDS) is useful to the workload, [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor does not recommend dropping it.</span></span>  
  
 <span data-ttu-id="d721e-430">**[インデックスのみ保持する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-430">**Keep indexes only**</span></span>  
 <span data-ttu-id="d721e-431">既存のインデックスをすべて保持しますが、不要なインデックス付きビューおよびパーティション分割の削除を推奨します。</span><span class="sxs-lookup"><span data-stu-id="d721e-431">Keep all existing indexes but recommend dropping unnecessary indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="d721e-432">**[既存の PDS をすべて保持する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-432">**Keep all existing PDS**</span></span>  
 <span data-ttu-id="d721e-433">既存のインデックス、インデックス付きビュー、およびパーティション分割をすべて保持します。</span><span class="sxs-lookup"><span data-stu-id="d721e-433">Keep all existing indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="d721e-434">**[クラスター化インデックスのみ保持する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-434">**Keep clustered indexes only**</span></span>  
 <span data-ttu-id="d721e-435">既存のクラスター化インデックスをすべて保持しますが、不要なインデックス付きビュー、パーティション分割、および非クラスター化インデックスの削除を推奨します。</span><span class="sxs-lookup"><span data-stu-id="d721e-435">Keep all existing clustered indexes but recommend dropping unnecessary indexed views, partitions, and nonclustered indexes.</span></span>  
  
 <span data-ttu-id="d721e-436">**[固定パーティション分割を保持する]**</span><span class="sxs-lookup"><span data-stu-id="d721e-436">**Keep aligned partitioning**</span></span>  
 <span data-ttu-id="d721e-437">現在固定されているパーティション分割構造を保持しますが、不要なインデックス付きビュー、インデックス、および固定されていないパーティション分割の削除を推奨します。</span><span class="sxs-lookup"><span data-stu-id="d721e-437">Keep partitioning structures that are currently aligned, but recommend dropping unnecessary indexed views, indexes, and non-aligned partitioning.</span></span> <span data-ttu-id="d721e-438">推奨される追加のパーティション分割はすべて現在のパーティション分割構成で固定されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-438">Any additional partitioning recommended will align with the current partitioning scheme.</span></span>  
  
###### <a name="progress-tab-options"></a><span data-ttu-id="d721e-439">[進行状況] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="d721e-439">Progress Tab Options</span></span>  
 <span data-ttu-id="d721e-440">データベース エンジン チューニング アドバイザーでワークロードの分析を開始すると、[データベース エンジン チューニング アドバイザー] の **[進行状況]** タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-440">The **Progress** tab of Database Engine Tuning Advisor appears after Database Engine Tuning Advisor begins analyzing a workload.</span></span>  
  
 <span data-ttu-id="d721e-441">チューニング セッションの開始後にセッションを停止する場合、 **[アクション]** メニューにある次のオプションから 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="d721e-441">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
-   <span data-ttu-id="d721e-442">**[分析の停止 (推奨設定を使用)]** を選択すると、チューニング セッションが停止され、この時点までに実行された分析に基づいて、データベース エンジン チューニング アドバイザーで推奨設定を生成するかどうかを決定するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-442">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
-   <span data-ttu-id="d721e-443">**[分析の停止]** を選択すると、推奨設定を生成せずにチューニング セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="d721e-443">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
 <span data-ttu-id="d721e-444">**[チューニングの進行状況]**</span><span class="sxs-lookup"><span data-stu-id="d721e-444">**Tuning Progress**</span></span>  
 <span data-ttu-id="d721e-445">現在の進行状況の状態を示します。</span><span class="sxs-lookup"><span data-stu-id="d721e-445">Indicates the current status of the progress.</span></span> <span data-ttu-id="d721e-446">実行された処理の数、および受け取ったエラー メッセージ、成功メッセージ、警告メッセージの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-446">Contains the number of actions performed, and the number of error, success, and warning messages received.</span></span>  
  
 <span data-ttu-id="d721e-447">**詳細**</span><span class="sxs-lookup"><span data-stu-id="d721e-447">**Details**</span></span>  
 <span data-ttu-id="d721e-448">状態を示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-448">Contains an icon indicating status.</span></span>  
  
 <span data-ttu-id="d721e-449">**操作**</span><span class="sxs-lookup"><span data-stu-id="d721e-449">**Action**</span></span>  
 <span data-ttu-id="d721e-450">実行中のステップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-450">Displays the steps being performed.</span></span>  
  
 <span data-ttu-id="d721e-451">**状態**</span><span class="sxs-lookup"><span data-stu-id="d721e-451">**Status**</span></span>  
 <span data-ttu-id="d721e-452">アクション ステップの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-452">Displays the status of the action step.</span></span>  
  
 <span data-ttu-id="d721e-453">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="d721e-453">**Message**</span></span>  
 <span data-ttu-id="d721e-454">アクション ステップで返されたメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-454">Contains any messages returned by the action steps.</span></span>  
  
 <span data-ttu-id="d721e-455">**[チューニング ログ]**</span><span class="sxs-lookup"><span data-stu-id="d721e-455">**Tuning Log**</span></span>  
 <span data-ttu-id="d721e-456">このチューニング セッションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d721e-456">Contains information regarding this tuning session.</span></span> <span data-ttu-id="d721e-457">このログを印刷するには、ログを右クリックして **[印刷]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d721e-457">To print this log, right-click the log, and then click **Print**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d721e-458">参照</span><span class="sxs-lookup"><span data-stu-id="d721e-458">See Also</span></span>  
 <span data-ttu-id="d721e-459">[データベース エンジン チューニング アドバイザーからの出力の表示および操作](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="d721e-459">[View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="d721e-460">dta ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="d721e-460">dta Utility</span></span>](../../tools/dta/dta-utility.md)  
  
  
