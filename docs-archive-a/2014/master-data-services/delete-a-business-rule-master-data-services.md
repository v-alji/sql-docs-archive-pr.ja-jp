---
title: ビジネス ルールを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8e6db486f71634cf025c57eabbedeeb9efdbc437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712094"
---
# <a name="delete-a-business-rule-master-data-services"></a><span data-ttu-id="26b5e-102">ビジネス ルールを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="26b5e-102">Delete a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="26b5e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になったビジネス ルールを削除します。</span><span class="sxs-lookup"><span data-stu-id="26b5e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a business rule when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26b5e-104">ビジネス ルールに対するデータの検証が行われないようにするには、ビジネス ルールを削除する代わりに除外することができます。</span><span class="sxs-lookup"><span data-stu-id="26b5e-104">You can prevent data from being validated against a business rule by excluding it, rather than deleting it.</span></span> <span data-ttu-id="26b5e-105">詳細については、「 [ビジネス ルールを除外する (マスター データ サービス)](exclude-a-business-rule-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26b5e-105">For more information, see [Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26b5e-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="26b5e-106">Prerequisites</span></span>  
 <span data-ttu-id="26b5e-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="26b5e-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="26b5e-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="26b5e-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="26b5e-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="26b5e-109">You must be a model administrator.</span></span> <span data-ttu-id="26b5e-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26b5e-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-business-rule"></a><span data-ttu-id="26b5e-111">ビジネス ルールを削除するには</span><span class="sxs-lookup"><span data-stu-id="26b5e-111">To delete a business rule</span></span>  
  
1.  <span data-ttu-id="26b5e-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="26b5e-113">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="26b5e-114">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="26b5e-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="26b5e-115">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="26b5e-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="26b5e-116">**[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="26b5e-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="26b5e-117">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="26b5e-118">グリッドで、削除するビジネス ルールの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-118">In the grid, click the row for the business rule you want to delete.</span></span>  
  
8.  <span data-ttu-id="26b5e-119">[**選択したビジネスルールの削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-119">Click **Delete selected business rule**.</span></span>  
  
9. <span data-ttu-id="26b5e-120">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-120">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="26b5e-121">[**状態**] 列の値が [**削除の保留中**] になっています。</span><span class="sxs-lookup"><span data-stu-id="26b5e-121">The value in the **Status** column is **Deletion pending**.</span></span>  
  
10. <span data-ttu-id="26b5e-122">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-122">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="26b5e-123">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26b5e-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b5e-124">参照</span><span class="sxs-lookup"><span data-stu-id="26b5e-124">See Also</span></span>  
 <span data-ttu-id="26b5e-125">[ビジネスルール &#40;マスターデータサービスを除外する&#41;](exclude-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26b5e-125">[Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="26b5e-126">[ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26b5e-126">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="26b5e-127">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="26b5e-127">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
