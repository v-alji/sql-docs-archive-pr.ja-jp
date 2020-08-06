---
title: ステータス バー (データベース エンジン クエリ エディター)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: rothja
ms.author: jroth
ms.openlocfilehash: 743ae0a4152daee19aa67f85337ae4077a3ed7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643767"
---
# <a name="status-bar-database-engine-query-editor"></a><span data-ttu-id="862c2-102">ステータス バー (データベース エンジン クエリ エディター)</span><span class="sxs-lookup"><span data-stu-id="862c2-102">Status Bar (Database Engine Query Editor)</span></span>
  <span data-ttu-id="862c2-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウのステータス バーでは、各ウィンドウが [!INCLUDE[ssDE](../../includes/ssde-md.md)] のどのインスタンスに接続しているかを色分けして示すことができます。</span><span class="sxs-lookup"><span data-stu-id="862c2-103">The status bar of [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows can be color coded to indicate which instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] each window is connected to.</span></span>  
  
1.  <span data-ttu-id="862c2-104">**作業を開始する準備:** [ステータス バーの色](#StatusBarColors)</span><span class="sxs-lookup"><span data-stu-id="862c2-104">**Before you begin:**  [Status Bar Colors](#StatusBarColors)</span></span>  
  
2.  <span data-ttu-id="862c2-105">**サーバーの状態の色を設定するには:** [オブジェクト エクスプローラー](#SetOEServerColor)、[登録済みサーバー](#SetRegServerColor)</span><span class="sxs-lookup"><span data-stu-id="862c2-105">**To set a server status color in:**  [Object Explorer](#SetOEServerColor), [Registered Server](#SetRegServerColor)</span></span>  
  
3.  <span data-ttu-id="862c2-106">**状態の色を使用するには:** [サーバーの色を使用したクエリ エディターの起動](#OpenServerColor)、[状態の色の指定によるクエリ エディターの起動](#OpenSpecColor)</span><span class="sxs-lookup"><span data-stu-id="862c2-106">**To use a status color:**  [Open Query Editor Using a Server Color](#OpenServerColor), [Open a Query Editor Specifying a Status Color](#OpenSpecColor)</span></span>  
  
##  <a name="status-bar-colors"></a><a name="StatusBarColors"></a> <span data-ttu-id="862c2-107">ステータス バーの色</span><span class="sxs-lookup"><span data-stu-id="862c2-107">Status Bar Colors</span></span>  
 <span data-ttu-id="862c2-108">**[オブジェクト エクスプローラー]** または **[登録済みサーバー]** の特定のサーバー ノードとステータス バーの色を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="862c2-108">You can associate a status bar color with a specific server node in either **Object Explorer** or **Registered Servers**.</span></span> <span data-ttu-id="862c2-109">ステータス バーの色を指定できるのは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続されているサーバー ノードのみで、他の SQL Server テクノロジのノードでは指定できません。</span><span class="sxs-lookup"><span data-stu-id="862c2-109">The colors can only be specified for server nodes connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], not server nodes for other SQL Server technologies.</span></span> <span data-ttu-id="862c2-110">また、新しい [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウを [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続するたびに、作成したステータス バーの色を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="862c2-110">You can also specify a custom status bar color each time you connect a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="862c2-111">その後、サーバー ノードに定義された状態の色を使用してクエリ エディター ウィンドウを開くか、そのエディター ウィンドウに対して一意の色を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="862c2-111">You can then open a query editor window using either the status color defined for the server node, or specify a unique color for that editor window.</span></span>  
  
 <span data-ttu-id="862c2-112">オブジェクト エクスプローラーのサーバー ノードに対して、作成したステータス バーの色を設定する場合、その設定を接続時に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="862c2-112">Setting a custom status bar color for a server node in Object Explorer must be done when making the connection.</span></span> <span data-ttu-id="862c2-113">既存のサーバー ノードに関連付けられている色を変更するには、接続解除してから、新しい色を指定して再接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="862c2-113">To change the color associated with an existing server node, you must disconnect and then reconnect specifying the new color.</span></span>  
  
##  <a name="set-the-status-color-for-a-server-in-object-explorer"></a><a name="SetOEServerColor"></a> <span data-ttu-id="862c2-114">オブジェクト エクスプローラーでのサーバー状態の色の設定</span><span class="sxs-lookup"><span data-stu-id="862c2-114">Set the Status Color for a Server in Object Explorer</span></span>  
 <span data-ttu-id="862c2-115">**オブジェクト エクスプローラーでサーバー状態の色を設定するには**</span><span class="sxs-lookup"><span data-stu-id="862c2-115">**To set a server status color in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="862c2-116">**[オブジェクト エクスプローラー]** で、 **[接続]** をクリックし、次に **[データベース エンジン...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-116">In **Object Explorer**, select the **Connect** button and then select **Database Engine...**.</span></span>  
  
2.  <span data-ttu-id="862c2-117">**[サーバーへの接続]** ダイアログで、 **[オプション >>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="862c2-117">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
3.  <span data-ttu-id="862c2-118">**[作成した色を使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="862c2-118">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="862c2-119">色を選択するには、 **[選択...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-119">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="862c2-120">基本の色または作成した色を選択して、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-120">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="862c2-121">残りの接続情報を入力して、 **[接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-121">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
##  <a name="set-the-status-color-for-a-registered-server"></a><a name="SetRegServerColor"></a> <span data-ttu-id="862c2-122">登録済みサーバーの状態の色の設定</span><span class="sxs-lookup"><span data-stu-id="862c2-122">Set the Status Color For a Registered Server</span></span>  
 <span data-ttu-id="862c2-123">**登録済みサーバーの状態の色を設定するには**</span><span class="sxs-lookup"><span data-stu-id="862c2-123">**To set a server color For a Registered Server**</span></span>  
  
1.  <span data-ttu-id="862c2-124">**[登録済みサーバー]** で、サーバー ノードを右クリックして、 **[プロパティ...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-124">In **Registered Servers**, right click the server node and then select **Properties...**.</span></span>  
  
2.  <span data-ttu-id="862c2-125">**[サーバー登録プロパティの編集]** ダイアログ ボックスで、 **[接続プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-125">On the **Edit Server Registration Properties** dialog, select the **Connection Properties** tab.</span></span>  
  
3.  <span data-ttu-id="862c2-126">**[作成した色を使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="862c2-126">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="862c2-127">色を選択するには、 **[選択...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-127">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="862c2-128">基本の色または作成した色を選択して、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-128">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="862c2-129">**[サーバー登録プロパティの編集]** ダイアログ ボックスで、 **[保存]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-129">Select the **Save** button on the **Edit Server Registration Properties** dialog.</span></span>  
  
##  <a name="open-an-editor-using-a-server-color"></a><a name="OpenServerColor"></a> <span data-ttu-id="862c2-130">サーバーの色を使用したエディターの起動</span><span class="sxs-lookup"><span data-stu-id="862c2-130">Open An Editor Using a Server Color</span></span>  
 <span data-ttu-id="862c2-131">**サーバーの色を使用してエディター ウィンドウを開くには**</span><span class="sxs-lookup"><span data-stu-id="862c2-131">**To open an editor window using a server color**</span></span>  
  
-   <span data-ttu-id="862c2-132">**オブジェクト エクスプローラー** または **[登録済みサーバー]** でサーバー ノードを右クリックして、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-132">Right-click a server node in either **Object Explorer** or **Registered Servers**, and select **New Query**.</span></span>  
  
-   <span data-ttu-id="862c2-133">または、サーバー ノードを強調表示して、 **[新しいクエリ]** ツール バー ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-133">Alternatively, highlight a server node, and then select the **New Query** toolbar button.</span></span>  
  
-   <span data-ttu-id="862c2-134">エディター ウィンドウのステータス バーでは、関連付けられたサーバーに定義されている色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="862c2-134">The status bar in the editor window will use the color defined for the associated server.</span></span>  
  
##  <a name="open-an-editor-specifying-a-status-color"></a><a name="OpenSpecColor"></a> <span data-ttu-id="862c2-135">状態の色の指定によるエディターの起動</span><span class="sxs-lookup"><span data-stu-id="862c2-135">Open an Editor Specifying a Status Color</span></span>  
 <span data-ttu-id="862c2-136">**状態の色を指定してエディター ウィンドウを開くには**</span><span class="sxs-lookup"><span data-stu-id="862c2-136">**To open an editor window specifying a status color**</span></span>  
  
-   <span data-ttu-id="862c2-137">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[データベース エンジン クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-137">Open the **File** menu, select **New**, and then select **Database Engine Query**.</span></span>  
  
-   <span data-ttu-id="862c2-138">**[サーバーへの接続]** ダイアログで、 **[オプション >>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="862c2-138">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
-   <span data-ttu-id="862c2-139">**[作成した色を使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="862c2-139">Select the **Use custom color** check box.</span></span>  
  
-   <span data-ttu-id="862c2-140">色を選択するには、 **[選択...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-140">To select the color, select the **Select...** button.</span></span>  
  
-   <span data-ttu-id="862c2-141">基本の色または作成した色を選択して、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-141">Select either a basic or custom color, then select OK.</span></span>  
  
-   <span data-ttu-id="862c2-142">残りの接続情報を入力して、 **[接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="862c2-142">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="862c2-143">参照</span><span class="sxs-lookup"><span data-stu-id="862c2-143">See Also</span></span>  
 [<span data-ttu-id="862c2-144">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="862c2-144">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
