---
title: 明示的階層名を変更する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, changing name
ms.assetid: 12991603-474e-4042-b160-b1f7979694b1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3cb8d1108650395ebd970edbb2ea31f5daebbd27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736480"
---
# <a name="change-an-explicit-hierarchy-name-master-data-services"></a><span data-ttu-id="b380b-102">明示的階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b380b-102">Change an Explicit Hierarchy Name (Master Data Services)</span></span>
  <span data-ttu-id="b380b-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、明示的階層の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b380b-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an explicit hierarchy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b380b-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="b380b-104">Prerequisites</span></span>  
 <span data-ttu-id="b380b-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="b380b-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b380b-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="b380b-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="b380b-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b380b-107">You must be a model administrator.</span></span> <span data-ttu-id="b380b-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b380b-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-an-explicit-hierarchy"></a><span data-ttu-id="b380b-109">明示的階層の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="b380b-109">To change the name of an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="b380b-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="b380b-111">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="b380b-112">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b380b-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b380b-113">名前を変更する明示的階層を含むエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="b380b-113">Select the row for the entity that contains the explicit hierarchy you want to rename.</span></span>  
  
5.  <span data-ttu-id="b380b-114">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="b380b-115">[**エンティティの編集**] ページで、名前を変更する明示的階層をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-115">On the **Edit Entity** page, click the explicit hierarchy you want to rename.</span></span>  
  
7.  <span data-ttu-id="b380b-116">[**選択した階層の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-116">Click **Edit selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="b380b-117">[**明示的階層名**] ボックスに、階層の更新後の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b380b-117">In the **Explicit hierarchy name** box, type the updated name of the hierarchy.</span></span>  
  
9. <span data-ttu-id="b380b-118">[**階層の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b380b-118">Click **Save hierarchy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b380b-119">参照</span><span class="sxs-lookup"><span data-stu-id="b380b-119">See Also</span></span>  
 <span data-ttu-id="b380b-120">[明示的階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b380b-120">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="b380b-121">[明示的階層 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b380b-121">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="b380b-122">明示的階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b380b-122">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)  
  
  
