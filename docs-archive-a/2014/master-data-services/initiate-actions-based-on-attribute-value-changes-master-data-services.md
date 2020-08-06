---
title: 属性値の変更に基づいてアクションを開始する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 50931b9f9c4bd5d08596d485ba695143b9c6594e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713233"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a><span data-ttu-id="7d4bd-102">属性値の変更に基づいてアクションを開始する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7d4bd-102">Initiate Actions Based on Attribute Value Changes (Master Data Services)</span></span>
  <span data-ttu-id="7d4bd-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、属性値に対する変更に基づいてアクションを開始するビジネス ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to initiate actions based on changes to attribute values.</span></span> <span data-ttu-id="7d4bd-104">たとえば、特定の属性値が変更されたときに、値の変更、通知の送信、または外部ワークフローの開始を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-104">For example, when a specific attribute value changes, you may want to change a value, send a notification, or start an external workflow.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7d4bd-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="7d4bd-105">Prerequisites</span></span>  
 <span data-ttu-id="7d4bd-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="7d4bd-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7d4bd-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7d4bd-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-108">You must be a model administrator.</span></span> <span data-ttu-id="7d4bd-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7d4bd-110">属性は、変更の追跡グループに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-110">Your attributes must be in a change tracking group.</span></span> <span data-ttu-id="7d4bd-111">詳細については、「 [変更の追跡グループに属性を追加する (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-111">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a><span data-ttu-id="7d4bd-112">属性値の変更に基づいてアクションを開始するビジネス ルールを作成するには</span><span class="sxs-lookup"><span data-stu-id="7d4bd-112">To create a business rule to initiate actions based on attribute value changes</span></span>  
  
1.  <span data-ttu-id="7d4bd-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7d4bd-114">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-114">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="7d4bd-115">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-115">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7d4bd-116">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="7d4bd-117">**[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-117">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="7d4bd-118">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-118">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="7d4bd-119">**[ビジネス ルールの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-119">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="7d4bd-120">**[選択したビジネス ルールの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-120">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="7d4bd-121">**[コンポーネント]** ペインで **[条件]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-121">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="7d4bd-122">**[値の比較演算]** ノードの下で、 **[が変更されている]** を **[IF]** ペインの **[条件]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-122">Under the **Value comparison** node, drag **has changed** to the **IF** pane's **Conditions** label.</span></span>  
  
11. <span data-ttu-id="7d4bd-123">[**属性**] ペインで属性をクリックし、[条件の**編集**] ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-123">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span> <span data-ttu-id="7d4bd-124">この属性はルールに影響しないので、使用可能な任意の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-124">This attribute has no effect on the rule, so select any available attribute.</span></span>  
  
12. <span data-ttu-id="7d4bd-125">**[条件の編集]** ペインの **[変更の追跡グループ]** ボックスに、前提条件の一部として割り当てた変更の追跡グループの数を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-125">In the **Edit Condition** pane, in the **Change tracking group** box, type the number of the change tracking group that you assigned as part of the prerequisites.</span></span>  
  
13. <span data-ttu-id="7d4bd-126">**[条件の編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-126">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="7d4bd-127">**[コンポーネント]** ペインで **[アクション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-127">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="7d4bd-128">アクションをクリックして、 **[THEN]** ペインの **[アクション]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-128">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="7d4bd-129">**[属性]** ペインで属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-129">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="7d4bd-130">**[アクションの編集]** ペインで、必須の各フィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-130">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="7d4bd-131">**[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-131">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="7d4bd-132">**[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-132">Click **Back**.</span></span>  
  
20. <span data-ttu-id="7d4bd-133">必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d4bd-134">通知は、検証アクションを含むルールに対してのみ送信されます。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
21. <span data-ttu-id="7d4bd-135">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-135">Click **Publish business rules**.</span></span>  
  
22. <span data-ttu-id="7d4bd-136">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="7d4bd-137">ルールの状態が **[アクティブ]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7d4bd-138">次の手順</span><span class="sxs-lookup"><span data-stu-id="7d4bd-138">Next Steps</span></span>  
  
-   <span data-ttu-id="7d4bd-139">以下のいずれかの手順でビジネス ルールをデータに適用します。</span><span class="sxs-lookup"><span data-stu-id="7d4bd-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="7d4bd-140">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7d4bd-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="7d4bd-141">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7d4bd-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d4bd-142">参照</span><span class="sxs-lookup"><span data-stu-id="7d4bd-142">See Also</span></span>  
 <span data-ttu-id="7d4bd-143">[Change Tracking グループ &#40;マスターデータサービスに属性を追加&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7d4bd-143">[Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span></span>  
 [<span data-ttu-id="7d4bd-144">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7d4bd-144">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
