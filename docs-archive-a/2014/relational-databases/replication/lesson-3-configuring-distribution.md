---
title: 'レッスン 3 : ディストリビューションの構成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 52b284b6186e599b7afe73bd37ab0a8348ec38da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739702"
---
# <a name="lesson-3-configuring-distribution"></a><span data-ttu-id="c1b90-102">レッスン 3 : ディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="c1b90-102">Lesson 3: Configuring Distribution</span></span>
  <span data-ttu-id="c1b90-103">このレッスンでは、パブリッシャー側のディストリビューションを構成し、パブリケーション データベースとディストリビューション データベースに対して必要な権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-103">In this lesson, you will configure distribution at the Publisher and set the required permissions on the publication and distribution databases.</span></span> <span data-ttu-id="c1b90-104">ディストリビューターを構成済みの場合は、このレッスンを開始する前に、パブリッシングとディストリビューションを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b90-104">If you have already configured the Distributor, you must first disable publishing and distribution before you begin this lesson.</span></span> <span data-ttu-id="c1b90-105">既存のレプリケーション トポロジを維持する必要がある場合は、このレッスンを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="c1b90-105">Do not do this if you must retain an existing replication topology.</span></span>  
  
 <span data-ttu-id="c1b90-106">パブリッシャー側のリモート ディストリビューターの構成は、このチュートリアルの対象外です。</span><span class="sxs-lookup"><span data-stu-id="c1b90-106">Configuring a Publisher with a remote Distributor is outside the scope of this tutorial.</span></span>  
  
### <a name="configuring-distribution-at-the-publisher"></a><span data-ttu-id="c1b90-107">パブリッシャー側のディストリビューションを構成するには</span><span class="sxs-lookup"><span data-stu-id="c1b90-107">Configuring distribution at the Publisher</span></span>  
  
