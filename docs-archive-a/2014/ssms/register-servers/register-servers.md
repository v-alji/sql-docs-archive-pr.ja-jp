---
title: サーバーの登録
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f4b23ba127c6b000b0abbe832c4c072ada78c5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634770"
---
# <a name="register-servers"></a><span data-ttu-id="21fec-102">サーバーの登録</span><span class="sxs-lookup"><span data-stu-id="21fec-102">Register Servers</span></span>
  <span data-ttu-id="21fec-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にサーバーを登録することで、サーバー接続情報を保存して、その後の接続時に使用できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]にサーバーを登録するには、次の 3 とおりの方法があります。</span><span class="sxs-lookup"><span data-stu-id="21fec-103">Registering a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] allows you to store the server connection information for future connections.There are three ways to register a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="21fec-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のインストール後の最初の起動時に、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="21fec-104">Local instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are automatically registered during the first launch of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] after its installation.</span></span>  
  
2.  <span data-ttu-id="21fec-105">また、この自動登録プロセスはいつでも開始でき、ローカル サーバー インスタンスの登録を復元できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-105">You can also initiate the automatic registration process at any time, to restore the registration of local server instances.</span></span>  
  
3.  <span data-ttu-id="21fec-106">さらに、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の登録済みサーバー ツールを使用してサーバーを登録できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-106">Lastly, you can register a server using the Registered Servers tool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="benefits-of-registered-servers"></a><span data-ttu-id="21fec-107">登録済みサーバーの利点</span><span class="sxs-lookup"><span data-stu-id="21fec-107">Benefits of Registered Servers</span></span>  
 <span data-ttu-id="21fec-108">登録済みサーバーを使用して、以下の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="21fec-108">With Registered Servers you can:</span></span>  
  
-   <span data-ttu-id="21fec-109">接続情報を保存するためにサーバーを登録できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-109">Register servers to preserve the connection information.</span></span>  
  
-   <span data-ttu-id="21fec-110">登録済みサーバーが実行中かどうかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-110">Determine if a registered server is running.</span></span>  
  
-   <span data-ttu-id="21fec-111">オブジェクト エクスプローラーとクエリ エディターを登録済みサーバーに簡単に接続できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-111">Easily connect Object Explorer and Query Editor to a registered server.</span></span>  
  
-   <span data-ttu-id="21fec-112">登録済みサーバーの登録情報の編集や削除を行えます。</span><span class="sxs-lookup"><span data-stu-id="21fec-112">Edit or delete the registration information for a registered server.</span></span>  
  
-   <span data-ttu-id="21fec-113">サーバーのグループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-113">Create groups of servers.</span></span>  
  
-   <span data-ttu-id="21fec-114">**[登録済みサーバーの名前]** ボックスに **[サーバー名]** 一覧とは別の値を指定して、登録済みサーバーにわかりやすい名前を設定できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-114">Provide user-friendly names for registered servers by providing a value in the **Registered server name** box that is different from the **Server name** list.</span></span>  
  
-   <span data-ttu-id="21fec-115">登録済みサーバーの詳細な説明を設定できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-115">Provide detailed descriptions for registered servers.</span></span>  
  
-   <span data-ttu-id="21fec-116">登録済みサーバーのグループの詳細な説明を設定できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-116">Provide detailed descriptions of registered server groups.</span></span>  
  
-   <span data-ttu-id="21fec-117">登録済みサーバーのグループをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="21fec-117">Export registered server groups.</span></span>  
  
-   <span data-ttu-id="21fec-118">登録済みサーバーのグループをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="21fec-118">Import registered server groups.</span></span>  
  
-   <span data-ttu-id="21fec-119">オンラインまたはオフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="21fec-119">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files for online or offline instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="21fec-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="21fec-120">Related Tasks</span></span>  
 <span data-ttu-id="21fec-121">登録したサーバーの基礎知識については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21fec-121">Use the following topics to get started with registered servers:</span></span>  
  
