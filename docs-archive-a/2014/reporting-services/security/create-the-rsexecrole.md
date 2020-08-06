---
title: RSExecRole を作成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RSExecRole
ms.assetid: 7ac17341-df7e-4401-870e-652caa2859c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0037ef0c4d7a949b5a30bb45356613f6114db130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715081"
---
# <a name="create-the-rsexecrole"></a><span data-ttu-id="669f0-102">RSExecRole を作成する</span><span class="sxs-lookup"><span data-stu-id="669f0-102">Create the RSExecRole</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="669f0-103">では、`RSExecRole` と呼ばれる定義済みのデータベース ロールを使用して、レポート サーバー データベースに対するレポート サーバーの権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-103">uses a predefined database role called `RSExecRole` to grant report server permissions to the report server database.</span></span> <span data-ttu-id="669f0-104">ロールは、 `RSExecRole` レポートサーバーデータベースと共に自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-104">The `RSExecRole` role is created automatically with the report server database.</span></span> <span data-ttu-id="669f0-105">原則として、このロールを変更したり、他のユーザーをこのロールに割り当てたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="669f0-105">As a rule, you should never modify it or assign other users to the role.</span></span> <span data-ttu-id="669f0-106">ただし、レポートサーバーデータベースを新規または別のに移動する場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 、MASTER および MSDB システムデータベースでロールを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-106">However, when you move a report server database to a new or different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)], must re-create the role in the Master and MSDB system databases.</span></span>

 <span data-ttu-id="669f0-107">ここで説明する手順に従って、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="669f0-107">Using the following instructions, you will perform the following steps:</span></span>

-   <span data-ttu-id="669f0-108">master システム データベースでの `RSExecRole` の作成と準備</span><span class="sxs-lookup"><span data-stu-id="669f0-108">Create and provision the `RSExecRole` in the Master system database.</span></span>

-   <span data-ttu-id="669f0-109">MSDB システム データベースでの `RSExecRole` の作成と準備</span><span class="sxs-lookup"><span data-stu-id="669f0-109">Create and provision the `RSExecRole` in the MSDB system database.</span></span>

> [!NOTE]
>  <span data-ttu-id="669f0-110">ここで説明する手順は、レポート サーバー データベースを準備する方法としてスクリプトの実行や WMI コードの作成を考えていないユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="669f0-110">The instructions in this topic are intended for users who do not want to run a script or write WMI code to provision the report server database.</span></span> <span data-ttu-id="669f0-111">大規模な配置を管理していて、データベースを定期的に移動する予定がある場合は、上記の操作を自動的に実行するスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-111">If you manage a large deployment and will be moving databases routinely, you should write a script to automate these steps.</span></span> <span data-ttu-id="669f0-112">詳細については、「 [Reporting Service WMI プロバイダーへのアクセス](../tools/access-the-reporting-services-wmi-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="669f0-112">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="669f0-113">開始する前に</span><span class="sxs-lookup"><span data-stu-id="669f0-113">Before you start</span></span>

