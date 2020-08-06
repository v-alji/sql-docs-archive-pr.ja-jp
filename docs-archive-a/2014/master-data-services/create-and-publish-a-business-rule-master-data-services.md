---
title: ビジネス ルールを作成しパブリッシュする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4dfca5613a1f328e02b3fd2c7337885a23889207
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644003"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a><span data-ttu-id="8b896-102">ビジネス ルールを作成しパブリッシュする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8b896-102">Create and Publish a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="8b896-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、マスター データの精度を保証するためにビジネス ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b896-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to ensure the accuracy of your master data.</span></span> <span data-ttu-id="8b896-104">ルールを作成した後、データに適用する前に、そのルールをパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b896-104">After you create a rule, you must publish it before you can apply it to data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b896-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="8b896-105">Prerequisites</span></span>  
 <span data-ttu-id="8b896-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8b896-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8b896-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="8b896-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="8b896-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b896-108">You must be a model administrator.</span></span> <span data-ttu-id="8b896-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b896-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-and-publish-a-business-rule"></a><span data-ttu-id="8b896-110">ビジネス ルールを作成してパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="8b896-110">To create and publish a business rule</span></span>  
  
1.  <span data-ttu-id="8b896-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="8b896-112">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="8b896-113">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b896-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="8b896-114">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b896-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="8b896-115">**[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b896-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="8b896-116">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="8b896-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="8b896-117">**[ビジネス ルールの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="8b896-118">**[選択したビジネス ルールの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="8b896-119">**[コンポーネント]** ペインで **[条件]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="8b896-119">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="8b896-120">条件をクリックし、[ **IF** ] ペインの [**条件**] ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b896-120">Click a condition and drag it to the **IF** pane's **Conditions** label.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="8b896-121">ビジネスルールからアイテムを削除するには、右クリックして [**削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b896-121">You can delete items from your business rule by right-clicking and choosing **Delete**.</span></span>  
  
11. <span data-ttu-id="8b896-122">[**属性**] ペインで属性をクリックし、[条件の**編集**] ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b896-122">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="8b896-123">[**条件の編集**] ウィンドウで、必要なフィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="8b896-123">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
13. <span data-ttu-id="8b896-124">**[条件の編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-124">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="8b896-125">**[コンポーネント]** ペインで **[アクション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="8b896-125">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="8b896-126">アクションをクリックして、 **[THEN]** ペインの **[アクション]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b896-126">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="8b896-127">**[属性]** ペインで属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8b896-127">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="8b896-128">**[アクションの編集]** ペインで、必須の各フィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="8b896-128">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="8b896-129">**[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-129">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="8b896-130">オプションで、ビジネス ルールに複数の条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="8b896-130">Optionally, add multiple conditions to the rule.</span></span> <span data-ttu-id="8b896-131">詳細については、「 [ビジネス ルールに複数の条件を追加する (マスター データ サービス)](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b896-131">For more information, see [Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).</span></span>  
  
20. <span data-ttu-id="8b896-132">**[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-132">Click **Back**.</span></span>  
  
21. <span data-ttu-id="8b896-133">必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。</span><span class="sxs-lookup"><span data-stu-id="8b896-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8b896-134">通知は、検証アクションを含むルールに対してのみ送信されます。</span><span class="sxs-lookup"><span data-stu-id="8b896-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
22. <span data-ttu-id="8b896-135">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-135">Click **Publish business rules**.</span></span>  
  
23. <span data-ttu-id="8b896-136">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b896-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="8b896-137">ルールの状態が **[アクティブ]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="8b896-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b896-138">次の手順</span><span class="sxs-lookup"><span data-stu-id="8b896-138">Next Steps</span></span>  
  
-   <span data-ttu-id="8b896-139">以下のいずれかの手順でビジネス ルールをデータに適用します。</span><span class="sxs-lookup"><span data-stu-id="8b896-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="8b896-140">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8b896-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="8b896-141">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8b896-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b896-142">参照</span><span class="sxs-lookup"><span data-stu-id="8b896-142">See Also</span></span>  
 <span data-ttu-id="8b896-143">[通知を送信するようにビジネスルールを構成する &#40;マスターデータサービス&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8b896-143">[Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="8b896-144">[ビジネスルールの名前を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8b896-144">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="8b896-145">ビジネス ルールに複数の条件を追加する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="8b896-145">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