|<span data-ttu-id="21fec-122">**説明**</span><span class="sxs-lookup"><span data-stu-id="21fec-122">**Description**</span></span>|<span data-ttu-id="21fec-123">**トピック**</span><span class="sxs-lookup"><span data-stu-id="21fec-123">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="21fec-124">ローカル サーバー インスタンスの登録</span><span class="sxs-lookup"><span data-stu-id="21fec-124">Register local server instances</span></span>|[<span data-ttu-id="21fec-125">接続済みのサーバーの登録 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-125">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](register-a-connected-server-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-126">サーバーの登録</span><span class="sxs-lookup"><span data-stu-id="21fec-126">Register a server</span></span>|[<span data-ttu-id="21fec-127">新しい登録済みサーバーの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-127">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-128">登録済みサーバーの表示</span><span class="sxs-lookup"><span data-stu-id="21fec-128">View registered servers</span></span>|[<span data-ttu-id="21fec-129">SQL Server Management Studio で登録済みサーバーを表示する方法</span><span class="sxs-lookup"><span data-stu-id="21fec-129">View Registered Servers in SQL Server Management Studio</span></span>](view-registered-servers-in-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-130">登録済みサーバーの削除</span><span class="sxs-lookup"><span data-stu-id="21fec-130">Remove a registered server</span></span>|[<span data-ttu-id="21fec-131">新しい登録済みサーバーの削除 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-131">Remove a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](remove-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-132">サーバーの登録の変更</span><span class="sxs-lookup"><span data-stu-id="21fec-132">Change a server's registration</span></span>|[<span data-ttu-id="21fec-133">サーバーの登録の変更 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-133">Change a Server's Registration &#40;SQL Server Management Studio&#41;</span></span>](change-a-server-s-registration-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-134">登録済みサーバーの接続</span><span class="sxs-lookup"><span data-stu-id="21fec-134">Connect to a registered server</span></span>|[<span data-ttu-id="21fec-135">登録済みサーバーへの接続 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-135">Connect to a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](connect-to-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-136">登録済みサーバーの切断</span><span class="sxs-lookup"><span data-stu-id="21fec-136">Disconnect from a registered server</span></span>|[<span data-ttu-id="21fec-137">登録済みサーバーの切断 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-137">Disconnect from a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-138">登録済みサーバーまたはサーバー グループの移動</span><span class="sxs-lookup"><span data-stu-id="21fec-138">Move a registered server or server group</span></span>|[<span data-ttu-id="21fec-139">登録済みサーバーまたは登録済みサーバー グループの移動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-139">Move a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](move-a-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="21fec-140">登録済みサーバーまたはサーバー グループの名前変更</span><span class="sxs-lookup"><span data-stu-id="21fec-140">Change the name of a registered server or server group</span></span>|[<span data-ttu-id="21fec-141">登録済みサーバーまたは登録済みサーバー グループの名前の変更 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-141">Change the Name of a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](change-the-name-of-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="21fec-142">サーバー グループの作成または編集</span><span class="sxs-lookup"><span data-stu-id="21fec-142">Create or edit a server group</span></span>|[<span data-ttu-id="21fec-143">サーバー グループの作成または編集 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-143">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-144">サーバー グループの削除</span><span class="sxs-lookup"><span data-stu-id="21fec-144">Remove a server group</span></span>|[<span data-ttu-id="21fec-145">サーバー グループの削除 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-145">Remove a Server Group &#40;SQL Server Management Studio&#41;</span></span>](remove-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-146">登録済みサーバーの情報のエクスポート</span><span class="sxs-lookup"><span data-stu-id="21fec-146">Export registered server information</span></span>|[<span data-ttu-id="21fec-147">登録済みサーバー情報のエクスポート &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-147">Export Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](export-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-148">登録済みサーバーの情報のインポート</span><span class="sxs-lookup"><span data-stu-id="21fec-148">Import registered server information</span></span>|[<span data-ttu-id="21fec-149">登録済みサーバー情報のインポート &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-149">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="21fec-150">中央管理サーバーおよびサーバー グループの作成</span><span class="sxs-lookup"><span data-stu-id="21fec-150">Create a Central Management Server and Server Group</span></span>|[<span data-ttu-id="21fec-151">中央管理サーバーとサーバー グループの作成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-151">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-a-central-management-server-and-server-group.md)|  
|<span data-ttu-id="21fec-152">複数のサーバーに対するステートメントの同時実行</span><span class="sxs-lookup"><span data-stu-id="21fec-152">Execute statements against multiple servers simultaneously</span></span>|[<span data-ttu-id="21fec-153">複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="21fec-153">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="21fec-154">参照</span><span class="sxs-lookup"><span data-stu-id="21fec-154">See Also</span></span>  
 [<span data-ttu-id="21fec-155">リモート サーバー</span><span class="sxs-lookup"><span data-stu-id="21fec-155">Remote Servers</span></span>](../../database-engine/configure-windows/remote-servers.md)  
  
  
