---
title: Always On クライアント接続 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 360e448e87b16b6fb97384bb9a85525a864eeef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640251"
---
# <a name="always-on-client-connectivity-sql-server"></a><span data-ttu-id="e972c-102">Always On クライアント接続 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e972c-102">Always On Client Connectivity (SQL Server)</span></span>
  <span data-ttu-id="e972c-103">このトピックでは、AlwaysOn 可用性グループへのクライアント接続に関して、クライアント構成および設定の前提条件、制限、推奨などの考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="e972c-103">This topic describes considerations for client connectivity to AlwaysOn Availability Groups, including prerequisites, restrictions, and recommendations for client configurations and settings.</span></span>  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a> <span data-ttu-id="e972c-104">クライアント接続のサポート</span><span class="sxs-lookup"><span data-stu-id="e972c-104">Client Connectivity Support</span></span>  
 <span data-ttu-id="e972c-105">以下のセクションでは、クライアント接続に対する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e972c-105">The section below provides information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] support for client connectivity.</span></span>  
  
 <span data-ttu-id="e972c-106">**ドライバー サポート**</span><span class="sxs-lookup"><span data-stu-id="e972c-106">**Driver Support**</span></span>  
  
 <span data-ttu-id="e972c-107">次の表は、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のドライバー サポートをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="e972c-107">The following table summarizes driver support for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:</span></span>  
  
