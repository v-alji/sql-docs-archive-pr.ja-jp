---
title: コレクションを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f76171b4fd9b07f751d4f919011a443253fbe31b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718363"
---
# <a name="create-a-collection-master-data-services"></a><span data-ttu-id="90e00-102">コレクションを作成する (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="90e00-102">Create a Collection (Master Data Services)</span></span>
  <span data-ttu-id="90e00-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、リーフ メンバーまたは統合メンバーの一覧表示を作成する必要があるときは、コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="90e00-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a collection when you want to create flat lists of leaf and consolidated members.</span></span> <span data-ttu-id="90e00-104">コレクションは、エンティティのすべてのメンバーを含む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="90e00-104">Collections do not need to include all members from the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="90e00-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="90e00-105">Prerequisites</span></span>  
 <span data-ttu-id="90e00-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="90e00-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="90e00-107">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90e00-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="90e00-108">エンティティのコレクション モデル オブジェクトに対して **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="90e00-108">You must have a minimum of **Update** permission to the collection model object for the entity.</span></span>  
  
-   <span data-ttu-id="90e00-109">エンティティは、明示的階層およびコレクションに対して有効化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e00-109">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="90e00-110">詳細については、「[明示的階層とコレクションのエンティティの有効化 &#40;マスターデータサービス&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90e00-110">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-a-collection"></a><span data-ttu-id="90e00-111">コレクションを作成するには</span><span class="sxs-lookup"><span data-stu-id="90e00-111">To create a collection</span></span>  
  
1.  <span data-ttu-id="90e00-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="90e00-112">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="90e00-113">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="90e00-113">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="90e00-114">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e00-114">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="90e00-115">メニュー バーの **[コレクション]** をポイントして、[ *entity_name*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e00-115">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="90e00-116">**[コレクションの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e00-116">Click **Add collection**.</span></span>  
  
6.  <span data-ttu-id="90e00-117">**[詳細]** タブの **[名前]** ボックスにコレクションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="90e00-117">On the **Details** tab, in the **Name** box, type a name for the collection.</span></span>  
  
7.  <span data-ttu-id="90e00-118">**[コード]** ボックスにコレクションの一意のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="90e00-118">In the **Code** box, type a unique code for the collection.</span></span>  
  
8.  <span data-ttu-id="90e00-119">必要に応じて、 **[説明]** ボックスにコレクションの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="90e00-119">Optionally, in the **Description** box, type a description for the collection.</span></span>  
  
9. <span data-ttu-id="90e00-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90e00-120">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="90e00-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="90e00-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="90e00-122">コレクションにメンバーを追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="90e00-122">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="90e00-123">参照</span><span class="sxs-lookup"><span data-stu-id="90e00-123">See Also</span></span>  
 <span data-ttu-id="90e00-124">[コレクション &#40;マスターデータサービス&#41;](../../2014/master-data-services/collections-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="90e00-124">[Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md) </span></span>  
 <span data-ttu-id="90e00-125">[マスターデータサービス &#40;のメンバーまたはコレクションを削除&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="90e00-125">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 [<span data-ttu-id="90e00-126">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="90e00-126">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  
