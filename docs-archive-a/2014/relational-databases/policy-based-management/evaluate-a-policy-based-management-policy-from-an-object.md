---
title: オブジェクトからのポリシー ベースの管理ポリシーの評価 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f0de02092c87a727b723a5940805f34a75052e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642736"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a><span data-ttu-id="ca98e-102">オブジェクトからのポリシー ベースの管理ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="ca98e-102">Evaluate a Policy-Based Management Policy from an Object</span></span>
  <span data-ttu-id="ca98e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサーバー インスタンス、データベース、またはデータベース オブジェクトからポリシーを評価する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca98e-103">This topic describes how to evaluate a policy from a server instance, database, or database object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ca98e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ca98e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ca98e-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ca98e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ca98e-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ca98e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ca98e-107">Security</span><span class="sxs-lookup"><span data-stu-id="ca98e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ca98e-108">**以下を使用してオブジェクトからポリシーを評価するには:**</span><span class="sxs-lookup"><span data-stu-id="ca98e-108">**To evaluate a policy from an object, using:**</span></span>  
  
     [<span data-ttu-id="ca98e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca98e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca98e-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="ca98e-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ca98e-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ca98e-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ca98e-112">実行モードは、ポリシーの一部として定義されており、 **[ポリシーの評価]** ダイアログ ボックスで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="ca98e-112">The execution mode is defined as part of the policy and cannot be changed in the **Evaluate Policies** dialog box.</span></span>  
  
-   <span data-ttu-id="ca98e-113">**[ポリシーの評価]** ダイアログ ボックスには、データベース オブジェクトに適したポリシーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ca98e-113">The **Evaluate Policies** dialog box only shows policies appropriate for the database object.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca98e-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ca98e-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca98e-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="ca98e-115">Permissions</span></span>  
 <span data-ttu-id="ca98e-116">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ca98e-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ca98e-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ca98e-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a><span data-ttu-id="ca98e-118">オブジェクトからポリシーを評価するには</span><span class="sxs-lookup"><span data-stu-id="ca98e-118">To evaluate a policy from an object</span></span>  
  
1.  <span data-ttu-id="ca98e-119">オブジェクト エクスプローラーで、サーバー インスタンス、データベース、またはデータベース オブジェクトを右クリックし、 **[ポリシー]** をポイントして、 **[評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca98e-119">In Object Explorer, right-click a server instance, a database, or a database object, point to **Policies**, and select **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="ca98e-120">**[ポリシーの評価]** ダイアログ ボックスで、1 つ以上のポリシーを選択し、 **[評価]** をクリックしてポリシーを評価モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="ca98e-120">In the **Evaluate Policies** dialog box, select one or more policies and click **Evaluate** to run the policy in evaluation mode.</span></span> <span data-ttu-id="ca98e-121">これにより対象セットの準拠レポートが生成されますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再構成されたり、今後の準拠が適用されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="ca98e-121">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span> <span data-ttu-id="ca98e-122">選択したポリシーに準拠せず、ポリシー ベースの管理で再構成可能なプロパティを持つ対象の場合は、 **[適用]** をクリックしてポリシーへの準拠を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ca98e-122">For targets that do not comply with the selected policies and have properties that can be reconfigured by Policy-Based Management, you can enforce policy compliance by clicking **Apply**.</span></span> <span data-ttu-id="ca98e-123">**[ポリシーの評価]** ダイアログ ボックスで使用可能なオプションの詳細については、「 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md)」、「 [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)」、および「 [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca98e-123">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md), and [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="ca98e-124">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ca98e-124">When finished, click **Close**.</span></span>  
  
  
