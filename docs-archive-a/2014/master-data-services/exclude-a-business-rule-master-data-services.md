---
title: ビジネス ルールを除外する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 317964dcbc7b2cbe212c415b3aa4f9f1a0743301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715518"
---
# <a name="exclude-a-business-rule-master-data-services"></a><span data-ttu-id="7718f-102">ビジネス ルールを除外する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7718f-102">Exclude a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="7718f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ビジネス ルールを完全に削除せずにそのルールに対するデータの検証が行われないようにする場合は、ビジネス ルールを除外します。</span><span class="sxs-lookup"><span data-stu-id="7718f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclude a business rule when you do not want to delete the rule permanently, but you do not want to validate data against it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7718f-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="7718f-104">Prerequisites</span></span>  
 <span data-ttu-id="7718f-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="7718f-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7718f-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7718f-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7718f-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7718f-107">You must be a model administrator.</span></span> <span data-ttu-id="7718f-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7718f-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-exclude-a-business-rule"></a><span data-ttu-id="7718f-109">ビジネス ルールを除外するには</span><span class="sxs-lookup"><span data-stu-id="7718f-109">To exclude a business rule</span></span>  
  
1.  <span data-ttu-id="7718f-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7718f-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7718f-111">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7718f-111">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="7718f-112">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7718f-112">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7718f-113">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="7718f-113">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="7718f-114">[**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7718f-114">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="7718f-115">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="7718f-115">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="7718f-116">グリッドのビジネスルールの行で、[**除外**] 列のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7718f-116">In the grid, in the row for the business rule, select the check box in the **Exclude** column.</span></span> <span data-ttu-id="7718f-117">[**状態**] 列の値が [**除外の保留中**] になっています。</span><span class="sxs-lookup"><span data-stu-id="7718f-117">The value in the **Status** column is **Exclusion pending**.</span></span>  
  
8.  <span data-ttu-id="7718f-118">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7718f-118">Click **Publish business rules**.</span></span>  
  
9. <span data-ttu-id="7718f-119">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7718f-119">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="7718f-120">**Status**列の値は**除外**されます。</span><span class="sxs-lookup"><span data-stu-id="7718f-120">The value in the **Status** column is **Excluded**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7718f-121">参照</span><span class="sxs-lookup"><span data-stu-id="7718f-121">See Also</span></span>  
 <span data-ttu-id="7718f-122">[ビジネスルール &#40;マスターデータサービスの削除&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7718f-122">[Delete a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="7718f-123">[ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7718f-123">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="7718f-124">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7718f-124">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
