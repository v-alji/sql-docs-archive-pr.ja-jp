---
title: SQL Server の既存のインスタンスのアンインストール (セットアップ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51d426a12a2f7f1b7bedbfb7770c4d9cb369f12b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640402"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a><span data-ttu-id="2274a-102">SQL Server の既存のインスタンスのアンインストール (セットアップ)</span><span class="sxs-lookup"><span data-stu-id="2274a-102">Uninstall an Existing Instance of SQL Server (Setup)</span></span>
  <span data-ttu-id="2274a-103">ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスタンドアロン インスタンスをアンインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2274a-103">This article describes how to uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2274a-104">また、このトピックの手順を実行してシステムを準備し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再インストールできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2274a-104">By following the steps in this topic, you also prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2274a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをアンインストールするには、サービスとしてログオンする権限を持つローカル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2274a-105">To uninstall an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be a local administrator with permission to log on as a service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2274a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによって提供されるノードの削除機能を使用して、各ノードを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="2274a-106">To uninstall a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="2274a-107">詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2274a-107">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="2274a-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアンインストールする前に、次の重要な情報について検討してください。</span><span class="sxs-lookup"><span data-stu-id="2274a-108">Consider the following important information before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="2274a-109">必要最小限の物理メモリを搭載したコンピューターから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを削除する場合、ページ ファイルのサイズが十分な大きさであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2274a-109">Before you remove [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components from a computer that has the minimum required amount of physical memory, make sure that the page file size is sufficient.</span></span> <span data-ttu-id="2274a-110">ページ ファイルのサイズは、物理メモリの 2 倍である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2274a-110">The page file size must be equal to two times the amount of physical memory.</span></span> <span data-ttu-id="2274a-111">仮想メモリが不足した状況では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の削除が不完全になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2274a-111">Insufficient virtual memory can cause an incomplete removal of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2274a-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを複数インストールしている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の最後のインスタンスがアンインストールされるときに自動的にアンインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2274a-112">If you have multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser uninstalls automatically when the last instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is uninstalled.</span></span>  
  
     <span data-ttu-id="2274a-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のすべてのコンポーネントをアンインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コントロール パネル **の** [プログラムと機能] **を使用して、** Browser コンポーネントを手動でアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2274a-113">If you want to uninstall all components of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must uninstall the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser component manually from **Programs and Features** in **Control Panel**.</span></span>  
  
### <a name="before-you-uninstall"></a><span data-ttu-id="2274a-114">アンインストールする前に</span><span class="sxs-lookup"><span data-stu-id="2274a-114">Before You Uninstall</span></span>  
  
1.  <span data-ttu-id="2274a-115">**データをバックアップする。**</span><span class="sxs-lookup"><span data-stu-id="2274a-115">**Back up your data.**</span></span> <span data-ttu-id="2274a-116">これは必須の手順ではありませんが、現在の状態で保存しておく必要のあるデータベースが存在する場合に行います。</span><span class="sxs-lookup"><span data-stu-id="2274a-116">Although this is not a required step, you might have databases that you want to save in their present state.</span></span> <span data-ttu-id="2274a-117">また、システム データベースに対して行った変更の保存が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="2274a-117">You might also want to save changes that were made to the system databases.</span></span> <span data-ttu-id="2274a-118">どのような状況でも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアンインストールする前にデータを必ずバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="2274a-118">If either situation is true, make sure that back up the data before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2274a-119">あるいは、MSSQL フォルダー以外のフォルダー内にあるすべてのデータとログ ファイルのコピーを保存してください。</span><span class="sxs-lookup"><span data-stu-id="2274a-119">Alternatively, save a copy of all the data and log files in a folder other than the MSSQL folder.</span></span> <span data-ttu-id="2274a-120">MSSQL フォルダーはアンインストール中に削除されます。</span><span class="sxs-lookup"><span data-stu-id="2274a-120">The MSSQL folder is deleted during uninstallation.</span></span>  
  
     <span data-ttu-id="2274a-121">保存する必要のあるファイルには、次のデータベース ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="2274a-121">The files that you must save include the following database files:</span></span>  
  
    -   <span data-ttu-id="2274a-122">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="2274a-122">Master.mdf</span></span>  
  
    -   <span data-ttu-id="2274a-123">Mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="2274a-123">Mastlog.ldf</span></span>  
  
    -   <span data-ttu-id="2274a-124">Model.mdf</span><span class="sxs-lookup"><span data-stu-id="2274a-124">Model.mdf</span></span>  
  
    -   <span data-ttu-id="2274a-125">Modellog.ldf</span><span class="sxs-lookup"><span data-stu-id="2274a-125">Modellog.ldf</span></span>  
  
    -   <span data-ttu-id="2274a-126">Msdbdata.mdf</span><span class="sxs-lookup"><span data-stu-id="2274a-126">Msdbdata.mdf</span></span>  
  
    -   <span data-ttu-id="2274a-127">Msdblog.ldf</span><span class="sxs-lookup"><span data-stu-id="2274a-127">Msdblog.ldf</span></span>  
  
    -   <span data-ttu-id="2274a-128">Mssqlsystemresource.mdf</span><span class="sxs-lookup"><span data-stu-id="2274a-128">Mssqlsystemresource.mdf</span></span>  
  
    -   <span data-ttu-id="2274a-129">Mssqlsustemresource.ldf</span><span class="sxs-lookup"><span data-stu-id="2274a-129">Mssqlsustemresource.ldf</span></span>  
  
    -   <span data-ttu-id="2274a-130">Tempdb.mdf</span><span class="sxs-lookup"><span data-stu-id="2274a-130">Tempdb.mdf</span></span>  
  
    -   <span data-ttu-id="2274a-131">Templog.ldf</span><span class="sxs-lookup"><span data-stu-id="2274a-131">Templog.ldf</span></span>  
  
    -   <span data-ttu-id="2274a-132">`ReportServer[$InstanceName]`(既定の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベース)。</span><span class="sxs-lookup"><span data-stu-id="2274a-132">`ReportServer[$InstanceName]` (Thisis the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default database.)</span></span>  
  
    -   <span data-ttu-id="2274a-133">ReportServer[$InstanceName]TempDB (これは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の既定の一時データベースです)</span><span class="sxs-lookup"><span data-stu-id="2274a-133">ReportServer[$InstanceName]TempDB (This is the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default temporary database.)</span></span>  
  
2.  <span data-ttu-id="2274a-134">**ローカル セキュリティ グループの削除。**</span><span class="sxs-lookup"><span data-stu-id="2274a-134">**Delete the local security groups.**</span></span> <span data-ttu-id="2274a-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアンインストールする前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントのローカル セキュリティ グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="2274a-135">Before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], delete the local security groups for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
3.  <span data-ttu-id="2274a-136">**すべての**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **サービスを停止します。**</span><span class="sxs-lookup"><span data-stu-id="2274a-136">**Stop all**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services.**</span></span> <span data-ttu-id="2274a-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアンインストールする前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスをすべて停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2274a-137">We recommend that you stop all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="2274a-138">アクティブな接続が存在すると、アンインストールに失敗する場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="2274a-138">Active connections can prevent successful uninstallation.</span></span>  
  
4.  <span data-ttu-id="2274a-139">**適切な権限を持つアカウントの使用。**</span><span class="sxs-lookup"><span data-stu-id="2274a-139">**Use an account that has the appropriate permissions.**</span></span> <span data-ttu-id="2274a-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを使用するか、同等の権限を持つアカウントを使用して、サーバーにログオンします。</span><span class="sxs-lookup"><span data-stu-id="2274a-140">Log on to the server by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account or by using an account that has equivalent permissions.</span></span> <span data-ttu-id="2274a-141">たとえば、ローカルの Administrators グループのメンバーであるアカウントを使用してサーバーにログオンできます。</span><span class="sxs-lookup"><span data-stu-id="2274a-141">For example, you can log on to the server by using an account that is a member of the local Administrators group.</span></span>  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a><span data-ttu-id="2274a-142">のインスタンスをアンインストールするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2274a-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="2274a-143">アンインストール プロセスを開始するには、 **コントロール パネル** で **[プログラムと機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2274a-143">To begin the uninstall process, go to **Control Panel** and then **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="2274a-144">右クリック **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** して [**アンインストール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2274a-144">Right click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** and select **Uninstall**.</span></span> <span data-ttu-id="2274a-145">次に、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2274a-145">Then click **Remove**.</span></span> <span data-ttu-id="2274a-146">これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="2274a-146">This starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
     <span data-ttu-id="2274a-147">セットアップ サポート ルールが実行され、コンピューターの構成が確認されます。</span><span class="sxs-lookup"><span data-stu-id="2274a-147">Setup Support Rules runs to verify your computer configuration.</span></span> <span data-ttu-id="2274a-148">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2274a-148">To continue, click **Next**.</span></span>  
  
3.  <span data-ttu-id="2274a-149">[インスタンスの選択] ページのドロップダウン ボックスを使用して、削除する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の共有機能と管理ツールだけを削除するオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2274a-149">On the Select Instance page, use the drop-down box to specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to remove, or specify the option to remove only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared features and management tools.</span></span> <span data-ttu-id="2274a-150">続行するには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2274a-150">To continue, click **Next**.</span></span>  
  
4.  <span data-ttu-id="2274a-151">[機能の選択] ページで、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスから削除する機能を指定します。</span><span class="sxs-lookup"><span data-stu-id="2274a-151">On the Select Features page, specify the features to remove from the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="2274a-152">削除ルールが実行され、操作を正常に完了できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="2274a-152">Removal rules runs to verify that the operation can complete successfully.</span></span>  
  
5.  <span data-ttu-id="2274a-153">**[削除の準備完了]** ページで、アンインストールされるコンポーネントおよび機能の一覧を確認します。</span><span class="sxs-lookup"><span data-stu-id="2274a-153">On the **Ready to Remove** page, review the list of components and features that will be uninstalled.</span></span> <span data-ttu-id="2274a-154">**[削除]** をクリックしてアンインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="2274a-154">Click **Remove** to begin uninstalling</span></span>  
  
6.  <span data-ttu-id="2274a-155">最後の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをアンインストールした直後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関連付けられたその他のプログラムがまだ **[プログラムと機能]** のプログラムの一覧に表示されています。</span><span class="sxs-lookup"><span data-stu-id="2274a-155">Immediately after you uninstall the last [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, the other programs associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will still be visible in the list of programs in **Programs and Features**.</span></span> <span data-ttu-id="2274a-156">ただし、 **[プログラムと機能]** を閉じ、次に **[プログラムと機能]** を開いたときには、プログラムの一覧は更新され、実際にインストールされているプログラムのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2274a-156">However, if you close **Programs and Features**, the next time you open **Programs and Features**, it will refresh the list of programs, to show only the ones that are actually still installed.</span></span>  
  
### <a name="if-the-uninstallation-fails"></a><span data-ttu-id="2274a-157">アンインストールが失敗した場合</span><span class="sxs-lookup"><span data-stu-id="2274a-157">If the Uninstallation Fails</span></span>  
  
1.  <span data-ttu-id="2274a-158">アンインストール プロセスが正常に完了しない場合は、アンインストールが失敗した原因となる問題の解決を試みます。</span><span class="sxs-lookup"><span data-stu-id="2274a-158">If the uninstallation process does not complete successfully, attempt to fix the problem that caused the uninstallation to fail.</span></span> <span data-ttu-id="2274a-159">アンインストールの失敗の原因を把握するには、次の記事が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2274a-159">The following articles can help you understand the cause of the failed uninstallation:</span></span>  
  
    -   [<span data-ttu-id="2274a-160">セットアップ ログ ファイルで SQL Server 2008 のセットアップの問題を特定する方法</span><span class="sxs-lookup"><span data-stu-id="2274a-160">How to identify SQL Server 2008 setup issues in the setup log files</span></span>](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [<span data-ttu-id="2274a-161">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="2274a-161">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  <span data-ttu-id="2274a-162">アンインストールが失敗した原因を解決できない場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="2274a-162">If you are unable to fix the cause of the uninstallation failure, you can contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support.</span></span> <span data-ttu-id="2274a-163">重要なファイルを誤って削除した場合など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再インストールする前に、オペレーティング システムの再インストールが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2274a-163">In some cases, such as unintentional deletion of important files, reinstalling the operating system may be required before reinstalling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2274a-164">参照</span><span class="sxs-lookup"><span data-stu-id="2274a-164">See Also</span></span>  
 [<span data-ttu-id="2274a-165">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="2274a-165">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
