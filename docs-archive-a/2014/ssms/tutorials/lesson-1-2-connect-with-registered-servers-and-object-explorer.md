---
title: 登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711502"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a><span data-ttu-id="919bb-102">登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続</span><span class="sxs-lookup"><span data-stu-id="919bb-102">Connect with Registered Servers and Object Explorer</span></span>
  <span data-ttu-id="919bb-103">このチュートリアルでは、登録済みサーバーとオブジェクト エクスプローラーの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="919bb-103">This tutorial demonstrates the use of Registered Servers and Object Explorer.</span></span>  
  
 <span data-ttu-id="919bb-104">このチュートリアルでは [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="919bb-104">This tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="919bb-105">セキュリティ強化のため、既定ではサンプル データベースはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="919bb-105">To help enhance security, by default, the sample databases are not installed.</span></span> <span data-ttu-id="919bb-106">詳細については、「 [SQL Server のサンプルとサンプル データベースのインストール](http://sqlserversamples.codeplex.com)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="919bb-106">For more information, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="connecting-to-servers"></a><span data-ttu-id="919bb-107">サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="919bb-107">Connecting to Servers</span></span>  
 <span data-ttu-id="919bb-108">[登録済みサーバー] コンポーネントのツール バーには、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="919bb-108">The toolbar of the Registered Servers component has buttons for the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="919bb-109">これらの種類のサーバーを 1 つ以上登録しておけば、その後の管理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="919bb-109">You can register one or more of these server types for convenient management.</span></span> <span data-ttu-id="919bb-110">次の手順で、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを登録してください。</span><span class="sxs-lookup"><span data-stu-id="919bb-110">Try the following exercise to register the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
#### <a name="to-register-the-database"></a><span data-ttu-id="919bb-111">データベースを登録するには</span><span class="sxs-lookup"><span data-stu-id="919bb-111">To register the database</span></span>  
  
1.  <span data-ttu-id="919bb-112">[登録済みサーバー] ツール バーの **[データベース エンジン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-112">On the Registered Servers toolbar, click **Database Engine** if you have to.</span></span> <span data-ttu-id="919bb-113">(通常は既に選択されています)。</span><span class="sxs-lookup"><span data-stu-id="919bb-113">(It may already be selected.)</span></span>  
  
2.  <span data-ttu-id="919bb-114">**[データベース エンジン]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="919bb-114">Expand **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="919bb-115">**[ローカル サーバー グループ]** を右クリックし、 **[新規サーバーの登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-115">Right-click **Local Server Groups**, and then click **New Server Registration**.</span></span>  
  
4.  <span data-ttu-id="919bb-116">**[新規サーバーの登録]** ダイアログ ボックスの **[サーバー名]** ボックスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="919bb-116">In the **New Server Registration** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="919bb-117">**[登録済みサーバーの名前]** ボックスに「 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="919bb-117">In the **Registered server name** box, type [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
6.  <span data-ttu-id="919bb-118">[**接続プロパティ**] タブの [**データベースへの接続**] ボックスの一覧で、を選択し **\<Browse server...>** ます。</span><span class="sxs-lookup"><span data-stu-id="919bb-118">On the **Connection Properties** tab, in the **Connect to database** list, select **\<Browse server...>**.</span></span>  
  
7.  <span data-ttu-id="919bb-119">**[データベースの参照]** ダイアログ ボックスで、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-119">In the **Browse for Databases** dialog box, click **Yes**.</span></span>  
  
8.  <span data-ttu-id="919bb-120">**[サーバーでデータベースを参照]** ダイアログ ボックスで、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-120">In the **Browse Server for Database** dialog box, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
9. <span data-ttu-id="919bb-121">サーバーが正しく登録されていることを確認するには、 **[テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-121">To verify that the server has been registered correctly, click **Test**.</span></span>  
  
10. <span data-ttu-id="919bb-122">**[新規サーバーの登録]** ダイアログ ボックスで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-122">In the **New Server Registration** dialog box, click **Save**.</span></span>  
  
## <a name="connecting-with-object-explorer"></a><span data-ttu-id="919bb-123">オブジェクト エクスプローラーを使用した接続</span><span class="sxs-lookup"><span data-stu-id="919bb-123">Connecting with Object Explorer</span></span>  
 <span data-ttu-id="919bb-124">[登録済みサーバー] と同様に、オブジェクト エクスプローラーから [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に接続できます。</span><span class="sxs-lookup"><span data-stu-id="919bb-124">Like Registered Servers, Object Explorer can connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
#### <a name="to-connect-with-object-explorer"></a><span data-ttu-id="919bb-125">オブジェクト エクスプローラーを使用して接続するには</span><span class="sxs-lookup"><span data-stu-id="919bb-125">To connect with Object Explorer</span></span>  
  
1.  <span data-ttu-id="919bb-126">オブジェクト エクスプローラーのツール バーで **[接続]** をクリックし、選択可能な接続の種類の一覧から **[データベース エンジン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="919bb-126">On the toolbar of Object Explorer, click **Connect** for a list of possible connection types, and then select **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="919bb-127">**[サーバーへの接続]** ダイアログ ボックスの **[サーバー名]** ボックスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="919bb-127">In the **Connect to Server** dialog box, in the **Server name** text box, type the name of your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="919bb-128">**[オプション]** をクリックし、選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="919bb-128">Click **Options** and explore the choices.</span></span>  
  
4.  <span data-ttu-id="919bb-129">サーバーに接続するため、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="919bb-129">To connect to the server, click **Connect**.</span></span> <span data-ttu-id="919bb-130">サーバーに既に接続している場合はオブジェクト エクスプローラーが表示され、そのサーバーが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="919bb-130">If you are already connected, this action just returns you to Object Explorer and sets the focus on that server.</span></span>  
  
     <span data-ttu-id="919bb-131">オブジェクト エクスプローラーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、レプリケーション、およびデータベース メールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="919bb-131">With Object Explorer you can administer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Security, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Replication, and Database Mail.</span></span> <span data-ttu-id="919bb-132">このほか、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssIS](../../includes/ssis-md.md)]の一部の機能を管理できます。</span><span class="sxs-lookup"><span data-stu-id="919bb-132">Object Explorer can only manage some of the features of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssIS](../../includes/ssis-md.md)].</span></span> <span data-ttu-id="919bb-133">これらのコンポーネントには、それぞれ新しい特殊なツールがあります。</span><span class="sxs-lookup"><span data-stu-id="919bb-133">Each of those components has additional specialized tools.</span></span>  
  
5.  <span data-ttu-id="919bb-134">オブジェクト エクスプローラーで、 **[データベース]** フォルダーを展開し、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]を選択します。</span><span class="sxs-lookup"><span data-stu-id="919bb-134">In Object Explorer, expand the **Databases** folder and select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
     <span data-ttu-id="919bb-135">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、システム データベースが別のフォルダーに表示される点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="919bb-135">Notice that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] presents the system databases in a separate folder.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="919bb-136">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="919bb-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="919bb-137">環境レイアウトの変更</span><span class="sxs-lookup"><span data-stu-id="919bb-137">Change the Environment Layout</span></span>](lesson-1-3-change-the-environment-layout.md)  
  
  