|<span data-ttu-id="e972c-108">Driver</span><span class="sxs-lookup"><span data-stu-id="e972c-108">Driver</span></span>|<span data-ttu-id="e972c-109">マルチサブネット フェールオーバー</span><span class="sxs-lookup"><span data-stu-id="e972c-109">Multi-Subnet Failover</span></span>|<span data-ttu-id="e972c-110">アプリケーションの目的</span><span class="sxs-lookup"><span data-stu-id="e972c-110">Application Intent</span></span>|<span data-ttu-id="e972c-111">読み取り専用ルーティング</span><span class="sxs-lookup"><span data-stu-id="e972c-111">Read-Only Routing</span></span>|<span data-ttu-id="e972c-112">マルチサブネット フェールオーバー: より高速な単一サブネット エンドポイント フェールオーバー</span><span class="sxs-lookup"><span data-stu-id="e972c-112">Multi-Subnet Failover: Faster Single Subnet Endpoint Failover</span></span>|<span data-ttu-id="e972c-113">マルチサブネット フェールオーバー: SQL クラスター インスタンスの名前付きインスタンスの解決</span><span class="sxs-lookup"><span data-stu-id="e972c-113">Multi-Subnet Failover: Named Instance Resolution For SQL Clustered Instances</span></span>|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|<span data-ttu-id="e972c-114">SQL Native Client 11.0 ODBC</span><span class="sxs-lookup"><span data-stu-id="e972c-114">SQL Native Client 11.0 ODBC</span></span>|<span data-ttu-id="e972c-115">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-115">Yes</span></span>|<span data-ttu-id="e972c-116">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-116">Yes</span></span>|<span data-ttu-id="e972c-117">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-117">Yes</span></span>|<span data-ttu-id="e972c-118">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-118">Yes</span></span>|<span data-ttu-id="e972c-119">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-119">Yes</span></span>|  
|<span data-ttu-id="e972c-120">SQL Native Client 11.0 OLEDB</span><span class="sxs-lookup"><span data-stu-id="e972c-120">SQL Native Client 11.0 OLEDB</span></span>|<span data-ttu-id="e972c-121">いいえ</span><span class="sxs-lookup"><span data-stu-id="e972c-121">No</span></span>|<span data-ttu-id="e972c-122">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-122">Yes</span></span>|<span data-ttu-id="e972c-123">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-123">Yes</span></span>|<span data-ttu-id="e972c-124">いいえ</span><span class="sxs-lookup"><span data-stu-id="e972c-124">No</span></span>|<span data-ttu-id="e972c-125">いいえ</span><span class="sxs-lookup"><span data-stu-id="e972c-125">No</span></span>|  
|<span data-ttu-id="e972c-126">ADO.NET との接続性に関する修正プログラムが適用される .NET Framework 4.0**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="e972c-126">ADO.NET with .NET Framework 4.0 with connectivity patch**<sup>\*</sup>**</span></span> |<span data-ttu-id="e972c-127">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-127">Yes</span></span>|<span data-ttu-id="e972c-128">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-128">Yes</span></span>|<span data-ttu-id="e972c-129">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-129">Yes</span></span>|<span data-ttu-id="e972c-130">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-130">Yes</span></span>|<span data-ttu-id="e972c-131">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-131">Yes</span></span>|  
|<span data-ttu-id="e972c-132">.NET Framework 3.5 SP1 と接続性に関する修正プログラム**<sup>**</sup>\*\*</span><span class="sxs-lookup"><span data-stu-id="e972c-132">ADO.NET with .NET Framework 3.5 SP1 with connectivity patch **<sup>**</sup>\*\*</span></span> |<span data-ttu-id="e972c-133">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-133">Yes</span></span>|<span data-ttu-id="e972c-134">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-134">Yes</span></span>|<span data-ttu-id="e972c-135">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-135">Yes</span></span>|<span data-ttu-id="e972c-136">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-136">Yes</span></span>|<span data-ttu-id="e972c-137">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-137">Yes</span></span>|  
|<span data-ttu-id="e972c-138">Microsoft JDBC Driver 4.0 for SQL Server</span><span class="sxs-lookup"><span data-stu-id="e972c-138">Microsoft JDBC driver 4.0 for SQL Server</span></span>|<span data-ttu-id="e972c-139">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-139">Yes</span></span>|<span data-ttu-id="e972c-140">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-140">Yes</span></span>|<span data-ttu-id="e972c-141">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-141">Yes</span></span>|<span data-ttu-id="e972c-142">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-142">Yes</span></span>|<span data-ttu-id="e972c-143">はい</span><span class="sxs-lookup"><span data-stu-id="e972c-143">Yes</span></span>|  
  
 <span data-ttu-id="e972c-144">**<sup>\*</sup>**.NET Framework 4.0: を使用して ADO .NET の接続性に関する修正プログラムをダウンロードし [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) ます。</span><span class="sxs-lookup"><span data-stu-id="e972c-144">**<sup>\*</sup>**  Download the connectivity patch for ADO .NET with .NET Framework 4.0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211).</span></span>  
  
 <span data-ttu-id="e972c-145">**<sup>**</sup>\* \* .NET Framework 3.5 SP1 で、ADO.NET の接続性に関する修正プログラムをダウンロード [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) します。</span><span class="sxs-lookup"><span data-stu-id="e972c-145">**<sup>**</sup>\*\*  Download the connectivity patch for ADO.NET with .NET Framework 3.5 SP1: [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e972c-146">クライアントは、可用性グループ リスナーに接続するために、TCP 接続文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e972c-146">To connect to an availability group listener, a client must use a TCP connection string.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e972c-147">関連タスク</span><span class="sxs-lookup"><span data-stu-id="e972c-147">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e972c-148">可用性グループの作成と構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e972c-148">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="e972c-149">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e972c-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="e972c-150">参照</span><span class="sxs-lookup"><span data-stu-id="e972c-150">See Also</span></span>  
 <span data-ttu-id="e972c-151">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e972c-151">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e972c-152">[フェールオーバークラスタリングと AlwaysOn 可用性グループ &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e972c-152">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e972c-153">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e972c-153">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="e972c-154">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="e972c-154">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="e972c-155">[可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e972c-155">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 <span data-ttu-id="e972c-156">[高可用性とディザスターリカバリーのための AlwaysOn ソリューションガイドの Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=227600) </span><span class="sxs-lookup"><span data-stu-id="e972c-156">[Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](https://go.microsoft.com/fwlink/?LinkId=227600) </span></span>  
 <span data-ttu-id="e972c-157">[SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ](https://blogs.msdn.com/b/sqlalwayson/) </span><span class="sxs-lookup"><span data-stu-id="e972c-157">[SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog](https://blogs.msdn.com/b/sqlalwayson/) </span></span>  
 <span data-ttu-id="e972c-158">[A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2 (Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7、または Windows Server 2008 R2 を実行しているコンピューターからの IPSec 接続の再接続時に長時間の遅延が発生する)](https://support.microsoft.com/kb/980915) </span><span class="sxs-lookup"><span data-stu-id="e972c-158">[A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2](https://support.microsoft.com/kb/980915) </span></span>  
 <span data-ttu-id="e972c-159">[クラスター サービスが Windows Server 2008 R2 で IPv6 IP アドレスのフェールオーバーに約 30 秒かかる](https://support.microsoft.com/kb/2578113) </span><span class="sxs-lookup"><span data-stu-id="e972c-159">[The Cluster service takes about 30 seconds to fail over IPv6 IP addresses in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113) </span></span>  
 [<span data-ttu-id="e972c-160">クラスターとアプリケーション サーバー間にルーターがない場合にフェールオーバー操作が遅い</span><span class="sxs-lookup"><span data-stu-id="e972c-160">Slow failover operation if no router exists between the cluster and an application server</span></span>](https://support.microsoft.com/kb/2582281)  
  
  
