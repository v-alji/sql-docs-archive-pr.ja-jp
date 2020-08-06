---
title: ポリシー ベースの管理ポリシーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e76b4dce17e00bae5e8ca4fcf071868c0641c786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641632"
---
# <a name="create-a-policy-based-management-policy"></a><span data-ttu-id="3b36f-102">ポリシー ベースの管理ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="3b36f-102">Create a Policy-Based Management Policy</span></span>
  <span data-ttu-id="3b36f-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-103">This topic describes how to create a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3b36f-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3b36f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3b36f-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3b36f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3b36f-106">Security</span><span class="sxs-lookup"><span data-stu-id="3b36f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3b36f-107">**以下を使用してポリシーを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="3b36f-107">**To create a policy, using:**</span></span>  
  
     [<span data-ttu-id="3b36f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b36f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3b36f-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="3b36f-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3b36f-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3b36f-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3b36f-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="3b36f-111">Permissions</span></span>  
 <span data-ttu-id="3b36f-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="3b36f-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3b36f-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3b36f-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-policy"></a><span data-ttu-id="3b36f-114">ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="3b36f-114">To create a policy</span></span>  
  
1.  <span data-ttu-id="3b36f-115">**オブジェクト エクスプローラー**で、プラス記号をクリックして、新しいポリシー ベースの管理ポリシーを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a new a Policy-Based Management policy.</span></span>  
  
2.  <span data-ttu-id="3b36f-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="3b36f-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="3b36f-118">**[ポリシー]** フォルダーを右クリックし、 **[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b36f-118">Right-click the **Policies** folder and select **New Policy**.</span></span>  
  
5.  <span data-ttu-id="3b36f-119">**[新しいポリシーの作成]** ダイアログ ボックスで、 **[名前]** ボックスに、新しいポリシーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-119">In the **Create New Policy** dialog box, in the **Name** box, type the name of the new policy.</span></span>  
  
6.  <span data-ttu-id="3b36f-120">作成されたポリシーを直ちに有効にする場合は、 **[有効]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3b36f-120">If you want the policy to be enabled as soon as it is created, select the **Enabled** check box.</span></span> <span data-ttu-id="3b36f-121">評価モードが **[要求時]** である場合、 **[有効]** チェック ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3b36f-121">If the evaluation mode is **On demand**, the **Enabled** check box is not available.</span></span>  
  
7.  <span data-ttu-id="3b36f-122">**[条件の確認]** ボックスの一覧で、既存の条件の 1 つを選択するか、 **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b36f-122">In the **Check condition** list, select one of the existing conditions, or select **New Condition**.</span></span> <span data-ttu-id="3b36f-123">条件を編集するには、条件を選択し、省略記号ボタン ( **[...]** ) をクリックします。詳細については、「 [新しいポリシー ベースの管理条件の作成](create-a-new-policy-based-management-condition.md) 」または「 [ポリシー ベースの管理条件のプロパティの表示または変更](view-or-modify-the-properties-of-a-policy-based-management-condition.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b36f-123">To edit a condition, select the condition and then click the ellipsis (**...**). For more information, see [Create a New Policy-Based Management Condition](create-a-new-policy-based-management-condition.md) or [View or Modify the Properties of a Policy-Based Management Condition](view-or-modify-the-properties-of-a-policy-based-management-condition.md).</span></span>  
  
8.  <span data-ttu-id="3b36f-124">**[対象]** ボックスで、このポリシーの対象になる種類を 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-124">In the **Against targets** box, select one or more target types for this policy.</span></span> <span data-ttu-id="3b36f-125">一部の条件とファセットは、特定の種類の対象にしか適用できません。</span><span class="sxs-lookup"><span data-stu-id="3b36f-125">Some conditions and facets can only be applied to certain types of targets.</span></span> <span data-ttu-id="3b36f-126">使用可能な対象セットが、関連するボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b36f-126">The available target sets appear in the associated box.</span></span> <span data-ttu-id="3b36f-127">**[すべて]** を展開して、一部の種類の対象に対してフィルター条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-127">Expand **Every** to select a filtering condition for some types of the targets.</span></span> <span data-ttu-id="3b36f-128">対象がこのボックスに表示されていない場合、条件の確認がサーバー レベルのスコープを持っています。</span><span class="sxs-lookup"><span data-stu-id="3b36f-128">If no targets appear in this box, the check condition is scoped at the server level.</span></span>  
  
9. <span data-ttu-id="3b36f-129">**[評価モード]** ボックスで、このポリシーの動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-129">In the **Evaluation Mode** box, select how this policy will behave.</span></span> <span data-ttu-id="3b36f-130">有効な評価モードは、条件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3b36f-130">Different conditions can have different valid evaluation modes.</span></span> <span data-ttu-id="3b36f-131">どの評価モードが有効かの詳細については、「 [ポリシー ベースの管理を使用したサーバーの管理](administer-servers-by-using-policy-based-management.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b36f-131">For more information about which evaluation modes are valid, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
10. <span data-ttu-id="3b36f-132">ポリシーをスケジュールで評価する場合は、評価モードを **[スケジュールで実行]** に設定し、 **[選択]** をクリックしてスケジュールを選択するか、 **[新規作成]** をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-132">If the policy will be evaluated on a schedule, set the evaluation mode to **On schedule**, and then click **Pick** to select a schedule, or click **New** to create a new schedule.</span></span>  
  
11. <span data-ttu-id="3b36f-133">ポリシーを対象の種類のサブセットに制限するには、 **[サーバーの制限]** ボックスで制限条件を選択するか、新しい条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b36f-133">To limit the policy to subset of the target types, in the **Server restriction** box, select from limiting conditions or create a new condition.</span></span>  
  
     <span data-ttu-id="3b36f-134">**[新しいポリシーの作成]** ダイアログ ボックスで使用可能なオプションの詳細については、「 [[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md) 」または「 [[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [説明] ページ](create-new-policy-or-open-policy-dialog-box-description-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b36f-134">For more information on the available options in the **Create New Policy** dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) or [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
12. <span data-ttu-id="3b36f-135">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b36f-135">When finished click **OK**.</span></span>  
  
  
