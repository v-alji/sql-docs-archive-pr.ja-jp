---
title: '[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [全般] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.newgroup.f1
- sql12.swb.dmf.policy.f1
- sql12.swb.dmf.policy.filter.f1
ms.assetid: c00bebd0-d04b-4c64-840e-8b7a2c603436
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4b67cb8faf18001b841824b806e7befc0683d457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634476"
---
# <a name="create-new-policy-or-open-policy-dialog-box-general-page"></a><span data-ttu-id="c5065-102">[新しいポリシーの作成] または [ポリシーを開く] ダイアログ ボックスの [全般] ページ</span><span class="sxs-lookup"><span data-stu-id="c5065-102">Create New Policy or Open Policy Dialog Box, General Page</span></span>
  <span data-ttu-id="c5065-103">このダイアログ ボックスを使用すると、ポリシー ベースの管理ポリシーを新規作成したり、既存のポリシーを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="c5065-103">Use this dialog box to create a new Policy-Based Management policy or modify an existing policy.</span></span> <span data-ttu-id="c5065-104">ポリシーの適用対象を一部のサーバーに制限するには、 **[対象]** 領域と **[サーバーの制限]** 領域をフィルターとして使用します。</span><span class="sxs-lookup"><span data-stu-id="c5065-104">Use the **Against targets** and **Server restriction** areas as a filter to limit policies to a subset of all possible targets.</span></span> <span data-ttu-id="c5065-105">対象フィルターとして使用する条件は、物理ファセットで定義する必要があり、関数や LIKE 演算子をその条件に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5065-105">For conditions to be used as target filters, they must be defined on a physical facet, must not contain functions, and must not contain the LIKE operator.</span></span> <span data-ttu-id="c5065-106">ポリシーのオブジェクト セットをシステムが計算する際、既定ではシステム オブジェクトが除外されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-106">When the system computes the object set for a policy, by default the system objects are excluded.</span></span>  <span data-ttu-id="c5065-107">たとえば、ポリシーのオブジェクト セットがすべてのテーブルを参照する場合、システム テーブルにはそのポリシーが適用されません。</span><span class="sxs-lookup"><span data-stu-id="c5065-107">For example, if the object set of the policy refers to all tables, the policy will not apply to system tables.</span></span> <span data-ttu-id="c5065-108">システム オブジェクトに対してポリシーを評価する必要がある場合は、ユーザーが、それらのオブジェクト セットに対し、システム オブジェクトを明示的に追加できます。</span><span class="sxs-lookup"><span data-stu-id="c5065-108">If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set.</span></span> <span data-ttu-id="c5065-109">**"スケジュールに基づいて確認"** の評価モードではすべてのポリシーがサポートされますが、パフォーマンス上の理由により、 **"変更時に確認"** の評価モードでは、任意のオブジェクト セットを含んだポリシーは、必ずしもすべてサポートされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c5065-109">However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode.</span></span> <span data-ttu-id="c5065-110">詳細については、[https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5065-110">For more information, see [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5065-111">オプション</span><span class="sxs-lookup"><span data-stu-id="c5065-111">Options</span></span>  
 <span data-ttu-id="c5065-112">**Name**</span><span class="sxs-lookup"><span data-stu-id="c5065-112">**Name**</span></span>  
 <span data-ttu-id="c5065-113">新しいポリシーの場合は、新しいポリシー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="c5065-113">For a new policy, type the new policy name.</span></span> <span data-ttu-id="c5065-114">既存のポリシーの場合は、その名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-114">For an existing policy, the name is displayed.</span></span>  
  
 <span data-ttu-id="c5065-115">**有効**</span><span class="sxs-lookup"><span data-stu-id="c5065-115">**Enabled**</span></span>  
 <span data-ttu-id="c5065-116">ポリシーを有効にするには、 **[有効]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c5065-116">Select the **Enabled** check box to enable the policy.</span></span> <span data-ttu-id="c5065-117">ポリシーを無効にするには、 **[有効]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c5065-117">Clear the **Enabled** check box to disable the policy.</span></span> <span data-ttu-id="c5065-118">**[有効]** チェック ボックスは、ポリシー オートメーションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-118">The **Enabled** box applies to policy automation.</span></span> <span data-ttu-id="c5065-119">このチェック ボックスをオンまたはオフにすると、ポリシー オートメーション システムが作成または削除されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-119">It creates or removes the automation system for the policy.</span></span> <span data-ttu-id="c5065-120">オートメーションでは、次のメカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5065-120">Automation uses the following mechanisms:</span></span>  
  
 <span data-ttu-id="c5065-121">**変更中 - 禁止**</span><span class="sxs-lookup"><span data-stu-id="c5065-121">**On change: prevent**</span></span>  
 <span data-ttu-id="c5065-122">データベース トリガーによって準拠が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-122">A database trigger enforces compliance.</span></span>  
  
 <span data-ttu-id="c5065-123">**[変更中 - ログのみ]**</span><span class="sxs-lookup"><span data-stu-id="c5065-123">**On change: log only**</span></span>  
 <span data-ttu-id="c5065-124">Notification Services イベントによって準拠がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="c5065-124">A notification services event checks for compliance.</span></span>  
  
 <span data-ttu-id="c5065-125">**スケジュールで実行**</span><span class="sxs-lookup"><span data-stu-id="c5065-125">**On schedule**</span></span>  
 <span data-ttu-id="c5065-126">スケジュールに従って準拠をチェックする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-126">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created to check for compliance on a schedule.</span></span>  
  
 <span data-ttu-id="c5065-127">**[要求時]** 評価モードを使用して実行されるポリシーでは、このチェック ボックスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c5065-127">Policies that are run using **On demand** evaluation mode do not use this check box.</span></span>  
  
 <span data-ttu-id="c5065-128">**[条件の確認]**</span><span class="sxs-lookup"><span data-stu-id="c5065-128">**Check condition**</span></span>  
 <span data-ttu-id="c5065-129">このポリシーが使用する、ポリシー ベースの管理条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5065-129">Select the Policy-Based Management condition that this policy uses.</span></span> <span data-ttu-id="c5065-130">サーバー上にある、関連するポリシー ベースの管理ファセットのすべての条件が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-130">All conditions on the server for the associated Policy-Based Management facet are listed.</span></span> <span data-ttu-id="c5065-131">新しい条件を作成するには、 **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5065-131">Click **New condition** to create a new condition.</span></span> <span data-ttu-id="c5065-132">条件を変更するには、参照ボタン ( **[…]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5065-132">Click the ellipsis (**...**) button to modify the condition.</span></span>  
  
 <span data-ttu-id="c5065-133">**[対象]**</span><span class="sxs-lookup"><span data-stu-id="c5065-133">**Against targets**</span></span>  
 <span data-ttu-id="c5065-134">フィルター式を完成するために、このファセットで使用できる対象の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5065-134">Select the target types that are available for this facet to complete a filter expression.</span></span>  
  
 <span data-ttu-id="c5065-135">**[評価モード]**</span><span class="sxs-lookup"><span data-stu-id="c5065-135">**Evaluation Mode**</span></span>  
 <span data-ttu-id="c5065-136">ポリシーの評価モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="c5065-136">Select the evaluation mode for the policy.</span></span> <span data-ttu-id="c5065-137">ポリシーの中には、チェックはできるものの、適用することができないポリシーがあります。</span><span class="sxs-lookup"><span data-stu-id="c5065-137">Some policies can be checked but not enforced.</span></span> <span data-ttu-id="c5065-138">評価モードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5065-138">The evaluation modes are as follows:</span></span>  
  
 <span data-ttu-id="c5065-139">**[要求時]**</span><span class="sxs-lookup"><span data-stu-id="c5065-139">**On demand**</span></span>  
 <span data-ttu-id="c5065-140">ポリシーが実行されるのは、 **[評価]** ダイアログ ボックスから実行された場合だけです。</span><span class="sxs-lookup"><span data-stu-id="c5065-140">Policy will only be run when you run it from the **Evaluate** dialog box.</span></span>  
  
 <span data-ttu-id="c5065-141">**スケジュールで実行**</span><span class="sxs-lookup"><span data-stu-id="c5065-141">**On schedule**</span></span>  
 <span data-ttu-id="c5065-142">定期的にポリシーを評価して、準拠していないポリシーのログ エントリを記録し、レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c5065-142">Periodically evaluates the policy, records a log entry for policies that have out-of-compliance, and creates a report.</span></span> <span data-ttu-id="c5065-143">**[スケジュール]** ボックスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5065-143">Enables the **Schedule** box.</span></span>  
  
 <span data-ttu-id="c5065-144">**[変更中 - ログのみ]**</span><span class="sxs-lookup"><span data-stu-id="c5065-144">**On change: log only**</span></span>  
 <span data-ttu-id="c5065-145">このモードでは、準拠していない変更が試みられたときに、ポリシー違反がログに記録されます。ただし、変更は防止されません。</span><span class="sxs-lookup"><span data-stu-id="c5065-145">When changes are tried, this option does not prevent out-of-compliance changes, but logs policy violations.</span></span>  
  
 <span data-ttu-id="c5065-146">**変更中 - 禁止**</span><span class="sxs-lookup"><span data-stu-id="c5065-146">**On change: prevent**</span></span>  
 <span data-ttu-id="c5065-147">このモードでは、変更が試みられたときに、ポリシーに違反する変更が防止されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-147">When changes are tried, this option prevents changes that would violate the policy.</span></span>  
  
 <span data-ttu-id="c5065-148">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="c5065-148">**Schedule**</span></span>  
 <span data-ttu-id="c5065-149">このオプションは、 **[スケジュールで実行]** 評価モードが選択されている場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5065-149">This option appears when **On schedule** evaluation mode is selected.</span></span> <span data-ttu-id="c5065-150">スケジュールの名前を入力します。 **[選択]** をクリックして一覧からスケジュールを選択するか、 **[新規作成]** をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="c5065-150">Type the name of the schedule, click **Pick** to select a schedule from a list, or click **New** to create a new schedule.</span></span> <span data-ttu-id="c5065-151">スケジュール領域を有効にするには、 **[スケジュールで実行]** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5065-151">To enable the schedule area, **On schedule** must be selected.</span></span>  
  
 <span data-ttu-id="c5065-152">**[サーバーの制限]**</span><span class="sxs-lookup"><span data-stu-id="c5065-152">**Server restriction**</span></span>  
 <span data-ttu-id="c5065-153">このポリシーに適したサーバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5065-153">Select the types of servers that are appropriate for this policy.</span></span> <span data-ttu-id="c5065-154">**[なし]** を選択するか、使用可能なサーバーをフィルター処理する条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="c5065-154">Options are **None** or select a condition that filters the possible servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5065-155">参照</span><span class="sxs-lookup"><span data-stu-id="c5065-155">See Also</span></span>  
 [<span data-ttu-id="c5065-156">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="c5065-156">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
