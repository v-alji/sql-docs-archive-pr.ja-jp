---
title: 明示的階層およびコレクションに対してエンティティを有効にする (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], enabling for collections
- entities [Master Data Services], enabling for explicit hierarchies
ms.assetid: 380e77e5-ad60-43d4-9605-34a84525f5dd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a8129b3f67f050603f85ffb782a9dd209cb303fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712077"
---
# <a name="enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services"></a><span data-ttu-id="57805-102">明示的階層とコレクションに対してエンティティを有効にする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="57805-102">Enable an Entity for Explicit Hierarchies and Collections (Master Data Services)</span></span>
  <span data-ttu-id="57805-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で明示的階層とコレクションに対してエンティティを有効にすると、エンティティに明示的階層とコレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="57805-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], enable an entity for explicit hierarchies and collections so that you can create explicit hierarchies and collections for the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="57805-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="57805-104">Prerequisites</span></span>  
 <span data-ttu-id="57805-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="57805-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="57805-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="57805-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="57805-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="57805-107">You must be a model administrator.</span></span> <span data-ttu-id="57805-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57805-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="57805-109">エンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57805-109">An entity must exist.</span></span> <span data-ttu-id="57805-110">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57805-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-enable-an-entity-for-explicit-hierarchies-and-collections"></a><span data-ttu-id="57805-111">明示的階層とコレクションに対してエンティティを有効にするには</span><span class="sxs-lookup"><span data-stu-id="57805-111">To enable an entity for explicit hierarchies and collections</span></span>  
  
1.  <span data-ttu-id="57805-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57805-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="57805-113">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57805-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="57805-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="57805-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="57805-115">更新するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="57805-115">Select the row for the entity that you want to update.</span></span>  
  
5.  <span data-ttu-id="57805-116">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57805-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="57805-117">[**明示的階層とコレクションを有効にする**] の一覧で、[**はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="57805-117">From the **Enable explicit hierarchies and collections** list, select **Yes**.</span></span>  
  
7.  <span data-ttu-id="57805-118">[**明示的階層名**] ボックスに、明示的階層の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="57805-118">In the **Explicit hierarchy name** box, type a name for an explicit hierarchy.</span></span>  
  
8.  <span data-ttu-id="57805-119">必要に応じて、 **[必須階層]** チェック ボックスをオフにして、任意の階層として明示的階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="57805-119">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="57805-120">[**エンティティの保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57805-120">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="57805-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="57805-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="57805-122">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="57805-122">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
-   [<span data-ttu-id="57805-123">コレクションを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="57805-123">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="57805-124">参照</span><span class="sxs-lookup"><span data-stu-id="57805-124">See Also</span></span>  
 <span data-ttu-id="57805-125">[エンティティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="57805-125">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="57805-126">[明示的階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="57805-126">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="57805-127">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="57805-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
