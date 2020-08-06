---
title: 属性値を要求する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42b412fc42138c5e186c6c7ad42373f20e35f3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633878"
---
# <a name="require-attribute-values-master-data-services"></a><span data-ttu-id="2736c-102">属性値を要求する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2736c-102">Require Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="2736c-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、マスター データが完全であることを保証するために属性値を要求します。</span><span class="sxs-lookup"><span data-stu-id="2736c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], require attribute values when you want to ensure your master data is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2736c-104">ドメイン ベースの属性値がないメンバーは、それらのリレーションシップに基づく派生階層に表示されません。</span><span class="sxs-lookup"><span data-stu-id="2736c-104">Members that are missing domain-based attribute values are not displayed in derived hierarchies that are based on those relationships.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2736c-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="2736c-105">Prerequisites</span></span>  
 <span data-ttu-id="2736c-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="2736c-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2736c-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="2736c-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2736c-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2736c-108">You must be a model administrator.</span></span> <span data-ttu-id="2736c-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2736c-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-require-attribute-values"></a><span data-ttu-id="2736c-110">属性値を要求するには</span><span class="sxs-lookup"><span data-stu-id="2736c-110">To require attribute values</span></span>  
  
1.  <span data-ttu-id="2736c-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2736c-112">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="2736c-113">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2736c-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2736c-114">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="2736c-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="2736c-115">**[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="2736c-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="2736c-116">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="2736c-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="2736c-117">**[ビジネス ルールの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="2736c-118">**[選択したビジネス ルールの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="2736c-119">**[コンポーネント]** ペインで **[アクション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2736c-119">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="2736c-120">[**必須**] をクリックし、 **[THEN** ] ペインの [**アクション**] ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2736c-120">Click **is required** and drag it to the **THEN** pane's **Action** label.</span></span>  
  
11. <span data-ttu-id="2736c-121">**[属性]** ペインで属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2736c-121">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="2736c-122">**[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-122">In the **Edit Action** pane, click **Save item**.</span></span>  
  
13. <span data-ttu-id="2736c-123">**[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-123">Click **Back**.</span></span>  
  
14. <span data-ttu-id="2736c-124">必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。</span><span class="sxs-lookup"><span data-stu-id="2736c-124">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
15. <span data-ttu-id="2736c-125">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-125">Click **Publish business rules**.</span></span>  
  
16. <span data-ttu-id="2736c-126">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2736c-126">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="2736c-127">ルールの状態が **[アクティブ]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="2736c-127">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2736c-128">次の手順</span><span class="sxs-lookup"><span data-stu-id="2736c-128">Next Steps</span></span>  
  
-   <span data-ttu-id="2736c-129">以下のいずれかの手順でビジネス ルールをデータに適用します。</span><span class="sxs-lookup"><span data-stu-id="2736c-129">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="2736c-130">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2736c-130">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="2736c-131">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2736c-131">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="2736c-132">参照</span><span class="sxs-lookup"><span data-stu-id="2736c-132">See Also</span></span>  
 <span data-ttu-id="2736c-133">[ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2736c-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="2736c-134">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2736c-134">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
