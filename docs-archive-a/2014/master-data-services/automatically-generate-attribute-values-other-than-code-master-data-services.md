---
title: Code 以外の属性の値の自動生成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8db6c89bdce2a11a5a54ed3a763a7bc41bd7f1be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644011"
---
# <a name="automatically-generate-attribute-values-other-than-code-master-data-services"></a><span data-ttu-id="a695e-102">Code 以外の属性の値の自動生成 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a695e-102">Automatically Generate Attribute Values Other Than Code (Master Data Services)</span></span>
  <span data-ttu-id="a695e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、ビジネス ルールが適用されるたびにエンティティの属性値に整数を自動的に割り当てる場合は、属性の値を自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="a695e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's attribute values when you want an integer to be automatically assigned as the value each time business rules are applied.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a695e-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="a695e-104">Prerequisites</span></span>  
 <span data-ttu-id="a695e-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="a695e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a695e-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="a695e-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a695e-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a695e-107">You must be a model administrator.</span></span> <span data-ttu-id="a695e-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a695e-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a695e-109">数値属性が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a695e-109">A numeric attribute must exist.</span></span> <span data-ttu-id="a695e-110">詳細については、「[数値属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a695e-110">For more information, see [Create a Numeric Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-an-attribute-value"></a><span data-ttu-id="a695e-111">属性値を自動的に生成するには</span><span class="sxs-lookup"><span data-stu-id="a695e-111">To automatically generate an attribute value</span></span>  
  
1.  <span data-ttu-id="a695e-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a695e-113">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="a695e-114">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a695e-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a695e-115">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="a695e-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="a695e-116">**[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="a695e-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="a695e-117">**[属性]** ボックスの一覧は、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="a695e-117">From the **Attribute** list, leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="a695e-118">**[ビジネス ルールの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-118">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="a695e-119">**[選択したビジネス ルールの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-119">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="a695e-120">**[コンポーネント]** ペインで **[アクション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a695e-120">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="a695e-121">既定値ノードで、**[の既定値が生成値である]** をクリックし、**[THEN]** ペインの **[アクション]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a695e-121">In the Default Value node, click **defaults to a generated value** and drag it to the **THEN** pane's **Actions** label.</span></span>  
  
11. <span data-ttu-id="a695e-122">**[属性]** ペインで値を生成する属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a695e-122">In the **Attributes** pane, click the attribute with the value you want to generated and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="a695e-123">**[開始]** および **[増分]** ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a695e-123">Type a value in the **Start with** and **Increment by** boxes.</span></span> <span data-ttu-id="a695e-124">メンバーが既に存在する場合、値は既存の最も大きい値に基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="a695e-124">If members already exist, the value will be set based on the highest existing value.</span></span> <span data-ttu-id="a695e-125">たとえば、既存の最も大きい値が 299 で、**[増分]** を **1**に設定してある場合、次のメンバーの値は 300 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a695e-125">For example, if the highest existing value is 299 and you set **Increment by** to **1**, the next member's value will be set to 300.</span></span>  
  
13. <span data-ttu-id="a695e-126">**[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-126">In the **Edit Action** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="a695e-127">**[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-127">Click **Back**.</span></span>  
  
15. <span data-ttu-id="a695e-128">必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。</span><span class="sxs-lookup"><span data-stu-id="a695e-128">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
16. <span data-ttu-id="a695e-129">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-129">Click **Publish business rules**.</span></span>  
  
17. <span data-ttu-id="a695e-130">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a695e-130">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="a695e-131">ルールの状態が **[アクティブ]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="a695e-131">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a695e-132">次の手順</span><span class="sxs-lookup"><span data-stu-id="a695e-132">Next Steps</span></span>  
  
-   [<span data-ttu-id="a695e-133">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a695e-133">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="a695e-134">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a695e-134">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="a695e-135">参照</span><span class="sxs-lookup"><span data-stu-id="a695e-135">See Also</span></span>  
 <span data-ttu-id="a695e-136">[自動コード作成 &#40;マスターデータサービス&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a695e-136">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 <span data-ttu-id="a695e-137">[ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a695e-137">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="a695e-138">検証 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a695e-138">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
  
