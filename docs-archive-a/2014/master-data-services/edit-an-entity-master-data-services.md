---
title: エンティティ名を変更する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9690fde44b0d56d790f4340779167fb55b400223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712082"
---
# <a name="change-an-entity-name-master-data-services"></a><span data-ttu-id="5c461-102">エンティティ名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="5c461-102">Change an Entity Name (Master Data Services)</span></span>
  <span data-ttu-id="5c461-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、エンティティの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="5c461-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c461-104">関連付けられているステージング テーブルの名前は更新されません。</span><span class="sxs-lookup"><span data-stu-id="5c461-104">The names of the associated staging tables will not be updated.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c461-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="5c461-105">Prerequisites</span></span>  
 <span data-ttu-id="5c461-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="5c461-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5c461-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="5c461-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="5c461-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c461-108">You must be a model administrator.</span></span> <span data-ttu-id="5c461-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c461-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-entity-name"></a><span data-ttu-id="5c461-110">エンティティ名を変更するには</span><span class="sxs-lookup"><span data-stu-id="5c461-110">To change an entity name</span></span>  
  
1.  <span data-ttu-id="5c461-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c461-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="5c461-112">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c461-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="5c461-113">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5c461-113">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="5c461-114">名前を変更するエンティティの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c461-114">Click the row for the entity with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="5c461-115">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c461-115">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="5c461-116">[**エンティティ名**] ボックスに、エンティティの更新後の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5c461-116">In the **Entity name** box, type the updated name of the entity.</span></span>  
  
7.  <span data-ttu-id="5c461-117">[**エンティティの保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c461-117">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c461-118">参照</span><span class="sxs-lookup"><span data-stu-id="5c461-118">See Also</span></span>  
 <span data-ttu-id="5c461-119">[エンティティ &#40;マスターデータサービスを作成し&#41;](create-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5c461-119">[Create an Entity &#40;Master Data Services&#41;](create-an-entity-master-data-services.md) </span></span>  
 <span data-ttu-id="5c461-120">[エンティティ &#40;マスターデータサービスの削除&#41;](delete-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5c461-120">[Delete an Entity &#40;Master Data Services&#41;](delete-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="5c461-121">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="5c461-121">Entities &#40;Master Data Services&#41;</span></span>](entities-master-data-services.md)  
  
  
