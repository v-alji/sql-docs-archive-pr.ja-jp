---
title: ビジネス ルール (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 00ac4b7d8970978ef111d56e5a809ada36362583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645728"
---
# <a name="business-rules-master-data-services"></a><span data-ttu-id="4bddb-102">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-102">Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="4bddb-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のビジネス ルールは、マスター データの品質と精度を保証するために使用するルールです。</span><span class="sxs-lookup"><span data-stu-id="4bddb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a business rule is a rule that you use to ensure the quality and accuracy of your master data.</span></span> <span data-ttu-id="4bddb-104">ビジネス ルールを使用して自動的にデータを更新したり、電子メールを送信したり、ビジネス プロセスまたはワークフローを開始したりできます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-104">You can use a business rule to automatically update data, to send email, or to start a business process or workflow.</span></span>  
  
## <a name="create-and-publish-business-rules"></a><span data-ttu-id="4bddb-105">ビジネス ルールの作成およびパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="4bddb-105">Create and Publish Business Rules</span></span>  
 <span data-ttu-id="4bddb-106">ビジネス ルールは、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で作成する `If/Then` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4bddb-106">Business rules are `If/Then` statements that you create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="4bddb-107">属性値が特定の条件を満たす場合、アクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-107">If an attribute value meets a specified condition, then an action is taken.</span></span> <span data-ttu-id="4bddb-108">実行可能なアクションは、既定値の設定または値の変更です。</span><span class="sxs-lookup"><span data-stu-id="4bddb-108">Possible actions include setting a default value or changing a value.</span></span> <span data-ttu-id="4bddb-109">これらのアクションを、電子メール通知の送信と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-109">These actions can be combined with sending an email notification.</span></span>  
  
 <span data-ttu-id="4bddb-110">ビジネス ルールは、特定の属性値に基づいて作成する (たとえば、Color=Blue の場合にアクションを実行する) か、属性値の変更に基づいて作成する (たとえば、Color 属性の値が変更されたときにアクションを実行する) ことができます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-110">Business rules can be based on specific attribute values (for example, take action if Color=Blue), or when attribute values change (for example, take action if the value of the Color attribute changes).</span></span> <span data-ttu-id="4bddb-111">不特定の変更の追跡の詳細については、「[変更の追跡 &#40;マスター データ サービス&#41;](change-tracking-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bddb-111">For more information about tracking non-specific changes, see [Change Tracking &#40;Master Data Services&#41;](change-tracking-master-data-services.md).</span></span>  
  
 <span data-ttu-id="4bddb-112">ビジネス ルールを使用するには、ルールを作成してパブリッシュし、パブリッシュしたルールをデータに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-112">To use business rules you must first create and publish your rules, then apply the published rules to data.</span></span> <span data-ttu-id="4bddb-113">バージョンを検証することによって、バージョンのデータのサブセットまたはすべてのデータにルールを適用できます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-113">You can apply rules to subsets of data or to all data for a version by validating the version.</span></span> <span data-ttu-id="4bddb-114">バージョンは、すべての属性がビジネス ルール検証に合格するまでコミットできません。</span><span class="sxs-lookup"><span data-stu-id="4bddb-114">A version cannot be committed until all attributes pass business rule validation.</span></span>  
  
 <span data-ttu-id="4bddb-115">ビジネス ルール検証に合格していない属性値を追加しようとした場合でも、値は保存されます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-115">If a user attempts to add an attribute value that doesn't pass business rule validation, the value can still be saved.</span></span> <span data-ttu-id="4bddb-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]に表示される検証の問題は、確認して修正できます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-116">You can review and correct validation issues, which are displayed in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="4bddb-117">モデル配置パッケージを作成するときにビジネス ルールを含める場合は、パッケージ内のバージョンからデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-117">When you create a model deployment package, if you want to include business rules you must include data from the version in the package.</span></span>  
  
 <span data-ttu-id="4bddb-118">**OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成してください。</span><span class="sxs-lookup"><span data-stu-id="4bddb-118">If you create a business rule that uses the **OR** operator, you should create a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="4bddb-119">そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-119">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="how-business-rules-are-applied"></a><span data-ttu-id="4bddb-120">ビジネス ルールの適用方法</span><span class="sxs-lookup"><span data-stu-id="4bddb-120">How Business Rules Are Applied</span></span>  
 <span data-ttu-id="4bddb-121">実行されるルールに優先順位を設定できます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-121">You can set priority order for rules to run in.</span></span> <span data-ttu-id="4bddb-122">ただし、優先順位が適用される前に、ビジネス ルールはそのルールによって実行されるアクションの種類に基づいて適用されます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-122">However, before priority is taken into account, business rules are applied based on the type of action the rule takes.</span></span> <span data-ttu-id="4bddb-123">順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4bddb-123">The order is as follows:</span></span>  
  
1.  <span data-ttu-id="4bddb-124">**既定値**</span><span class="sxs-lookup"><span data-stu-id="4bddb-124">**Default Value**</span></span>  
  
2.  <span data-ttu-id="4bddb-125">**値の変更**</span><span class="sxs-lookup"><span data-stu-id="4bddb-125">**Change Value**</span></span>  
  
3.  <span data-ttu-id="4bddb-126">**検証**</span><span class="sxs-lookup"><span data-stu-id="4bddb-126">**Validation**</span></span>  
  
4.  <span data-ttu-id="4bddb-127">**外部アクション**</span><span class="sxs-lookup"><span data-stu-id="4bddb-127">**External Action**</span></span>  
  
 <span data-ttu-id="4bddb-128">これらのグループの中で、アクションが優先順位に基づいて (値が小さいものから順に) 適用されます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-128">Within these groups, actions are applied in priority order, from lowest to highest.</span></span> <span data-ttu-id="4bddb-129">そのため、たとえば別々の 4 つのルールに **既定値** アクションが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-129">So for example, four separate rules might have **Default Value** actions.</span></span> <span data-ttu-id="4bddb-130">最初に実行される **既定値** アクションは、Web UI で指定された優先順位によって決まります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-130">The **Default Value** action that occurs first depends on the priority order specified in the web UI.</span></span>  
  
 <span data-ttu-id="4bddb-131">ルールの適用については、次の点についても注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bddb-131">Other important notes about applying rules:</span></span>  
  
-   <span data-ttu-id="4bddb-132">ビジネス ルールが除外された場合、または **[アクティブ]** の状態でパブリッシュされていない場合、そのルールは使用可能ですが、ビジネス ルールが適用されるときには対象となりません。</span><span class="sxs-lookup"><span data-stu-id="4bddb-132">If a business rule is excluded or is not published with a status of **Active**, the rule is still available but is not included when business rules are applied.</span></span>  
  
-   <span data-ttu-id="4bddb-133">ビジネス ルールは、すべてのリーフ メンバーまたはすべての統合メンバーのいずれかの属性値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-133">Business rules apply to the attribute values for all leaf or all consolidated members, not both.</span></span>  
  
-   <span data-ttu-id="4bddb-134">ビジネス ルールは、 **[未処理]** または **[ロック済み]** である、任意のバージョンのモデルに適用できます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-134">Business rules can be applied to any version of a model that is **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="4bddb-135">ビジネス ルールに適用するときにデータに加えられた変更は、トランザクションとしては記録されません。</span><span class="sxs-lookup"><span data-stu-id="4bddb-135">Changes made to data when business rules are applied are not logged as transactions.</span></span>  
  
-   <span data-ttu-id="4bddb-136">ビジネス ルールには、 **"がワークフローで始まる"** アクションを複数含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="4bddb-136">A business rule cannot contain more than one **start workflow** action.</span></span>  
  
## <a name="system-settings"></a><span data-ttu-id="4bddb-137">システム設定</span><span class="sxs-lookup"><span data-stu-id="4bddb-137">System Settings</span></span>  
 <span data-ttu-id="4bddb-138">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、ビジネス ルールに影響する設定が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="4bddb-138">There are two settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect business rules.</span></span> <span data-ttu-id="4bddb-139">これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するかSystem Settings テーブルで直接調整することができます。</span><span class="sxs-lookup"><span data-stu-id="4bddb-139">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table.</span></span> <span data-ttu-id="4bddb-140">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bddb-140">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4bddb-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4bddb-141">Related Tasks</span></span>  
  
|<span data-ttu-id="4bddb-142">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="4bddb-142">Task Description</span></span>|<span data-ttu-id="4bddb-143">トピック</span><span class="sxs-lookup"><span data-stu-id="4bddb-143">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="4bddb-144">新しいビジネス ルールを作成してパブリッシュする。</span><span class="sxs-lookup"><span data-stu-id="4bddb-144">Create and publish a new business rule.</span></span>|[<span data-ttu-id="4bddb-145">ビジネス ルールを作成しパブリッシュする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-145">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="4bddb-146">ビジネス ルールに複数の条件を追加する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-146">Add multiple conditions to a business rule.</span></span>|[<span data-ttu-id="4bddb-147">ビジネス ルールに複数の条件を追加する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="4bddb-147">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="4bddb-148">属性が値を持つことを必須とするビジネス ルールを作成する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-148">Create a business rule to require that attributes have values.</span></span>|[<span data-ttu-id="4bddb-149">属性値を要求する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="4bddb-149">Require Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|<span data-ttu-id="4bddb-150">属性値の変更に基づくアクションを行うためのビジネス ルールを作成する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-150">Create a business rule to take an action based on changes to attribute values.</span></span>|[<span data-ttu-id="4bddb-151">属性値の変更に基づいてアクションを開始する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-151">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|<span data-ttu-id="4bddb-152">既存のビジネス ルールの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-152">Change the name of an existing business rule.</span></span>|[<span data-ttu-id="4bddb-153">ビジネス ルールの名前を変更する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="4bddb-153">Change a Business Rule Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|<span data-ttu-id="4bddb-154">ビジネス ルールが適用されたときに通知を送信するように [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を構成する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-154">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when business rules are applied.</span></span>|[<span data-ttu-id="4bddb-155">通知を送信するようにビジネス ルールを構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-155">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|<span data-ttu-id="4bddb-156">特定のメンバーにビジネス ルールを適用する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-156">Apply business rules to specific members.</span></span>|[<span data-ttu-id="4bddb-157">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-157">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|<span data-ttu-id="4bddb-158">ビジネス ルールを除外して、使用されないようにする。</span><span class="sxs-lookup"><span data-stu-id="4bddb-158">Exclude a business rule so it is not used.</span></span>|[<span data-ttu-id="4bddb-159">ビジネス ルールを除外する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="4bddb-159">Exclude a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="4bddb-160">既存のビジネス ルールを削除する。</span><span class="sxs-lookup"><span data-stu-id="4bddb-160">Delete an existing business rule.</span></span>|[<span data-ttu-id="4bddb-161">ビジネス ルールを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-161">Delete a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="4bddb-162">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="4bddb-162">Related Content</span></span>  
  
-   [<span data-ttu-id="4bddb-163">マスター データ サービス概要</span><span class="sxs-lookup"><span data-stu-id="4bddb-163">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="4bddb-164">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-164">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="4bddb-165">検証 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4bddb-165">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="4bddb-166">変更の追跡 &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="4bddb-166">Change Tracking &#40;Master Data Services&#41;</span></span>](change-tracking-master-data-services.md)  
  
  
