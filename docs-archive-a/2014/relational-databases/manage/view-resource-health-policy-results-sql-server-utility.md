---
title: リソース正常性ポリシーの結果の表示 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4ab30ad0e87782f8187370a53747be4cf5d313d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716290"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a><span data-ttu-id="14be1-102">リソース正常性ポリシーの結果の表示 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="14be1-102">View Resource Health Policy Results (SQL Server Utility)</span></span>
  <span data-ttu-id="14be1-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のマネージド インスタンスおよびデータ層アプリケーションに関する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ユーティリティのリソース パラメーターを表示するには、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] でユーティリティのダッシュボードを使用します。</span><span class="sxs-lookup"><span data-stu-id="14be1-103">Use the Utility dashboard in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="14be1-104">詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14be1-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a><span data-ttu-id="14be1-105">SQL Server ユーティリティのリソース正常性ポリシーの結果の表示</span><span class="sxs-lookup"><span data-stu-id="14be1-105">View SQL Server Utility resource health policy results.</span></span>  
  
1.  <span data-ttu-id="14be1-106">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS) で、 **[表示]** をクリックし、 **[ユーティリティ エクスプローラー]** をクリックして、ユーティリティ エクスプローラーのナビゲーション ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="14be1-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS), click **View**, then click **Utility Explorer** to view the Utility Explorer navigation pane.</span></span> <span data-ttu-id="14be1-107">コンテンツ ウィンドウを表示するには、 **[表示]** をクリックし、 **[ユーティリティ エクスプローラーのコンテンツ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14be1-107">To view the content pane, click **View**, then click **Utility Explorer Content**.</span></span>  
  
2.  <span data-ttu-id="14be1-108">ナビゲーション ウィンドウで、![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility") (**ユーティリティへの接続**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14be1-108">In the navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span> <span data-ttu-id="14be1-109">ユーティリティ コントロール ポイント (UCP) を作成していない場合、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスまたはデータ層アプリケーションを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ユーティリティに登録していない場合は、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14be1-109">If you have not created a utility control point (UCP) or if you have not enrolled instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or data-tier applications into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
3.  <span data-ttu-id="14be1-110">UCP ノードをクリックし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マネージド インスタンスおよびデータ層アプリケーションの概要データを表示します (更新するには右クリックします)。</span><span class="sxs-lookup"><span data-stu-id="14be1-110">Click the UCP node to view summary data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="14be1-111">ダッシュボードのデータは、コンテンツ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="14be1-111">Dashboard data is displayed in the content pane.</span></span>  
  
4.  <span data-ttu-id="14be1-112">**[マネージド インスタンス]** ノードをクリックし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マネージド インスタンスのリスト ビュー データを表示します (更新するには右クリックします)。</span><span class="sxs-lookup"><span data-stu-id="14be1-112">Click the **Managed Instances** node to view list view data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (right-click to refresh).</span></span> <span data-ttu-id="14be1-113">リスト ビューのデータは、コンテンツ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="14be1-113">List view data is displayed in the content pane.</span></span>  
  
5.  <span data-ttu-id="14be1-114">**[配置済みのデータ層アプリケーション]** ノードをクリックし、データ層アプリケーションのリスト ビュー データを表示します (更新するには右クリックします)。</span><span class="sxs-lookup"><span data-stu-id="14be1-114">Click the **Deployed Data-tier Applications** node to view list view data for data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="14be1-115">リスト ビューのデータは、コンテンツ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="14be1-115">List view data is displayed in the content pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14be1-116">参照</span><span class="sxs-lookup"><span data-stu-id="14be1-116">See Also</span></span>  
 <span data-ttu-id="14be1-117">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="14be1-117">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="14be1-118">[CPU 使用率のポリシー &#40;SQL Server ユーティリティのノイズを減らす&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="14be1-118">[Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span></span>  
 <span data-ttu-id="14be1-119">[配置されたデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="14be1-119">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="14be1-120">[Managed Instance の詳細 &#40;SQL Server ユーティリティ&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="14be1-120">[Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="14be1-121">ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;</span><span class="sxs-lookup"><span data-stu-id="14be1-121">Utility Administration &#40;SQL Server Utility&#41;</span></span>](../../database-engine/utility-administration-sql-server-utility.md)  
  
  
