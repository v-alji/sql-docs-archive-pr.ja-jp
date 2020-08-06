---
title: 明示的階層を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 744f96a2705a3abbc2318ecd3c9b0c7fffb7605e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646196"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="dd913-102">明示的階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dd913-102">Delete an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="dd913-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になった明示的階層を削除します。</span><span class="sxs-lookup"><span data-stu-id="dd913-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an explicit hierarchy when you no longer need it.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="dd913-104">明示的階層を削除すると、階層内の統合メンバーもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="dd913-104">When you delete an explicit hierarchy, all consolidated members in the hierarchy are deleted also.</span></span> <span data-ttu-id="dd913-105">エンティティに対する明示的階層を削除すると、エンティティのコレクションもすべて削除され、明示的階層およびコレクションに対してエンティティが無効になります。</span><span class="sxs-lookup"><span data-stu-id="dd913-105">If you delete all explicit hierarchies for an entity, all collections for the entity are also deleted and the entity is no longer enabled for explicit hierarchies and collections.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dd913-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="dd913-106">Prerequisites</span></span>  
 <span data-ttu-id="dd913-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="dd913-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="dd913-108">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="dd913-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="dd913-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd913-109">You must be a model administrator.</span></span> <span data-ttu-id="dd913-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd913-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-explicit-hierarchy"></a><span data-ttu-id="dd913-111">明示的階層を削除するには</span><span class="sxs-lookup"><span data-stu-id="dd913-111">To delete an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="dd913-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="dd913-113">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="dd913-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="dd913-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="dd913-115">削除する明示的階層を含むエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd913-115">Select the row for the entity that contains the explicit hierarchy you want to delete.</span></span>  
  
5.  <span data-ttu-id="dd913-116">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="dd913-117">[**エンティティの編集**] ページの [**明示的階層**] ペインで、削除する明示的階層をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-117">On the **Edit Entity** page, in the **Explicit Hierarchies** pane, click the explicit hierarchy you want to delete.</span></span>  
  
7.  <span data-ttu-id="dd913-118">[**選択した階層の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-118">Click **Delete selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="dd913-119">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="dd913-120">追加の確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd913-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd913-121">参照</span><span class="sxs-lookup"><span data-stu-id="dd913-121">See Also</span></span>  
 <span data-ttu-id="dd913-122">[明示的階層 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd913-122">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="dd913-123">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dd913-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
