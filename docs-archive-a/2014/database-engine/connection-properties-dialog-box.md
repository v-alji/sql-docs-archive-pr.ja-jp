---
title: '[接続プロパティ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db2817ebaf3f1655f146c060fcb79d550ad0cc8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740345"
---
# <a name="connection-properties-dialog-box"></a><span data-ttu-id="11a0f-102">[接続プロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="11a0f-102">Connection Properties Dialog Box</span></span>
  <span data-ttu-id="11a0f-103">このダイアログ ボックスを使用すると、現在の接続プロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="11a0f-103">Use this dialog box to view the current connection properties.</span></span> <span data-ttu-id="11a0f-104">このダイアログ ボックスは、オブジェクト エクスプローラーの各種のダイアログ ボックスで **[接続のプロパティを表示します]** をクリックすると表示されます。</span><span class="sxs-lookup"><span data-stu-id="11a0f-104">This dialog box is available when you click **View connection properties** in various Object Explorer dialog boxes.</span></span> <span data-ttu-id="11a0f-105">このページに表示されるプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="11a0f-105">The properties displayed on this page are read-only.</span></span>  
  
 <span data-ttu-id="11a0f-106">**[データベース]** などのプロパティを変更するには、オブジェクト エクスプローラーを使用して目的のデータベースに接続してから、 **[接続プロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="11a0f-106">To change properties such as **Database**, connect to the desired database with Object Explorer before opening the **Connection Properties** dialog box.</span></span>  
  
 <span data-ttu-id="11a0f-107">SQL Azure のクエリ タイムアウト期間は 30 分であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11a0f-107">Note that the query time-out period for SQL Azure is 30 minutes.</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="11a0f-108">認証</span><span class="sxs-lookup"><span data-stu-id="11a0f-108">Authentication</span></span>  
 <span data-ttu-id="11a0f-109">現在の接続の認証プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-109">View authentication properties for the current connection.</span></span> <span data-ttu-id="11a0f-110">認証プロパティとは、接続が確立されたときのログインと認証方法です。</span><span class="sxs-lookup"><span data-stu-id="11a0f-110">Authentication properties are the login and authentication method when the connection was established.</span></span> <span data-ttu-id="11a0f-111">認証プロパティを変更するには、から切断してから、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 目的の接続オプションを使用してオブジェクトエクスプローラーサーバーにもう一度接続します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-111">To change the authentication properties, disconnect from [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then connect Object Explorer to the server again, using the desired connection options.</span></span>  
  
 <span data-ttu-id="11a0f-112">**認証方法**</span><span class="sxs-lookup"><span data-stu-id="11a0f-112">**Authentication Method**</span></span>  
 <span data-ttu-id="11a0f-113">現在の接続に使用された認証方法。</span><span class="sxs-lookup"><span data-stu-id="11a0f-113">The authentication method used for the current connection.</span></span>  
  
 <span data-ttu-id="11a0f-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="11a0f-114">**User Name**</span></span>  
 <span data-ttu-id="11a0f-115">接続認証に使用されたログインのユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="11a0f-115">The name of the user of login used for the connection authentication.</span></span>  
  
## <a name="connection-category"></a><span data-ttu-id="11a0f-116">[接続] カテゴリ</span><span class="sxs-lookup"><span data-stu-id="11a0f-116">Connection Category</span></span>  
 <span data-ttu-id="11a0f-117">現在の接続の接続プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-117">View connection properties for the current connection.</span></span> <span data-ttu-id="11a0f-118">ほとんどの接続プロパティは、接続プロセス中に **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブで選択されます。</span><span class="sxs-lookup"><span data-stu-id="11a0f-118">Most connection properties were selected on the **Connection Properties** tab of the **Connect to server** dialog box during the connection process.</span></span>  
  
 <span data-ttu-id="11a0f-119">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="11a0f-119">**Database**</span></span>  
 <span data-ttu-id="11a0f-120">現在接続されているデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="11a0f-120">The name of the database currently connected to.</span></span> <span data-ttu-id="11a0f-121">この値を変更するには、SQL エディター ツール バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-121">To change this use, the SQL Editor toolbar.</span></span>  
  
 <span data-ttu-id="11a0f-122">**SPID**</span><span class="sxs-lookup"><span data-stu-id="11a0f-122">**SPID**</span></span>  
 <span data-ttu-id="11a0f-123">サーバーから接続に割り当てられているシステム プロセス ID。</span><span class="sxs-lookup"><span data-stu-id="11a0f-123">The system process ID assigned by the server to the connection.</span></span> <span data-ttu-id="11a0f-124">この接続に対してこの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="11a0f-124">This cannot be changed for this connection.</span></span>  
  
 <span data-ttu-id="11a0f-125">**ネットワークプロトコル**</span><span class="sxs-lookup"><span data-stu-id="11a0f-125">**Network Protocol**</span></span>  
 <span data-ttu-id="11a0f-126">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 接続のネットワーク プロトコル。</span><span class="sxs-lookup"><span data-stu-id="11a0f-126">The network protocol of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] connection.</span></span> <span data-ttu-id="11a0f-127">この値を変更するには、適切な接続プロパティを使用して接続し直します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-127">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="11a0f-128">**[ネットワーク パケット サイズ]**</span><span class="sxs-lookup"><span data-stu-id="11a0f-128">**Network Packet Size**</span></span>  
 <span data-ttu-id="11a0f-129">サーバーとの通信に使用されるパケット サイズ。</span><span class="sxs-lookup"><span data-stu-id="11a0f-129">The packet size used when communicating with the server.</span></span> <span data-ttu-id="11a0f-130">この値を変更するには、適切な接続プロパティを使用して接続し直します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-130">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="11a0f-131">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="11a0f-131">**Connection Timeout**</span></span>  
 <span data-ttu-id="11a0f-132">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] への接続を待つ秒数。この時間が経過すると、タイムアウトが発生し、接続失敗エラーがユーザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="11a0f-132">The amount of time is seconds to wait when connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before timing out and returning a failure to connect error to the user.</span></span> <span data-ttu-id="11a0f-133">この値を変更するには、適切な接続プロパティを使用して接続し直します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-133">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="11a0f-134">**実行タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="11a0f-134">**Execution Timeout**</span></span>  
 <span data-ttu-id="11a0f-135">サーバー上でタスクの実行が完了するまで待つ秒数。</span><span class="sxs-lookup"><span data-stu-id="11a0f-135">The amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="11a0f-136">この値を変更するには、適切な接続プロパティを使用して接続し直します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-136">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="11a0f-137">**Encrypted**</span><span class="sxs-lookup"><span data-stu-id="11a0f-137">**Encrypted**</span></span>  
 <span data-ttu-id="11a0f-138">現在の接続が暗号化されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-138">Whether the current connection is encrypted.</span></span> <span data-ttu-id="11a0f-139">この値を変更するには、適切な接続プロパティを使用して接続し直します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-139">To change this, connect again with the desired connection properties.</span></span>  
  
