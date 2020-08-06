---
title: 正常性ポリシーの構成 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c5ee466dd2d5bac2ea64364bfc78de8f2f5bea10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633150"
---
# <a name="configure-health-policies-sql-server-utility"></a><span data-ttu-id="894ef-102">正常性ポリシーの構成 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="894ef-102">Configure Health Policies (SQL Server Utility)</span></span>
  <span data-ttu-id="894ef-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスおよびデータ層アプリケーションに関する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ユーティリティのリソース パラメーターを表示するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードを使用します。</span><span class="sxs-lookup"><span data-stu-id="894ef-103">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="894ef-104">詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="894ef-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="894ef-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーの結果を表示するには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からユーティリティ コントロール ポイントに接続します。</span><span class="sxs-lookup"><span data-stu-id="894ef-105">To view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility health policy results, connect to a utility control point from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="894ef-106">詳細については、「 [ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](use-utility-explorer-to-manage-the-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="894ef-106">For more information, see [Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="894ef-107">ユーティリティの正常性ポリシーは、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンス用に構成できます。</span><span class="sxs-lookup"><span data-stu-id="894ef-107">Utility health policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="894ef-108">正常性ポリシーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのデータ層アプリケーションおよびマネージド インスタンスに対してグローバルに定義できます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ層アプリケーションごと、およびマネージド インスタンスごとに個別に定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="894ef-108">Health policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
## <a name="monitoring-policies-for-data-tier-applications"></a><span data-ttu-id="894ef-109">データ層アプリケーションのポリシーの監視</span><span class="sxs-lookup"><span data-stu-id="894ef-109">Monitoring Policies for Data-tier Applications</span></span>  
 <span data-ttu-id="894ef-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ層アプリケーションの過大使用ポリシーと過小使用ポリシーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="894ef-110">Overutilization and underutilization policies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data-tier applications are as follows:</span></span>  
  
-   <span data-ttu-id="894ef-111">データ層アプリケーションのプロセッサ使用率</span><span class="sxs-lookup"><span data-stu-id="894ef-111">Data-tier application processor utilization.</span></span>  
  
-   <span data-ttu-id="894ef-112">データ層アプリケーションのデータベース ファイル用のファイル領域</span><span class="sxs-lookup"><span data-stu-id="894ef-112">Data-tier application file space for database files.</span></span>  
  
-   <span data-ttu-id="894ef-113">データ層アプリケーションの記憶域ボリューム用のファイル領域</span><span class="sxs-lookup"><span data-stu-id="894ef-113">Data-tier application file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="894ef-114">コンピューターのプロセッサ使用率</span><span class="sxs-lookup"><span data-stu-id="894ef-114">Computer processor utilization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="894ef-115">データ層アプリケーションの場合、記憶域ボリュームとプロセッサ使用率は読み取り専用ポリシーです。</span><span class="sxs-lookup"><span data-stu-id="894ef-115">Storage volume and processor utilization are read-only policies for data-tier applications.</span></span>  
  
 <span data-ttu-id="894ef-116">データ層アプリケーションのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../../database-engine/utility-administration-sql-server-utility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="894ef-116">For more information about viewing or changing global monitoring policies for data-tier applications, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="894ef-117">データ層アプリケーション個々の監視ポリシーの表示および変更の詳細については、「[配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="894ef-117">For more information about viewing or changing monitoring policies for individual data-tier applications, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a><span data-ttu-id="894ef-118">SQL Server のマネージド インスタンスのポリシーの監視</span><span class="sxs-lookup"><span data-stu-id="894ef-118">Monitoring Policies for Managed Instances of SQL Server</span></span>  
 <span data-ttu-id="894ef-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスの過大使用ポリシーと過小使用ポリシーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="894ef-119">Overutilization and underutilization policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are as follows:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="894ef-120">インスタンスのプロセッサ使用率。</span><span class="sxs-lookup"><span data-stu-id="894ef-120">instance processor utilization.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="894ef-121">インスタンスのデータベース ファイル用のファイル領域。</span><span class="sxs-lookup"><span data-stu-id="894ef-121">instance file space for database files.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="894ef-122">インスタンスの記憶域ボリューム用のファイル領域。</span><span class="sxs-lookup"><span data-stu-id="894ef-122">instance file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="894ef-123">コンピューターのプロセッサ使用率</span><span class="sxs-lookup"><span data-stu-id="894ef-123">Computer processor utilization.</span></span>  
  
 <span data-ttu-id="894ef-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../../database-engine/utility-administration-sql-server-utility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="894ef-124">For more information about viewing or changing global monitoring policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="894ef-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の個々のマネージド インスタンスの監視ポリシーの表示および変更の詳細については、「[マネージド インスタンスの詳細 &#40;SQL Server ユーティリティ&#41;](../../database-engine/managed-instance-details-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="894ef-125">For more information about viewing or changing monitoring policies for individual managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894ef-126">参照</span><span class="sxs-lookup"><span data-stu-id="894ef-126">See Also</span></span>  
 <span data-ttu-id="894ef-127">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="894ef-127">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="894ef-128">CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="894ef-128">Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;</span></span>](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
