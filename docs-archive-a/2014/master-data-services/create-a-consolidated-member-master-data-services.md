---
title: 統合メンバーを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c41673f6f3bf1f4de2a831ecd659321b273b6af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718350"
---
# <a name="create-a-consolidated-member-master-data-services"></a><span data-ttu-id="24c11-102">統合メンバーを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="24c11-102">Create a Consolidated Member (Master Data Services)</span></span>
  <span data-ttu-id="24c11-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で明示的階層の親ノードが必要な場合、統合メンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="24c11-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a consolidated member when you want a parent node for an explicit hierarchy.</span></span> <span data-ttu-id="24c11-104">統合メンバーには、独自の属性を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="24c11-104">Consolidated members can have their own attributes.</span></span> <span data-ttu-id="24c11-105">これはグループ化のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="24c11-105">They are used for grouping.</span></span> <span data-ttu-id="24c11-106">次の例に示すように、統合メンバーは、その下にアカウントを持つアカウント グループに使用できます。</span><span class="sxs-lookup"><span data-stu-id="24c11-106">As shown in the following example, consolidated members can be used for account groups that have accounts under them.</span></span>

 <span data-ttu-id="24c11-107">![MDS 統合メンバー](../../2014/master-data-services/media/mds-consolidated-members.png "MDS 統合メンバー")</span><span class="sxs-lookup"><span data-stu-id="24c11-107">![MDS Consolidated Members](../../2014/master-data-services/media/mds-consolidated-members.png "MDS Consolidated Members")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24c11-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="24c11-108">Prerequisites</span></span>
 <span data-ttu-id="24c11-109">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="24c11-109">To perform this procedure:</span></span>

-   <span data-ttu-id="24c11-110">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="24c11-110">You must have permission to access the **Explorer** functional area.</span></span>

-   <span data-ttu-id="24c11-111">メンバーを追加するエンティティの統合モデル オブジェクトに対する **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="24c11-111">You must have a minimum of **Update** permission to the consolidated model object for the entity you are adding a member to.</span></span>

### <a name="to-create-a-consolidated-member"></a><span data-ttu-id="24c11-112">統合メンバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="24c11-112">To create a consolidated member</span></span>

1.  <span data-ttu-id="24c11-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="24c11-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>

2.  <span data-ttu-id="24c11-114">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="24c11-114">From the **Version** list, select a version.</span></span>

3.  <span data-ttu-id="24c11-115">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24c11-115">Click **Explorer**.</span></span>

4.  <span data-ttu-id="24c11-116">メニュー バーの **[階層]** をポイントして、統合メンバーを追加する階層の名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24c11-116">From the menu bar, point to **Hierarchies** and click the name of the hierarchy you want to add a consolidated member to.</span></span>

5.  <span data-ttu-id="24c11-117">グリッドの上にある **[統合メンバー]** または **[階層内のすべての統合メンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24c11-117">Above the grid, select either the **Consolidated members** or the **All consolidated members in hierarchy** option.</span></span>

6.  <span data-ttu-id="24c11-118">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24c11-118">Click **Add**.</span></span>

7.  <span data-ttu-id="24c11-119">右側のペインのフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="24c11-119">In the pane on the right, complete the fields.</span></span>

8.  <span data-ttu-id="24c11-120">省略可能。</span><span class="sxs-lookup"><span data-stu-id="24c11-120">Optional.</span></span> <span data-ttu-id="24c11-121">**[注釈]** ボックスに、メンバーを追加した理由についてのコメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="24c11-121">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="24c11-122">そのメンバーにアクセスできるすべてのユーザーが、その注釈を表示できます。</span><span class="sxs-lookup"><span data-stu-id="24c11-122">All users who have access to the member can view the annotation.</span></span>

9. <span data-ttu-id="24c11-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24c11-123">Click **OK**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="24c11-124">次の手順</span><span class="sxs-lookup"><span data-stu-id="24c11-124">Next Steps</span></span>

-   [<span data-ttu-id="24c11-125">階層内のメンバーを移動する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="24c11-125">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a><span data-ttu-id="24c11-126">参照</span><span class="sxs-lookup"><span data-stu-id="24c11-126">See Also</span></span>
 <span data-ttu-id="24c11-127">[明示的階層を作成する &#40;マスターデータサービス](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)[リーフ &#40;メンバーを作成](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)する&#41;、ステージング処理の[メンバー](../../2014/master-data-services/members-master-data-services.md)マスターデータサービス&#41;マスターデータサービス[明示的階層 &#40;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)マスターデータサービス[を使用して&#41;のメンバーを読み込みまたは更新](add-update-and-delete-data-master-data-services.md)&#40;マスターデータサービス</span><span class="sxs-lookup"><span data-stu-id="24c11-127">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [Create a Leaf Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) [Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) [Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)</span></span>