## <a name="product-category"></a><span data-ttu-id="11a0f-140">製品カテゴリ</span><span class="sxs-lookup"><span data-stu-id="11a0f-140">Product Category</span></span>  
 <span data-ttu-id="11a0f-141">現在の接続の製品プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-141">View product properties for the current connection.</span></span> <span data-ttu-id="11a0f-142">これらのプロパティは、サーバー製品、バージョン、インスタンス名、および照合順序を記述します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-142">These properties describe the server product, version, instance name, and collation.</span></span> <span data-ttu-id="11a0f-143">これらのプロパティは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール時に設定します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-143">The properties are set during [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="11a0f-144">**製品名**</span><span class="sxs-lookup"><span data-stu-id="11a0f-144">**Product Name**</span></span>  
 <span data-ttu-id="11a0f-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の製品名。</span><span class="sxs-lookup"><span data-stu-id="11a0f-145">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product name.</span></span>  
  
 <span data-ttu-id="11a0f-146">**製品バージョン**</span><span class="sxs-lookup"><span data-stu-id="11a0f-146">**Product Version**</span></span>  
 <span data-ttu-id="11a0f-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の製品バージョン。</span><span class="sxs-lookup"><span data-stu-id="11a0f-147">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product version.</span></span>  
  
 <span data-ttu-id="11a0f-148">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="11a0f-148">**Server Name**</span></span>  
 <span data-ttu-id="11a0f-149">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を実行しているコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="11a0f-149">The name of the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="11a0f-150">**インスタンス名**</span><span class="sxs-lookup"><span data-stu-id="11a0f-150">**Instance Name**</span></span>  
 <span data-ttu-id="11a0f-151">サーバーのインスタンス名。</span><span class="sxs-lookup"><span data-stu-id="11a0f-151">The instance name of the server.</span></span> <span data-ttu-id="11a0f-152">既定のインスタンスは空白です。</span><span class="sxs-lookup"><span data-stu-id="11a0f-152">The default instance is blank.</span></span>  
  
 <span data-ttu-id="11a0f-153">**Language**</span><span class="sxs-lookup"><span data-stu-id="11a0f-153">**Language**</span></span>  
 <span data-ttu-id="11a0f-154">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 製品の言語バージョン。</span><span class="sxs-lookup"><span data-stu-id="11a0f-154">The language version of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product.</span></span>  
  
 <span data-ttu-id="11a0f-155">**Collation**</span><span class="sxs-lookup"><span data-stu-id="11a0f-155">**Collation**</span></span>  
 <span data-ttu-id="11a0f-156">サーバーの照合順序。</span><span class="sxs-lookup"><span data-stu-id="11a0f-156">The collation of the server.</span></span>  
  
