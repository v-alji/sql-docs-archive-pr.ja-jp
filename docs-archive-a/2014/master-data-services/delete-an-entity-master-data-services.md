---
title: エンティティを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], deleting
- deleting entities [Master Data Services]
ms.assetid: 71fffb03-38fd-46f0-9e10-6ec75da19ab2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f1920b9b77a8d46035308eed9ce251b9fbc8228f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645713"
---
# <a name="delete-an-entity-master-data-services"></a><span data-ttu-id="84507-102">エンティティを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="84507-102">Delete an Entity (Master Data Services)</span></span>
  <span data-ttu-id="84507-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でエンティティを削除して、そのエンティティのすべてのメンバーおよび属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="84507-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an entity to delete all members and attributes for the entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84507-104">すべてのバージョンからのエンティティのメンバーが恒久的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="84507-104">The entity's members from all versions will be permanently deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="84507-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="84507-105">Prerequisites</span></span>  
 <span data-ttu-id="84507-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="84507-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="84507-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="84507-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="84507-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="84507-108">You must be a model administrator.</span></span> <span data-ttu-id="84507-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84507-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-entity"></a><span data-ttu-id="84507-110">エンティティを削除するには</span><span class="sxs-lookup"><span data-stu-id="84507-110">To delete an entity</span></span>  
  
1.  <span data-ttu-id="84507-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84507-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="84507-112">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84507-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="84507-113">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="84507-113">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="84507-114">削除するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="84507-114">Select the row for the entity that you want to delete.</span></span>  
  
5.  <span data-ttu-id="84507-115">[**選択したエンティティの削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84507-115">Click **Delete selected entity**.</span></span>  
  
6.  <span data-ttu-id="84507-116">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84507-116">In the confirmation dialog box, click **OK**.</span></span>  
  
7.  <span data-ttu-id="84507-117">追加の確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84507-117">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84507-118">参照</span><span class="sxs-lookup"><span data-stu-id="84507-118">See Also</span></span>  
 <span data-ttu-id="84507-119">[エンティティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="84507-119">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 [<span data-ttu-id="84507-120">エンティティを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="84507-120">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)  
  
  
