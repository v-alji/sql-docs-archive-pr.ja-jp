---
title: リソース正常性ポリシーの定義の変更 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.UTILITY.ADMINISTRATION.F1
ms.assetid: 27bec0b6-92e9-448e-8c70-fe36802cf128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d2651a2dd0b4994a6dacaad6c01d3f1ec68c98e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640928"
---
# <a name="modify-a-resource-health-policy-definition-sql-server-utility"></a><span data-ttu-id="a5a29-102">リソース正常性ポリシーの定義の変更 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="a5a29-102">Modify a Resource Health Policy Definition (SQL Server Utility)</span></span>
  <span data-ttu-id="a5a29-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でリソース正常性ポリシーの定義を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-103">This topic describes how to modify a resource health policy definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a5a29-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティでリソース使用率のポリシーを変更する前に、ユーティリティ コントロール ポイント (UCP) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5a29-104">Before you modify a resource utilization policy in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="a5a29-105">詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5a29-105">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a5a29-106">ユーティリティのリソース使用率のポリシーは、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンス用に構成できます。</span><span class="sxs-lookup"><span data-stu-id="a5a29-106">Utility resource utilization policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5a29-107">リソース使用率のポリシーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスすべてに対してグローバルに定義できます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、データ層アプリケーションごと、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスごとに個別に定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5a29-107">Resource utilization policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a5a29-108">さらに、グローバル ポリシーを実装し、個々のデータ層アプリケーションまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の個々のマネージド インスタンスを独自のポリシー定義を使用して構成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="a5a29-108">You can also implement global policies and have individual data-tier applications or managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configured with their own policy definitions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a5a29-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a5a29-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="modify-global-resource-utilization-policies-in-a-sql-server-utility"></a><span data-ttu-id="a5a29-110">SQL Server ユーティリティによるグローバル リソース使用率のポリシーの変更</span><span class="sxs-lookup"><span data-stu-id="a5a29-110">Modify global resource utilization policies in a SQL Server Utility.</span></span>  
  
1.  <span data-ttu-id="a5a29-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で UCP に接続します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-111">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5a29-112">ユーティリティ エクスプローラーのナビゲーション ウィンドウで、 **[ユーティリティ管理]** をクリックして、グローバルな監視ポリシーを表示または変更した後、ユーティリティ エクスプローラーのコンテンツ ウィンドウで **[ポリシー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-112">In the Utility Explorer navigation pane, click **Utility Administration** to view or modify global monitoring policies, then click the **Policy** tab in the Utility Explorer content pane.</span></span>  
  
3.  <span data-ttu-id="a5a29-113">ユーティリティ エクスプローラーのコンテンツ ウィンドウで、矢印またはポリシーの説明をクリックして、 **[グローバルなデータ層監視ポリシーの設定]** または **[グローバルなマネージド インスタンス監視ポリシーの設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-113">In the Utility Explorer content pane, select **Set global data-tier monitoring policies** or **Set global managed instance monitoring policies** by clicking on the arrow or the policy description.</span></span>  
  
4.  <span data-ttu-id="a5a29-114">ポリシーの説明の右側にあるコントロールを使用して、過小使用ポリシーまたは過大使用ポリシーのしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-114">Use the controls on the right side of the policy descriptions to set underutilization or overutilization policy thresholds.</span></span>  
  
5.  <span data-ttu-id="a5a29-115">必要に応じて、 **[適用]** 、 **[破棄]** 、または **[既定値に戻す]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-115">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="a5a29-116">ポリシーの変更は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードおよびリスト ビューの詳細に反映されるまで最大 15 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5a29-116">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
6.  <span data-ttu-id="a5a29-117">データを更新するには、ユーティリティ エクスプローラーのナビゲーション ウィンドウで **[ユーティリティ管理]** ノードを右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-117">To refresh data, right-click on the **Utility Administration** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
#### <a name="modify-resource-health-policy-definitions-for-an-individual-data-tier-application-or-an-individual-managed-instance-of-sql-server-in-a-sql-server-utility"></a><span data-ttu-id="a5a29-118">SQL Server ユーティリティによる個々のデータ層アプリケーションまたは SQL Server マネージド インスタンスのリソース正常性ポリシー定義の変更</span><span class="sxs-lookup"><span data-stu-id="a5a29-118">Modify resource health policy definitions for an individual data-tier application or an individual managed instance of SQL Server in a SQL Server Utility</span></span>  
  
1.  <span data-ttu-id="a5a29-119">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で UCP に接続します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-119">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="a5a29-120">ユーティリティ エクスプローラーのナビゲーション ウィンドウで、 **[配置済みのデータ層アプリケーション]** または **[マネージド インスタンス]** をクリックして、個々のデータ層アプリケーションやマネージド インスタンスの監視ポリシーを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-120">In the Utility Explorer navigation pane, click **Deployed Date-tier Applications**, or click **Managed Instances**, to view or modify monitoring policies for an individual data-tier application or managed instance.</span></span>  
  
3.  <span data-ttu-id="a5a29-121">ユーティリティ エクスプローラーのコンテンツ ウィンドウのリスト ビューで、ポリシーを変更するデータ層アプリケーションまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前をクリックし、 **[ポリシーの詳細]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-121">In the Utility Explorer content pane list view, click the data-tier application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name whose policies you would like to modify, then click on the **Policy Details** tab.</span></span>  
  
4.  <span data-ttu-id="a5a29-122">矢印またはポリシーの説明をクリックして、表示または変更するポリシーを選択します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-122">Select the policy to view or modify by clicking on the arrow or the policy description.</span></span> <span data-ttu-id="a5a29-123">既定では、グローバル ポリシーが選択されます。</span><span class="sxs-lookup"><span data-stu-id="a5a29-123">Global policies are selected by default.</span></span>  
  
5.  <span data-ttu-id="a5a29-124">グローバル ポリシーをオーバーライドして、指定したデータ層アプリケーションに個別のポリシー定義を実装するには、 **[グローバル ポリシーをオーバーライド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-124">Select the radio button to **Override the global policy** to override global policies and implement an individual policy definition for the specified data-tier application.</span></span>  
  
6.  <span data-ttu-id="a5a29-125">ポリシーの説明の右側にあるコントロールを使用して、過小使用ポリシーまたは過大使用ポリシーのしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a5a29-125">Use the controls on the right side of the policy description to set underutilization or overutilization policy thresholds.</span></span>  
  
7.  <span data-ttu-id="a5a29-126">必要に応じて、 **[適用]** 、 **[破棄]** 、または **[既定値に戻す]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-126">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="a5a29-127">ポリシーの変更は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードおよびリスト ビューの詳細に反映されるまで最大 15 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5a29-127">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
8.  <span data-ttu-id="a5a29-128">データを更新するには、ユーティリティ エクスプローラーのナビゲーション ウィンドウで **[配置済みのデータ層アプリケーション]** ノードを右クリックし、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5a29-128">To refresh data, right-click on the **Deployed Data-tier Applications** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a29-129">参照</span><span class="sxs-lookup"><span data-stu-id="a5a29-129">See Also</span></span>  
 <span data-ttu-id="a5a29-130">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a5a29-130">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="a5a29-131">リソース正常性ポリシーの結果の表示 &#40;SQL Server ユーティリティ&#40;</span><span class="sxs-lookup"><span data-stu-id="a5a29-131">View Resource Health Policy Results &#40;SQL Server Utility&#41;</span></span>](view-resource-health-policy-results-sql-server-utility.md)  
  
  
