---
title: コレクションにメンバーを追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], adding members
ms.assetid: 1a7155e6-2d4a-4ed1-a72c-edb37fa1a46b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce2038f3bc90a2f17506b0aadaaf9707fa911896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645157"
---
# <a name="add-members-to-a-collection-master-data-services"></a><span data-ttu-id="eef05-102">コレクションにメンバーを追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eef05-102">Add Members to a Collection (Master Data Services)</span></span>
  <span data-ttu-id="eef05-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、リーフ メンバーおよび統合メンバーをコレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="eef05-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can add leaf and consolidated members to a collection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eef05-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="eef05-104">Prerequisites</span></span>  
 <span data-ttu-id="eef05-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="eef05-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="eef05-106">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eef05-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="eef05-107">メンバーを追加するコレクション モデル オブジェクトに対して、 **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="eef05-107">You must have a minimum of **Update** permission to the collection model object that you are adding members to.</span></span>  
  
-   <span data-ttu-id="eef05-108">コレクションが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eef05-108">A collection must exist.</span></span> <span data-ttu-id="eef05-109">詳細については、「[コレクションを作成する (マスター データ サービス)](create-a-collection-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eef05-109">For more information, see [Create a Collection &#40;Master Data Services&#41;](create-a-collection-master-data-services.md).</span></span>  
  
### <a name="to-add-members-to-a-collection"></a><span data-ttu-id="eef05-110">コレクションにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="eef05-110">To add members to a collection</span></span>  
  
1.  <span data-ttu-id="eef05-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eef05-111">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="eef05-112">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="eef05-112">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="eef05-113">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-113">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="eef05-114">メニュー バーの **[コレクション]** をポイントして、[ *entity_name*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-114">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="eef05-115">グリッドで、メンバーを追加するコレクションの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-115">In the grid, click the row for the collection you want to add members to.</span></span>  
  
6.  <span data-ttu-id="eef05-116">**[コレクション メンバー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-116">Click the **Collection Members** tab.</span></span>  
  
7.  <span data-ttu-id="eef05-117">**[メンバーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-117">Click **Edit Members**.</span></span>  
  
8.  <span data-ttu-id="eef05-118">使用できるメンバーの一覧をフィルター処理するには、左側の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="eef05-118">To filter the list of available members, select from the list on the left.</span></span>  
  
9. <span data-ttu-id="eef05-119">追加するメンバーの行をクリックして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eef05-119">Click the row with the member you want to add and click **Add**.</span></span>  
  
10. <span data-ttu-id="eef05-120">必要に応じて、 **[上へ]** または **[下へ]** をクリックして、コレクションのメンバーを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="eef05-120">Optionally, rearrange collection members by clicking **Up** or **Down**.</span></span>  
  
11. <span data-ttu-id="eef05-121">必要に応じて、 **[重み]** 列の値をクリックして、重みの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="eef05-121">Optionally, set weight values by clicking the value in the **Weight** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef05-122">参照</span><span class="sxs-lookup"><span data-stu-id="eef05-122">See Also</span></span>  
 [<span data-ttu-id="eef05-123">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eef05-123">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
