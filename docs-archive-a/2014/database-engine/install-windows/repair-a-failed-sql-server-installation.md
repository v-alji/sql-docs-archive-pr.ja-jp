---
title: SQL Server 2014 のインストールを修復する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e382137a971b3f8b23cf1d814bff9908f04150
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716582"
---
# <a name="drop-a-sql-server-2014-installation"></a><span data-ttu-id="6c872-102">SQL Server 2014 のインストールの削除</span><span class="sxs-lookup"><span data-stu-id="6c872-102">Drop a SQL Server 2014 Installation</span></span>
  <span data-ttu-id="6c872-103">修復操作は、以下のシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c872-103">Repair operation can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="6c872-104">適切にインストールした後に壊れた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを修復する。</span><span class="sxs-lookup"><span data-stu-id="6c872-104">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is corrupted after it was successfully installed.</span></span>  
  
-   <span data-ttu-id="6c872-105">新たにアップグレードされたインスタンスにインスタンス名がマップされた後、アップグレード操作のキャンセルまたは失敗が生じた場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを修復する。</span><span class="sxs-lookup"><span data-stu-id="6c872-105">Repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if the upgrade operation is cancelled or fails after the instance name is mapped to the newly-upgraded instance.</span></span>  
  
    -   <span data-ttu-id="6c872-106">概要ログに次のメッセージが表示されている場合は、失敗したアップグレード インスタンスを修復できます。</span><span class="sxs-lookup"><span data-stu-id="6c872-106">If you see the following message in the summary log, you can repair the failed upgrade instance:</span></span>  
  
         <span data-ttu-id="6c872-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアップグレードに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6c872-107">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="6c872-108">続行するには、失敗の理由を調べて問題を修正し、インストールされたシステムを修復します。"</span><span class="sxs-lookup"><span data-stu-id="6c872-108">To continue, investigate the reason for the failure, correct the problem, and then repair your installation."</span></span>  
  
    -   <span data-ttu-id="6c872-109">概要ログに次のメッセージが表示されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアンインストールして、再度インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c872-109">If you see the following message in the summary log, you need to uninstall and reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6c872-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを修復することはできません。</span><span class="sxs-lookup"><span data-stu-id="6c872-110">You cannot repair the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="6c872-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアップグレードに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6c872-111">"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade failed.</span></span> <span data-ttu-id="6c872-112">続行するには、失敗の理由を調べて問題を修正します。"</span><span class="sxs-lookup"><span data-stu-id="6c872-112">To continue, investigate the reason for the failure, correct the problem."</span></span>  
  
 <span data-ttu-id="6c872-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを修復すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6c872-113">When you repair an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="6c872-114">欠落または破損していたすべてのファイルが差し替わります。</span><span class="sxs-lookup"><span data-stu-id="6c872-114">All missing or corrupt files are replaced.</span></span>  
  
-   <span data-ttu-id="6c872-115">欠落または破損していたすべてのレジストリ キーが差し替わります。</span><span class="sxs-lookup"><span data-stu-id="6c872-115">All missing or corrupt registry keys are replaced.</span></span>  
  
-   <span data-ttu-id="6c872-116">欠落または破損していたすべての構成値が既定値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-116">All missing or invalid configuration values are set to default values.</span></span>  
  
 <span data-ttu-id="6c872-117">続行する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターに関して、次の重要な情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="6c872-117">Before you continue, for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover clusters, review the following important information:</span></span>  
  
-   <span data-ttu-id="6c872-118">修復は個々のクラスター ノードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c872-118">Repair must be run on individual cluster nodes.</span></span>  
  
-   <span data-ttu-id="6c872-119">準備操作に失敗した後でフェールオーバー クラスター ノードを修復するには、 **[ノードの削除]** を使用してから準備手順をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="6c872-119">To repair a failover cluster node after a failed Prepare operation, use **Remove node** and then perform the Prepare step again.</span></span> <span data-ttu-id="6c872-120">詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c872-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-from-the-installation-center"></a><span data-ttu-id="6c872-121">インストール センターから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の失敗したインストールを修復するには</span><span class="sxs-lookup"><span data-stu-id="6c872-121">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the Installation Center</span></span>  
  
1.  <span data-ttu-id="6c872-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ プログラム (setup.exe) を起動します。</span><span class="sxs-lookup"><span data-stu-id="6c872-122">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program (setup.exe) from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span>  
  
2.  <span data-ttu-id="6c872-123">必須コンポーネントのインストールとシステムの検証が実行された後、セットアップ プログラムによって [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-123">After prerequisites and system verification, the Setup program will display the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center page.</span></span>  
  
3.  <span data-ttu-id="6c872-124">左側のナビゲーション領域の **[メンテナンス]** をクリックし、 **[修復]** をクリックして修復操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="6c872-124">Click **Maintenance** in the left-hand navigation area, and then click **Repair** to start the repair operation.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="6c872-125">[スタート] メニューを使用してインストール センターを起動した場合は、この時点で、インストール メディアの場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c872-125">If the Installation Center was launched using the start menu, you will need to provide the location of the installation media at this time.</span></span>  
  
4.  <span data-ttu-id="6c872-126">セットアップ サポート ルールおよびセットアップ サポート ファイルのルーチンが実行されて、システムに必須コンポーネントがインストールされていること、およびコンピューターがセットアップの検証ルールに合格していることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-126">Setup support rule and file routines will run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="6c872-127">続行するには、 **[OK]** または **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c872-127">Click **OK** or **Install** to continue.</span></span>  
  
5.  <span data-ttu-id="6c872-128">[インスタンスの選択] ページで、修復するインスタンスを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c872-128">On the Select Instance page, select the instance to repair, and then click **Next** to continue.</span></span>  
  
6.  <span data-ttu-id="6c872-129">修復ルールが実行され、操作が検証されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-129">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="6c872-130">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c872-130">To continue, click **Next**.</span></span>  
  
7.  <span data-ttu-id="6c872-131">[修復の準備完了] ページで、操作を続行する準備ができたことが示されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-131">The Ready to Repair page indicates that the operation is ready to proceed.</span></span> <span data-ttu-id="6c872-132">続行するには、 **[修復]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c872-132">To continue, click **Repair**.</span></span>  
  
8.  <span data-ttu-id="6c872-133">[修復の進行状況] ページに、修復操作の進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-133">The Repair Progress page shows the status of the repair operation.</span></span> <span data-ttu-id="6c872-134">[完了] ページでは、操作が完了したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="6c872-134">The Complete page indicates that the operation is finished.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-using-command-prompt"></a><span data-ttu-id="6c872-135">コマンド プロンプトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の失敗したインストールを修復するには</span><span class="sxs-lookup"><span data-stu-id="6c872-135">To repair a failed installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Command Prompt</span></span>  
  
1.  <span data-ttu-id="6c872-136">コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c872-136">Run the following command at a command prompt:</span></span>  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6c872-137">参照</span><span class="sxs-lookup"><span data-stu-id="6c872-137">See Also</span></span>  
 <span data-ttu-id="6c872-138">[SQL Server セットアップ ログ ファイルの表示と読み取り](view-and-read-sql-server-setup-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="6c872-138">[View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md) </span></span>  
 [<span data-ttu-id="6c872-139">インストール方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="6c872-139">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
  
  
