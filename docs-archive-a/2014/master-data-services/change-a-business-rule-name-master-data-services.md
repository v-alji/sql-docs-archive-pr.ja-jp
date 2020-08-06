---
title: ビジネス ルールの名前を変更する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], changing name
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0e99047ffe27332aaed4514394ca2357942a1297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645726"
---
# <a name="change-a-business-rule-name-master-data-services"></a><span data-ttu-id="4363a-102">ビジネス ルールの名前を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4363a-102">Change a Business Rule Name (Master Data Services)</span></span>
  <span data-ttu-id="4363a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ビジネス ルールに割り当てられている名前がビジネス ニーズに合わない場合には、名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="4363a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], change a business rule name when the name assigned does not meet your business needs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4363a-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="4363a-104">Prerequisites</span></span>  
 <span data-ttu-id="4363a-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="4363a-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="4363a-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="4363a-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="4363a-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4363a-107">You must be a model administrator.</span></span> <span data-ttu-id="4363a-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4363a-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="4363a-109">ビジネス ルールが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4363a-109">A business rule must exist.</span></span> <span data-ttu-id="4363a-110">詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4363a-110">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-a-business-rule"></a><span data-ttu-id="4363a-111">ビジネス ルールの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="4363a-111">To change the name of a business rule</span></span>  
  
1.  <span data-ttu-id="4363a-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4363a-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="4363a-113">メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4363a-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="4363a-114">**[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4363a-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="4363a-115">**[エンティティ]** の一覧からエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="4363a-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="4363a-116">[**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="4363a-116">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="4363a-117">**[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="4363a-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="4363a-118">グリッドのビジネスルールの行で、[**名前**] フィールドをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4363a-118">In the grid, in the row for the business rule, double-click the **Name** field.</span></span>  
  
8.  <span data-ttu-id="4363a-119">ビジネス ルールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4363a-119">Type a name for the business rule.</span></span>  
  
9. <span data-ttu-id="4363a-120">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4363a-120">Press ENTER.</span></span>  
  
10. <span data-ttu-id="4363a-121">**[ビジネス ルールのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4363a-121">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="4363a-122">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4363a-122">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="4363a-123">ルールの状態が **[アクティブ]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="4363a-123">The rule's status changes to **Active**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4363a-124">参照</span><span class="sxs-lookup"><span data-stu-id="4363a-124">See Also</span></span>  
 [<span data-ttu-id="4363a-125">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="4363a-125">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