-   <span data-ttu-id="669f0-114">データベースを移動した後に復元できるように、暗号化キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="669f0-114">Back up the encryption keys so that you can restore them after the database is moved.</span></span> <span data-ttu-id="669f0-115">この手順は `RSExecRole` の作成と準備には直接影響しませんが、作業を確認するためにはキーのバックアップが必要です。</span><span class="sxs-lookup"><span data-stu-id="669f0-115">This is step does not directly affect your ability to create and provision the `RSExecRole`, but you must have a backup of the keys in order to verify your work.</span></span> <span data-ttu-id="669f0-116">詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="669f0-116">For more information, see [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span>

-   <span data-ttu-id="669f0-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスでの `sysadmin` 権限を持つユーザー アカウントでログオンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="669f0-117">Verify you are logged on as a user account that has `sysadmin` permissions on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>

-   <span data-ttu-id="669f0-118">使用する予定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに [!INCLUDE[ssDE](../../../includes/ssde-md.md)] エージェント サービスがインストールされ、実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="669f0-118">Verify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is installed and running on the instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that you plan to use.</span></span>

-   <span data-ttu-id="669f0-119">reportservertempdb および reportserver データベースをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="669f0-119">Attach the reportservertempdb and reportserver databases.</span></span> <span data-ttu-id="669f0-120">実際のロールを作成するためにデータベースをアタッチする必要はありませんが、作業を確認する場合は事前にデータベースをアタッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-120">You are not required to attach the databases to create the actual role, but they must be attached before you can test your work.</span></span>

 <span data-ttu-id="669f0-121">`RSExecRole` を手動で作成する手順は、レポート サーバー インストールの移行というコンテキストで使用されることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="669f0-121">The instructions for manually creating the `RSExecRole` are intended to be used within the context of migrating a report server installation.</span></span> <span data-ttu-id="669f0-122">レポート サーバー データベースのバックアップや移動などの重要なタスクは、このトピックでは取り上げませんが、データベース エンジンのドキュメントで説明されています。</span><span class="sxs-lookup"><span data-stu-id="669f0-122">Important tasks such as backing up and moving the report server database are not addressed in this topic, but are documented in the Database Engine documentation.</span></span>

## <a name="create-rsexecrole-in-master"></a><span data-ttu-id="669f0-123">master での RSExecRole の作成</span><span class="sxs-lookup"><span data-stu-id="669f0-123">Create RSExecRole in Master</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="669f0-124">では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスの拡張ストアド プロシージャを使用して、スケジュールされた操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="669f0-124">uses extended stored procedures for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service to support scheduled operations.</span></span> <span data-ttu-id="669f0-125">次の手順では、プロシージャの実行権限を `RSExecRole` ロールに付与する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="669f0-125">The following steps explain how to grant Execute permissions for the procedures to the `RSExecRole` role.</span></span>

#### <a name="to-create-rsexecrole-in-the-master-system-database-using-management-studio"></a><span data-ttu-id="669f0-126">Management Studio を使用して master システム データベースに RSExecRole を作成するには</span><span class="sxs-lookup"><span data-stu-id="669f0-126">To create RSExecRole in the Master system database using Management Studio</span></span>

1.  <span data-ttu-id="669f0-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を起動し、レポート サーバー データベースをホストする [!INCLUDE[ssDE](../../../includes/ssde-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="669f0-127">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that hosts the report server database.</span></span>

2.  <span data-ttu-id="669f0-128">**[データベース]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-128">Open **Databases**.</span></span>

3.  <span data-ttu-id="669f0-129">**[システム データベース]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-129">Open **System Databases**.</span></span>

4.  <span data-ttu-id="669f0-130">`Master`を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-130">Open `Master`.</span></span>

5.  <span data-ttu-id="669f0-131">**[セキュリティ]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-131">Open **Security**.</span></span>

6.  <span data-ttu-id="669f0-132">**[ロール]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-132">Open **Roles**.</span></span>

7.  <span data-ttu-id="669f0-133">**[データベース ロール]** を右クリックして **[新しいデータベース ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-133">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="669f0-134">[全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-134">The General page appears.</span></span>

8.  <span data-ttu-id="669f0-135">[**ロール名**] に「」と入力 `RSExecRole` します。</span><span class="sxs-lookup"><span data-stu-id="669f0-135">In **Role name**, type `RSExecRole`.</span></span>

9. <span data-ttu-id="669f0-136">**[所有者]** に「 **DBO**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="669f0-136">In **Owner**, type **DBO**.</span></span>

10. <span data-ttu-id="669f0-137">**[セキュリティ保護可能なリソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-137">Click **Securables**.</span></span>

11. <span data-ttu-id="669f0-138">**[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-138">Click **Search**.</span></span> <span data-ttu-id="669f0-139">**[オブジェクトの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-139">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="669f0-140">既定では、 **[特定のオブジェクト]** オプションが選択されています。</span><span class="sxs-lookup"><span data-stu-id="669f0-140">The **Specific Objects** option is selected by default.</span></span>

12. <span data-ttu-id="669f0-141">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-141">Click **OK**.</span></span> <span data-ttu-id="669f0-142">**[オブジェクトの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-142">The **Select Objects** dialog box appears.</span></span>

13. <span data-ttu-id="669f0-143">**[オブジェクトの種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-143">Click **Object Types**.</span></span>

14. <span data-ttu-id="669f0-144">**[拡張ストアド プロシージャ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-144">Click **Extended Stored Procedures**.</span></span>

15. <span data-ttu-id="669f0-145">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-145">Click **OK**.</span></span>

16. <span data-ttu-id="669f0-146">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-146">Click **Browse**.</span></span>

17. <span data-ttu-id="669f0-147">拡張ストアド プロシージャの一覧を下にスクロールし、以下を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-147">Scroll down the list of extended stored procedures and select the following:</span></span>

    1.  <span data-ttu-id="669f0-148">xp_sqlagent_enum_jobs</span><span class="sxs-lookup"><span data-stu-id="669f0-148">xp_sqlagent_enum_jobs</span></span>

    2.  <span data-ttu-id="669f0-149">xp_sqlagent_is_starting</span><span class="sxs-lookup"><span data-stu-id="669f0-149">xp_sqlagent_is_starting</span></span>

    3.  <span data-ttu-id="669f0-150">xp_sqlagent_notify</span><span class="sxs-lookup"><span data-stu-id="669f0-150">xp_sqlagent_notify</span></span>

18. <span data-ttu-id="669f0-151">**[OK]** をクリックし、もう一度 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-151">Click **OK**, and the click **OK** again.</span></span>

19. <span data-ttu-id="669f0-152">**[実行]** 行の **[許可]** 列で、チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-152">In the **Execute** row, in the **Grant** column, click the check box, and then click **OK**.</span></span>

20. <span data-ttu-id="669f0-153">残りの各ストアド プロシージャに同じ操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="669f0-153">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="669f0-154">`RSExecRole` には、3 つのストアド プロシージャすべてに対する実行権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-154">`RSExecRole` must be granted Execute permissions for all three stored procedures.</span></span>

 <span data-ttu-id="669f0-155">![データベース ロールのプロパティ ページ](../media/rsexecroledbproperties.gif "データベース ロールのプロパティ ページ")</span><span class="sxs-lookup"><span data-stu-id="669f0-155">![Database Role Properties page](../media/rsexecroledbproperties.gif "Database Role Properties page")</span></span>

## <a name="create-rsexecrole-in-msdb"></a><span data-ttu-id="669f0-156">MSDB での RSExecRole の作成</span><span class="sxs-lookup"><span data-stu-id="669f0-156">Create RSExecRole in MSDB</span></span>
 <span data-ttu-id="669f0-157">Reporting Services は、スケジュールされた操作をサポートするために、SQL Server エージェント サービスのストアド プロシージャを使用し、システム テーブルからジョブ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="669f0-157">Reporting Services uses stored procedures for SQL Server Agent service and retrieves job information from system tables to support scheduled operations.</span></span> <span data-ttu-id="669f0-158">次の手順では、プロシージャに対する実行権限およびテーブルでの選択権限を RSExecRole に付与する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="669f0-158">The following steps explain how to grant Execute permissions for the procedures and Select permissions on the tables to the RSExecRole.</span></span>

#### <a name="to-create-rsexecrole-in-the-msdb-system-database"></a><span data-ttu-id="669f0-159">MSDB システム データベースで RSExecRole を作成するには</span><span class="sxs-lookup"><span data-stu-id="669f0-159">To create RSExecRole in the MSDB system database</span></span>

1.  <span data-ttu-id="669f0-160">MSDB のストアド プロシージャとテーブルに対する権限を付与する場合は、同様の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="669f0-160">Repeat similar steps for granting permissions to stored procedures and tables in MSDB.</span></span> <span data-ttu-id="669f0-161">手順を簡素化するために、ストアド プロシージャとテーブルを別々に準備します。</span><span class="sxs-lookup"><span data-stu-id="669f0-161">To simplify the steps, you will provision the stored procedures and tables separately.</span></span>

2.  <span data-ttu-id="669f0-162">`MSDB`を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-162">Open `MSDB`.</span></span>

3.  <span data-ttu-id="669f0-163">**[セキュリティ]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-163">Open **Security**.</span></span>

4.  <span data-ttu-id="669f0-164">**[ロール]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="669f0-164">Open **Roles**.</span></span>

5.  <span data-ttu-id="669f0-165">**[データベース ロール]** を右クリックして **[新しいデータベース ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-165">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="669f0-166">[全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-166">The General page appears.</span></span>

6.  <span data-ttu-id="669f0-167">[ロール名] に「」と入力 `RSExecRole` します。</span><span class="sxs-lookup"><span data-stu-id="669f0-167">In Role name, type `RSExecRole`.</span></span>

7.  <span data-ttu-id="669f0-168">[所有者] に「 **DBO**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="669f0-168">In Owner, type **DBO**.</span></span>

8.  <span data-ttu-id="669f0-169">**[セキュリティ保護可能なリソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-169">Click **Securables**.</span></span>

9. <span data-ttu-id="669f0-170">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-170">Click **Add**.</span></span> <span data-ttu-id="669f0-171">**[オブジェクトの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-171">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="669f0-172">**[オブジェクトの指定]** オプションが既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-172">The **Specify Objects** option is selected by default.</span></span>

10. <span data-ttu-id="669f0-173">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-173">Click **OK**.</span></span>

11. <span data-ttu-id="669f0-174">**[オブジェクトの種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-174">Click **Object Types**.</span></span>

12. <span data-ttu-id="669f0-175">**[ストアド プロシージャ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-175">Click **Stored Procedures.**</span></span>

13. <span data-ttu-id="669f0-176">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-176">Click **OK**.</span></span>

14. <span data-ttu-id="669f0-177">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-177">Click **Browse**.</span></span>

15. <span data-ttu-id="669f0-178">項目の一覧を下にスクロールし、以下を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-178">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="669f0-179">sp_add_category</span><span class="sxs-lookup"><span data-stu-id="669f0-179">sp_add_category</span></span>

    2.  <span data-ttu-id="669f0-180">sp_add_job</span><span class="sxs-lookup"><span data-stu-id="669f0-180">sp_add_job</span></span>

    3.  <span data-ttu-id="669f0-181">sp_add_jobschedule</span><span class="sxs-lookup"><span data-stu-id="669f0-181">sp_add_jobschedule</span></span>

    4.  <span data-ttu-id="669f0-182">sp_add_jobserver</span><span class="sxs-lookup"><span data-stu-id="669f0-182">sp_add_jobserver</span></span>

    5.  <span data-ttu-id="669f0-183">sp_add_jobstep</span><span class="sxs-lookup"><span data-stu-id="669f0-183">sp_add_jobstep</span></span>

    6.  <span data-ttu-id="669f0-184">sp_delete_job</span><span class="sxs-lookup"><span data-stu-id="669f0-184">sp_delete_job</span></span>

    7.  <span data-ttu-id="669f0-185">sp_help_category</span><span class="sxs-lookup"><span data-stu-id="669f0-185">sp_help_category</span></span>

    8.  <span data-ttu-id="669f0-186">sp_help_job</span><span class="sxs-lookup"><span data-stu-id="669f0-186">sp_help_job</span></span>

    9. <span data-ttu-id="669f0-187">sp_help_jobschedule</span><span class="sxs-lookup"><span data-stu-id="669f0-187">sp_help_jobschedule</span></span>

    10. <span data-ttu-id="669f0-188">sp_verify_job_identifiers</span><span class="sxs-lookup"><span data-stu-id="669f0-188">sp_verify_job_identifiers</span></span>

16. <span data-ttu-id="669f0-189">**[OK]** をクリックし、もう一度 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-189">Click **OK**, and the click **OK** again.</span></span>

17. <span data-ttu-id="669f0-190">最初のストアド プロシージャ sp_add_category を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-190">Select the first stored procedure: sp_add_category.</span></span>

18. <span data-ttu-id="669f0-191">**[実行]** 行の **[許可]** 列で、チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-191">In the **Execute** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

19. <span data-ttu-id="669f0-192">残りの各ストアド プロシージャに同じ操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="669f0-192">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="669f0-193">RSExecRole には、10 個のストアド プロシージャすべてに対する実行権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-193">RSExecRole must be granted Execute permissions for all ten stored procedures.</span></span>

20. <span data-ttu-id="669f0-194">[セキュリティ保護可能なリソース] タブで、もう一度 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-194">On the Securables tab, and click **Add** again.</span></span> <span data-ttu-id="669f0-195">**[オブジェクトの追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-195">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="669f0-196">**[オブジェクトの指定]** オプションが既定で選択されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-196">The **Specify Objects** option is selected by default.</span></span>

21. <span data-ttu-id="669f0-197">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-197">Click **OK**.</span></span>

22. <span data-ttu-id="669f0-198">**[オブジェクトの種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-198">Click **Object Types**.</span></span>

23. <span data-ttu-id="669f0-199">**[テーブル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-199">Click **Tables.**</span></span>

24. <span data-ttu-id="669f0-200">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-200">Click **OK**.</span></span>

25. <span data-ttu-id="669f0-201">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-201">Click **Browse**.</span></span>

26. <span data-ttu-id="669f0-202">項目の一覧を下にスクロールし、以下を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-202">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="669f0-203">syscategories</span><span class="sxs-lookup"><span data-stu-id="669f0-203">syscategories</span></span>

    2.  <span data-ttu-id="669f0-204">sysjobs</span><span class="sxs-lookup"><span data-stu-id="669f0-204">sysjobs</span></span>

27. <span data-ttu-id="669f0-205">**[OK]** をクリックし、もう一度 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-205">Click **OK**, and the click **OK** again.</span></span>

28. <span data-ttu-id="669f0-206">最初のテーブル syscategories を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-206">Select the first table: syscategories.</span></span>

29. <span data-ttu-id="669f0-207">**[選択]** 行の **[許可]** 列で、チェック ボックスをオンにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-207">In the **Select** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

30. <span data-ttu-id="669f0-208">sysjobs テーブルに同じ操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="669f0-208">Repeat for the sysjobs table.</span></span> <span data-ttu-id="669f0-209">RSExecRole には、両方のテーブルに対する選択権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="669f0-209">RSExecRole must be granted Select permissions for both tables.</span></span>

## <a name="move-the-report-server-database"></a><span data-ttu-id="669f0-210">レポート サーバー データベースの移動</span><span class="sxs-lookup"><span data-stu-id="669f0-210">Move the Report Server Database</span></span>
 <span data-ttu-id="669f0-211">ロールを作成したら、レポート サーバー データベースを新しい SQL Server インスタンスに移動できます。</span><span class="sxs-lookup"><span data-stu-id="669f0-211">After you create the roles, you can move the report server database to new SQL Server instance.</span></span> <span data-ttu-id="669f0-212">詳細については、「 [別のコンピューターへのレポート サーバー データベースの移動 (SSRS ネイティブ モード)](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="669f0-212">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>

 <span data-ttu-id="669f0-213">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] を [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]にアップグレードする場合、そのアップグレードはデータベースを移動する前と後のどちらでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="669f0-213">If you are upgrading the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can upgrade it before or after moving the database.</span></span>

 <span data-ttu-id="669f0-214">レポート サーバー データベースは、レポート サーバーがそのデータベースに接続するときに、自動的に [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] へとアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="669f0-214">The report server database will be upgraded to the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] automatically when the report server connects to it.</span></span> <span data-ttu-id="669f0-215">データベースをアップグレードするために特定の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="669f0-215">There are no specific steps required for upgrading the database.</span></span>

## <a name="restore-encryption-keys-and-verify-your-work"></a><span data-ttu-id="669f0-216">暗号化キーの復元と作業の確認</span><span class="sxs-lookup"><span data-stu-id="669f0-216">Restore Encryption Keys and Verify Your Work</span></span>
 <span data-ttu-id="669f0-217">レポート サーバー データベースをアタッチしたら、次の手順を実行して作業を確認します。</span><span class="sxs-lookup"><span data-stu-id="669f0-217">If you have attached the report server databases, you should now be able to complete the following steps to verify your work.</span></span>

#### <a name="to-verify-report-server-operability-after-a-database-move"></a><span data-ttu-id="669f0-218">データベース移動後にレポート サーバーの運用性を確認するには</span><span class="sxs-lookup"><span data-stu-id="669f0-218">To verify report server operability after a database move</span></span>

1.  <span data-ttu-id="669f0-219">Reporting Services 構成ツールを起動して、レポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="669f0-219">Start the Reporting Services Configuration tool and connect to the report server.</span></span>

2.  <span data-ttu-id="669f0-220">**[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-220">Click **Database**.</span></span>

3.  <span data-ttu-id="669f0-221">**[データベースの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-221">Click **Change Database**.</span></span>

4.  <span data-ttu-id="669f0-222">**[既存のレポート サーバー データベースを選択する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-222">Click **Choose an existing report server database**.</span></span>

5.  <span data-ttu-id="669f0-223">データベース エンジンのサーバー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="669f0-223">Enter the server name of the Database Engine.</span></span> <span data-ttu-id="669f0-224">レポートサーバーデータベースを名前付きインスタンスにアタッチした場合は、<instancename の形式でインスタンス名を入力する必要があります \<servername> \\ \> 。</span><span class="sxs-lookup"><span data-stu-id="669f0-224">If you attached the report server databases to a named instance, you must type the instance name in this format: \<servername>\\<instancename\>.</span></span>

6.  <span data-ttu-id="669f0-225">**[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-225">Click **Test Connection**.</span></span>

7.  <span data-ttu-id="669f0-226">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-226">Click **Next**.</span></span>

8.  <span data-ttu-id="669f0-227">[データベース] で、レポート サーバー データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-227">On the Database, select the report server database.</span></span>

9. <span data-ttu-id="669f0-228">**[次へ]** をクリックして、ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="669f0-228">Click **Next** and complete the wizard.</span></span>

10. <span data-ttu-id="669f0-229">**[暗号化キー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-229">Click **Encryption Keys**.</span></span>

11. <span data-ttu-id="669f0-230">**[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-230">Click **Restore**.</span></span>

12. <span data-ttu-id="669f0-231">レポート サーバー データベースに格納されている資格情報および接続情報の暗号化を解除するために使用される対称キーのバックアップ コピーが含まれている厳密な名前のキー ファイル (.snk) を選択します。</span><span class="sxs-lookup"><span data-stu-id="669f0-231">Select the strong file (.snk) that has the backup copy of the symmetric key used to decrypt stored credentials and connection information in the report server database.</span></span>

13. <span data-ttu-id="669f0-232">パスワードを入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-232">Enter the password and click **OK**.</span></span>

14. <span data-ttu-id="669f0-233">**[レポート マネージャー URL]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-233">Click **Report Manager URL**.</span></span>

15. <span data-ttu-id="669f0-234">レポート マネージャーを開くリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="669f0-234">Click the link to open Report Manager.</span></span> <span data-ttu-id="669f0-235">レポート サーバー データベースのレポート サーバー アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="669f0-235">You should see the report server items from the report server database.</span></span>

## <a name="see-also"></a><span data-ttu-id="669f0-236">参照</span><span class="sxs-lookup"><span data-stu-id="669f0-236">See Also</span></span>
 <span data-ttu-id="669f0-237">[レポートサーバーデータベースの別のコンピューターへの移動 &#40;Ssrs ネイティブモード&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services Configuration Manager ネイティブモード &#40;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)ネイティブモード[レポートサーバーデータベースの作成&#41;SSRS &#40;Configuration Manager の](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)[暗号化キーのバックアップと復元](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="669f0-237">[Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span></span>


