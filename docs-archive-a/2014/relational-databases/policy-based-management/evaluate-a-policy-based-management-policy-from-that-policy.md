---
title: ポリシーからのポリシー ベースの管理ポリシーの評価 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 207c86f1465c49238fc9b50ee75489b43d956caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642738"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a><span data-ttu-id="5de87-102">ポリシーからのポリシー ベースの管理ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="5de87-102">Evaluate a Policy-Based Management Policy from That Policy</span></span>
  <span data-ttu-id="5de87-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシーを使用してそのポリシーを評価する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5de87-103">This topic describes how to evaluate a policy using that policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5de87-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5de87-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5de87-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5de87-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5de87-106">Security</span><span class="sxs-lookup"><span data-stu-id="5de87-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5de87-107">**以下を使用してポリシーを評価するには:**</span><span class="sxs-lookup"><span data-stu-id="5de87-107">**To evaluate a policy, using:**</span></span>  
  
     [<span data-ttu-id="5de87-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5de87-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5de87-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="5de87-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5de87-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5de87-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5de87-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="5de87-111">Permissions</span></span>  
 <span data-ttu-id="5de87-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="5de87-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5de87-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5de87-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy"></a><span data-ttu-id="5de87-114">ポリシーを評価するには</span><span class="sxs-lookup"><span data-stu-id="5de87-114">To evaluate a policy</span></span>  
  
1.  <span data-ttu-id="5de87-115">**オブジェクト エクスプローラー**で、評価するポリシーを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="5de87-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="5de87-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5de87-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="5de87-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="5de87-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="5de87-118">プラス記号をクリックして **[ポリシー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5de87-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="5de87-119">評価するポリシーを右クリックして、 **[評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5de87-119">Right-click the policy that you want to evaluate and select **Evaluate**.</span></span>  
  
6.  <span data-ttu-id="5de87-120">**[評価の結果]**  ダイアログ ボックスに、ポリシーの評価結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5de87-120">In the **Evaluate Results**  dialog box, you see the results of the policy evaluation.</span></span> <span data-ttu-id="5de87-121">ポリシーに準拠せず、ポリシー ベースの管理で再構成可能なプロパティを持つ対象の場合は、 **[適用]** をクリックしてポリシーへの準拠を適用できます。</span><span class="sxs-lookup"><span data-stu-id="5de87-121">For targets that do not comply with the policy and have properties that can be reconfigured by Policy-Based Management, you can enforce compliance by clicking **Apply**.</span></span> <span data-ttu-id="5de87-122">**[ポリシーの評価]** ダイアログ ボックスで使用可能なオプションの詳細については、「 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) 」および「 [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5de87-122">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) and [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).</span></span>  
  
7.  <span data-ttu-id="5de87-123">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5de87-123">When finished, click **Close**.</span></span>  
  
  
