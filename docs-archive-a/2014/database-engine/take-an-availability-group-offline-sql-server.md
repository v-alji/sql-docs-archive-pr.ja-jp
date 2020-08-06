---
title: 可用性グループをオフラインにする
description: Always On 可用性グループをオフラインに設定する手順
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
ms.openlocfilehash: db2f56befe6905b9c3de6bd1ab6a2e5a4a00b1b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641840"
---
# <a name="take-an-availability-group-offline-sql-server"></a><span data-ttu-id="d7463-103">可用性グループをオフラインにする (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d7463-103">Take an Availability Group Offline (SQL Server)</span></span>
  <span data-ttu-id="d7463-104">このトピックでは、 [!INCLUDE[tsql](../includes/tsql-md.md)] の [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 以降のバージョンを使用して、AlwaysOn 可用性グループを ONLINE 状態から OFFLINE 状態にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7463-104">This topic describes how to take an AlwaysOn availability group from the ONLINE state to the OFFLINE state by using [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="d7463-105">同期コミット レプリカが同期されていない場合は OFFLINE 操作でエラーが発生し、可用性グループは ONLINE を維持するため、同期コミット データベースのデータ損失はありません。</span><span class="sxs-lookup"><span data-stu-id="d7463-105">There is no data loss for synchronous-commit databases because if any synchronous-commit replica is not synchronized, the OFFLINE operation raises an error and leaves the availability group ONLINE.</span></span> <span data-ttu-id="d7463-106">可用性グループをオンラインにしておくと、非同期コミット データベースで発生する可能性があるデータ損失が防止されます。</span><span class="sxs-lookup"><span data-stu-id="d7463-106">Keeping the availability group online protects unsynchronized synchronous-commit databases from possible data loss.</span></span> <span data-ttu-id="d7463-107">可用性グループがオフラインになると、クライアントはそのデータベースを使用できなくなりますが、可用性グループをオンラインに戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="d7463-107">After an availability group goes offline, its databases become unavailable to clients and you cannot bring the availability group back online.</span></span> <span data-ttu-id="d7463-108">したがって、可用性グループは、可用性グループのリソースを WSFC クラスター間で移行する場合のみオフラインにしてください。</span><span class="sxs-lookup"><span data-stu-id="d7463-108">Therefore, take an availability group offline only to migrate the availability group resources from one WSFC cluster to another.</span></span>  
  
 <span data-ttu-id="d7463-109">[!INCLUDE[ssHADR](../includes/sshadr-md.md)]のクラスター間での移行時は、任意のアプリケーションが可用性グループのプライマリ レプリカに直接接続している場合は、可用性グループをオフラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7463-109">During a cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)], if any applications connect directly to the primary replica of an availability group, the availability group must be taken offline.</span></span> <span data-ttu-id="d7463-110">[!INCLUDE[ssHADR](../includes/sshadr-md.md)] のクラスター間の移行は、可用性グループの最小限のダウンタイムで OS のアップグレードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d7463-110">Cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] supports OS upgrade with minimal downtime of availability groups.</span></span> <span data-ttu-id="d7463-111">一般的なシナリオは、 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] のクラスター間の移行を、 [!INCLUDE[win8](../includes/win8-md.md)] または [!INCLUDE[win8srv](../includes/win8srv-md.md)]への OS のアップグレードで使用することです。</span><span class="sxs-lookup"><span data-stu-id="d7463-111">The typical scenario is to use cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] for OS upgrade to [!INCLUDE[win8](../includes/win8-md.md)] or [!INCLUDE[win8srv](../includes/win8srv-md.md)].</span></span> <span data-ttu-id="d7463-112">詳細については、「[OS アップグレードのための AlwaysOn 可用性グループのクラスター間での移行](https://msdn.microsoft.com/library/jj873730.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7463-112">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d7463-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="d7463-113">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d7463-114">OFFLINE オプションは、可用性グループのリソースをクラスター間で移行する場合のみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="d7463-114">Use the OFFLINE option only for a cross-cluster migration of availability group resources.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d7463-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="d7463-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="d7463-116">OFFLINE コマンドを入力するサーバー インスタンスが、 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 以上 (Enterprise Edition 以上) を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7463-116">The server instance on which you enter the OFFLINE command must be running [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="d7463-117">可用性グループが現在オンラインになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7463-117">The availability group must currently be online.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d7463-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="d7463-118">Recommendations</span></span>  
 <span data-ttu-id="d7463-119">可用性グループをオフラインにする前に、可用性グループ リスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="d7463-119">Before you take the availability group offline, delete the availability group listener or listeners.</span></span> <span data-ttu-id="d7463-120">詳細については、「 [可用性グループ リスナーの削除 &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)への OS のアップグレードで使用することです。</span><span class="sxs-lookup"><span data-stu-id="d7463-120">For more information, see [Remove an Availability Group Listener &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d7463-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d7463-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d7463-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="d7463-122">Permissions</span></span>  
 <span data-ttu-id="d7463-123">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d7463-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d7463-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d7463-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="d7463-125">**可用性グループをオフラインにするには**</span><span class="sxs-lookup"><span data-stu-id="d7463-125">**To take an availability group offline**</span></span>  
  
1.  <span data-ttu-id="d7463-126">可用性グループの可用性レプリカをホストしているサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d7463-126">Connect to a server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="d7463-127">このレプリカは、プライマリ レプリカでもセカンダリ レプリカでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d7463-127">This replica can be the primary replica or a secondary replica.</span></span>  
  
2.  <span data-ttu-id="d7463-128">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="d7463-128">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="d7463-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span><span class="sxs-lookup"><span data-stu-id="d7463-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span></span>  
  
     <span data-ttu-id="d7463-130">*group_name* は可用性グループの名前です。</span><span class="sxs-lookup"><span data-stu-id="d7463-130">where *group_name* is the name of the availability group.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d7463-131">例</span><span class="sxs-lookup"><span data-stu-id="d7463-131">Example</span></span>  
 <span data-ttu-id="d7463-132">次の例では、 `AccountsAG` 可用性グループをオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="d7463-132">The following example takes the `AccountsAG` availability group offline.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a><span data-ttu-id="d7463-133">補足情報: 可用性グループがオフラインになった後</span><span class="sxs-lookup"><span data-stu-id="d7463-133">Follow Up: After the Availability Group Goes Offline</span></span>  
  
-   <span data-ttu-id="d7463-134">**OFFLINE 操作のログ記録:** OFFLINE 操作が開始された WSFC ノードの ID が、WSFC クラスター ログと SQL ERRORLOG の両方に保存されます。</span><span class="sxs-lookup"><span data-stu-id="d7463-134">**Logging of OFFLINE operation:**  The identity of the WSFC node where the OFFLINE operation was initiated is stored in both the WSFC cluster log and the SQL ERRORLOG.</span></span>  
  
-   <span data-ttu-id="d7463-135">**グループをオフラインにする前に、可用性グループ リスナーを削除しなかった場合:** 可用性グループを別の WSFC クラスターに移行している場合は、リスナーの VNN と VIP を削除します。</span><span class="sxs-lookup"><span data-stu-id="d7463-135">**If you did not delete the availability group listener before taking the group offline:**  If you are migrating the availability group to another WSFC cluster, delete the VNN and VIP of the listener.</span></span> <span data-ttu-id="d7463-136">これらは、フェールオーバー クラスター管理コンソール、 [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell コマンドレット、または [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)を使用して削除できます。</span><span class="sxs-lookup"><span data-stu-id="d7463-136">You can delete them by using either the Failover Cluster Management console, the [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet, or [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx).</span></span> <span data-ttu-id="d7463-137">cluster.exe は Windows 8 では非推奨とされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d7463-137">Note that cluster.exe is deprecated on Windows 8.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d7463-138">関連タスク</span><span class="sxs-lookup"><span data-stu-id="d7463-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d7463-139">可用性グループ リスナーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d7463-139">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="d7463-140">サーバー インスタンスの HADR クラスター コンテキストの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d7463-140">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="d7463-141">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d7463-141">Related Content</span></span>  
  
-   <span data-ttu-id="d7463-142">[SQL Server 2012 技術記事](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d7463-142">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="d7463-143">SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ</span><span class="sxs-lookup"><span data-stu-id="d7463-143">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="d7463-144">参照</span><span class="sxs-lookup"><span data-stu-id="d7463-144">See Also</span></span>  
 [<span data-ttu-id="d7463-145">AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d7463-145">AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/always-on-availability-groups-sql-server.md)  