## <a name="server-environment-category"></a><span data-ttu-id="11a0f-157">[サーバー環境] カテゴリ</span><span class="sxs-lookup"><span data-stu-id="11a0f-157">Server Environment Category</span></span>  
 <span data-ttu-id="11a0f-158">サーバーのハードウェアおよびオペレーティング システムに関係する、現在の接続のサーバー環境プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="11a0f-158">View server environment properties for the current connection related to the server hardware and operating system.</span></span> <span data-ttu-id="11a0f-159">これらのプロパティは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では構成できません。</span><span class="sxs-lookup"><span data-stu-id="11a0f-159">The properties cannot be configured by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="11a0f-160">**コンピューター名**</span><span class="sxs-lookup"><span data-stu-id="11a0f-160">**Computer Name**</span></span>  
 <span data-ttu-id="11a0f-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を実行しているサーバー コンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="11a0f-161">The name of the server computer that is running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="11a0f-162">**プラットフォーム**</span><span class="sxs-lookup"><span data-stu-id="11a0f-162">**Platform**</span></span>  
 <span data-ttu-id="11a0f-163">サーバーのオペレーティング システム名、メーカー名、および CPU ファミリ。</span><span class="sxs-lookup"><span data-stu-id="11a0f-163">The operating system name, manufacturer name, and CPU family of the server.</span></span>  
  
 <span data-ttu-id="11a0f-164">**オペレーティング システム**</span><span class="sxs-lookup"><span data-stu-id="11a0f-164">**Operating System**</span></span>  
 <span data-ttu-id="11a0f-165">サーバーにインストールされている [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows バージョン。</span><span class="sxs-lookup"><span data-stu-id="11a0f-165">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows version installed on the server.</span></span>  
  
 <span data-ttu-id="11a0f-166">**[プロセッサ]**</span><span class="sxs-lookup"><span data-stu-id="11a0f-166">**Processors**</span></span>  
 <span data-ttu-id="11a0f-167">サーバーに搭載されているプロセッサの数。</span><span class="sxs-lookup"><span data-stu-id="11a0f-167">The number of processors on the server.</span></span>  
  
 <span data-ttu-id="11a0f-168">**[オペレーティング システムのメモリ]**</span><span class="sxs-lookup"><span data-stu-id="11a0f-168">**Operating System Memory**</span></span>  
 <span data-ttu-id="11a0f-169">サーバーに搭載されている物理メモリの合計 (MB 単位)。</span><span class="sxs-lookup"><span data-stu-id="11a0f-169">The total amount of physical memory on the server, in megabytes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a0f-170">参照</span><span class="sxs-lookup"><span data-stu-id="11a0f-170">See Also</span></span>  
 <span data-ttu-id="11a0f-171">[SQL Server Management Studio のプロパティページ](../ssms/property-pages-in-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="11a0f-171">[Property Pages in SQL Server Management Studio](../ssms/property-pages-in-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="11a0f-172">[[サーバーへの接続] ([ログイン] ページ) データベース エンジン](../ssms/f1-help/connect-to-server-login-page-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="11a0f-172">[Connect to Server &#40;Login Page&#41; Database Engine](../ssms/f1-help/connect-to-server-login-page-database-engine.md)</span></span>  
  
  
