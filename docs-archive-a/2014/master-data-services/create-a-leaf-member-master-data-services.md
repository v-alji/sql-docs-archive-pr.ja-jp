---
title: リーフ メンバーを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe0245dd30019e1cb9112754bd8b8eeafed93aa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631136"
---
# <a name="create-a-leaf-member-master-data-services"></a><span data-ttu-id="7c9a8-102">リーフ メンバーを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7c9a8-102">Create a Leaf Member (Master Data Services)</span></span>
  <span data-ttu-id="7c9a8-103">で [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 、マスターデータをシステムに追加し、ステージングテーブルまたはを使用してデータをインポートしない場合は、リーフメンバーを作成し [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a leaf member when you want to add master data to your system and are not using staging tables or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] to import data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7c9a8-104">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="7c9a8-104">Prerequisites</span></span>  
 <span data-ttu-id="7c9a8-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="7c9a8-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7c9a8-106">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="7c9a8-107">メンバーを追加するエンティティのリーフモデルオブジェクトに対する**更新**権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-107">You must have a minimum of **Update** permission to the leaf model object for the entity you are adding a member to.</span></span>  
  
### <a name="to-create-a-leaf-member"></a><span data-ttu-id="7c9a8-108">リーフ メンバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="7c9a8-108">To create a leaf member</span></span>  
  
1.  <span data-ttu-id="7c9a8-109">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-109">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="7c9a8-110">ユーザーの場合は、 **[バージョン]** ボックスの一覧から未処理のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-110">If you are a user, select an open version from the **Version** list.</span></span> <span data-ttu-id="7c9a8-111">管理者の場合は、 **[バージョン]** ボックスの一覧から、状態が未処理またはロック済みのバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-111">If you are an administrator, select a version with open or locked status from the **Version** list.</span></span>  
  
3.  <span data-ttu-id="7c9a8-112">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="7c9a8-113">メニュー バーの **[エンティティ]** をポイントして、メンバーを追加するエンティティの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-113">From the menu bar, point to **Entities** and click the name of the entity you want to add a member to.</span></span>  
  
5.  <span data-ttu-id="7c9a8-114">**[メンバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-114">Click **Add member**.</span></span>  
  
6.  <span data-ttu-id="7c9a8-115">**[詳細]** ペインのフィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-115">In the **Details** pane, complete the fields.</span></span>  
  
7.  <span data-ttu-id="7c9a8-116">省略可能。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-116">Optional.</span></span> <span data-ttu-id="7c9a8-117">**[注釈]** ボックスに、メンバーを追加した理由についてのコメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-117">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="7c9a8-118">そのメンバーにアクセスできるすべてのユーザーが、その注釈を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-118">All users who have access to the member can view the annotation.</span></span>  
  
8.  <span data-ttu-id="7c9a8-119">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7c9a8-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9a8-120">参照</span><span class="sxs-lookup"><span data-stu-id="7c9a8-120">See Also</span></span>  
 <span data-ttu-id="7c9a8-121">[ステージング処理を使用したマスターデータサービスのメンバーの読み込みまたは更新](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7c9a8-121">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="7c9a8-122">[統合メンバー &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7c9a8-122">[Create a Consolidated Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span></span>  
 [<span data-ttu-id="7c9a8-123">メンバー (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="7c9a8-123">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
  
