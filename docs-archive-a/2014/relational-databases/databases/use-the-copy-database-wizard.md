---
title: データベース コピー ウィザードの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0baaeef6cb196a67b2f615aa280b61b61fbc5119
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741082"
---
# <a name="use-the-copy-database-wizard"></a><span data-ttu-id="8445b-102">データベース コピー ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="8445b-102">Use the Copy Database Wizard</span></span>
  <span data-ttu-id="8445b-103">データベース コピー ウィザードを使用すると、サーバーを停止することなく、データベースとそのオブジェクトをサーバー間で簡単にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="8445b-103">The Copy Database Wizard lets you move or copy databases and their objects easily from one server to another, with no server downtime.</span></span> <span data-ttu-id="8445b-104">また、以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンから [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にデータベースをアップグレードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8445b-104">You can also upgrade databases from a previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8445b-105">このウィザードを使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-105">By using this wizard, you can do the following:</span></span>  
  
-   <span data-ttu-id="8445b-106">移動元またはコピー元、および移動先またはコピー先サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-106">Pick a source and destination server.</span></span>  
  
-   <span data-ttu-id="8445b-107">移動、コピー、またはアップグレードするデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-107">Select databases to move, copy or upgrade.</span></span>  
  
-   <span data-ttu-id="8445b-108">データベースのファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-108">Specify the file location for the databases.</span></span>  
  
-   <span data-ttu-id="8445b-109">移動先またはコピー先サーバー上にログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="8445b-109">Create logins on the destination server.</span></span>  
  
-   <span data-ttu-id="8445b-110">追加のサポート オブジェクト、ジョブ、ユーザー定義のストアド プロシージャ、およびエラー メッセージをコピーします。</span><span class="sxs-lookup"><span data-stu-id="8445b-110">Copy additional supporting objects, jobs, user-defined stored procedures, and error messages.</span></span>  
  
-   <span data-ttu-id="8445b-111">データベースを移動またはコピーする時期をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="8445b-111">Schedule when to move or copy the databases.</span></span>  
  
 <span data-ttu-id="8445b-112">データベース以外にも、関連したメタデータ (コピーしたデータベースに必要な **master** データベースのログインやオブジェクトなど) をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="8445b-112">In addition to copying databases, you can copy associated metadata, for example, logins and objects from the **master** database that are required by a copied database.</span></span>  
  
 <span data-ttu-id="8445b-113">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="8445b-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8445b-114">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="8445b-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8445b-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8445b-115">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8445b-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="8445b-116">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="8445b-117">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="8445b-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="8445b-118">Security</span><span class="sxs-lookup"><span data-stu-id="8445b-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8445b-119">**データベース コピー ウィザードを使用して以下のことを行うには:**</span><span class="sxs-lookup"><span data-stu-id="8445b-119">**Using the Copy Database Wizard to:**</span></span>  
  
     [<span data-ttu-id="8445b-120">データベースのコピー、移動、またはアップグレード</span><span class="sxs-lookup"><span data-stu-id="8445b-120">Copy, Move, or Upgrade Databases</span></span>](#Copy_Move)  
  
-   <span data-ttu-id="8445b-121">**補足情報 (アップグレード後):**</span><span class="sxs-lookup"><span data-stu-id="8445b-121">**Follow up, after upgrade:**</span></span>  
  
     [<span data-ttu-id="8445b-122">SQL Server データベースのアップグレード後</span><span class="sxs-lookup"><span data-stu-id="8445b-122">After Upgrading a SQL Server Database</span></span>](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8445b-123">はじめに</span><span class="sxs-lookup"><span data-stu-id="8445b-123">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8445b-124">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="8445b-124">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8445b-125">データベース コピー ウィザードは、Express Edition では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8445b-125">The Copy Database Wizard is not available in the Express edition.</span></span>  
  
-   <span data-ttu-id="8445b-126">データベース コピー ウィザードを使用して、次のデータベースをコピーしたり移動したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8445b-126">The Copy Database Wizard cannot be used to copy or move the following databases.</span></span>  
  
    -   <span data-ttu-id="8445b-127">システム データベース</span><span class="sxs-lookup"><span data-stu-id="8445b-127">System databases</span></span>  
  
    -   <span data-ttu-id="8445b-128">データベースはレプリケーション用に設定されています。</span><span class="sxs-lookup"><span data-stu-id="8445b-128">Databases marked for replication.</span></span>  
  
    -   <span data-ttu-id="8445b-129">アクセス不可、読み込み中、オフライン、復旧中、未確認、または緊急モードのマークが付いたデータベース</span><span class="sxs-lookup"><span data-stu-id="8445b-129">Databases marked Inaccessible, Loading, Offline, Recovering, Suspect, or in Emergency Mode.</span></span>  
  
-   <span data-ttu-id="8445b-130">データベースをアップグレードした後、以前のバージョンにダウングレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8445b-130">After a database has been upgraded, it cannot be downgraded to a previous version.</span></span>  
  
-   <span data-ttu-id="8445b-131">**[移動]** オプションを選択した場合、データベースを移動した後で、コピー元データベースが自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-131">If you select the **Move** option, the wizard deletes the source database automatically after moving the database.</span></span> <span data-ttu-id="8445b-132">**[コピー]** オプションを選択した場合は、コピー元データベースが削除されません。</span><span class="sxs-lookup"><span data-stu-id="8445b-132">The Copy Database Wizard does not delete a source database if you select the **Copy** option.</span></span>  
  
-   <span data-ttu-id="8445b-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクトの方法を使用してフルテキスト カタログを移動する場合は、移動後にインデックスを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-133">If you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method to move the full-text catalog, you must repopulate the index after the move.</span></span>  
  
-   <span data-ttu-id="8445b-134">デタッチ後にアタッチする方法では、データベースをデタッチして、データベースの .mdf、.ndf、.ldf ファイルを移動するかコピーして、新しい場所でデータベースをもう一度アタッチします。</span><span class="sxs-lookup"><span data-stu-id="8445b-134">The detach-and-attach method detaches the database, moves or copies the database .mdf, .ndf, .ldf files and reattaches the database in the new location.</span></span> <span data-ttu-id="8445b-135">デタッチおよびアタッチによる方法でデータの損失や不整合を避けるため、移動またはコピーするデータベースにアクティブなセッションをアタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8445b-135">For the detach-and-attach method, to avoid data loss or inconsistency, active sessions cannot be attached to the database being moved or copied.</span></span> <span data-ttu-id="8445b-136">アクティブなセッションが存在する場合、データベース コピー ウィザードでは、移動またはコピー操作は実行されません。</span><span class="sxs-lookup"><span data-stu-id="8445b-136">If any active sessions exist, the Copy Database Wizard does not execute the move or copy operation.</span></span> <span data-ttu-id="8445b-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクトの方法では、データベースがオフラインになることがないため、アクティブなセッションが許可されています。</span><span class="sxs-lookup"><span data-stu-id="8445b-137">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method, active sessions are allowed because the database is never taken offline.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8445b-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="8445b-138">Prerequisites</span></span>  
 <span data-ttu-id="8445b-139">移動先またはコピー先のサーバーで SQL Server エージェントが起動されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8445b-139">Ensure that SQL Server Agent is started on the destination server.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8445b-140">推奨事項</span><span class="sxs-lookup"><span data-stu-id="8445b-140">Recommendations</span></span>  
  
-   <span data-ttu-id="8445b-141">アップグレードしたデータベースのパフォーマンスを最適化するには、アップグレードしたデータベースに対して sp_updatestats (統計の更新) を実行します。</span><span class="sxs-lookup"><span data-stu-id="8445b-141">To ensure optimal performance of an upgraded database, run sp_updatestats (update statistics) against the upgraded database.</span></span>  
  
-   <span data-ttu-id="8445b-142">データベースを別のサーバー インスタンスにコピーするときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、アタッチ先のサーバー インスタンスで、ログインやジョブなどのデータベースのメタデータの一部またはすべてを作成し直す必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-142">When you copy a database to another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="8445b-143">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8445b-143">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8445b-144">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8445b-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8445b-145">Permissions</span><span class="sxs-lookup"><span data-stu-id="8445b-145">Permissions</span></span>  
 <span data-ttu-id="8445b-146">コピー元または移動元とコピー先または移動先の両方のサーバーにおいて **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-146">You must be a member of the **sysadmin** fixed server role on both the source and destination servers.</span></span>  
  
##  <a name="copy-move-or-upgrade-databases"></a><a name="Copy_Move"></a><span data-ttu-id="8445b-147">データベースのコピー、移動、またはアップグレード</span><span class="sxs-lookup"><span data-stu-id="8445b-147">Copy, Move or Upgrade Databases</span></span>  
  
1.  <span data-ttu-id="8445b-148">の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクトエクスプローラーで、[**データベース**] を展開し、データベースを右クリックして [**タスク**] をポイントし、[**データベースのコピー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8445b-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Copy Database**.</span></span>  
  
2.  <span data-ttu-id="8445b-149">**[転送元サーバーの選択]** ページで、移動またはコピーするデータベースがあるサーバーの指定や、ログイン情報の入力を行います。</span><span class="sxs-lookup"><span data-stu-id="8445b-149">From the **Select a Source Server** page, specify the server with the database to move or copy, and to enter login information.</span></span> <span data-ttu-id="8445b-150">認証方法を選択し、ログイン情報を入力したら、 **[次へ]** をクリックして転送元サーバーとの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="8445b-150">After you select the authentication method and enter login information, click **Next** to establish the connection to the source server.</span></span> <span data-ttu-id="8445b-151">セッションの間、この接続は開いています。</span><span class="sxs-lookup"><span data-stu-id="8445b-151">This connection remains open throughout the session.</span></span>  
  
     <span data-ttu-id="8445b-152">**移行元サーバー**</span><span class="sxs-lookup"><span data-stu-id="8445b-152">**Source server**</span></span>  
     <span data-ttu-id="8445b-153">移動またはコピーするデータベースが配置されているサーバーの名前を選択するか、参照ボタン ([.**.**.]) をクリックして目的のサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-153">Select the name of the server on which the database or databases you want to move or copy are located, or click the browse (**...**) button to locate the server you want.</span></span> <span data-ttu-id="8445b-154">サーバーは、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-154">The server must be at least [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="8445b-155">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-155">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="8445b-156">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントを使用して接続することをユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="8445b-156">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="8445b-157">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-157">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="8445b-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証用のユーザー名とパスワードを入力して接続することをユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="8445b-158">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="8445b-159">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="8445b-159">**User name**</span></span>  
     <span data-ttu-id="8445b-160">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="8445b-160">Enter the user name to connect with.</span></span> <span data-ttu-id="8445b-161">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証による接続が選ばれている場合にのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-161">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication .</span></span>  
  
     <span data-ttu-id="8445b-162">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="8445b-162">**Password**</span></span>  
     <span data-ttu-id="8445b-163">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8445b-163">Enter the password for the login.</span></span> <span data-ttu-id="8445b-164">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続が指定されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-164">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="8445b-165">**次へ**</span><span class="sxs-lookup"><span data-stu-id="8445b-165">**Next**</span></span>  
     <span data-ttu-id="8445b-166">サーバーに接続し、ユーザーを検証します。</span><span class="sxs-lookup"><span data-stu-id="8445b-166">Connect to the server and validate the user.</span></span> <span data-ttu-id="8445b-167">このプロセスでは、選択したコンピューター上でユーザーが固定サーバー ロール **sysadmin** のメンバーであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8445b-167">This process checks whether the user is a member of the **sysadmin** fixed server role on the selected computer.</span></span>  
  
3.  <span data-ttu-id="8445b-168">**[転送先サーバーの選択]** ページで、データベースが移動またはコピーされるサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-168">From the **Select a Destination Server** page, specify the server where the database will be moved or copied.</span></span> <span data-ttu-id="8445b-169">転送先またはコピー先のサーバーと、転送元またはコピー元のサーバーに同じサーバー インスタンスを設定した場合、データベースのコピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-169">If you set the source and destination servers to the same server instance, you will make a copy of a database.</span></span> <span data-ttu-id="8445b-170">この場合、後でウィザードでデータベースの名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-170">In this case you must rename the database at a later point in the wizard.</span></span> <span data-ttu-id="8445b-171">コピー元または移動元データベースの名前をコピー先または移動先データベースの名前に使用できるのは、コピー先または移動先サーバーに名前の競合がない場合のみです。</span><span class="sxs-lookup"><span data-stu-id="8445b-171">The source database name can be used for the copied or moved database only if name conflicts do not exist on the destination server.</span></span> <span data-ttu-id="8445b-172">名前が競合する場合、コピー元または移動元のデータベース名を使用する前にコピー先または移動先サーバーの競合を手動で解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-172">If name conflicts exist, you must resolve them manually on the destination server before you can use the source database name there.</span></span>  
  
     <span data-ttu-id="8445b-173">**[転送先サーバー]**</span><span class="sxs-lookup"><span data-stu-id="8445b-173">**Destination server**</span></span>  
     <span data-ttu-id="8445b-174">データベースまたはデータベースを移動またはコピーするサーバーの名前を選択するか、参照ボタン ([.**.**.]) をクリックして移行先サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-174">Select the name of the server to which the database or databases will be moved or copied, or click the browse (**...**) button to locate a destination server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8445b-175">転送先またはコピー先のサーバーとして、クラスター化されたサーバーを選択できます。その場合、データベース コピー ウィザードは、そのクラスター化された転送先またはコピー先のサーバーの共有ドライブのみが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8445b-175">You can use a destination that is a clustered server; the Copy Database Wizard will make sure you select only shared drives on a clustered destination server.</span></span>  
  
     <span data-ttu-id="8445b-176">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-176">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="8445b-177">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントを使用して接続することをユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="8445b-177">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="8445b-178">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-178">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="8445b-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証用のユーザー名とパスワードを入力して接続することをユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="8445b-179">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="8445b-180">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="8445b-180">**User name**</span></span>  
     <span data-ttu-id="8445b-181">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="8445b-181">Enter the user name to connect with.</span></span> <span data-ttu-id="8445b-182">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-182">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="8445b-183">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="8445b-183">**Password**</span></span>  
     <span data-ttu-id="8445b-184">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8445b-184">Enter the password for the login.</span></span> <span data-ttu-id="8445b-185">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-185">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="8445b-186">**次へ**</span><span class="sxs-lookup"><span data-stu-id="8445b-186">**Next**</span></span>  
     <span data-ttu-id="8445b-187">サーバーに接続し、ユーザーを検証します。</span><span class="sxs-lookup"><span data-stu-id="8445b-187">Connect to the server and validate the user.</span></span> <span data-ttu-id="8445b-188">このプロセスでは、選択したコンピューター上でユーザーが上記の権限を所有しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8445b-188">This process checks whether the user has the permissions listed above on the selected computers.</span></span>  
  
4.  <span data-ttu-id="8445b-189">**[転送方法の選択]** ページで転送方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-189">From the **Select a Transfer Method** page, select the transfer method.</span></span>  
  
     <span data-ttu-id="8445b-190">**[デタッチ後にアタッチする方法を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-190">**Use the detach and attach method**</span></span>  
     <span data-ttu-id="8445b-191">コピー元サーバーのデータベースをデタッチし、データベース ファイル (.mdf、.ndf、.ldf) をコピー先サーバーにコピーした後、データベースをコピー先サーバーにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="8445b-191">Detach the database from the source server, copy the database files (.mdf, .ndf, and .ldf) to the destination server, and attach the database at the destination server.</span></span> <span data-ttu-id="8445b-192">主な処理はコピー元ディスクを読み取り、コピー先ディスクに書き込むだけなので、通常は高速に処理されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-192">This method is usually the faster method because the principal work is reading the source disk and writing the destination disk.</span></span> <span data-ttu-id="8445b-193">データベース内にオブジェクトを作成したり、データ ストレージ構造体を作成したりするために必要な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロジックは不要です。</span><span class="sxs-lookup"><span data-stu-id="8445b-193">No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logic is required to create objects within the database, or create data storage structures.</span></span> <span data-ttu-id="8445b-194">ただし、データベースに割り当て済みの未使用の領域が多量にある場合は、この方法では時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-194">This method can be slower, however, if the database contains a large amount of allocated but unused space.</span></span> <span data-ttu-id="8445b-195">たとえば、100 MB の割り当てで新しく作成された事実上空のデータベースの場合、5 MB のみが使用されているだけでも、全 100 MB がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="8445b-195">For instance, a new and practically empty database that is created allocating 100 MB, copies the entire 100 MB, even if only 5 MB is full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8445b-196">この方法の場合、転送中はユーザーがデータベースを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8445b-196">This method makes the database unavailable to users during the transfer.</span></span>  
  
     <span data-ttu-id="8445b-197">**[失敗した場合にソース データベースを再アタッチする]**</span><span class="sxs-lookup"><span data-stu-id="8445b-197">**If a failure occurs, reattach the source database**</span></span>  
     <span data-ttu-id="8445b-198">データベースのコピー時には、元のデータベース ファイルが必ずコピー元サーバーに再アタッチされます。</span><span class="sxs-lookup"><span data-stu-id="8445b-198">When a database is copied, the original database files are always reattached to the source server.</span></span> <span data-ttu-id="8445b-199">データベースの移動を完了できない場合に元のファイルをソース データベースに再アタッチするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8445b-199">Use this box to reattach original files to the source database if a database move cannot be completed.</span></span>  
  
     <span data-ttu-id="8445b-200">**[SQL 管理オブジェクトの方法を使用する]**</span><span class="sxs-lookup"><span data-stu-id="8445b-200">**Use the SQL Management Object method**</span></span>  
     <span data-ttu-id="8445b-201">コピー元データベースの各データベース オブジェクトの定義を読み取って、コピー先データベースに各オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8445b-201">This method reads the definition of each database object on the source database and creates each object in the destination database.</span></span> <span data-ttu-id="8445b-202">その後、コピー元テーブルのデータをコピー先テーブルに転送し、インデックスとメタデータを再作成します。</span><span class="sxs-lookup"><span data-stu-id="8445b-202">Then it transfers the data from the source tables to the destination tables, recreating indexes and metadata.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8445b-203">データベース ユーザーは転送中もデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8445b-203">Database users can continue to access the database during the transfer.</span></span>  
  
5.  <span data-ttu-id="8445b-204">**[データベースの選択]** ページで、サーバーからサーバーへ移動またはコピーする 1 つ以上のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-204">From the **Select Database** page, select the database or databases you want to move or copy from the source server to the destination server.</span></span> <span data-ttu-id="8445b-205">このトピックの「開始する前に」セクションの「[制限事項と制約](#Restrictions)事項」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8445b-205">See [Limitations and Restrictions](#Restrictions) in the 'Before You Begin' section of this topic.</span></span>  
  
     <span data-ttu-id="8445b-206">**移動**</span><span class="sxs-lookup"><span data-stu-id="8445b-206">**Move**</span></span>  
     <span data-ttu-id="8445b-207">データベースが移動先サーバーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-207">Move the database to the destination server.</span></span>  
  
     <span data-ttu-id="8445b-208">**コピー**</span><span class="sxs-lookup"><span data-stu-id="8445b-208">**Copy**</span></span>  
     <span data-ttu-id="8445b-209">データベースがコピー先サーバーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="8445b-209">Copy the database to the destination server.</span></span>  
  
     <span data-ttu-id="8445b-210">**ソース**</span><span class="sxs-lookup"><span data-stu-id="8445b-210">**Source**</span></span>  
     <span data-ttu-id="8445b-211">移動またはコピー元のサーバーに存在するデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-211">Displays the databases that exist on the source server.</span></span>  
  
     <span data-ttu-id="8445b-212">**状態**</span><span class="sxs-lookup"><span data-stu-id="8445b-212">**Status**</span></span>  
     <span data-ttu-id="8445b-213">データベースを移動できる場合は、 **[OK]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-213">Displays **OK** if the database can be moved.</span></span> <span data-ttu-id="8445b-214">データベースを移動できない場合はその理由が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-214">Otherwise displays the reason why the database cannot be moved.</span></span>  
  
     <span data-ttu-id="8445b-215">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="8445b-215">**Refresh**</span></span>  
     <span data-ttu-id="8445b-216">データベースの一覧が更新されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-216">Refresh the list of databases.</span></span>  
  
     <span data-ttu-id="8445b-217">**次へ**</span><span class="sxs-lookup"><span data-stu-id="8445b-217">**Next**</span></span>  
     <span data-ttu-id="8445b-218">検証プロセスが開始され、次の画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-218">Start the validation process, and then move to the next screen.</span></span>  
  
6.  <span data-ttu-id="8445b-219">**[転送先データベースの構成]** ページで、データベース名を必要に応じて変更し、データベース ファイルの場所と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-219">From the **Configure Destination Database** page, change the database name if appropriate and specify the location and names of the database files.</span></span> <span data-ttu-id="8445b-220">このページは、移動またはコピーするデータベースごとに一度表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-220">This page appears once for each database being moved or copied.</span></span>  
  
7.  <span data-ttu-id="8445b-221">**[データベース オブジェクトの選択]** ページで、移動操作またはコピー操作の対象となるオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-221">From the **Select Database Objects** page, select the objects to include in the move or copy operation.</span></span> <span data-ttu-id="8445b-222">このページは、移動元のサーバーと移動先のサーバーが異なる場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-222">This page is only available when the source and destination are different servers.</span></span> <span data-ttu-id="8445b-223">オブジェクトを操作の対象にするには、 **[使用可能な関連オブジェクト]** ボックスでオブジェクト名をクリックした後、 **>>** ボタンをクリックして **[選択した関連オブジェクト]** ボックスにオブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="8445b-223">To include an object, click the object name in the **Available related objects** box, and then click the **>>** button to move the object to the **Selected related objects** box.</span></span> <span data-ttu-id="8445b-224">オブジェクトを除外するには、[**選択した関連オブジェクト**] ボックスでオブジェクト名をクリックし、ボタンをクリックして [ **<\<** **使用可能な関連オブジェクト**] ボックスにオブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="8445b-224">To exclude an object, click the object name in the **Selected related objects** box, and then click the **<\<** button to move the object to the **Available related objects** box.</span></span> <span data-ttu-id="8445b-225">既定では、選択したそれぞれの種類のオブジェクトがすべて転送されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-225">By default all objects of each selected type are transferred.</span></span> <span data-ttu-id="8445b-226">特定の種類のオブジェクトを個別に選択するには、 **[選択した関連オブジェクト]** ボックスの横にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8445b-226">To choose individual objects of any type, click the ellipsis button next to any object type in the **Selected related objects** box.</span></span> <span data-ttu-id="8445b-227">ここで開くダイアログ ボックスを使用して、オブジェクトを個別に選択できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-227">This opens a dialog box where you can select individual objects.</span></span>  
  
     <span data-ttu-id="8445b-228">**[ログイン] (実行時のすべてのログイン)**</span><span class="sxs-lookup"><span data-stu-id="8445b-228">**Logins (All logins at run time)**</span></span>  
     <span data-ttu-id="8445b-229">移動またはコピー操作でのログインが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8445b-229">Include logins in the move or copy operation.</span></span> <span data-ttu-id="8445b-230">既定で選択されています。</span><span class="sxs-lookup"><span data-stu-id="8445b-230">Selected by default.</span></span>  
  
     <span data-ttu-id="8445b-231">**[master データベースからのストアド プロシージャ]**</span><span class="sxs-lookup"><span data-stu-id="8445b-231">**Stored procedures from master database**</span></span>  
     <span data-ttu-id="8445b-232">移動操作またはコピー操作で、 **master**データベースのストアドプロシージャを含めます。</span><span class="sxs-lookup"><span data-stu-id="8445b-232">Include stored procedures from the **master** database in the move or copy operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8445b-233">拡張ストアド プロシージャおよび関連する DLL は、自動コピーの対象になりません。</span><span class="sxs-lookup"><span data-stu-id="8445b-233">Extended stored procedures and their associated DLLs are not eligible for automated copy.</span></span>  
  
     <span data-ttu-id="8445b-234">**SQL Server エージェント ジョブ**</span><span class="sxs-lookup"><span data-stu-id="8445b-234">**SQL Server Agent jobs**</span></span>  
     <span data-ttu-id="8445b-235">移動操作またはコピー操作で**msdb**データベースからのジョブを含めます。</span><span class="sxs-lookup"><span data-stu-id="8445b-235">Include jobs from the **msdb** database in the move or copy operation.</span></span>  
  
     <span data-ttu-id="8445b-236">**ユーザー定義エラーメッセージ**</span><span class="sxs-lookup"><span data-stu-id="8445b-236">**User-defined error messages**</span></span>  
     <span data-ttu-id="8445b-237">ユーザー定義のエラー メッセージを移動またはコピー操作の対象にします。</span><span class="sxs-lookup"><span data-stu-id="8445b-237">Include user-defined error messages in the move or copy operation.</span></span>  
  
     <span data-ttu-id="8445b-238">**エンドポイント**</span><span class="sxs-lookup"><span data-stu-id="8445b-238">**Endpoints**</span></span>  
     <span data-ttu-id="8445b-239">ソース データベースに定義されているエンドポイントを対象にします。</span><span class="sxs-lookup"><span data-stu-id="8445b-239">Include endpoints defined in the source database.</span></span>  
  
     <span data-ttu-id="8445b-240">**フルテキストカタログ**</span><span class="sxs-lookup"><span data-stu-id="8445b-240">**Full-text catalog**</span></span>  
     <span data-ttu-id="8445b-241">ソース データベースのフルテキスト カタログを対象にします。</span><span class="sxs-lookup"><span data-stu-id="8445b-241">Include full-text catalogs from the source database.</span></span>  
  
     <span data-ttu-id="8445b-242">**SSIS パッケージ**</span><span class="sxs-lookup"><span data-stu-id="8445b-242">**SSIS Package**</span></span>  
     <span data-ttu-id="8445b-243">ソース データベースに定義されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを対象にします。</span><span class="sxs-lookup"><span data-stu-id="8445b-243">Include [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages defined in the source database.</span></span>  
  
     <span data-ttu-id="8445b-244">**説明**</span><span class="sxs-lookup"><span data-stu-id="8445b-244">**Description**</span></span>  
     <span data-ttu-id="8445b-245">オブジェクトの説明。</span><span class="sxs-lookup"><span data-stu-id="8445b-245">A description of the object.</span></span>  
  
8.  <span data-ttu-id="8445b-246">**[転送元のデータベース ファイルの場所]** ページで、転送元サーバー上のデータベース ファイルが格納されているファイル システム共有を指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-246">From the **Location of Source Database Files** page, specify a file system share that contains the database files on the source server.</span></span> <span data-ttu-id="8445b-247">転送元と転送先のサーバー インスタンスが異なるコンピューター上に存在する場合、この設定は必須です。</span><span class="sxs-lookup"><span data-stu-id="8445b-247">This is required if the source and destination server instances are on different computers.</span></span>  
  
     <span data-ttu-id="8445b-248">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="8445b-248">**Database**</span></span>  
     <span data-ttu-id="8445b-249">移動される各データベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="8445b-249">Displays the name of each database being moved.</span></span>  
  
     <span data-ttu-id="8445b-250">**[フォルダーの場所]**</span><span class="sxs-lookup"><span data-stu-id="8445b-250">**Folder location**</span></span>  
     <span data-ttu-id="8445b-251">ファイル システム上にあるソース データベース ファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-251">Specify the location of the source database files on the file system.</span></span>  
  
     <span data-ttu-id="8445b-252">例 : C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span><span class="sxs-lookup"><span data-stu-id="8445b-252">For example: C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span></span>  
  
     <span data-ttu-id="8445b-253">**[転送元のサーバーでのファイル共有]**</span><span class="sxs-lookup"><span data-stu-id="8445b-253">**File share on source server**</span></span>  
     <span data-ttu-id="8445b-254">ソース データベース ファイルの場所をファイル共有のパスとして指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-254">Specify the location of the source database files as a path of a file share.</span></span>  
  
     <span data-ttu-id="8445b-255">例: " \\ \\ *server_name*\c $ Server\MSSQL110." SQLMSSQLSERVER\MSSQL\Data</span><span class="sxs-lookup"><span data-stu-id="8445b-255">For example: "\\\\*server_name*\C$\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\Data</span></span>  
  
9. <span data-ttu-id="8445b-256">データベースを転送するための [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージがデータベース コピー ウィザードによって作成されます。 **[パッケージの構成]** ページで、適宜パッケージをカスタマイズしてください。</span><span class="sxs-lookup"><span data-stu-id="8445b-256">The Copy Database Wizard creates a [!INCLUDE[ssIS](../../includes/ssis-md.md)] package to transfer the database From the **Configure the Package** page, customize the package if appropriate.</span></span>  
  
     <span data-ttu-id="8445b-257">**[パッケージの場所]**</span><span class="sxs-lookup"><span data-stu-id="8445b-257">**Package location**</span></span>  
     <span data-ttu-id="8445b-258">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを書き込む場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-258">Displays where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package will be written.</span></span>  
  
     <span data-ttu-id="8445b-259">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="8445b-259">**Package name**</span></span>  
     <span data-ttu-id="8445b-260">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8445b-260">Enter a name for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
     <span data-ttu-id="8445b-261">**[ログ オプション]**</span><span class="sxs-lookup"><span data-stu-id="8445b-261">**Logging options**</span></span>  
     <span data-ttu-id="8445b-262">ログ情報を Windows イベント ログとして保存するか、テキスト ファイルとして保存するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-262">Select whether to store the logging information in the Windows event log, or in a text file.</span></span>  
  
     <span data-ttu-id="8445b-263">**[エラー ログ ファイルのパス]**</span><span class="sxs-lookup"><span data-stu-id="8445b-263">**Error log file path**</span></span>  
     <span data-ttu-id="8445b-264">ログ ファイルの場所のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-264">Provide a path for the location of the log file.</span></span> <span data-ttu-id="8445b-265">このオプションは、テキスト ファイルのログのオプションが選択されている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-265">This option is only available if the text file logging option is selected.</span></span>  
  
10. <span data-ttu-id="8445b-266">**[パッケージのスケジュール設定]** ページで、移動操作またはコピー操作をいつ開始するのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8445b-266">From the **Schedule the Package** page, specify when you want the move or copy operation to start.</span></span> <span data-ttu-id="8445b-267">システム管理者でない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSIS) パッケージ実行サブシステムへのアクセス権がある [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エージェント プロキシ アカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8445b-267">If you are not a system administrator, you must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy account that has access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Package execution subsystem.</span></span>  
  
     <span data-ttu-id="8445b-268">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="8445b-268">**Run immediately**</span></span>  
     <span data-ttu-id="8445b-269">[**次へ**] をクリックした後、移動またはコピー操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="8445b-269">Start the move or copy operation after you click **Next**.</span></span>  
  
     <span data-ttu-id="8445b-270">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="8445b-270">**Schedule**</span></span>  
     <span data-ttu-id="8445b-271">移動操作またはコピー操作を後で開始します。</span><span class="sxs-lookup"><span data-stu-id="8445b-271">Start the move or copy operation later.</span></span> <span data-ttu-id="8445b-272">説明ボックスには、現在のスケジュール設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-272">The current schedule settings appear in the description box.</span></span> <span data-ttu-id="8445b-273">スケジュールを変更するには、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8445b-273">To change the schedule, click **Change**.</span></span>  
  
     <span data-ttu-id="8445b-274">**変更**</span><span class="sxs-lookup"><span data-stu-id="8445b-274">**Change**</span></span>  
     <span data-ttu-id="8445b-275">[**新しいジョブスケジュール**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="8445b-275">Open the **New Job Schedule** dialog box.</span></span>  
  
     <span data-ttu-id="8445b-276">**[Integration Services プロキシ アカウント]**</span><span class="sxs-lookup"><span data-stu-id="8445b-276">**Integration Services proxy account**</span></span>  
     <span data-ttu-id="8445b-277">利用可能なプロキシ アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="8445b-277">Select an available proxy account.</span></span> <span data-ttu-id="8445b-278">転送をスケジュールするには、1 つ以上のプロキシ アカウントをユーザーが使用できる状態であり、SQL Server Integration Services パッケージ実行用サブシステムに対する権限がこれらのアカウントに対して構成されている必要があります。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8445b-278">To schedule the transfer, there must be at least one proxy account available to the user, configured with permission to the **SQL Server Integration Services package execution** subsystem.</span></span>  
  
     <span data-ttu-id="8445b-279">パッケージ実行用のプロキシアカウントを作成するに [!INCLUDE[ssIS](../../includes/ssis-md.md)] は、オブジェクトエクスプローラーで [ **SQL Server エージェント**] を展開し、[**プロキシ**] を展開します。次に、[ **SSIS パッケージ実行**] を右クリックし、[**新しいプロキシ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8445b-279">To create a proxy account for [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution, in Object Explorer, expand **SQL Server Agent**, expand **Proxies**, right-click **SSIS Package Execution**, and then click **New Proxy**.</span></span>  
  
     <span data-ttu-id="8445b-280">**sysadmin** 固定サーバー ロールのメンバーは、必要なアクセス許可のある **SQL Server エージェント サービス アカウント**を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8445b-280">Members of the **sysadmin** fixed server role can select the **SQL Server Agent Service Account**, which has the necessary permissions.</span></span>  
  
11. <span data-ttu-id="8445b-281">**[ウィザードの完了]** ページで、選択したオプションの概要を確認します。</span><span class="sxs-lookup"><span data-stu-id="8445b-281">From the **Complete the Wizard** page, review the summary of the selected options.</span></span> <span data-ttu-id="8445b-282">オプションを変更するには、 **[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8445b-282">Click **Back** to change an option.</span></span> <span data-ttu-id="8445b-283">**[完了]** をクリックして、データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="8445b-283">Click **Finish** to create the database.</span></span> <span data-ttu-id="8445b-284">転送中は、 **データベース コピー ウィザード** の実行に関する状態情報が **[操作を実行しています]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-284">During the transfer, the **Performing operation** page monitors status information about the execution of the **Copy Database Wizard**.</span></span>  
  
     <span data-ttu-id="8445b-285">**操作**</span><span class="sxs-lookup"><span data-stu-id="8445b-285">**Action**</span></span>  
     <span data-ttu-id="8445b-286">実行されている各アクションが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-286">Lists each action being performed.</span></span>  
  
     <span data-ttu-id="8445b-287">**状態**</span><span class="sxs-lookup"><span data-stu-id="8445b-287">**Status**</span></span>  
     <span data-ttu-id="8445b-288">アクションが全体として成功したか、失敗したかを示します。</span><span class="sxs-lookup"><span data-stu-id="8445b-288">Indicates whether the action as a whole succeeded or failed.</span></span>  
  
     <span data-ttu-id="8445b-289">**Message**</span><span class="sxs-lookup"><span data-stu-id="8445b-289">**Message**</span></span>  
     <span data-ttu-id="8445b-290">各ステップで返されるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-290">Provides any messages returned from each step.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a><span data-ttu-id="8445b-291">補足情報: SQL Server データベースのアップグレード後</span><span class="sxs-lookup"><span data-stu-id="8445b-291">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="8445b-292">データベース コピー ウィザードを使用して、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のバージョンにアップグレードした後は、データベースが直ちに使用可能となり、自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="8445b-292">After you use the Copy Database Wizard to upgrade a database from an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="8445b-293">データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、 **"フルテキスト アップグレード オプション"** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。</span><span class="sxs-lookup"><span data-stu-id="8445b-293">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="8445b-294">アップグレード オプションが **[インポート]** または **[再構築]** に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8445b-294">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="8445b-295">インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8445b-295">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="8445b-296">なお、アップグレード オプションが **[インポート]** に設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="8445b-296">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="8445b-297">**フルテキスト アップグレード オプション** プロパティの設定の表示と変更については、「 [サーバー インスタンスでのフルテキスト検索の管理と監視](../search/manage-and-monitor-full-text-search-for-a-server-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8445b-297">For information about viewing or changing the setting of the **Full-Text Upgrade Option** property, see [Manage and Monitor Full-Text Search for a Server Instance](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).</span></span>  
  
 <span data-ttu-id="8445b-298">アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。</span><span class="sxs-lookup"><span data-stu-id="8445b-298">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="8445b-299">アップグレードされたデータベースの互換性レベルが 90 の場合、互換性レベルは 100 に設定されます。これは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされている下限の互換性レベルです。</span><span class="sxs-lookup"><span data-stu-id="8445b-299">If the compatibility level was 90 in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8445b-300">詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8445b-300">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8445b-301">参照</span><span class="sxs-lookup"><span data-stu-id="8445b-301">See Also</span></span>  
 <span data-ttu-id="8445b-302">[デタッチとアタッチを使用してデータベースをアップグレードする &#40;Transact-sql&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="8445b-302">[Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span></span>  
 [<span data-ttu-id="8445b-303">Create a SQL Server Agent Proxy</span><span class="sxs-lookup"><span data-stu-id="8445b-303">Create a SQL Server Agent Proxy</span></span>](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
