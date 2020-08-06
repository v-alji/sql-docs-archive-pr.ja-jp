---
title: 可用性グループ リスナーの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 057b9c137cb4d8bbbdd03be61df600f7e59b264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634062"
---
# <a name="remove-an-availability-group-listener-sql-server"></a><span data-ttu-id="dd1e5-102">可用性グループ リスナーの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd1e5-102">Remove an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="dd1e5-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループから可用性グループ リスナーを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-103">This topic describes how to remove an availability group listener from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="dd1e5-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dd1e5-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="dd1e5-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="dd1e5-106">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="dd1e5-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="dd1e5-107">Security</span><span class="sxs-lookup"><span data-stu-id="dd1e5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dd1e5-108">**リスナーを削除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-108">**To remove a listener, using:**</span></span>  
  
     [<span data-ttu-id="dd1e5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dd1e5-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dd1e5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dd1e5-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="dd1e5-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd1e5-111">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dd1e5-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="dd1e5-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="dd1e5-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="dd1e5-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="dd1e5-114">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-114">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="dd1e5-115">推奨事項</span><span class="sxs-lookup"><span data-stu-id="dd1e5-115">Recommendations</span></span>  
 <span data-ttu-id="dd1e5-116">可用性グループ リスナーを削除する前に、それを使用しているアプリケーションがないことを確認するようにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-116">Before you delete an availability group listener, we recommend that you ensure that no applications are using it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dd1e5-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dd1e5-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dd1e5-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="dd1e5-118">Permissions</span></span>  
 <span data-ttu-id="dd1e5-119">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dd1e5-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="dd1e5-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="dd1e5-121">**可用性グループ リスナーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-121">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="dd1e5-122">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-122">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="dd1e5-123">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="dd1e5-124">可用性グループのノード、 **[可用性グループ リスナー]** ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-124">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="dd1e5-125">削除するリスナーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-125">Right-click the listener to be removed, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="dd1e5-126">これにより、 **[可用性グループからのリスナーの削除]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-126">This opens the **Remove Listener from Availability Group** dialog box.</span></span> <span data-ttu-id="dd1e5-127">詳細については、このトピックの「 [[可用性グループからのリスナーの削除]](#AgListenerPropertiesDialog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-127">For more information, see [Remove Listener from Availability Group](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="remove-listener-from-availability-group-dialog-box"></a><a name="AgListenerPropertiesDialog"></a> <span data-ttu-id="dd1e5-128">[可用性グループからのリスナーの削除] (ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="dd1e5-128">Remove Listener from Availability Group (Dialog Box)</span></span>  
 <span data-ttu-id="dd1e5-129">**名前**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-129">**Name**</span></span>  
 <span data-ttu-id="dd1e5-130">削除するリスナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-130">The name of the listener to be removed.</span></span>  
  
 <span data-ttu-id="dd1e5-131">**結果**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-131">**Result**</span></span>  
 <span data-ttu-id="dd1e5-132">**[成功]** または **[エラー]** のリンクが表示されます。リンクをクリックすると、詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-132">Displays a link, either **Success** or **Error**, which you can click for more information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dd1e5-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="dd1e5-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="dd1e5-134">**可用性グループ リスナーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-134">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="dd1e5-135">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-135">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="dd1e5-136">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="dd1e5-137">可用性グループの変更*GROUP_NAME*リスナー **' *`dns_name`* ' の**削除</span><span class="sxs-lookup"><span data-stu-id="dd1e5-137">ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **'*`dns_name`*'**</span></span>  
  
     <span data-ttu-id="dd1e5-138">*group_name* の部分には、可用性グループの名前を指定します。 *dns_name* の部分には、可用性グループ リスナーの DNS 名を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-138">where *group_name* is the name of the availability group and *dns_name* is the DNS name of the availability group listener.</span></span>  
  
     <span data-ttu-id="dd1e5-139">次の例では、 `AccountsAG` 可用性グループのリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-139">The following example deletes the listener of the `AccountsAG` availability group.</span></span> <span data-ttu-id="dd1e5-140">DNS 名は AccountsAG_Listener です。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-140">The DNS name is AccountsAG_Listener.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="dd1e5-141">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="dd1e5-141">Using PowerShell</span></span>  
 <span data-ttu-id="dd1e5-142">**可用性グループ リスナーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="dd1e5-142">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="dd1e5-143">既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-143">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="dd1e5-144">組み込み `Remove-Item` コマンドレットを使用して、リスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-144">Use the built in `Remove-Item` cmdlet to remove a listener.</span></span> <span data-ttu-id="dd1e5-145">たとえば、次のコマンドは、 `MyListener` という名前のリスナーを `MyAg`という名前の可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-145">For example, the following command removes a listener named `MyListener` from an availability group named `MyAg`.</span></span>  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd1e5-146">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="dd1e5-147">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd1e5-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dd1e5-148">関連タスク</span><span class="sxs-lookup"><span data-stu-id="dd1e5-148">Related Tasks</span></span>  
  
-   [<span data-ttu-id="dd1e5-149">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd1e5-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="dd1e5-150">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd1e5-150">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd1e5-151">参照</span><span class="sxs-lookup"><span data-stu-id="dd1e5-151">See Also</span></span>  
 <span data-ttu-id="dd1e5-152">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd1e5-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="dd1e5-153">可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd1e5-153">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
