---
title: AlwaysOn 可用性グループの有効化と無効化 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632710"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a><span data-ttu-id="1ebde-102">AlwaysOn 可用性グループの有効化と無効化 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1ebde-102">Enable and Disable AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="1ebde-103">サーバー インスタンスで可用性グループを使用するには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-103">Enabling [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is a prerequisite for a server instance to use availability groups.</span></span> <span data-ttu-id="1ebde-104">可用性グループを作成したり構成したりするためには、少なくとも 1 つの可用性グループの可用性レプリカがホストされる [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の各インスタンスで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-104">Before you can create and configure any availability group, the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature must have been enabled on the each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host an availability replica for one or more availability groups.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ebde-105">WSFC クラスターを削除してから再作成した場合は、元の WSFC クラスター上の可用性レプリカをホストしていた [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の各インスタンスについて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能を無効にしてから再度有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-105">If you delete and re-create a WSFC cluster, you must disable and re-enable the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosted an availability replica on the original WSFC cluster.</span></span>  
  
-   <span data-ttu-id="1ebde-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1ebde-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1ebde-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="1ebde-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1ebde-108">Security</span><span class="sxs-lookup"><span data-stu-id="1ebde-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1ebde-109">**操作方法：**</span><span class="sxs-lookup"><span data-stu-id="1ebde-109">**How To:**</span></span>  
  
    -   [<span data-ttu-id="1ebde-110">AlwaysOn 可用性グループが有効になっているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="1ebde-110">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>](#IsEnabled)  
  
    -   [<span data-ttu-id="1ebde-111">AlwaysOn 可用性グループを有効にする</span><span class="sxs-lookup"><span data-stu-id="1ebde-111">Enable AlwaysOn Availability Groups</span></span>](#EnableAOAG)  
  
    -   [<span data-ttu-id="1ebde-112">AlwaysOn 可用性グループを無効にする</span><span class="sxs-lookup"><span data-stu-id="1ebde-112">Disable AlwaysOn Availability Groups</span></span>](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ebde-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="1ebde-113">Before You Begin</span></span>  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a><span data-ttu-id="1ebde-114">AlwaysOn 可用性グループを有効にするための前提条件</span><span class="sxs-lookup"><span data-stu-id="1ebde-114">Prerequisites for Enabling AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="1ebde-115">このサーバー インスタンスは、Windows Server フェールオーバー クラスタリング (WSFC) ノードに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-115">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="1ebde-116">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートする SQL Server エディションが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-116">The server instance must be running an edition of SQL Server that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="1ebde-117">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-117">For more information, see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="1ebde-118">一度に 1 つのサーバー インスタンスでのみ AlwaysOn 可用性グループを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-118">Enable AlwaysOn Availability Groups on only one server instance at a time.</span></span> <span data-ttu-id="1ebde-119">AlwaysOn 可用性グループを有効にした後は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-119">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
 <span data-ttu-id="1ebde-120">可用性グループを作成および構成するための追加の前提条件については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-120">For information about additional prerequisites for creating and configuring availability groups, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ebde-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1ebde-121">Security</span></span>  
 <span data-ttu-id="1ebde-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンス上で AlwaysOn 可用性グループが有効になっている限り、そのサーバー インスタンスには、WSFC クラスターに対するフル コントロール権限があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-122">While AlwaysOn Availability Groups is enabled on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server instance has full control on the WSFC cluster.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ebde-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="1ebde-123">Permissions</span></span>  
 <span data-ttu-id="1ebde-124">ローカル コンピューターの **Administrator** グループのメンバーシップおよび WSFC クラスターに対するフル コントロール権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1ebde-124">Requires membership in the **Administrator** group on the local computer and full control on the WSFC cluster.</span></span> <span data-ttu-id="1ebde-125">PowerShell を使用して AlwaysOn を有効にする場合は、 **[管理者として実行]** オプションを使用してコマンド プロンプト ウィンドウを開いてください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-125">When enabling AlwaysOn by using PowerShell, open the Command Prompt window using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="1ebde-126">Active Directory の Create Objects 権限と Manage Objects 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="1ebde-126">Requires Active Directory Create Objects and Manage Objects permissions.</span></span>  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a><span data-ttu-id="1ebde-127">AlwaysOn 可用性グループが有効になっているかどうかを判断する</span><span class="sxs-lookup"><span data-stu-id="1ebde-127">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>  
  
-   [<span data-ttu-id="1ebde-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1ebde-128">SQL Server Management Studio</span></span>](#SSMS1Procedure)  
  
-   [<span data-ttu-id="1ebde-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ebde-129">Transact-SQL</span></span>](#Tsql1Procedure)  
  
-   [<span data-ttu-id="1ebde-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ebde-130">PowerShell</span></span>](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> <span data-ttu-id="1ebde-131">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1ebde-132">**AlwaysOn 可用性グループが有効になっているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-132">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="1ebde-133">オブジェクト エクスプローラーでサーバー インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-133">In Object Explorer, right-click the server instance, and  click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1ebde-134">**[サーバーのプロパティ]** ダイアログ ボックスの **[全般]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-134">In the **Server Properties** dialog box, click the **General** page.</span></span> <span data-ttu-id="1ebde-135">**[HADR が有効]** プロパティに、次のいずれかの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-135">The **Is HADR Enabled** property displays one of the following values:</span></span>  
  
    -   <span data-ttu-id="1ebde-136">**True**(AlwaysOn 可用性グループが有効である場合)</span><span class="sxs-lookup"><span data-stu-id="1ebde-136">**True**, if AlwaysOn Availability Groups is enabled</span></span>  
  
    -   <span data-ttu-id="1ebde-137">**False**(AlwaysOn 可用性グループが無効である場合)</span><span class="sxs-lookup"><span data-stu-id="1ebde-137">**False**, if AlwaysOn Availability Groups is disabled.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> <span data-ttu-id="1ebde-138">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-138">Using Transact-SQL</span></span>  
 <span data-ttu-id="1ebde-139">**AlwaysOn 可用性グループが有効になっているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-139">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="1ebde-140">次の [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-140">Use the following [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) statement:</span></span>  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     <span data-ttu-id="1ebde-141">`IsHadrEnabled` サーバー プロパティの設定は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに対して AlwaysOn 可用性グループが有効であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-141">The setting of the `IsHadrEnabled` server property indicates whether an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is enabled for AlwaysOn Availability Groups, as follows:</span></span>  
  
    -   <span data-ttu-id="1ebde-142">`IsHadrEnabled` = 1 の場合: AlwaysOn 可用性グループが有効</span><span class="sxs-lookup"><span data-stu-id="1ebde-142">If `IsHadrEnabled` = 1, AlwaysOn Availability Groups is enabled.</span></span>  
  
    -   <span data-ttu-id="1ebde-143">`IsHadrEnabled` = 0 の場合: AlwaysOn 可用性グループが無効</span><span class="sxs-lookup"><span data-stu-id="1ebde-143">If `IsHadrEnabled` = 0, AlwaysOn Availability Groups is disabled.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ebde-144">サーバープロパティの詳細につい `IsHadrEnabled` ては、「 [serverproperty &#40;transact-sql&#41;](/sql/t-sql/functions/serverproperty-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-144">For more information about the `IsHadrEnabled` server property, see [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a><span data-ttu-id="1ebde-145">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-145">Using PowerShell</span></span>  
 <span data-ttu-id="1ebde-146">**AlwaysOn 可用性グループが有効になっているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-146">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="1ebde-147">`cd` `\SQL\NODE1\DEFAULT` [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が有効になっているかどうかを確認するサーバーインスタンス (例:) に default () を設定します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-147">Set default (`cd`) to the server instance (e.g. `\SQL\NODE1\DEFAULT`) on which you want to determine whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled.</span></span>  
  
2.  <span data-ttu-id="1ebde-148">PowerShell コマンド `Get-Item` を入力します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-148">Enter the following PowerShell `Get-Item` command:</span></span>  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ebde-149">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1ebde-150">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="1ebde-151">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-151">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="1ebde-152">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1ebde-152">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a> <span data-ttu-id="1ebde-153">[AlwaysOn 可用性グループを有効にする]</span><span class="sxs-lookup"><span data-stu-id="1ebde-153">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="1ebde-154">**AlwaysOn を有効にする場合に使用するツール:**</span><span class="sxs-lookup"><span data-stu-id="1ebde-154">**To enable AlwaysOn, using:**</span></span>  
  
-   [<span data-ttu-id="1ebde-155">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="1ebde-155">SQL Server Configuration Manager</span></span>](#SQLCM2Procedure)  
  
-   [<span data-ttu-id="1ebde-156">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ebde-156">PowerShell</span></span>](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a> <span data-ttu-id="1ebde-157">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-157">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="1ebde-158">**AlwaysOn 可用性グループを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-158">**To enable AlwaysOn Availability Groups**</span></span>  
  
1.  <span data-ttu-id="1ebde-159">対象の (AlwaysOn 可用性グループを有効にする) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスがホストされている Windows Server フェールオーバー クラスタリング (WSFC) ノードに接続します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-159">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to enable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="1ebde-160">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and  click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="1ebde-161">**SQL Server 構成マネージャー**で、[ **SQL Server Services**] をクリックし、[SQL Server (\*\* < *`instance name`*>)**] を右クリックします。ここで、 **<*`instance name`*>** は AlwaysOn 可用性グループを有効にするローカルサーバーインスタンスの名前です。 [プロパティ] をクリックし**ます。\*\*</span><span class="sxs-lookup"><span data-stu-id="1ebde-161">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click **Properties.**</span></span>  
  
4.  <span data-ttu-id="1ebde-162">**[AlwaysOn 高可用性]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-162">Select the **AlwaysOn High Availability** tab.</span></span>  
  
5.  <span data-ttu-id="1ebde-163">**[Windows フェールオーバー クラスター名]** フィールドに、ローカル フェールオーバー クラスターの名前が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-163">Verify that **Windows failover cluster name** field contains the name of the local failover cluster.</span></span> <span data-ttu-id="1ebde-164">このフィールドが空白の場合、このサーバー インスタンスは現在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-164">If this field is blank, this server instance currently does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="1ebde-165">ローカル コンピューターがクラスター ノードではないか、WSFC クラスターがシャットダウンされています。または、このエディションの [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] では [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-165">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span>  
  
6.  <span data-ttu-id="1ebde-166">[ **AlwaysOn 可用性グループを有効にする**] チェックボックスをオンにし、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-166">Select the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ebde-167">構成マネージャーによって変更内容が保存されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-167">Configuration Manager saves your change.</span></span> <span data-ttu-id="1ebde-168">その後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを手動で再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-168">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="1ebde-169">業務上の要件に合った時間帯を選んで再起動することができます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-169">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="1ebde-170">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを再起動すると、AlwaysOn が有効になり、`IsHadrEnabled` サーバー プロパティが 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-170">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the `IsHadrEnabled` server property will be set to 1.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> <span data-ttu-id="1ebde-171">SQL Server PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-171">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="1ebde-172">**AlwaysOn を有効にするには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-172">**To enable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="1ebde-173">ディレクトリ変更コマンド (`cd`) を使用して、AlwaysOn 可用性グループを有効にするサーバー インスタンスに移動します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-173">Change directory (`cd`) to a server instance that you want to enable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="1ebde-174">AlwaysOn 可用性グループを無効にするには、`Enable-SqlAlwaysOn` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-174">Use the `Enable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="1ebde-175">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-175">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1ebde-176">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-176">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ebde-177">コマンドレットでサービスを再起動するかどうかを制御する方法の詳細については `Enable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、このトピックの「[コマンドレットが SQL Server サービスを再起動するタイミング](#WhenCmdletRestartsSQL)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-177">For information about how to control whether the `Enable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
 <span data-ttu-id="1ebde-178">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="1ebde-179">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1ebde-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> <span data-ttu-id="1ebde-180">例: Enable-SqlAlwaysOn</span><span class="sxs-lookup"><span data-stu-id="1ebde-180">Example: Enable-SqlAlwaysOn</span></span>  
 <span data-ttu-id="1ebde-181">次の PowerShell コマンドは、SQL Server のインスタンス ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Computer*Instance*\\ *) の*を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-181">The following PowerShell command enables [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a><span data-ttu-id="1ebde-182">AlwaysOn 可用性グループを無効にする</span><span class="sxs-lookup"><span data-stu-id="1ebde-182">Disable AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="1ebde-183">**AlwaysOn を無効にする前に:**</span><span class="sxs-lookup"><span data-stu-id="1ebde-183">**Before you disable AlwaysOn:**</span></span>  
  
     [<span data-ttu-id="1ebde-184">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="1ebde-184">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="1ebde-185">**AlwaysOn を無効にする場合に使用するツール:**</span><span class="sxs-lookup"><span data-stu-id="1ebde-185">**To disable AlwaysOn, using:**</span></span>  
  
    -   [<span data-ttu-id="1ebde-186">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="1ebde-186">SQL Server Configuration Manager</span></span>](#SQLCM3Procedure)  
  
    -   [<span data-ttu-id="1ebde-187">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ebde-187">PowerShell</span></span>](#PScmd3Procedure)  
  
-   <span data-ttu-id="1ebde-188">**補足情報:**  [AlwaysOn を無効にした後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1ebde-188">**Follow Up:**  [After Disabling AlwaysOn](#FollowUp)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ebde-189">AlwaysOn を無効にできるサーバー インスタンスは一度に 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="1ebde-189">Disable AlwaysOn on only one server instance at a time.</span></span> <span data-ttu-id="1ebde-190">AlwaysOn 可用性グループを無効にした後は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-190">After disabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1ebde-191">推奨事項</span><span class="sxs-lookup"><span data-stu-id="1ebde-191">Recommendations</span></span>  
 <span data-ttu-id="1ebde-192">サーバー インスタンスで AlwaysOn を無効にする前に、次の操作を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-192">Before you disable AlwaysOn on a server instance, we recommend that you do the following:</span></span>  
  
1.  <span data-ttu-id="1ebde-193">保持する可用性グループのプライマリ レプリカをサーバー インスタンスがホスト中の場合は、同期されたセカンダリ レプリカに可用性グループを手動でフェールオーバーすることをお勧めします (可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="1ebde-193">If the server instance is currently hosting the primary replica of an availability group that you want to keep, we recommend that you manually fail over the availability group to a synchronized secondary replica, if possible.</span></span> <span data-ttu-id="1ebde-194">詳細については、「[可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-194">For more information, see [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1ebde-195">ローカル セカンダリ レプリカをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-195">Remove all local secondary replicas.</span></span> <span data-ttu-id="1ebde-196">詳細については、「[可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-196">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a> <span data-ttu-id="1ebde-197">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-197">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="1ebde-198">**AlwaysOn を無効にするには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-198">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="1ebde-199">対象の (AlwaysOn 可用性グループを無効にする) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスがホストされている Windows Server フェールオーバー クラスタリング (WSFC) ノードに接続します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-199">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to disable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="1ebde-200">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-200">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="1ebde-201">**SQL Server 構成マネージャー**で、[ **SQL Server Services**] をクリックし、[SQL Server (\*\* < *`instance name`*>)**] を右クリックします。ここで、 **<*`instance name`*>** は AlwaysOn 可用性グループを無効にするローカルサーバーインスタンスの名前です。 [**プロパティ\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-201">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to disable AlwaysOn Availability Groups, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1ebde-202">**[AlwaysOn 高可用性]** タブで、 **[AlwaysOn 可用性グループを有効にする]** チェック ボックスをオフにし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-202">On the**AlwaysOn High Availability**tab, deselect the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ebde-203">構成マネージャーによって変更内容が保存され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-203">Configuration Manager saves your change and restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="1ebde-204">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動すると、AlwaysOn が無効になり、`IsHadrEnabled` サーバー プロパティは、AlwaysOn 可用性グループが無効であることを示す 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-204">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be disabled, and the `IsHadrEnabled` server property will be set to 0, to indicate that AlwaysOn Availability Groups is disabled.</span></span>  
  
5.  <span data-ttu-id="1ebde-205">このトピックの「 [補足情報: AlwaysOn を無効にした後](#FollowUp)」を読むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-205">We recommend that you read the information in [Follow Up: After Disabling AlwaysOn](#FollowUp), later in this topic.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> <span data-ttu-id="1ebde-206">SQL Server PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="1ebde-206">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="1ebde-207">**AlwaysOn を無効にするには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-207">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="1ebde-208">ディレクトリの変更 ( `cd` ) を、AlwaysOn 可用性グループに対して無効にする、現在有効なサーバーインスタンスに変更します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-208">Change directory (`cd`) to a currently-enabled server instance that you want to disenable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="1ebde-209">AlwaysOn 可用性グループを無効にするには、`Disable-SqlAlwaysOn` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-209">Use the `Disable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="1ebde-210">たとえば、次のコマンドは、SQL Server (*コンピューター*インスタンス) のインスタンスの AlwaysOn 可用性グループを無効にし \\ *Instance*ます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-210">For example, the following command disables AlwaysOn Availability Groups on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  <span data-ttu-id="1ebde-211">このコマンドの場合、インスタンスを再起動する必要があり、再起動するかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-211">This command requires restarting the instance, and you will be prompted to confirm this restart.</span></span>  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1ebde-212">コマンドレットでサービスを再起動するかどうかを制御する方法の詳細については `Disable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、このトピックの「[コマンドレットが SQL Server サービスを再起動するタイミング](#WhenCmdletRestartsSQL)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-212">For information about how to control whether the `Disable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
     <span data-ttu-id="1ebde-213">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-213">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1ebde-214">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-214">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="1ebde-215">**SQL Server PowerShell プロバイダーを設定して使用するには**</span><span class="sxs-lookup"><span data-stu-id="1ebde-215">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="1ebde-216">SQL Server PowerShell プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1ebde-216">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a><span data-ttu-id="1ebde-217">補足情報: AlwaysOn を無効にした後</span><span class="sxs-lookup"><span data-stu-id="1ebde-217">Follow Up: After Disabling AlwaysOn</span></span>  
 <span data-ttu-id="1ebde-218">AlwaysOn 可用性グループを無効にした後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-218">After you disable AlwaysOn Availability Groups, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must be restarted.</span></span> <span data-ttu-id="1ebde-219">サーバー インスタンスは、SQL 構成マネージャーによって自動的に再起動されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-219">SQL Configuration Manager restarts the server instance automatically.</span></span> <span data-ttu-id="1ebde-220">ただし、`Disable-SqlAlwaysOn` コマンドレットを使用した場合は、サーバー インスタンスを手動で再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-220">However, if you used the `Disable-SqlAlwaysOn` cmdlet, you will need to restart the server instance manually.</span></span> <span data-ttu-id="1ebde-221">詳細については、「 [sqlservr Application](../../../tools/sqlservr-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-221">For more information, see [sqlservr Application](../../../tools/sqlservr-application.md).</span></span>  
  
 <span data-ttu-id="1ebde-222">再起動後のサーバー インスタンスに該当する状況を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-222">On the restarted server instance:</span></span>  
  
-   <span data-ttu-id="1ebde-223">SQL Server の起動時に可用性データベースは開始されず、アクセス不能となります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-223">Availability databases do not start up at SQL Server startup, making them inaccessible.</span></span>  
  
-   <span data-ttu-id="1ebde-224">サポートされる AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)のみとなります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-224">The only supported AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql).</span></span> <span data-ttu-id="1ebde-225">CREATE AVAILABILITY GROUP と ALTER AVAILABILITY GROUP、および ALTER DATABASE の SET HADR オプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-225">CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and the SET HADR options of ALTER DATABASE are not supported.</span></span>  
  
-   <span data-ttu-id="1ebde-226">AlwaysOn 可用性グループを無効にしても、WSFC 内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の構成データと [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のメタデータにその影響が及ぶことはありません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-226">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] metadata and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration data in WSFC are unaffected by disabling AlwaysOn Availability Groups.</span></span>  
  
 <span data-ttu-id="1ebde-227">1 つまたは複数の可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで AlwaysOn 可用性グループを永続的に無効にする場合は、次の手順を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ebde-227">If you permanently disable AlwaysOn Availability Groups on every server instance that hosts an availability replica for one or more availability groups, we recommend that you complete the following steps:</span></span>  
  
1.  <span data-ttu-id="1ebde-228">AlwaysOn を無効にする前にローカル可用性レプリカを削除しなかった場合は、サーバー インスタンスが可用性レプリカをホストしている可用性グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-228">If you did not remove the local availability replicas before disabling AlwaysOn, delete (drop) each availability group for which the server instance is hosting an availability replica.</span></span> <span data-ttu-id="1ebde-229">可用性グループの削除については、「[可用性グループの削除 &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebde-229">For information about deleting an availability group, see [Remove an Availability Group &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1ebde-230">残されたメタデータを除去するには、元の WSFC クラスターの一部であるサーバー インスタンスから影響を受ける可用性グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ebde-230">To remove the metadata left behind, delete (drop) each affected availability group on a server instance that is part of the original WSFC cluster.</span></span>  
  
3.  <span data-ttu-id="1ebde-231">プライマリ データベースには引き続きすべての接続からアクセスできますが、プライマリ データベースとセカンダリ データベース間のデータの同期は中止されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-231">Any primary databases continue to be accessible to all connections but the data synchronization between the primary and secondary databases stops.</span></span>  
  
4.  <span data-ttu-id="1ebde-232">セカンダリ データベースは、RESTORING 状態に入ります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-232">The secondary databases enter the RESTORING state.</span></span> <span data-ttu-id="1ebde-233">これらは削除するか、RESTORE WITH RECOVERY を使用して復元できます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-233">You can delete them, or you can restore them by using RESTORE WITH RECOVERY.</span></span> <span data-ttu-id="1ebde-234">ただし、復元されたデータベースは、それ以降、可用性グループのデータの同期対象とはなりません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-234">However, restored databases are no longer participating in availability-group data synchronization.</span></span>  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> <span data-ttu-id="1ebde-235">SQL Server サービスがコマンドレットによって再起動される条件</span><span class="sxs-lookup"><span data-stu-id="1ebde-235">When Does a Cmdlet Restart the SQL Server Service?</span></span>  
 <span data-ttu-id="1ebde-236">現在実行中のサーバー インスタンスで、`Enable-SqlAlwaysOn` または `Disable-SqlAlwaysOn` を使用して現在の AlwaysOn 設定を変更すると、SQL Server サービスが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-236">On a server instance that is currently running, using `Enable-SqlAlwaysOn` or `Disable-SqlAlwaysOn` to change the current AlwaysOn setting could cause the SQL Server service to restart.</span></span> <span data-ttu-id="1ebde-237">再起動の動作は次の条件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1ebde-237">The restart behavior on depends on the following conditions:</span></span>  
  
|<span data-ttu-id="1ebde-238">-NoServiceRestart パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="1ebde-238">-NoServiceRestart parameter specified</span></span>|<span data-ttu-id="1ebde-239">-Force パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="1ebde-239">-Force parameter specified</span></span>|<span data-ttu-id="1ebde-240">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの再起動</span><span class="sxs-lookup"><span data-stu-id="1ebde-240">Is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarted?</span></span>|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="1ebde-241">いいえ</span><span class="sxs-lookup"><span data-stu-id="1ebde-241">No</span></span>|<span data-ttu-id="1ebde-242">いいえ</span><span class="sxs-lookup"><span data-stu-id="1ebde-242">No</span></span>|<span data-ttu-id="1ebde-243">既定では再起動されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-243">By default.</span></span> <span data-ttu-id="1ebde-244">ただし、次のプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-244">But the cmdlet prompts you as follows:</span></span><br /><br /> <span data-ttu-id="1ebde-245">**このアクションを完了するには、サーバー インスタンス '<instance_name>' の SQL Server サービスを再起動する必要があります。続行しますか?**</span><span class="sxs-lookup"><span data-stu-id="1ebde-245">**To complete this action, we must restart the SQL Server service for server instance '<instance_name>'. Do you want to continue?**</span></span><br /><br /> <span data-ttu-id="1ebde-246">**[Y] はい  [N] いいえ  [S] 中断  [?] ヘルプ (既定値は "Y"):**</span><span class="sxs-lookup"><span data-stu-id="1ebde-246">**[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):**</span></span><br /><br /> <span data-ttu-id="1ebde-247">**N** または **S**を指定した場合、サービスは再起動されません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-247">If you specify **N** or **S**, the service is not restarted.</span></span>|  
|<span data-ttu-id="1ebde-248">いいえ</span><span class="sxs-lookup"><span data-stu-id="1ebde-248">No</span></span>|<span data-ttu-id="1ebde-249">はい</span><span class="sxs-lookup"><span data-stu-id="1ebde-249">Yes</span></span>|<span data-ttu-id="1ebde-250">サービスは再起動されます。</span><span class="sxs-lookup"><span data-stu-id="1ebde-250">Service is restarted.</span></span>|  
|<span data-ttu-id="1ebde-251">はい</span><span class="sxs-lookup"><span data-stu-id="1ebde-251">Yes</span></span>|<span data-ttu-id="1ebde-252">いいえ</span><span class="sxs-lookup"><span data-stu-id="1ebde-252">No</span></span>|<span data-ttu-id="1ebde-253">サービスは再起動されません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-253">Service is not restarted.</span></span>|  
|<span data-ttu-id="1ebde-254">はい</span><span class="sxs-lookup"><span data-stu-id="1ebde-254">Yes</span></span>|<span data-ttu-id="1ebde-255">はい</span><span class="sxs-lookup"><span data-stu-id="1ebde-255">Yes</span></span>|<span data-ttu-id="1ebde-256">サービスは再起動されません。</span><span class="sxs-lookup"><span data-stu-id="1ebde-256">Service is not restarted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ebde-257">参照</span><span class="sxs-lookup"><span data-stu-id="1ebde-257">See Also</span></span>  
 <span data-ttu-id="1ebde-258">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1ebde-258">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1ebde-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ebde-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
