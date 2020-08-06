---
title: 管理データ ウェアハウスの構成 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollection.wizard_finish.f1
- sql12.swb.dc.datacollection.wizard_maploginuser.f1
- sql12.swb.dc.datacollection.wizard_welcome.f1
- sql12.swb.dc.datacollection.wizard_choosemdw.f1
- sql12.swb.dc.datacollection.wizard_completecfg.f1
- sql12.swb.dc.datacollection.wizard_config.f1
- sql12.swb.dc.datacollection.wizard_createmdw.f1
helpviewer_keywords:
- data warehouse [SQL Server], multiple instances
- data warehouse [SQL Server], configuring
- Configure Management Data Warehouse Wizard
- management data warehouse, configuring
ms.assetid: 23a584f3-c5e1-414c-9afe-73cd7efbda4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ef4ddd518343a3076c72ecc41f9b15ddf092dc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646173"
---
# <a name="configure-the-management-data-warehouse-sql-server-management-studio"></a><span data-ttu-id="4f594-102">管理データ ウェアハウスの構成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4f594-102">Configure the Management Data Warehouse (SQL Server Management Studio)</span></span>
  <span data-ttu-id="4f594-103">このトピックでは、データ コレクターを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つまたは複数のインスタンスのデータ ストレージをサポートするように管理データ ウェアハウスを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f594-103">This topic describes how to configure the management data warehouse to support data storage on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the data collector.</span></span> <span data-ttu-id="4f594-104">対象のインスタンスは、同じサーバーまたは別々のサーバーのどちらに配置されていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4f594-104">These instances can be on the same server or on different servers.</span></span> <span data-ttu-id="4f594-105">このトピックでは、 [管理データ ウェアハウス構成ウィザード](#Wizard) のユーザー インターフェイスについても説明します。</span><span class="sxs-lookup"><span data-stu-id="4f594-105">This topic also provides descriptions of the user interface for the [Configure Data Management Warehouse Wizard](#Wizard) dialog box.</span></span> <span data-ttu-id="4f594-106">データ コレクターの構成の詳細については、「 [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f594-106">For information about configuring a data collector, see [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f594-107">システム サービス アカウント (ローカル システム、ネットワーク サービス、またはローカル サービス) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行するように構成している場合に、管理データ ウェアハウスをデータ コレクターとは別のインスタンス上に作成するときは、プロキシを使用して管理データ ウェアハウスにデータをアップロードするようにコレクション セットを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f594-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is configured to run using one of the System service accounts (Local System, Network Service, or Local Service), and the management data warehouse is created on a different instance from the data collector, you must configure collection sets to use a proxy for uploading data to the management data warehouse.</span></span>  
  
### <a name="configure-the-management-data-warehouse-on-a-single-instance-or-multiple-instances-of-ssnoversion"></a><span data-ttu-id="4f594-108">の 1 つまたは複数のインスタンスの管理データ ウェアハウスの構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f594-108">Configure the management data warehouse on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="4f594-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f594-109">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
2.  <span data-ttu-id="4f594-110">オブジェクト エクスプローラーで、 **[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="4f594-110">In Object Explorer, expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="4f594-111">**[データ コレクション]** を右クリックし、 **[タスク]** を展開して **[管理データ ウェアハウスの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f594-111">Right-click **Data Collection**, expand **Tasks**, and then click **Configure Management Data Warehouse**.</span></span>  
  
4.  <span data-ttu-id="4f594-112">[管理データ ウェアハウス構成ウィザード](#Wizard) で、管理データ ウェアハウスを作成し、ログインを構成します。次に、データ コレクションを有効化し、 **システム データ コレクション セット**を開始します。</span><span class="sxs-lookup"><span data-stu-id="4f594-112">Use the [Configure Management Data Warehouse Wizard](#Wizard) to create a management data warehouse, configure logins, enable data collection, and start the **System Data Collection Sets**.</span></span>  
  
     <span data-ttu-id="4f594-113">複数のインスタンスを構成するには、手順 5 に進みます。</span><span class="sxs-lookup"><span data-stu-id="4f594-113">To configure multiple instances, continue with step 5.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f594-114">同じ管理データ ウェアハウスを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンスにデータ コレクターがインストールされている配置では、プロキシを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f594-114">It is considered best practice to use proxies in deployments where the data collector is installed on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the same management data warehouse.</span></span>  
  
5.  <span data-ttu-id="4f594-115">別のインスタンスで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f594-115">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on another instance and do either of the following:</span></span>  
  
    -   <span data-ttu-id="4f594-116">管理データ ウェアハウス構成ウィザードを使用して、既存の管理データ ウェアハウス用にデータ コレクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="4f594-116">Use the Configure Management Data Warehouse wizard to configure data collection for the existing management data warehouse.</span></span>  
  
    -   <span data-ttu-id="4f594-117">**[データ コレクション]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f594-117">Right-click **Data Collection**, and then click **Properties**.</span></span> <span data-ttu-id="4f594-118">**[全般]** タブで、既存の管理データ ウェアハウス、およびそれがインストールされたサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f594-118">On the **General** tab, specify the existing management data warehouse and the server that it is installed on.</span></span>  
  
6.  <span data-ttu-id="4f594-119">データ コレクターを使用するすべてのデータベース インスタンスが共有管理データ ウェアハウスにデータをアップロードするように構成されるまで、手順 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4f594-119">Repeat step 5 until all the database instances that use the data collector are configured to upload data to the shared management data warehouse.</span></span>  
  
####  <a name="configure-management-data-warehouse-wizard"></a><a name="Wizard"></a> <span data-ttu-id="4f594-120">管理データ ウェアハウス構成ウィザード</span><span class="sxs-lookup"><span data-stu-id="4f594-120">Configure Management Data Warehouse Wizard</span></span>  
 <span data-ttu-id="4f594-121">**[ようこそ] ページ**</span><span class="sxs-lookup"><span data-stu-id="4f594-121">**Welcome Page**</span></span>  
  
 <span data-ttu-id="4f594-122">ようこそページは、データ コレクション構成ウィザードの開始ページです。</span><span class="sxs-lookup"><span data-stu-id="4f594-122">The Welcome page is the starting page of the Configure Data Collection Wizard.</span></span> <span data-ttu-id="4f594-123">このページを表示するかどうかは任意です。</span><span class="sxs-lookup"><span data-stu-id="4f594-123">Displaying this page is optional.</span></span>  
  
 <span data-ttu-id="4f594-124">**[次回からこの開始ページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="4f594-124">**Do not show this starting page again.**</span></span>  
 <span data-ttu-id="4f594-125">データ コレクション構成ウィザードを次回起動したときにこのページを表示しない場合にオンにします。</span><span class="sxs-lookup"><span data-stu-id="4f594-125">Select to suppress this page the next time you launch the Configure Data Collection Wizard.</span></span>  
  
 <span data-ttu-id="4f594-126">**[管理データ ウェアハウス ストレージの構成] ページ**</span><span class="sxs-lookup"><span data-stu-id="4f594-126">**Configure Management Data Warehouse Storage Page**</span></span>  
  
 <span data-ttu-id="4f594-127">このページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース サーバーと管理データ ウェアハウスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f594-127">Use this page to select a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and management data warehouse.</span></span> <span data-ttu-id="4f594-128">管理データ ウェアハウスは、収集したデータを格納するリレーショナル データベースです。</span><span class="sxs-lookup"><span data-stu-id="4f594-128">The management data warehouse is a relational database that will store collected data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f594-129">サーバー上に管理データ ウェアハウスを作成するには、適切なレベルのアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f594-129">You must have the appropriate level of permissions in order to create the management data warehouse on the server.</span></span> <span data-ttu-id="4f594-130">詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f594-130">For more information, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span> <span data-ttu-id="4f594-131">また、管理データ ウェアハウス ロール用のログインを作成するための、適切なレベルのアクセス許可も必要です。</span><span class="sxs-lookup"><span data-stu-id="4f594-131">You also must have the appropriate level of permissions to create logins for management data warehouse roles.</span></span>  
  
 <span data-ttu-id="4f594-132">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="4f594-132">**Server name**</span></span>  
 <span data-ttu-id="4f594-133">管理データ ウェアハウスをホストするサーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f594-133">Specifies the name of the server that will host the management data warehouse.</span></span>  
  
 <span data-ttu-id="4f594-134">管理データ ウェアハウスを構成する場合は常に、 **[サーバー名]** がローカル サーバー名になり、この名前を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4f594-134">When configuring a management data warehouse, **Server name** is always the name of the local server and cannot be modified.</span></span>  
  
 <span data-ttu-id="4f594-135">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="4f594-135">**Database name**</span></span>  
 <span data-ttu-id="4f594-136">収集したデータを格納するリレーショナル データベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f594-136">Specifies the relational database that will store collected data.</span></span> <span data-ttu-id="4f594-137">一覧を使用して既存のデータベースを選択するか、 **[新規作成]** をクリックし、 **[新しいデータベース]** ダイアログ ボックスを使用して新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4f594-137">Use the list to select an existing database or click **New** to create a new database using the **New Database** dialog.</span></span>  
  
 <span data-ttu-id="4f594-138">**[新規作成]** オプションはデータ コレクション セットを構成する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f594-138">The **New** option is available only when configuring a data collection set</span></span>  
  
 <span data-ttu-id="4f594-139">**[ログインとユーザーのマップ] ページ**</span><span class="sxs-lookup"><span data-stu-id="4f594-139">**Map Logins and Users Page**</span></span>  
  
 <span data-ttu-id="4f594-140">このページを使用すると、管理データ ウェアハウスのデータベース ユーザー ロールにログインをマップできます。</span><span class="sxs-lookup"><span data-stu-id="4f594-140">Use this page to map logins to database user roles for the management data warehouse.</span></span>  
  
 <span data-ttu-id="4f594-141">**[このログインにマップされたユーザー]**</span><span class="sxs-lookup"><span data-stu-id="4f594-141">**Users mapped to this login**</span></span>  
 <span data-ttu-id="4f594-142">管理データ ウェアハウスをホストするサーバーの既存のログインを表示します。</span><span class="sxs-lookup"><span data-stu-id="4f594-142">Displays the existing logins on the server that will host the management data warehouse.</span></span> <span data-ttu-id="4f594-143">各行には、編集可能な **[マップ]** チェック ボックス、 **[ログイン]** 名、およびログインの **[種類]** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4f594-143">Each row contains an editable **Map** check box, a **Login** name, and a **Type** of login.</span></span>  
  
 <span data-ttu-id="4f594-144">ログインの **[マップ]** チェック ボックスをオンにしてログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f594-144">Specify a login by selecting the **Map** checkbox for the login.</span></span>  
  
 <span data-ttu-id="4f594-145">***\<data warehouse name>* のデータベース ロール メンバーシップ**</span><span class="sxs-lookup"><span data-stu-id="4f594-145">**Database role membership for:**  *\<data warehouse name>*</span></span>  
 <span data-ttu-id="4f594-146">次のオプションの 1 つ以上についてチェック ボックスをオンにし、ログインがマップされる管理データ ウェアハウス ロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f594-146">Select the management data warehouse role that the login is mapped to by clicking the checkbox by one or more of the following options:</span></span>  
  
-   <span data-ttu-id="4f594-147">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="4f594-147">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="4f594-148">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="4f594-148">**mdw_reader**</span></span>  
  
-   <span data-ttu-id="4f594-149">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="4f594-149">**mdw_writer**</span></span>  
  
 <span data-ttu-id="4f594-150">**[新しいログイン]**</span><span class="sxs-lookup"><span data-stu-id="4f594-150">**New Login**</span></span>  
 <span data-ttu-id="4f594-151">**[ログイン - 新規作成]** ダイアログ ボックスを開いて、管理データ ウェアハウスの新しいログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f594-151">Open the **Login - New** dialog box and create a new login for the management data warehouse.</span></span>  
  
 <span data-ttu-id="4f594-152">**[ウィザードの完了] ページ**</span><span class="sxs-lookup"><span data-stu-id="4f594-152">**Complete the Wizard Page**</span></span>  
  
 <span data-ttu-id="4f594-153">このページを使用すると、データ コレクションの構成を確認して完了できます。</span><span class="sxs-lookup"><span data-stu-id="4f594-153">Use this page to verify and complete data collection configuration.</span></span> <span data-ttu-id="4f594-154">表示ウィンドウに表示されるツリーは、適用される構成と、 **[完了]** をクリックしたときに実行されるアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="4f594-154">The tree displayed in the viewing window shows what configurations will applied as well as what actions will take place when you click **Finish**.</span></span>  
  
 <span data-ttu-id="4f594-155">**[データ コレクション構成ウィザードの進行状況] ページ**</span><span class="sxs-lookup"><span data-stu-id="4f594-155">**Configure Data Collection Wizard Progress Page**</span></span>  
  
 <span data-ttu-id="4f594-156">このページを使用すると、各構成手順の結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="4f594-156">Use this page to view the results of each configuration step.</span></span>  
  
 <span data-ttu-id="4f594-157">**詳細**</span><span class="sxs-lookup"><span data-stu-id="4f594-157">**Details**</span></span>  
 <span data-ttu-id="4f594-158">各構成手順を **[詳細]** グリッド内の行として表示します。</span><span class="sxs-lookup"><span data-stu-id="4f594-158">Displays each configuration step as a row in the **Details** grid.</span></span> <span data-ttu-id="4f594-159">各行には、手順について説明する **[アクション]** 列と、手順の成功または失敗を示す **[状態]** 列があります。</span><span class="sxs-lookup"><span data-stu-id="4f594-159">Each row contains an **Action** column that describes the step, and a **Status** column that indicates the success or failure of the step.</span></span> <span data-ttu-id="4f594-160">エラーが発生した場合は、 **[メッセージ]** 列にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f594-160">If there is an error, a message appears in the **Message** column.</span></span>  
  
 <span data-ttu-id="4f594-161">**Stop**</span><span class="sxs-lookup"><span data-stu-id="4f594-161">**Stop**</span></span>  
 <span data-ttu-id="4f594-162">ウィザードの処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="4f594-162">Stop wizard processing.</span></span>  
  
 <span data-ttu-id="4f594-163">**Report**</span><span class="sxs-lookup"><span data-stu-id="4f594-163">**Report**</span></span>  
 <span data-ttu-id="4f594-164">データ コレクション構成のレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="4f594-164">View a report of the data collection configuration.</span></span> <span data-ttu-id="4f594-165">次のレポート オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4f594-165">The following report options are provided:</span></span>  
  
-   <span data-ttu-id="4f594-166">[レポートの表示]</span><span class="sxs-lookup"><span data-stu-id="4f594-166">View Report</span></span>  
  
-   <span data-ttu-id="4f594-167">[レポートをファイルに保存]</span><span class="sxs-lookup"><span data-stu-id="4f594-167">Save Report to File</span></span>  
  
-   <span data-ttu-id="4f594-168">[レポートをクリップボードにコピー]</span><span class="sxs-lookup"><span data-stu-id="4f594-168">Copy Report to Clipboard</span></span>  
  
-   <span data-ttu-id="4f594-169">[レポートを電子メールとして送信]</span><span class="sxs-lookup"><span data-stu-id="4f594-169">Send Report as E-mail</span></span>  
  
 <span data-ttu-id="4f594-170">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="4f594-170">**Close**</span></span>  
 <span data-ttu-id="4f594-171">ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4f594-171">Close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f594-172">参照</span><span class="sxs-lookup"><span data-stu-id="4f594-172">See Also</span></span>  
 <span data-ttu-id="4f594-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f594-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span></span>  
 <span data-ttu-id="4f594-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4f594-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span></span>  
 <span data-ttu-id="4f594-175">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="4f594-175">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="4f594-176">データ コレクションの管理</span><span class="sxs-lookup"><span data-stu-id="4f594-176">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
