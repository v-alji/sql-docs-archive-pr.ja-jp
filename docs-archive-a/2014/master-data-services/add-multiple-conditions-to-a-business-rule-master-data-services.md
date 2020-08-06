---
title: ビジネス ルールに複数の条件を追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c62b8dfa4f459958d12bd384b85aa74bef382b21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642857"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a><span data-ttu-id="7a56e-102">ビジネス ルールに複数の条件を追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7a56e-102">Add Multiple Conditions to a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="7a56e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ではより複雑なルールが必要な場合に、複数の **AND** 条件または **OR** 条件をビジネス ルールに追加します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add multiple **AND** or **OR** conditions to a business rule when you want a more complex rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a56e-104">**OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7a56e-104">If you create a business rule that uses the **OR** operator, consider creating a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="7a56e-105">そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。</span><span class="sxs-lookup"><span data-stu-id="7a56e-105">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7a56e-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="7a56e-106">Prerequisites</span></span>  
 <span data-ttu-id="7a56e-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="7a56e-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7a56e-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a56e-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7a56e-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a56e-109">You must be a model administrator.</span></span> <span data-ttu-id="7a56e-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a56e-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7a56e-111">ビジネス ルールが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a56e-111">A business rule must exist.</span></span> <span data-ttu-id="7a56e-112">詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a56e-112">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a><span data-ttu-id="7a56e-113">ビジネス ルールに複数の条件を追加するには</span><span class="sxs-lookup"><span data-stu-id="7a56e-113">To add multiple conditions to a business rule</span></span>  
  
1.  <span data-ttu-id="7a56e-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7a56e-115">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-115">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="7a56e-116">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-116">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7a56e-117">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="7a56e-118">[**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-118">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="7a56e-119">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-119">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="7a56e-120">編集するビジネス ルールの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-120">Click the row for the business rule you want to edit.</span></span>  
  
8.  <span data-ttu-id="7a56e-121">**[選択したビジネス ルールの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-121">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="7a56e-122">[**コンポーネント**] ウィンドウで、[**論理演算子**] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-122">In the **Components** pane, expand the **Logical Operators** node.</span></span>  
  
10. <span data-ttu-id="7a56e-123">[ **And** ] または [ **or** ] をクリックし、[ **IF** ] ペインの **[and** ] ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-123">Click **AND** or **OR** and drag it to the **IF** pane's **AND** label.</span></span>  
  
11. <span data-ttu-id="7a56e-124">**[コンポーネント]** ペインで **[条件]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-124">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
12. <span data-ttu-id="7a56e-125">条件をクリックし、[ **IF** ] ペインにドラッグして、手順10の **[And** ] また**は**[] ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-125">Click a condition and drag it to **IF** pane, to the **AND** or **OR** label from step 10.</span></span>  
  
13. <span data-ttu-id="7a56e-126">[**属性**] ペインで属性をクリックし、[条件の**編集**] ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-126">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
14. <span data-ttu-id="7a56e-127">[**条件の編集**] ウィンドウで、必要なフィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-127">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
15. <span data-ttu-id="7a56e-128">**[条件の編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-128">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
16. <span data-ttu-id="7a56e-129">必要に応じて、さらに条件を追加するには、[**コンポーネント**]**ペインで** **[And** **] また\*\*\*\*は [** **or** ] をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-129">Optionally, to add more conditions, from the **Components** pane, drag **AND** or **OR** to any **AND** or **OR** in the **IF** pane.</span></span> <span data-ttu-id="7a56e-130">手順 13～15 を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a56e-130">Then follow steps 13-15.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="7a56e-131">条件を削除するには、条件の名前をクリックし、[**条件の編集**] ペインで [項目の**削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a56e-131">To delete a condition, click the name of the condition and in the **Edit Condition** pane, click **Delete item**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a56e-132">参照</span><span class="sxs-lookup"><span data-stu-id="7a56e-132">See Also</span></span>  
 <span data-ttu-id="7a56e-133">[ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7a56e-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 <span data-ttu-id="7a56e-134">[ビジネスルールの名前を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7a56e-134">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="7a56e-135">通知を送信するようにビジネス ルールを構成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7a56e-135">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