1.  <span data-ttu-id="c1b90-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-108">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="c1b90-109">**[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューションの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-109">Right-click the **Replication** folder and click **Configure Distribution**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1b90-110">実際のサーバー名ではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **を使用して** に接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が **'localhost'** サーバーに接続できないことを示す警告とメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1b90-110">If you have connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using **localhost** rather than the actual server name you will be prompted with a warning that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is unable to connect to server **'localhost'**.</span></span> <span data-ttu-id="c1b90-111">警告ダイアログで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-111">Click **OK** on the warning dialog.</span></span> <span data-ttu-id="c1b90-112">**[サーバーへの接続]** ダイアログで、 **[サーバー名]** を **localhost** から使用しているサーバーの名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-112">In the **Connect to Server** dialog change the **Server name** from **localhost** to the name of your server.</span></span> <span data-ttu-id="c1b90-113">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-113">Click **Connect**.</span></span>  
  
     <span data-ttu-id="c1b90-114">ディストリビューション構成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-114">The Distribution Configuration Wizard launches.</span></span>  
  
3.  <span data-ttu-id="c1b90-115">[**ディストリビューター** ] ページで、[' ' を **'** _\<ServerName>_ **独自のディストリビューターとして動作させる] を選択します。SQL Server によってディストリビューションデータベースとログが作成され**、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-115">On the **Distributor** page, select **'**_\<ServerName>_**' will act as its own Distributor; SQL Server will create a distribution database and log**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c1b90-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていない場合は、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントの起動** ] ページで **[はい]** を選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが自動的に起動するように構成します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-116">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running, on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent Start** page, select **Yes**, configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically.</span></span> <span data-ttu-id="c1b90-117">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-117">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="c1b90-118">[ **\\\\** \<_Machine_Name> **スナップショットフォルダー** ] テキストボックスに「_**\repldata」と**」と入力します。ここで、 \<*Machine_Name> \* はパブリッシャーの名前です。次に、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-118">Enter **\\\\**\<_Machine_Name>_**\repldata** in the **Snapshot folder** text box, where \<*Machine_Name>\* is the name of the Publisher, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="c1b90-119">ウィザードの残りのページでは、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-119">Accept the default values on the remaining pages of the wizard.</span></span>  
  
7.  <span data-ttu-id="c1b90-120">**[完了]** をクリックしてディストリビューションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-120">Click **Finish** to enable distribution.</span></span>  
  
### <a name="setting-database-permissions-at-the-publisher"></a><span data-ttu-id="c1b90-121">パブリッシャー側のデータベース権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="c1b90-121">Setting database permissions at the Publisher</span></span>  
  
1.  <span data-ttu-id="c1b90-122">で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、[**セキュリティ**] を展開し、[**ログイン**] を右クリックして、[**新しいログイン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
2.  <span data-ttu-id="c1b90-123">[**全般**] ページで、[**検索**] をクリックし、[ \<_Machine_Name> **選択するオブジェクト名を入力**してください] ボックスに「_**\ repl_snapshot** 」と入力します。ここで、 \<*Machine_Name> \* はローカルパブリッシャーサーバーの名前です。 [**名前の確認**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1b90-123">On the **General** page, click **Search**, enter \<_Machine_Name>_**\repl_snapshot** in the **Enter the object name to select** box, where \<*Machine_Name>\* is the name of the local Publisher server, click **Check Names**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c1b90-124">[**ユーザーマッピング**] ページの [**このログインにマップ**されたユーザー] ボックスの一覧で、**ディストリビューション**とデータベースの両方を選択し [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c1b90-124">On the **User Mapping** page, in the **Users mapped to this login** list select both the **distribution** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] databases.</span></span>  
  
     <span data-ttu-id="c1b90-125">[**データベースロールのメンバーシップ**] ボックスの一覧で、 `db_owner` 両方のデータベースのログインのロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-125">In the **Database role membership** list select the `db_owner` role for the login for both databases.</span></span>  
  
4.  <span data-ttu-id="c1b90-126">**[OK]** をクリックすると、ログインが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1b90-126">Click **OK** to create the login.</span></span>  
  
5.  <span data-ttu-id="c1b90-127">手順 1. ～ 4. を繰り返して、ローカルの repl_logreader アカウントのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-127">Repeat steps 1-4 to create a login for the local repl_logreader account.</span></span> <span data-ttu-id="c1b90-128">このログインは `db_owner` 、**ディストリビューション**データベースと**AdventureWorks**データベースの固定データベースロールのメンバーであるユーザーにもマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b90-128">This login must also be mapped to users that are members of the `db_owner` fixed database role in the **distribution** and **AdventureWorks** databases.</span></span>  
  
6.  <span data-ttu-id="c1b90-129">手順 1. ～ 4. を繰り返して、ローカルの repl_distribution アカウントのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-129">Repeat steps 1-4 to create a login for the local repl_distribution account.</span></span> <span data-ttu-id="c1b90-130">このログインは、 `db_owner` **ディストリビューション**データベースの固定データベースロールのメンバーであるユーザーにマップされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b90-130">This login must be mapped to a user that is a member of the `db_owner` fixed database role in the **distribution** database.</span></span>  
  
7.  <span data-ttu-id="c1b90-131">手順 1. ～ 4. を繰り返して、ローカルの repl_merge アカウントのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1b90-131">Repeat steps 1-4 to create a login for the local repl_merge account.</span></span> <span data-ttu-id="c1b90-132">このログインは、 **ディストリビューション** データベースと **AdventureWorks** データベースのユーザーにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b90-132">This login must have user mappings in the **distribution** and **AdventureWorks** databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b90-133">参照</span><span class="sxs-lookup"><span data-stu-id="c1b90-133">See Also</span></span>  
 <span data-ttu-id="c1b90-134">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="c1b90-134">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="c1b90-135">レプリケーション エージェントのセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="c1b90-135">Replication Agent Security Model</span></span>](security/replication-agent-security-model.md)  
  
  
