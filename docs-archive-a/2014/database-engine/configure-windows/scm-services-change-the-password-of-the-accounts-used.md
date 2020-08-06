---
title: SQL Server によって使用されるアカウントのパスワードを変更する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7da2b5f60187d7e3060dc6616686c493c893c21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742577"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="e5570-102">SQL Server で使用されるアカウントのパスワードの変更 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="e5570-102">Change the Password of the Accounts Used by SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="e5570-103">このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] エージェントによって使用されるアカウントのパスワードを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5570-103">This topic describes how to change the password of the accounts used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="e5570-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、セットアップ時に最初に指定される資格情報を使用して、コンピューター上でサービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="e5570-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent run on a computer as a service using credentials that are initially provided during setup.</span></span> <span data-ttu-id="e5570-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがドメイン アカウントで実行されていて、そのアカウントのパスワードが変更された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されているパスワードを新しいパスワードに更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5570-105">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running under a domain account and the password for that account is changed, the password used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be updated to the new password.</span></span> <span data-ttu-id="e5570-106">パスワードを更新しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は一部のドメイン リソースにアクセスできなくなる可能性があります。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が停止すると、パスワードを更新するまでサービスが再開されません。</span><span class="sxs-lookup"><span data-stu-id="e5570-106">If the password is not updated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may lose access to some domain resources and if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops, the service will not restart until the password is updated.</span></span>  
  
 <span data-ttu-id="e5570-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワードを変更するには、「 [[パスワードの有効期限が切れました]](../password-expired.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5570-107">To change [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication passwords, see [Password Expired](../password-expired.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e5570-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="e5570-108">Before You Begin</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e5570-109">構成マネージャーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの設定を変更するように設計および承認されたツールです。</span><span class="sxs-lookup"><span data-stu-id="e5570-109">Configuration Manager is the tool designed and authorized to change the settings of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="e5570-110">Windows サービス コントロール マネージャー ( **services.msc** ) アプリケーションを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスを変更すると、必要なすべての設定が変更されず、サービスが適切に機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5570-110">Changing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service by using the Windows Service Control Manager (**services.msc**) application does not always change all of the necessary settings and might prevent the service from functioning properly.</span></span> <span data-ttu-id="e5570-111">ただし、クラスター環境では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用してアクティブ ノードのパスワードを変更した後、サービス コントロール マネージャーを使用してパッシブ ノードでパスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5570-111">However, in a clustered environment, after changing the password on the active node by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, you must change the password on the passive node by using the Service Control Manager.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e5570-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e5570-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e5570-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="e5570-113">Permissions</span></span>  
 <span data-ttu-id="e5570-114">サービスで使用されるパスワードを変更するには、コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5570-114">You must be an administrator of the computer to change the password used by a service.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e5570-115">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="e5570-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a><span data-ttu-id="e5570-116">SQL Server (データベース エンジン) サービスで使用されるパスワードを変更するには</span><span class="sxs-lookup"><span data-stu-id="e5570-116">To change the password used by the SQL Server (Database Engine) service</span></span>  
  
1.  <span data-ttu-id="e5570-117">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-117">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5570-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="e5570-118">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="e5570-119">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="e5570-119">**Windows 10**:</span></span>  
    >          <span data-ttu-id="e5570-120">Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="e5570-120">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="e5570-121">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e5570-121">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="e5570-122">SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="e5570-122">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="e5570-123">Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-123">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="e5570-124">Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-124">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="e5570-125">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="e5570-125">**Windows 8**:</span></span>  
    >          <span data-ttu-id="e5570-126">Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 \*\*SQLServerManager \<version> \*\* 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e5570-126">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="e5570-127">SQL Server 構成マネージャーで **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-127">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="e5570-128">詳細ペインで **[SQL Server (** \<instancename> **)]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-128">In the details pane, right-click **SQL Server (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e5570-129">**[SQL Server (** \<instancename> **) のプロパティ]** ダイアログ ボックスの [ログオン] タブで、 **[アカウント名]** ボックスに表示されるアカウントの新しいパスワードを **[パスワード]** ボックスと **[パスワードの確認入力]** ボックスに入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-129">In the **SQL Server (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e5570-130">パスワードは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="e5570-130">The password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a><span data-ttu-id="e5570-131">SQL Server エージェント サービスで使用されるパスワードを変更するには</span><span class="sxs-lookup"><span data-stu-id="e5570-131">To change the password used by the SQL Server Agent service</span></span>  
  
1.  <span data-ttu-id="e5570-132">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-132">Click the **Start** button, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="e5570-133">SQL Server 構成マネージャーで **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-133">In SQL Server Configuration Manager, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="e5570-134">詳細ペインで **[SQL Server エージェント (** \<instancename> **)]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-134">In the details pane, right-click **SQL Server Agent (**\<instancename>**)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e5570-135">**[SQL Server エージェント (** \<instancename> **) のプロパティ]** ダイアログ ボックスの [ログオン] タブで、 **[アカウント名]** ボックスに表示されるアカウントの新しいパスワードを **[パスワード]** ボックスと **[パスワードの確認入力]** ボックスに入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5570-135">In the **SQL Server Agent (**\<instancename>**) Properties** dialog box, on the Log On tab, for the account listed in the **Account Name** box, type the new password in the **Password** and **Confirm Password** boxes, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e5570-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動しなくてもパスワードがすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="e5570-136">On a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the password takes effect immediately, without restarting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e5570-137">クラスター インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースをオフラインにする場合があり、再起動が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e5570-137">On a clustered instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline, and require a restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5570-138">参照</span><span class="sxs-lookup"><span data-stu-id="e5570-138">See Also</span></span>  
 [<span data-ttu-id="e5570-139">サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="e5570-139">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
