---
title: サーバー インスタンスの HADR クラスター コンテキストの変更 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbc29fa2ebaaf2bbc9e577b5bd303e8a0dd0ec4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741317"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a><span data-ttu-id="783bb-102">サーバー インスタンスの HADR クラスター コンテキストの変更 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="783bb-102">Change the HADR Cluster Context of Server Instance (SQL Server)</span></span>
  <span data-ttu-id="783bb-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以降で [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] インスタンスの HADR クラスター コンテキストを切り替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="783bb-103">This topic describes how to switch the HADR cluster context of an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="783bb-104">*HADR クラスター コンテキスト* は、サーバー インスタンスによってホストされる可用性レプリカのメタデータを管理する Windows Server フェールオーバー クラスタリング (WSFC) クラスターを決定します。</span><span class="sxs-lookup"><span data-stu-id="783bb-104">The *HADR cluster context* determines which Windows Server Failover Clustering (WSFC) cluster manages the metadata for availability replicas hosted by the server instance.</span></span>  
  
 <span data-ttu-id="783bb-105">HADR クラスター コンテキストの切り替えは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を新しい WSFC クラスター上の [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] インスタンスに移行するクラスター間での移行中にのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="783bb-105">Switch the HADR cluster context only during a cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] to an instance of [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] on a new WSFC cluster.</span></span> <span data-ttu-id="783bb-106">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のクラスター間の移行は、可用性グループの最小限のダウンタイムで [!INCLUDE[win8](../../../includes/win8-md.md)] または [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] への OS のアップグレードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="783bb-106">Cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] supports OS upgrade to [!INCLUDE[win8](../../../includes/win8-md.md)] or [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] with minimal downtime of availability groups.</span></span> <span data-ttu-id="783bb-107">詳細については、「[OS アップグレードのための AlwaysOn 可用性グループのクラスター間での移行](https://msdn.microsoft.com/library/jj873730.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="783bb-107">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="783bb-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="783bb-108">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="783bb-109">HADR クラスター コンテキストの切り替えは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 配置のクラスター間での移行中にのみ実行してください。</span><span class="sxs-lookup"><span data-stu-id="783bb-109">Switch the HADR cluster context only during cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] deployments.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="783bb-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="783bb-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="783bb-111">HADR クラスター コンテキストの切り替えは、ローカル WSFC クラスターとリモート クラスター間でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="783bb-111">You can switch the HADR cluster context only from the local WSFC cluster to a remote cluster and then back from the remote cluster to the local cluster.</span></span> <span data-ttu-id="783bb-112">リモート クラスター間で HADR クラスター コンテキストを切り替えることはできません。</span><span class="sxs-lookup"><span data-stu-id="783bb-112">You cannot switch the HADR cluster context from one remote cluster to another remote cluster.</span></span>  
  
-   <span data-ttu-id="783bb-113">HADR クラスター コンテキストは、SQL Server インスタンスが可用性レプリカをホストしていない場合のみリモート クラスターに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="783bb-113">The HADR cluster context can be switched to a remote cluster only when the instance of SQL Server is not hosting any availability replicas.</span></span>  
  
-   <span data-ttu-id="783bb-114">リモート HADR クラスター コンテキストは、いつでもローカル クラスターに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="783bb-114">A remote HADR cluster context can be switched back to the local cluster at any time.</span></span> <span data-ttu-id="783bb-115">ただし、コンテキストは、サーバー インスタンスが可用性レプリカをホストしている限り、再度切り替えることはできません。</span><span class="sxs-lookup"><span data-stu-id="783bb-115">However, the context cannot be switched again as long as the server instance is hosting any availability replicas.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="783bb-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="783bb-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="783bb-117">HADR クラスター コンテキストを変更するサーバー インスタンスは、 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 以上 (Enterprise Edition 以上) を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-117">The server instance on which you change the HADR cluster context must be running [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="783bb-118">サーバー インスタンスで AlwaysOn が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-118">The server instance must be enabled for AlwaysOn.</span></span> <span data-ttu-id="783bb-119">詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="783bb-119">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="783bb-120">ローカル クラスター コンテキストからリモート クラスターに切り替えるための条件を満たすには、サーバー インスタンスで可用性レプリカをホストしていないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="783bb-120">To be eligible to be switched from the local cluster context to a remote cluster cluster, a server instance cannot be hosting any availability replicas.</span></span> <span data-ttu-id="783bb-121">[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) カタログ ビューに行は返されません。</span><span class="sxs-lookup"><span data-stu-id="783bb-121">The [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) catalog view should not return any rows.</span></span>  
  
     <span data-ttu-id="783bb-122">サーバー インスタンス上に可用性レプリカが存在する場合は、HADR クラスター コンテキストを変更する前に、次のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-122">If any availability replicas exist on the server instance, before you can change the HADR cluster context, you must do one of the following:</span></span>  
  
    |<span data-ttu-id="783bb-123">レプリカのロール</span><span class="sxs-lookup"><span data-stu-id="783bb-123">Replica Role</span></span>|<span data-ttu-id="783bb-124">アクション</span><span class="sxs-lookup"><span data-stu-id="783bb-124">Action</span></span>|<span data-ttu-id="783bb-125">Link</span><span class="sxs-lookup"><span data-stu-id="783bb-125">Link</span></span>|  
    |------------------|------------|----------|  
    |<span data-ttu-id="783bb-126">プライマリ</span><span class="sxs-lookup"><span data-stu-id="783bb-126">Primary</span></span>|<span data-ttu-id="783bb-127">可用性グループをオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="783bb-127">Take the availability group offline.</span></span>|[<span data-ttu-id="783bb-128">可用性グループをオフラインにする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-128">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)|  
    |<span data-ttu-id="783bb-129">セカンダリ</span><span class="sxs-lookup"><span data-stu-id="783bb-129">Secondary</span></span>|<span data-ttu-id="783bb-130">可用性グループからセカンダリ レプリカを削除する</span><span class="sxs-lookup"><span data-stu-id="783bb-130">Remove the replica from its availability group</span></span>|[<span data-ttu-id="783bb-131">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-131">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   <span data-ttu-id="783bb-132">リモート クラスターからローカル クラスターに切り替える前に、すべての同期コミット レプリカを SYNCHRONIZED にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-132">Before you can switch from a remote cluster to the local cluster, all synchronous-commit replicas must be SYNCHRONIZED.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="783bb-133">推奨事項</span><span class="sxs-lookup"><span data-stu-id="783bb-133">Recommendations</span></span>  
  
-   <span data-ttu-id="783bb-134">完全なドメイン名を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="783bb-134">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="783bb-135">これは、短い名前のターゲット IP アドレスを検出するとき、ALTER SERVER CONFIGURATION は DNS 解決を使用するためです。</span><span class="sxs-lookup"><span data-stu-id="783bb-135">This is because to find the target IP address of a short name, ALTER SERVER CONFIGURATION uses DNS resolution.</span></span> <span data-ttu-id="783bb-136">ある種の状況では、DNS の検索順序によっては、短い名前を使用すると混乱が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-136">Under some situations, depending on the DNS searching order, using a short name could cause confusion.</span></span> <span data-ttu-id="783bb-137">たとえば、 `abc` ドメインのノード (`node1.abc.com`) で実行される次のコマンドを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="783bb-137">For example, consider the following command, which is executed on a node in the `abc` domain, (`node1.abc.com`).</span></span> <span data-ttu-id="783bb-138">目的のクラスターは、 `CLUS01` ドメインの `xyz` クラスターです (`clus01.xyz.com`)。</span><span class="sxs-lookup"><span data-stu-id="783bb-138">The intended destination cluster is the `CLUS01` cluster in the `xyz` domain (`clus01.xyz.com`).</span></span> <span data-ttu-id="783bb-139">ただし、ローカル ドメイン ホストも、 `CLUS01` という名前のクラスターをホストしています (`clus01.abc.com`)。</span><span class="sxs-lookup"><span data-stu-id="783bb-139">However, the local  domain hosts also hosts a cluster named `CLUS01` (`clus01.abc.com`).</span></span>  
  
     <span data-ttu-id="783bb-140">ターゲット クラスターの短い名前である `CLUS01`を指定した場合、DNS の名前の解決で、違うクラスター ( `clus01.abc.com`) が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-140">If the short name of the target cluster, `CLUS01`, were specified, DNS name resolution could return the IP address of the wrong cluster, `clus01.abc.com`.</span></span> <span data-ttu-id="783bb-141">このような混乱を避けるには、次の例に示すように、ターゲット クラスターの完全な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="783bb-141">To avoid such confusion, specify the full name of the target cluster, as in the following example:</span></span>  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="783bb-142">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="783bb-142">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="783bb-143">Permissions</span><span class="sxs-lookup"><span data-stu-id="783bb-143">Permissions</span></span>  
  
-   <span data-ttu-id="783bb-144">**ログインの SQL Server**</span><span class="sxs-lookup"><span data-stu-id="783bb-144">**SQL Server login**</span></span>  
  
     <span data-ttu-id="783bb-145">CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="783bb-145">Requires CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="783bb-146">**SQL Server サービスアカウント**</span><span class="sxs-lookup"><span data-stu-id="783bb-146">**SQL Server service account**</span></span>  
  
     <span data-ttu-id="783bb-147">サーバー インスタンスの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントは、以下を所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="783bb-147">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of the server instance must have:</span></span>  
  
    -   <span data-ttu-id="783bb-148">宛先 WSFC クラスターを開く権限。</span><span class="sxs-lookup"><span data-stu-id="783bb-148">Permission to open the destination WSFC cluster.</span></span>  
  
    -   <span data-ttu-id="783bb-149">リモート WSFC 読み取り/書き込みアクセス。</span><span class="sxs-lookup"><span data-stu-id="783bb-149">Remote WSFC read-write access.</span></span>  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="783bb-150">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="783bb-150">Using Transact-SQL</span></span>  
 <span data-ttu-id="783bb-151">**可用性レプリカの WSFC クラスター コンテキストを変更するには**</span><span class="sxs-lookup"><span data-stu-id="783bb-151">**To change the WSFC cluster context of an availability replica**</span></span>  
  
1.  <span data-ttu-id="783bb-152">可能性グループのプライマリ レプリカまたはセカンダリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="783bb-152">Connect to the server instance that hosts either the primary replica or a secondary replica of the availability group.</span></span>  
  
2.  <span data-ttu-id="783bb-153">次に示すように、 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) ステートメントの SET HADR CLUSTER CONTEXT 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="783bb-153">Use the SET HADR CLUSTER CONTEXT clause of the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="783bb-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **' *`windows_cluster`* '** |LAN</span><span class="sxs-lookup"><span data-stu-id="783bb-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCAL }</span></span>  
  
     <span data-ttu-id="783bb-155">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="783bb-155">where,</span></span>  
  
     <span data-ttu-id="783bb-156">*windows_cluster*</span><span class="sxs-lookup"><span data-stu-id="783bb-156">*windows_cluster*</span></span>  
     <span data-ttu-id="783bb-157">WSFC クラスターのクラスター オブジェクト名 (CON)。</span><span class="sxs-lookup"><span data-stu-id="783bb-157">The cluster object name (CON) of a WSFC cluster.</span></span> <span data-ttu-id="783bb-158">短い名前または完全なドメイン名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="783bb-158">You can specify either the short name or the full domain name.</span></span> <span data-ttu-id="783bb-159">完全なドメイン名を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="783bb-159">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="783bb-160">詳細については、このトピックの「[推奨事項](#Recommendations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="783bb-160">For more information, see [Recommendations](#Recommendations), earlier in this topic.</span></span>  
  
     <span data-ttu-id="783bb-161">LOCAL</span><span class="sxs-lookup"><span data-stu-id="783bb-161">LOCAL</span></span>  
     <span data-ttu-id="783bb-162">ローカル WSFC クラスター。</span><span class="sxs-lookup"><span data-stu-id="783bb-162">The local WSFC cluster.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="783bb-163">例</span><span class="sxs-lookup"><span data-stu-id="783bb-163">Examples</span></span>  
 <span data-ttu-id="783bb-164">次の例では、HADR クラスター コンテキストを別のクラスターに変更します。</span><span class="sxs-lookup"><span data-stu-id="783bb-164">The following example changes the HADR cluster context to a different cluster.</span></span> <span data-ttu-id="783bb-165">変更先の WSFC クラスターである `clus01`を識別するため、この例では、完全なクラスター オブジェクト名である `clus01.xyz.com`を指定します。</span><span class="sxs-lookup"><span data-stu-id="783bb-165">To identify the destination WSFC cluster, `clus01`, the example specifies the full cluster object name, `clus01.xyz.com`.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 <span data-ttu-id="783bb-166">次の例では、HADR クラスター コンテキストをローカル WSFC クラスターに変更します。</span><span class="sxs-lookup"><span data-stu-id="783bb-166">The following example changes the HADR cluster context to the local WSFC cluster.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="783bb-167">補足情報: 可用性レプリカのクラスター コンテキストの切り替え後</span><span class="sxs-lookup"><span data-stu-id="783bb-167">Follow Up: After Switching the Cluster Context of an Availability Replica</span></span>  
 <span data-ttu-id="783bb-168">新しい HADR クラスター コンテキストは、サーバー インスタンスの再起動なしですぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="783bb-168">The new HADR cluster context takes effect immediately, without restarting the server instance.</span></span> <span data-ttu-id="783bb-169">HADR クラスター コンテキスト設定は、サーバー インスタンスが再起動した場合でも変更されない永続的なインスタンス レベルの設定です。</span><span class="sxs-lookup"><span data-stu-id="783bb-169">The HADR cluster context setting is a persistent instance-level setting that remains unchanged if the server instance restarts.</span></span>  
  
 <span data-ttu-id="783bb-170">次に示すように、 [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) 動的管理ビューをクエリすることで、新しい HADR クラスター コンテキストを確認します。</span><span class="sxs-lookup"><span data-stu-id="783bb-170">Confirm the new HADR cluster context by querying the [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) dynamic management view, as follows:</span></span>  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 <span data-ttu-id="783bb-171">このクエリは、HADR クラスター コンテキストを設定するクラスターの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="783bb-171">This query should return the name of the cluster to which you set the HADR cluster context.</span></span>  
  
 <span data-ttu-id="783bb-172">HADR クラスター コンテキストが新しいクラスターに切り替わるとき:</span><span class="sxs-lookup"><span data-stu-id="783bb-172">When the HADR cluster context is switched to a new cluster:</span></span>  
  
-   <span data-ttu-id="783bb-173">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスによって現在ホストされている可用性レプリカのメタデータがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="783bb-173">The metadata is cleaned up for any availability replicas that are currently hosted by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="783bb-174">可用性レプリカに所属していたすべてのデータベースが、RESTORING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="783bb-174">All the databases that previously belonged to an availability replica are now in the RESTORING state.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="783bb-175">関連タスク</span><span class="sxs-lookup"><span data-stu-id="783bb-175">Related Tasks</span></span>  
  
-   [<span data-ttu-id="783bb-176">可用性グループ リスナーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-176">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="783bb-177">可用性グループをオフラインにする &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-177">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
-   [<span data-ttu-id="783bb-178">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="783bb-179">可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-179">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="783bb-180">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-180">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="783bb-181">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-181">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="783bb-182">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="783bb-182">Related Content</span></span>  
  
-   <span data-ttu-id="783bb-183">[SQL Server 2012 技術記事](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="783bb-183">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="783bb-184">SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ</span><span class="sxs-lookup"><span data-stu-id="783bb-184">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="783bb-185">参照</span><span class="sxs-lookup"><span data-stu-id="783bb-185">See Also</span></span>  
 <span data-ttu-id="783bb-186">[AlwaysOn 可用性グループ (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server フェールオーバークラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="783bb-186">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="783bb-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="783bb-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
