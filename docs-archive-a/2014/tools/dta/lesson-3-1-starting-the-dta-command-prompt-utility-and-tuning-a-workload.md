---
title: dta コマンド プロンプト ユーティリティの起動とワークロードのチューニング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b2b1755a2ce8299556ab7d0ae14c89d3b2c8554
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711326"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a><span data-ttu-id="f6114-102">dta コマンド プロンプト ユーティリティの起動とワークロードのチューニング</span><span class="sxs-lookup"><span data-stu-id="f6114-102">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>
  <span data-ttu-id="f6114-103"> ここでは、**dta** ユーティリティを起動してヘルプを表示した後、同ユーティリティを使用してコマンド プロンプトからワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="f6114-103">This task guides you through starting the **dta** utility, viewing its Help, and then using it to tune a workload from the command prompt.</span></span> <span data-ttu-id="f6114-104">この例では、データベースエンジンチューニングアドバイザーのグラフィカルユーザーインターフェイス (GUI) で[ワークロードをチューニング](lesson-1-1-tuning-a-workload.md)するために作成したワークロード myscript.sql を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6114-104">It uses the workload, MyScript.sql, which you created for the Database Engine Tuning Advisor graphical user interface (GUI) practice [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
 <span data-ttu-id="f6114-105">このチュートリアルでは [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6114-105">The tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="f6114-106">セキュリティ上の理由から、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="f6114-106">For security reasons, the sample databases are not installed by default.</span></span> <span data-ttu-id="f6114-107">サンプル データベースをインストールするには、「 [SQL Server のサンプルとサンプル データベースのインストール](http://sqlserversamples.codeplex.com)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-107">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
 <span data-ttu-id="f6114-108">この後の実習では、コマンド プロンプトを開き、 **dta** コマンド プロンプト ユーティリティを起動して、構文ヘルプを表示します。さらに、「 [ワークロードのチューニング](lesson-1-1-tuning-a-workload.md)」で作成した簡単なワークロード MyScript.sql をチューニングします。</span><span class="sxs-lookup"><span data-stu-id="f6114-108">The following tasks guide you through opening a command prompt, starting the **dta** command prompt utility, viewing its syntax Help, and tuning a simple workload, MyScript.sql, which you created in [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a><span data-ttu-id="f6114-109">dta コマンド プロンプト ユーティリティを起動してヘルプを表示するには</span><span class="sxs-lookup"><span data-stu-id="f6114-109">To start the dta command prompt utility and view Help</span></span>  
  
1.  <span data-ttu-id="f6114-110">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[アクセサリ]** の順にポイントして、 **[コマンド プロンプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6114-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="f6114-111">コマンド プロンプトで以下を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f6114-111">At the command prompt, type the following, and press ENTER:</span></span>  
  
    ```  
    dta -? | more  
    ```  
  
     <span data-ttu-id="f6114-112">このコマンドの `| more` の部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f6114-112">The `| more` part of this command is optional.</span></span> <span data-ttu-id="f6114-113">これを指定した場合は、ユーティリティの構文ヘルプが 1 画面ずつ表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6114-113">However, using it enables you to page through the syntax help for the utility.</span></span> <span data-ttu-id="f6114-114">ヘルプを 1 行ずつ表示するには Enter キーを押し、1 ページずつ表示するにはスペース キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f6114-114">Press ENTER to advance the help text by the line, or press the SPACEBAR to advance it by the page.</span></span>  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a><span data-ttu-id="f6114-115">dta コマンド プロンプト ユーティリティを使用して簡単なワークロードをチューニングするには</span><span class="sxs-lookup"><span data-stu-id="f6114-115">To tune a simple workload by using the dta command prompt utility</span></span>  
  
1.  <span data-ttu-id="f6114-116">コマンド プロンプトで、MyScript.sql ファイルが保存されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="f6114-116">At the command prompt, navigate to the directory where you have stored the MyScript.sql file.</span></span>  
  
2.  <span data-ttu-id="f6114-117">コマンド プロンプトで次のコマンドを入力し、Enter キーを押します (コマンドの解釈時には大文字と小文字が区別される点に注意してください)。コマンドが実行され、チューニング セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="f6114-117">At the command prompt, type the following, and press ENTER to run the command and start the tuning session (note that the utility is case-sensitive when it parses commands):</span></span>  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     <span data-ttu-id="f6114-118">ここで、 `-S` には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースがインストールされているサーバーおよび [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] インスタンスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f6114-118">where `-S` specifies the name of your server and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is installed.</span></span> <span data-ttu-id="f6114-119">設定 `-E` は、Windows ドメイン アカウントで接続している場合に、適切なインスタンスへの信頼できる接続を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6114-119">The setting `-E` specifies that you want to use a trusted connection to the instance, which is appropriate if you are connecting with a Windows domain account.</span></span> <span data-ttu-id="f6114-120">設定 `-D` にはチューニングするデータベース名、 `-if` にはワークロード ファイル名、 `-s` にはセッション名を指定します。 `-of` には [!INCLUDE[tsql](../../includes/tsql-md.md)] の推奨設定スクリプトを書き込むファイルを指定し、 `-ox` には XML 形式で推奨設定を書き込むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6114-120">The setting `-D` specifies the database that you want to tune, `-if` specifies the workload file, `-s` specifies the session name, `-of` specifies the file to which you want the tool to write the [!INCLUDE[tsql](../../includes/tsql-md.md)] recommendations script, and `-ox` specifies the file to which you want the tool to write the recommendations in XML format.</span></span> <span data-ttu-id="f6114-121">最後の 3 つのスイッチは次のチューニング オプションを指定しています。 `-fa IDX_IV` は、インデックスとインデックス付きビューの追加のみを考慮するように指定します (クラスター化インデックス、非クラスター化インデックスが共に考慮されます)。 `-fp NONE` は、分析時にパーティション分割ストラテジを考慮しないように指定します。 `-fk NONE` は、データベース エンジン チューニング アドバイザーが推奨設定を作成する際に、データベースの既存の物理設計構造を保持しないように指定しています。</span><span class="sxs-lookup"><span data-stu-id="f6114-121">The last three switches specify tuning options as follows: `-fa IDX_IV` specifies that Database Engine Tuning Advisor should only consider adding indexes (both clustered and nonclustered) and indexed views; `-fp NONE` specifies that no partition strategy should be considered during analysis; and `-fk NONE` specifies that no existing physical design structures in the database must be kept when Database Engine Tuning Advisor makes its recommendations.</span></span>  
  
3.  <span data-ttu-id="f6114-122">データベース エンジン チューニング アドバイザーによるワークロードのチューニングが完了すると、チューニング セッションが正常に完了したことを知らせるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6114-122">After Database Engine Tuning Advisor finishes tuning the workload, it displays a message indicating that your tuning session completed successfully.</span></span> <span data-ttu-id="f6114-123">チューニング結果を表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して MySession2OutputScript.sql および MySession2Output.xml を開きます。</span><span class="sxs-lookup"><span data-stu-id="f6114-123">You can view the tuning results, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open the files MySession2OutputScript.sql and MySession2Output.xml.</span></span> <span data-ttu-id="f6114-124">また、データベース エンジン チューニング アドバイザーの GUI でチューニング セッション MySession2 を開き、その推奨設定とレポートを表示する方法もあります。これは、「 [チューニング推奨設定の表示](lesson-1-2-viewing-tuning-recommendations.md) 」および「 [チューニング レポートの表示](lesson-1-3-viewing-tuning-reports.md)」で行った操作と同様です。</span><span class="sxs-lookup"><span data-stu-id="f6114-124">Alternatively, you can also open the MySession2 tuning session in the Database Engine Tuning Advisor GUI and view its recommendations and reports in the same way that you did in [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) and [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f6114-125">まとめ</span><span class="sxs-lookup"><span data-stu-id="f6114-125">Summary</span></span>  
 <span data-ttu-id="f6114-126">**dta** ユーティリティを使用し、コマンド プロンプトから簡単なワークロードをチューニングしました。</span><span class="sxs-lookup"><span data-stu-id="f6114-126">You have completed tuning a simple workload from the command prompt by using the **dta** utility.</span></span> <span data-ttu-id="f6114-127">このツールには、これ以外にも多数のチューニング オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="f6114-127">This tool provides many other tuning options.</span></span> <span data-ttu-id="f6114-128">詳細については、ヘルプ (**dta -?**) および関連項目「 [dta ユーティリティ](dta-utility.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-128">Refer to the tool Help (**dta -?**) and the reference topic [dta Utility](dta-utility.md) for more information.</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="f6114-129">このチュートリアルが終了したら</span><span class="sxs-lookup"><span data-stu-id="f6114-129">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="f6114-130">このチュートリアルのレッスンが終了したら、次のトピックを参照し、データベース エンジン チューニング アドバイザーの詳細を学習してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-130">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="f6114-131">このツールを使用した作業の実行方法の説明については、「[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="f6114-132">コマンド プロンプト ユーティリティおよびユーティリティの動作の制御に使用できるオプションの XML ファイルに関するリファレンス情報については、「[dta Utility](dta-utility.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-132">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
 <span data-ttu-id="f6114-133">チュートリアルの開始に戻るには、「 [チュートリアル:データベース エンジン チューニング アドバイザー](tutorial-database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6114-133">To return to the start of the tutorial, see [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6114-134">参照</span><span class="sxs-lookup"><span data-stu-id="f6114-134">See Also</span></span>  
 [<span data-ttu-id="f6114-135">データベース エンジンのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="f6114-135">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
