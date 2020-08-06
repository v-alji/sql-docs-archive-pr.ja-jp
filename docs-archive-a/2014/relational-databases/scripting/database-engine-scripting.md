---
title: データベース エンジン スクリプト
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dca27e2aa5f2c0bc473534e0a8b204345b3993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630882"
---
# <a name="database-engine-scripting"></a><span data-ttu-id="cc5ba-102">データベース エンジン スクリプト</span><span class="sxs-lookup"><span data-stu-id="cc5ba-102">Database Engine Scripting</span></span>
  <span data-ttu-id="cc5ba-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインスタンスとそのインスタンスに含まれるオブジェクトを管理するための [!INCLUDE[ssDE](../../includes/ssde-md.md)] PowerShell スクリプト環境をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-103">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] supports the [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell scripting environment to manage instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the objects in the instances.</span></span> <span data-ttu-id="cc5ba-104">スクリプト環境と非常によく似た環境で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] と XQuery を含む [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを作成および実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-104">You can also build and run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries that contain [!INCLUDE[tsql](../../includes/tsql-md.md)] and XQuery in environments very similar to scripting environments.</span></span>  
  
## <a name="sql-server-powershell"></a><span data-ttu-id="cc5ba-105">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc5ba-105">SQL Server PowerShell</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc5ba-106">には、次を実装する 2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell スナップインが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-106">includes two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins that implement:</span></span>  
  
-   <span data-ttu-id="cc5ba-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデル階層を、ファイル システム パスと同様の PowerShell パスとして公開する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-107">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider that exposes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model hierarchies as PowerShell paths that are similar to file system paths.</span></span> <span data-ttu-id="cc5ba-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデル クラスを使用して、パスの各ノードで表されるオブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-108">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model classes to manage the objects represented at each node of the path.</span></span>  
  
-   <span data-ttu-id="cc5ba-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドを実装する一連の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-109">A set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlets that implement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commands.</span></span> <span data-ttu-id="cc5ba-110">コマンドレットの 1 つは **Invoke-Sqlcmd**です。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-110">One of the cmdlets is **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="cc5ba-111">これは [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、ユーティリティで実行されるクエリスクリプトを実行するために使用され `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-111">This is used to run [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query scripts to be run with the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc5ba-112">は、PowerShell を実行するための次の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-112">provides these features for running PowerShell:</span></span>  
  
-   <span data-ttu-id="cc5ba-113">PowerShell セッションにインポートできる **sqlps** PowerShell モジュール。さらにこのモジュールによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スナップインが読み込まれます。アドホック PowerShell コマンドは対話形式で実行できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-113">The **sqlps** PowerShell module that can be imported to a PowerShell session, the module then loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-ins. You can interactively run ad hoc PowerShell commands.</span></span> <span data-ttu-id="cc5ba-114">\MyFolder\MyScript.ps1 などのコマンドを使用してスクリプト ファイルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-114">You can run script files using a command such as .\MyFolder\MyScript.ps1.</span></span>  
  
-   <span data-ttu-id="cc5ba-115">PowerShell スクリプト ファイルは、スケジュールされた間隔で、またはシステム イベントに応答してスクリプトを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの PowerShell ジョブ ステップへの入力として使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-115">PowerShell script files can be used as input to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell job steps that run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
-   <span data-ttu-id="cc5ba-116">PowerShell を起動し、 **モジュールをインポートする** sqlps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティ。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-116">The **sqlps** utility that starts PowerShell and imports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module.</span></span> <span data-ttu-id="cc5ba-117">これによって、そのモジュールがサポートするすべてのアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-117">You can then perform all actions supported by the module.</span></span> <span data-ttu-id="cc5ba-118">**sqlps** ユーティリティは、コマンド プロンプトで、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio のオブジェクト エクスプローラー ツリーのノードを右クリックし、 **[PowerShell の起動]** をクリックして開始できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-118">You can start the **sqlps** utility either in a command prompt or by right-clicking on the nodes in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio Object Explorer tree and selecting **Start PowerShell**.</span></span>  
  
## <a name="database-engine-queries"></a><span data-ttu-id="cc5ba-119">データベース エンジン クエリ</span><span class="sxs-lookup"><span data-stu-id="cc5ba-119">Database Engine Queries</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="cc5ba-120">クエリ スクリプトには、次の 3 種類の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-120">query scripts contain three types of elements:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="cc5ba-121">言語ステートメント</span><span class="sxs-lookup"><span data-stu-id="cc5ba-121">language statements.</span></span>  
  
-   <span data-ttu-id="cc5ba-122">XQuery 言語ステートメント</span><span class="sxs-lookup"><span data-stu-id="cc5ba-122">XQuery language statements</span></span>  
  
-   <span data-ttu-id="cc5ba-123">ユーティリティのコマンドと変数 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-123">Commands and variables from the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc5ba-124">は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリを作成および実行するための次の 3 つの環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-124">provides three environments for building and running [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries:</span></span>  
  
-   <span data-ttu-id="cc5ba-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]クエリを対話形式で実行およびデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-125">You can interactively run and debug [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cc5ba-126">1 つのセッションで複数のステートメントをコーディングおよびデバッグしてから、1 つのスクリプト ファイルにすべてのステートメントを保存できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-126">You can code and debug several statements in one session, then save all of the statements in a single script file.</span></span>  
  
-   <span data-ttu-id="cc5ba-127">`sqlcmd`コマンドプロンプトユーティリティを使用すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリを対話形式で実行したり、既存のクエリスクリプトファイルを実行したりすることができ [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-127">The `sqlcmd` command prompt utility lets you interactively run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries, and also run existing [!INCLUDE[ssDE](../../includes/ssde-md.md)] query script files.</span></span>  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="cc5ba-128">クエリ スクリプト ファイルは、通常 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターを使用して対話形式でコーディングされます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-128">query script files are typically coded interactively in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="cc5ba-129">ファイルは、次のいずれかの環境で後から開くことができます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-129">The file can later be opened in one of these environments:</span></span>  
  
-   <span data-ttu-id="cc5ba-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ファイル]** / **[開く]** メニューを使用して、新しい [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウでファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-130">Use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **File**/**Open** menu to open the file in a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
-   <span data-ttu-id="cc5ba-131">**-I**_input_file_パラメーターを使用して、ユーティリティでファイルを実行し `sqlcmd` ます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-131">Use the **-i**_input_file_ parameter to run the file with the `sqlcmd` utility.</span></span>  
  
-   <span data-ttu-id="cc5ba-132">**-QueryFromFile** パラメーターを使用して、 **PowerShell スクリプトの** Invoke-Sqlcmd [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドレットでファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-132">Use the **-QueryFromFile** parameter to run the file with the **Invoke-Sqlcmd** cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell scripts.</span></span>  
  
-   <span data-ttu-id="cc5ba-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの [!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップを使用して、スケジュールされた間隔で、またはシステム イベントに応答してスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-133">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps to run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
 <span data-ttu-id="cc5ba-134">また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト生成ウィザードを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-134">In addition, you can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Generate Script Wizard to generate [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="cc5ba-135">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーでオブジェクトを右クリックし、 **[スクリプトの生成]** メニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-135">You can right-click objects in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, then select the **Generate Script** menu item.</span></span> <span data-ttu-id="cc5ba-136">**[スクリプトの生成]** を選択すると、スクリプトの作成プロセスを支援するウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-136">**Generate Script** launches the wizard, which guides you through the process of creating a script.</span></span>  
  
## <a name="database-engine-scripting-tasks"></a><span data-ttu-id="cc5ba-137">データベース エンジン スクリプトのタスク</span><span class="sxs-lookup"><span data-stu-id="cc5ba-137">Database Engine Scripting Tasks</span></span>  
  
|<span data-ttu-id="cc5ba-138">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="cc5ba-138">Task Description</span></span>|<span data-ttu-id="cc5ba-139">トピック</span><span class="sxs-lookup"><span data-stu-id="cc5ba-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="cc5ba-140">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] スクリプトを対話形式で開発、デバッグ、および実行するために、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のコード エディターとテキスト エディターを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-140">Describes how to use the code and text editors in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to interactively develop, debug, and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts</span></span>|[<span data-ttu-id="cc5ba-141">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cc5ba-141">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|<span data-ttu-id="cc5ba-142">対話形式でスクリプトを開発する機能も含めて、コマンド プロンプトから [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを実行するために、`sqlcmd` ユーティリティを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-142">Describes how to use the `sqlcmd` utility to run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts from the command prompt, including the ability to interactively develop scripts.</span></span>|[<span data-ttu-id="cc5ba-143">sqlcmd 操作方法のトピック</span><span class="sxs-lookup"><span data-stu-id="cc5ba-143">sqlcmd How-to Topics</span></span>](../../database-engine/sqlcmd-how-to-topics.md)|  
|<span data-ttu-id="cc5ba-144">Windows PowerShell 2.0 環境に SQL Server コンポーネントを統合し、SQL Server インスタンスおよびオブジェクトを管理するための PowerShell スクリプトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-144">Describes how to integrate the SQL Server components into a Windows PowerShell 2.0 environment and then build PowerShell scripts for managing SQL Server instances and objects.</span></span>|[<span data-ttu-id="cc5ba-145">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc5ba-145">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)|  
|<span data-ttu-id="cc5ba-146">データベースの 1 つまたは複数のオブジェクトを再作成する **スクリプトを作成するために、** スクリプトの生成とパブリッシュ [!INCLUDE[tsql](../../includes/tsql-md.md)] ウィザードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-146">Describes how to use the **Generate and Publish Scripts** wizard to create [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that recreate one or more of the objects from a database.</span></span>|[<span data-ttu-id="cc5ba-147">スクリプトの生成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cc5ba-147">Generate Scripts &#40;SQL Server Management Studio&#41;</span></span>](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="cc5ba-148">参照</span><span class="sxs-lookup"><span data-stu-id="cc5ba-148">See Also</span></span>  
 <span data-ttu-id="cc5ba-149">[sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="cc5ba-149">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="cc5ba-150">チュートリアル:Transact-SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="cc5ba-150">Tutorial: Writing Transact-SQL Statements</span></span>](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  