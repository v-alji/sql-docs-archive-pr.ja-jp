---
title: ミラー化されたデータベースの登録 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 24732f82c971959ed202358613ef98c5ccc714d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716765"
---
# <a name="register-mirrored-database"></a><span data-ttu-id="63e94-102">[ミラー化されたデータベースの登録]</span><span class="sxs-lookup"><span data-stu-id="63e94-102">Register Mirrored Database</span></span>
  <span data-ttu-id="63e94-103">このダイアログ ボックスを使用すると、特定のサーバー インスタンスに対し、ミラー化されたデータベース (複数可) を登録できます。登録は、データベースをデータベース ミラーリング モニターに追加することによって行います。</span><span class="sxs-lookup"><span data-stu-id="63e94-103">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="63e94-104">データベースを追加すると、データベースとそのパートナーに関する情報、およびパートナーへの接続方法に関する情報が、データベース ミラーリング モニターによってローカルにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="63e94-104">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63e94-105">プリンシパル サーバー インスタンスで、 **sysadmin** 固定サーバー ロールのメンバーであったとしても、ミラー サーバー インスタンスで、そのロールのメンバーになっていない場合、プリンシパル サーバー インスタンスの状態は読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="63e94-105">If you are a member of the **sysadmin** fixed server role on the principal server instance but not on the mirror server instance, you can only see status on the principal server instance.</span></span>  
  
 <span data-ttu-id="63e94-106">**SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="63e94-106">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="63e94-107">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="63e94-107">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="63e94-108">Options</span><span class="sxs-lookup"><span data-stu-id="63e94-108">Options</span></span>  
 <span data-ttu-id="63e94-109">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="63e94-109">**Server instance**</span></span>  
 <span data-ttu-id="63e94-110">データベース ミラーリング モニターが接続を保持しているサーバー インスタンスが一覧表示されます。この一覧からサーバー インスタンスを選択するか、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63e94-110">Select a server instance from the list, which contains server instances to which Database Mirroring Monitor already has a connection stored, or click **Connect**.</span></span> <span data-ttu-id="63e94-111">一覧表示されたサーバー インスタンスの資格情報を更新するには、 **[接続]** をクリックして、新しい資格情報を使って接続します。</span><span class="sxs-lookup"><span data-stu-id="63e94-111">To specify new credentials for a listed server instance, click **Connect** and connect using the new credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63e94-112">複数のサーバー インスタンスに対してデータベースを登録する場合は、登録対象のデータベースのチェック ボックスをオンにした後、 **[適用]** をクリックし、続けて、別のサーバー インスタンスを選択して同じ作業を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="63e94-112">To register databases on multiple server instances, after you finish checking the desired databases for one server instance, click **Apply**, and then select another server instance.</span></span>  
  
 <span data-ttu-id="63e94-113">**接続する**</span><span class="sxs-lookup"><span data-stu-id="63e94-113">**Connect**</span></span>  
 <span data-ttu-id="63e94-114">サーバー インスタンスの資格情報を更新するには、 **[接続]** をクリックして、新しい資格情報を使って接続します。</span><span class="sxs-lookup"><span data-stu-id="63e94-114">To specify new credentials for the server instance, click **Connect** and connect using the new credentials.</span></span> <span data-ttu-id="63e94-115">サーバー インスタンスに接続している間、データベース ミラーリング モニターには、 **"データを待機しています"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-115">While connecting to a server instance, Database Mirroring Monitor displays **Waiting for data**.</span></span>  
  
 <span data-ttu-id="63e94-116">**[ミラー化されたデータベース]**</span><span class="sxs-lookup"><span data-stu-id="63e94-116">**Mirrored databases**</span></span>  
 <span data-ttu-id="63e94-117">**[ミラー化されたデータベース]** グリッドには、サーバー インスタンスでミラー化されているデータベースが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-117">The **Mirrored databases** grid lists the mirrored databases on the server instance.</span></span>  
  
 <span data-ttu-id="63e94-118">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="63e94-118">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="63e94-119">列名</span><span class="sxs-lookup"><span data-stu-id="63e94-119">Column name</span></span>|<span data-ttu-id="63e94-120">説明</span><span class="sxs-lookup"><span data-stu-id="63e94-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63e94-121">**[登録]**</span><span class="sxs-lookup"><span data-stu-id="63e94-121">**Register**</span></span>|<span data-ttu-id="63e94-122">登録する各データベースのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="63e94-122">Check each of the databases that you want to register.</span></span> <span data-ttu-id="63e94-123">現在監視されているデータベースのチェック ボックスはオンに設定され、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="63e94-123">If a database is currently monitored, its check box is checked and is disabled.</span></span><br /><br /> <span data-ttu-id="63e94-124">注:データベースの登録を解除するには、 **[ミラー化されたデータベースの登録]** ダイアログ ボックスを閉じ、ナビゲーション ツリーでデータベースを選択して、 **[アクション]** メニューの **[登録解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63e94-124">Note: To unregister a database, close the **Registered Mirrored Database** dialog box, select the database in the navigation tree, and select **Unregister** from the **Action** menu.</span></span>|  
|<span data-ttu-id="63e94-125">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="63e94-125">**Database**</span></span>|<span data-ttu-id="63e94-126">選択されたサーバー インスタンスでミラー化されたデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="63e94-126">The name of a mirrored database on the selected server instance.</span></span>|  
|<span data-ttu-id="63e94-127">**[現在のロール]**</span><span class="sxs-lookup"><span data-stu-id="63e94-127">**Current Role**</span></span>|<span data-ttu-id="63e94-128">選択されているサーバー インスタンスのデータベースについて、現在のミラーリング ロール ([プリンシパル] または [ミラー]) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-128">The current mirroring role of the database, either Principal or Mirror, on the selected server instance.</span></span>|  
|<span data-ttu-id="63e94-129">**[パートナー (接続するユーザー)]**</span><span class="sxs-lookup"><span data-stu-id="63e94-129">**Partner (Connect as)**</span></span>|<span data-ttu-id="63e94-130">データベースのフェールオーバー パートナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="63e94-130">The name of the failover partner for the database.</span></span> <span data-ttu-id="63e94-131">**[コンソール ユーザーの Windows 認証]** または **['***\<login name>***' の SQL Server 認証]** が、かっこで囲まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-131">Either **Windows Authentication of console user** or **SQL Server Authentication of login '***\<login name>***'** is displayed within the parentheses.</span></span> <span data-ttu-id="63e94-132">これは、既に追加されたインスタンスの場合は、現在使用されている認証情報を、まだモニターに追加されていないインスタンスの場合は、これから使用される認証情報を表します。</span><span class="sxs-lookup"><span data-stu-id="63e94-132">This is the authentication information currently used, if the instance has been added before, or that will be used, if this instance has not been added to the monitor.</span></span>|  
  
 <span data-ttu-id="63e94-133">**[[OK] をクリックしたときに [サーバー インスタンスの接続管理] ダイアログ ボックスを表示する]**</span><span class="sxs-lookup"><span data-stu-id="63e94-133">**Show the Manage Server Connections dialog box when I click OK.**</span></span>  
 <span data-ttu-id="63e94-134">パートナーのサーバー インスタンスに既存の資格情報が存在しない場合、既定では、Windows 認証の資格情報がデータベース ミラーリング モニターによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-134">By default, Database Mirroring Monitor uses Windows Authentication credentials for partner server instances for which credentials have not been previously given.</span></span> <span data-ttu-id="63e94-135">データベースの登録が完了し、1 つ以上のサーバー インスタンスについて資格情報を変更する場合は、このオプションを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="63e94-135">Enable this option to change the credentials for one or more server instances when you finish registering databases.</span></span>  
  
 <span data-ttu-id="63e94-136">このオプションを有効にした場合、 **[OK]** をクリックしたときに、 **[サーバー インスタンスの接続管理]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-136">If this option is enabled, when you click **OK**, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="63e94-137">ここでサーバー インスタンスを選択し、モニターが特定のフェールオーバー パートナーへの接続時に使用する資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="63e94-137">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given failover partner.</span></span>  
  
 <span data-ttu-id="63e94-138">パートナーの資格情報を編集するには、 **[サーバー インスタンス]** グリッドから対応するエントリを探し、その行の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63e94-138">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="63e94-139">サーバー インスタンス名に対応する **[サーバーへの接続]** ダイアログ ボックスが開き、現在キャッシュされている値に初期化された資格情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-139">This opens the **Connect to Server** dialog box for that server instance name, with the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="63e94-140">資格情報を必要に応じて変更し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63e94-140">Change the credentials as necessary and click **Connect**.</span></span> <span data-ttu-id="63e94-141">その資格情報に十分な特権がある場合は、 **[接続に使用する認証]** 列が新しい資格情報で更新されます。</span><span class="sxs-lookup"><span data-stu-id="63e94-141">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>  
  
 <span data-ttu-id="63e94-142">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="63e94-142">**Apply**</span></span>  
 <span data-ttu-id="63e94-143">このボタンをクリックすると、ダイアログ ボックスを開いた状態で、選択したデータベースを登録し、パートナー サーバー インスタンスの資格情報を保存できます。</span><span class="sxs-lookup"><span data-stu-id="63e94-143">Click this button to register the selected databases (and save credentials for the partner server instances) while keeping the dialog box open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e94-144">参照</span><span class="sxs-lookup"><span data-stu-id="63e94-144">See Also</span></span>  
 <span data-ttu-id="63e94-145">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="63e94-145">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="63e94-146">[データベース ミラーリングの監視 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63e94-146">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="63e94-147">データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="63e94-147">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
