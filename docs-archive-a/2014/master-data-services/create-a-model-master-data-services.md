---
title: モデルを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07b2f44798a689a7ceca7ec39a2ffc95f015d9b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642856"
---
# <a name="create-a-model-master-data-services"></a><span data-ttu-id="eb081-102">モデルを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eb081-102">Create a Model (Master Data Services)</span></span>
  <span data-ttu-id="eb081-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルを作成してモデル オブジェクトを含めます。</span><span class="sxs-lookup"><span data-stu-id="eb081-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model to contain model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eb081-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="eb081-104">Prerequisites</span></span>  
 <span data-ttu-id="eb081-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="eb081-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="eb081-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb081-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
### <a name="to-create-a-model"></a><span data-ttu-id="eb081-107">モデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="eb081-107">To create a model</span></span>  
  
1.  <span data-ttu-id="eb081-108">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb081-108">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="eb081-109">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[モデル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb081-109">On the **Model View** page, from the menu bar, point to **Manage** and click **Models**.</span></span>  
  
3.  <span data-ttu-id="eb081-110">[**モデルのメンテナンス**] ページで、[**モデルの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb081-110">On the **Model Maintenance** page, click **Add model**.</span></span>  
  
4.  <span data-ttu-id="eb081-111">[**モデル名**] ボックスにモデルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="eb081-111">In the **Model name** box, type the name of the model.</span></span>  
  
5.  <span data-ttu-id="eb081-112">(オプション) **[モデルと同じ名前のエンティティを作成する]** をクリックして、モデルと同じ名前のエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb081-112">Optionally, select **Create entity with same name as model** to create an entity with the same name as the model.</span></span>  
  
6.  <span data-ttu-id="eb081-113">必要に応じ**て、[モデルと同じ名前の明示的階層を作成**する] を選択して、モデルと同じ名前の明示的階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="eb081-113">Optionally, select **Create explicit hierarchy with same name as model** to create an explicit hierarchy with the same name as the model.</span></span> <span data-ttu-id="eb081-114">このオプションを使用すると、コレクションのエンティティも有効になります。</span><span class="sxs-lookup"><span data-stu-id="eb081-114">This option also enables the entity for collections.</span></span>  
  
7.  <span data-ttu-id="eb081-115">必要に応じて、[必須階層] を選択します (必須階層として明示的階層を作成するに**は、すべてのリーフメンバーが含ま**れます)。</span><span class="sxs-lookup"><span data-stu-id="eb081-115">Optionally, select **Mandatory hierarchy (all leaf members are included** to create the explicit hierarchy as a mandatory hierarchy.</span></span>  
  
8.  <span data-ttu-id="eb081-116">**[モデルの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb081-116">Click **Save model**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eb081-117">次の手順</span><span class="sxs-lookup"><span data-stu-id="eb081-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="eb081-118">エンティティを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="eb081-118">Create an Entity &#40;Master Data Services&#41;</span></span>](create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="eb081-119">参照</span><span class="sxs-lookup"><span data-stu-id="eb081-119">See Also</span></span>  
 <span data-ttu-id="eb081-120">[モデル &#40;マスターデータサービス&#41;](../../2014/master-data-services/models-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb081-120">[Models &#40;Master Data Services&#41;](../../2014/master-data-services/models-master-data-services.md) </span></span>  
 <span data-ttu-id="eb081-121">[エンティティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb081-121">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="eb081-122">[モデル &#40;マスターデータサービスの削除&#41;](../../2014/master-data-services/delete-a-model-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb081-122">[Delete a Model &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-model-master-data-services.md) </span></span>  
 [<span data-ttu-id="eb081-123">モデル名を変更する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="eb081-123">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)  
  
  
