---
title: オブジェクト エクスプローラーからインスタンスへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: stevestein
ms.author: sstein
ms.openlocfilehash: 918dd3ed6e8eb765f2cb7077107407c324c51a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630782"
---
# <a name="connect-to-an-instance-from-object-explorer"></a><span data-ttu-id="ae9b7-102">オブジェクト エクスプローラーからインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="ae9b7-102">Connect to an Instance From Object Explorer</span></span>
  <span data-ttu-id="ae9b7-103">オブジェクト エクスプローラーを使用してオブジェクトを管理するには、まず、オブジェクトを含むインスタンスにオブジェクト エクスプローラーを接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-103">To manage objects by using Object Explorer, you must first connect Object Explorer to the instance that contains the objects.</span></span> <span data-ttu-id="ae9b7-104">オブジェクト エクスプローラーは複数のインスタンスに同時に接続できます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-104">You can connect Object Explorer to multiple instances at the same time.</span></span>  
  
## <a name="connecting-object-explorer-to-a-server"></a><span data-ttu-id="ae9b7-105">オブジェクト エクスプローラーからサーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="ae9b7-105">Connecting Object Explorer to a Server</span></span>  
 <span data-ttu-id="ae9b7-106">オブジェクト エクスプローラーを使用するには、まずサーバーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-106">To use Object Explorer you must first connect to a server.</span></span> <span data-ttu-id="ae9b7-107">[オブジェクト エクスプローラー] ツール バーの **[接続]** をクリックし、ドロップダウン リストからサーバーの種類を選択してください。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-107">Click **Connect** on the Object Explorer toolbar and choose the type of server from the drop-down list.</span></span> <span data-ttu-id="ae9b7-108">**[サーバーへの接続]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-108">The **Connect to Server** dialog box opens.</span></span> <span data-ttu-id="ae9b7-109">接続するには、少なくともサーバーの名前と正しい認証情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-109">To connect, you must provide at least the name of the server and the correct authentication information.</span></span>  
  
## <a name="optional-object-explorer-connection-settings"></a><span data-ttu-id="ae9b7-110">オブジェクト エクスプローラーの省略可能な接続設定</span><span class="sxs-lookup"><span data-stu-id="ae9b7-110">Optional Object Explorer Connection Settings</span></span>  
 <span data-ttu-id="ae9b7-111">サーバーに接続するときに、 **[サーバーへの接続]** ダイアログ ボックスで追加の接続情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-111">When connecting to a server, you can specify additional connection information in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="ae9b7-112">**[サーバーへの接続]** ダイアログ ボックスでは最後に使用した設定が保存され、新しい接続 (新しいコード エディターのウィンドウなど) ではその設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-112">The **Connect to Server** dialog box will retain the last used settings, and new connections, such as new code editor windows, will use those settings.</span></span>  
  
 <span data-ttu-id="ae9b7-113">省略可能な接続設定を指定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-113">To specify optional connection settings, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ae9b7-114">[オブジェクト エクスプローラー] ツール バーの **[接続]** をクリックし、接続先のサーバーの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-114">Click **Connect** on the Object Explorer toolbar, and click the type of server to connect to.</span></span> <span data-ttu-id="ae9b7-115">**[サーバーに接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-115">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ae9b7-116">**[サーバー名]** ボックスに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-116">In the **Server Name** box, type the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
3.  <span data-ttu-id="ae9b7-117">**[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-117">Click **Options**.</span></span> <span data-ttu-id="ae9b7-118">**[サーバーへの接続]** ダイアログ ボックスに追加のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-118">The **Connect to Server** dialog box displays additional options.</span></span>  
  
4.  <span data-ttu-id="ae9b7-119">**[接続プロパティ]** タブをクリックし、追加の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-119">Click the **Connection Properties** tab to configure the additional settings.</span></span> <span data-ttu-id="ae9b7-120">使用可能な設定は、サーバーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-120">The settings that are available vary depending upon the server type.</span></span> <span data-ttu-id="ae9b7-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]で使用可能な設定は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-121">The following settings are available for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    |<span data-ttu-id="ae9b7-122">設定</span><span class="sxs-lookup"><span data-stu-id="ae9b7-122">Setting</span></span>|<span data-ttu-id="ae9b7-123">説明</span><span class="sxs-lookup"><span data-stu-id="ae9b7-123">Description</span></span>|  
    |-------------|-----------------|  
    |<span data-ttu-id="ae9b7-124">**データベースへの接続**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-124">**Connect to database**</span></span>|<span data-ttu-id="ae9b7-125">サーバー上の使用可能なデータベースのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-125">Choose from the available databases on the server.</span></span> <span data-ttu-id="ae9b7-126">一覧には、表示権限のあるデータベースだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-126">This list will only show databases that you have permission to view.</span></span>|  
    |<span data-ttu-id="ae9b7-127">**ネットワーク プロトコル**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-127">**Network protocol**</span></span>|<span data-ttu-id="ae9b7-128">共有メモリ、TCP/IP、名前付きパイプのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-128">Select from Shared Memory, TCP/IP, or Named Pipes.</span></span>|  
    |<span data-ttu-id="ae9b7-129">**ネットワークパケットサイズ**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-129">**Network packet size**</span></span>|<span data-ttu-id="ae9b7-130">バイト単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-130">Configure in bytes.</span></span> <span data-ttu-id="ae9b7-131">既定の設定は 4096 バイトです。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-131">The default setting is 4096 bytes.</span></span>|  
    |<span data-ttu-id="ae9b7-132">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-132">**Connection timeout**</span></span>|<span data-ttu-id="ae9b7-133">秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-133">Configure in seconds.</span></span> <span data-ttu-id="ae9b7-134">既定の設定は 15 秒です。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-134">The default setting is 15 seconds.</span></span>|  
    |<span data-ttu-id="ae9b7-135">**実行タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-135">**Execution timeout**</span></span>|<span data-ttu-id="ae9b7-136">秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-136">Configure in seconds.</span></span> <span data-ttu-id="ae9b7-137">既定の設定 (0) の場合、実行はタイムアウトになりません。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-137">The default setting (0) indicates that execution will never time out.</span></span>|  
    |<span data-ttu-id="ae9b7-138">**接続を暗号化する**</span><span class="sxs-lookup"><span data-stu-id="ae9b7-138">**Encrypt connection**</span></span>|<span data-ttu-id="ae9b7-139">暗号化を強制的に行います。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-139">Forces encryption.</span></span>|  
  
5.  <span data-ttu-id="ae9b7-140">指定したサーバーを登録済みサーバーの一覧に追加するには、 **[登録済みサーバー]** タブをクリックし、その新しいサーバーを表示する場所をクリックしてから、接続を完了します。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-140">To add the specified server to your list of registered servers, click the **Registered Server** tab, click on the location where you want the new server to appear, and then complete the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae9b7-141">**[追加の接続パラメーター]** ページを使用すると、接続文字列に接続パラメーターをさらに追加できます。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-141">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span> <span data-ttu-id="ae9b7-142">詳細については、「[[サーバーへの接続] ([追加の接続パラメーター] ページ)](../../database-engine/connect-to-server-additional-connection-parameters-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae9b7-142">For more information, see [Connect to Server &#40;Additional Connection Parameters Page&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).</span></span>  
  
  
