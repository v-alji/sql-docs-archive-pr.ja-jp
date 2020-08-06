---
title: '[サーバーへの接続] ([接続プロパティ] ページ) (データベース エンジン) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41f2aa3fd5004a371515ee5d8905c7bb73699829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739031"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a><span data-ttu-id="f55ff-102">[サーバーへの接続] ([接続プロパティ] ページ) (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="f55ff-102">Connect to Server (Connection Properties Page) Database Engine</span></span>
  <span data-ttu-id="f55ff-103">このタブを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続するとき、または [!INCLUDE[ssDE](../../includes/ssde-md.md)] を**登録済みサーバー**に登録するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-103">Use this tab to view or specify options when connecting to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="f55ff-104">**のインスタンスに接続するときには、** [接続] **および** [オプション] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-104">**Connect** and **Options** only appear in this dialog box when connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f55ff-105">**を登録するときには、** [テスト] **および** [保存] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="f55ff-106">Options</span><span class="sxs-lookup"><span data-stu-id="f55ff-106">Options</span></span>  
 <span data-ttu-id="f55ff-107">**データベースへの接続**</span><span class="sxs-lookup"><span data-stu-id="f55ff-107">**Connect to database**</span></span>  
 <span data-ttu-id="f55ff-108">接続するデータベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="f55ff-109">を選択した場合は、 **\<default>** サーバーの既定のデータベースに接続されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="f55ff-110">を選択した場合は、接続先の **\<Browse server>** データベースのサーバーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-110">If you select **\<Browse server>**, you can browse the server for the database to which to connect.</span></span>  
  
 <span data-ttu-id="f55ff-111">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] を通じて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンのインスタンスに接続する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、 **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブでデータベースを指定する必要があります。 **[暗号化接続]** チェック ボックスがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f55ff-111">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="f55ff-112">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は **master**に接続されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-112">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="f55ff-113">ユーザー データベースを指定すると、オブジェクト エクスプローラーにそのデータベースとそのオブジェクトのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-113">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="f55ff-114">**master**に接続すると、すべてのデータベースを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f55ff-114">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="f55ff-115">詳細については、「 [Azure SQL Database の概要](/azure/sql-database/sql-database-technical-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f55ff-115">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="f55ff-116">**ネットワーク プロトコル**</span><span class="sxs-lookup"><span data-stu-id="f55ff-116">**Network protocol**</span></span>  
 <span data-ttu-id="f55ff-117">一覧からプロトコルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-117">Select a protocol from the list.</span></span> <span data-ttu-id="f55ff-118">使用できるクライアント プロトコルは、[コンピューターの管理] の [SQL Native Client の構成] を使用して設定されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="f55ff-118">The available client protocols are those that you configured using the Client Network Configuration in Computer Management.</span></span>  
  
 <span data-ttu-id="f55ff-119">**ネットワークパケットサイズ**</span><span class="sxs-lookup"><span data-stu-id="f55ff-119">**Network packet size**</span></span>  
 <span data-ttu-id="f55ff-120">送信されるネットワーク パケットのサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-120">Enter the size of the network packets to be sent.</span></span> <span data-ttu-id="f55ff-121">既定値は 4096 バイトです。</span><span class="sxs-lookup"><span data-stu-id="f55ff-121">The default is 4096 bytes.</span></span>  
  
 <span data-ttu-id="f55ff-122">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="f55ff-122">**Connection timeout**</span></span>  
 <span data-ttu-id="f55ff-123">接続が確立されるまで待機する秒数を入力します。この時間が経過するとタイムアウトになります。既定値は15秒です。</span><span class="sxs-lookup"><span data-stu-id="f55ff-123">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="f55ff-124">**実行タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="f55ff-124">**Execution timeout**</span></span>  
 <span data-ttu-id="f55ff-125">タスクの実行がサーバーで完了するまで待機する秒数を入力します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-125">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="f55ff-126">既定値は 0 秒です。つまり、タイムアウトはありません。</span><span class="sxs-lookup"><span data-stu-id="f55ff-126">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="f55ff-127">**接続を暗号化する**</span><span class="sxs-lookup"><span data-stu-id="f55ff-127">**Encrypt connection**</span></span>  
 <span data-ttu-id="f55ff-128">接続の暗号化を強制します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-128">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="f55ff-129">**[作成した色を使用する]**</span><span class="sxs-lookup"><span data-stu-id="f55ff-129">**Use custom color**</span></span>  
 <span data-ttu-id="f55ff-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディター ウィンドウのステータス バーの背景色を指定します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-130">Select to specify the background color for the status bar in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="f55ff-131">色を指定するには、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f55ff-131">To specify the color, click **Select**.</span></span> <span data-ttu-id="f55ff-132">**[色の設定]** ダイアログ ボックスで、 **[基本色]** グリッドから定義済みの色を選択するか、 **[色の作成]** をクリックし、カスタムの色を定義して使用します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-132">In the **Color** dialog box, select a predefined color from the **Basic Colors** grid or click **Define Custom Colors** to define and use a custom color.</span></span>  
  
-   <span data-ttu-id="f55ff-133">**[オブジェクト エクスプローラー]** ペインのサーバー エントリの色を指定すると、クエリ エディター ウィンドウを開いたときにその色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-133">When you specify a color for a server entry in the **Object Explorer** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="f55ff-134">クエリ エディター ウィンドウを開くには、サーバー エントリを右クリックし、 **[新しいクエリ]** を選択します。または、 **[オブジェクト エクスプローラー]** ペインがアクティブで、このサーバーにフォーカスが置かれている場合は、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f55ff-134">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Object Explorer** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="f55ff-135">**[登録済みサーバー]** ペインのサーバー エントリの色を指定すると、クエリ エディター ウィンドウを開いたときにその色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-135">When you specify a color for a server entry in the **Registered Servers** pane, that color is used when you open a Query Editor window.</span></span> <span data-ttu-id="f55ff-136">クエリ エディター ウィンドウを開くには、サーバー エントリを右クリックし、 **[新しいクエリ]** を選択します。または、 **[登録済みサーバー]** ペインがアクティブで、このサーバーにフォーカスが置かれている場合は、ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f55ff-136">To open a Query Editor window, either right-click the server entry and select **New Query**; or, when the **Registered Server** pane is active and focused on this server, click **New Query** on the toolbar.</span></span>  
  
-   <span data-ttu-id="f55ff-137">**[ファイル]** メニューで、 **[新規作成]** 、 **[データベース エンジン クエリ]** の順にクリックすると、 **[サーバーへの接続]** ダイアログ ボックスで指定した色がそのクエリ エディター ウィンドウに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-137">On the **File** menu, when you click **New** and then **Database Engine Query**, the color you that you specify in the **Connect to Server** dialog box applies to that Query Editor window.</span></span>  
  
 <span data-ttu-id="f55ff-138">**[すべてリセット]**</span><span class="sxs-lookup"><span data-stu-id="f55ff-138">**Reset All**</span></span>  
 <span data-ttu-id="f55ff-139">手動で入力された接続プロパティ値をすべて既定値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f55ff-139">Replace all manually entered connection property values with their defaults.</span></span>  
  
 <span data-ttu-id="f55ff-140">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="f55ff-140">**Connect**</span></span>  
 <span data-ttu-id="f55ff-141">一覧表示された値を使用して接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-141">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="f55ff-142">**Options**</span><span class="sxs-lookup"><span data-stu-id="f55ff-142">**Options**</span></span>  
 <span data-ttu-id="f55ff-143">クリックすると、ダイアログ ボックスが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="f55ff-143">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="f55ff-144">**テスト**</span><span class="sxs-lookup"><span data-stu-id="f55ff-144">**Test**</span></span>  
 <span data-ttu-id="f55ff-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] を **登録済みサーバー**に登録するときに、クリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="f55ff-145">When registering [!INCLUDE[ssDE](../../includes/ssde-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="f55ff-146">**および**</span><span class="sxs-lookup"><span data-stu-id="f55ff-146">**Save**</span></span>  
 <span data-ttu-id="f55ff-147">**登録済みサーバー**に設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="f55ff-147">Saves the settings in **Registered Servers**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f55ff-148">参照</span><span class="sxs-lookup"><span data-stu-id="f55ff-148">See Also</span></span>  
 <span data-ttu-id="f55ff-149">[[接続プロパティ] ダイアログ ボックス](../../database-engine/connection-properties-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="f55ff-149">[Connection Properties Dialog Box](../../database-engine/connection-properties-dialog-box.md)</span></span>  
  
  
