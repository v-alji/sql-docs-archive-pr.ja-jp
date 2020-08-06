---
title: モデル (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d5a4a431d3ca7b6fa499de68a2bc4c5033cd086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645137"
---
# <a name="models-master-data-services"></a><span data-ttu-id="dcd9c-102">モデル (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-102">Models (Master Data Services)</span></span>
  <span data-ttu-id="dcd9c-103">モデルは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の最上位レベルのデータ編成単位です。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-103">Models are the highest level of data organization in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="dcd9c-104">モデルは、マスター データ管理ソリューションでのデータの構造を定義します。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-104">A model defines the structure of data in your master data management solution.</span></span> <span data-ttu-id="dcd9c-105">モデルには次のオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-105">A model contains the following objects:</span></span>  
  
-   <span data-ttu-id="dcd9c-106">エンティティ</span><span class="sxs-lookup"><span data-stu-id="dcd9c-106">Entities</span></span>  
  
-   <span data-ttu-id="dcd9c-107">属性と属性グループ</span><span class="sxs-lookup"><span data-stu-id="dcd9c-107">Attributes and attribute groups</span></span>  
  
-   <span data-ttu-id="dcd9c-108">明示的階層と派生階層</span><span class="sxs-lookup"><span data-stu-id="dcd9c-108">Explicit and derived hierarchies</span></span>  
  
-   <span data-ttu-id="dcd9c-109">コレクション</span><span class="sxs-lookup"><span data-stu-id="dcd9c-109">Collections</span></span>  
  
 <span data-ttu-id="dcd9c-110">モデルは、マスター データの構造を整理します。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-110">Models organize the structure of your master data.</span></span> <span data-ttu-id="dcd9c-111">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の実装は 1 つまたは多くのモデルを保持し、各モデルが類似のデータをグループ化します</span><span class="sxs-lookup"><span data-stu-id="dcd9c-111">Your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] implementation can have one or many models that each group similar kinds of data.</span></span> <span data-ttu-id="dcd9c-112">マスター データは通常、4 つのカテゴリ (人、場所、物、概念) のうちの 1 つに分類されます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-112">In general, master data can be categorized in one of four ways: people, places, things, or concepts.</span></span> <span data-ttu-id="dcd9c-113">たとえば、製品関連のデータを含む Product モデルや、顧客関連のデータを含む Customer モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-113">For example, you can create a Product model to contain product-related data or a Customer model to contain customer-related data.</span></span>  
  
 <span data-ttu-id="dcd9c-114">ユーザーとグループには、モデル内のオブジェクトを表示および更新する権限を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-114">You can assign users and groups permission to view and update objects within the model.</span></span> <span data-ttu-id="dcd9c-115">モデルに権限を与えない場合、モデルは表示されません。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-115">If you do not give permission to the model, it is not displayed.</span></span>  
  
 <span data-ttu-id="dcd9c-116">任意の時点で、モデル内のマスター データのコピーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-116">At any given time, you can create copies of the master data within a model.</span></span> <span data-ttu-id="dcd9c-117">このコピーをバージョンと呼びます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-117">These copies are called versions.</span></span>  
  
 <span data-ttu-id="dcd9c-118">テスト環境でモデルが既に定義済みの場合は、対応するデータの有無に関係なく、テスト環境から運用環境にモデルを配置できます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-118">When you have defined a model in a test environment, you can deploy it, with or without the corresponding data, from the test environment to a production environment.</span></span> <span data-ttu-id="dcd9c-119">これにより、運用環境でモデルを再作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-119">This eliminates the need to recreate your models in your production environment.</span></span>  
  
## <a name="how-models-relate-to-other-objects"></a><span data-ttu-id="dcd9c-120">モデルと他のオブジェクトの関連付け</span><span class="sxs-lookup"><span data-stu-id="dcd9c-120">How Models Relate to Other Objects</span></span>  
 <span data-ttu-id="dcd9c-121">モデルは複数のエンティティを含みます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-121">A model contains entities.</span></span> <span data-ttu-id="dcd9c-122">エンティティは属性、明示的階層、およびコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-122">Entities contain attributes, explicit hierarchies, and collections.</span></span> <span data-ttu-id="dcd9c-123">属性は属性グループに含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-123">Attributes can be contained in attribute groups.</span></span> <span data-ttu-id="dcd9c-124">エンティティを別のエンティティの属性として使用するときは、ドメイン ベースの属性が存在します。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-124">Domain-based attributes exist when an entity is used as an attribute for another entity.</span></span>  
  
 <span data-ttu-id="dcd9c-125">次の図は、1 つのモデル内のオブジェクト間のリレーションシップを示しています。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-125">This image shows the relationships among the objects in a model.</span></span>  
  
 <span data-ttu-id="dcd9c-126">![マスター データ サービス モデル内のオブジェクト](../../2014/master-data-services/media/mds-conc-model-circles.gif "マスター データ サービス モデル内のオブジェクト")</span><span class="sxs-lookup"><span data-stu-id="dcd9c-126">![Objects in a Master Data Services Model](../../2014/master-data-services/media/mds-conc-model-circles.gif "Objects in a Master Data Services Model")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcd9c-127">派生階層はモデル オブジェクトでもありますが、図には示されていません。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-127">Derived hierarchies are also model objects, but they are not shown in the image.</span></span> <span data-ttu-id="dcd9c-128">派生階層は、エンティティ間に存在するドメイン ベースの属性リレーションシップから派生します。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-128">Derived hierarchies are derived from the domain-based attribute relationships that exist between entities.</span></span> <span data-ttu-id="dcd9c-129">詳細については、「[派生階層 (マスター データ サービス)](derived-hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-129">See [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md) for more information.</span></span>  
  
 <span data-ttu-id="dcd9c-130">マスター データは、モデル オブジェクトに含まれるデータです。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-130">Master data is the data that is contained in the model objects.</span></span> <span data-ttu-id="dcd9c-131">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、マスター データはエンティティのメンバーとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-131">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], master data is stored as members in an entity.</span></span>  
  
 <span data-ttu-id="dcd9c-132">モデル オブジェクトは、 **のユーザー インターフェイスの** [システム管理] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 機能領域で管理されます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-132">Model objects are maintained in the **System Administration** functional area of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface.</span></span>  
  
## <a name="model-example"></a><span data-ttu-id="dcd9c-133">モデルの例</span><span class="sxs-lookup"><span data-stu-id="dcd9c-133">Model Example</span></span>  
 <span data-ttu-id="dcd9c-134">次の例では、Product モデルのオブジェクトは製品 (product) に関連するデータを論理的にグループ化します。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-134">In the following example, the objects in the Product model logically group product-related data.</span></span>  
  
 <span data-ttu-id="dcd9c-135">![製品モデル マスター データの例](../../2014/master-data-services/media/mds-conc-model.gif "製品モデル マスター データの例")</span><span class="sxs-lookup"><span data-stu-id="dcd9c-135">![Product Model Master Data Example](../../2014/master-data-services/media/mds-conc-model.gif "Product Model Master Data Example")</span></span>  
  
 <span data-ttu-id="dcd9c-136">その他の一般的なモデルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-136">Other common models are:</span></span>  
  
-   <span data-ttu-id="dcd9c-137">Accounts: 貸借対照表勘定科目、損益計算書勘定科目、統計、勘定科目の種類などのエンティティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-137">Accounts, which could include entities such as balance sheet accounts, income statement accounts, statistics, and account type.</span></span>  
  
-   <span data-ttu-id="dcd9c-138">Customer: 性別、学歴、職業、配偶者の有無などのエンティティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-138">Customer, which could include entities such as gender, education, occupation, and marital status.</span></span>  
  
-   <span data-ttu-id="dcd9c-139">Geography: 郵便番号、都道府県、郡市町村、地域、区域、国、大陸などのエンティティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-139">Geography, which could include entities such as postal codes, cities, counties, states, provinces, regions, territories, countries, and continents.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="dcd9c-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="dcd9c-140">Related Tasks</span></span>  
  
|<span data-ttu-id="dcd9c-141">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="dcd9c-141">Task Description</span></span>|<span data-ttu-id="dcd9c-142">トピック</span><span class="sxs-lookup"><span data-stu-id="dcd9c-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="dcd9c-143">モデルを作成してマスター データを整理する。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-143">Create a model to organize your master data.</span></span>|[<span data-ttu-id="dcd9c-144">モデルを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-144">Create a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|<span data-ttu-id="dcd9c-145">既存のモデルの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-145">Change the name of an existing model.</span></span>|[<span data-ttu-id="dcd9c-146">モデル名を変更する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="dcd9c-146">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)|  
|<span data-ttu-id="dcd9c-147">既存のモデルを削除する。</span><span class="sxs-lookup"><span data-stu-id="dcd9c-147">Delete an existing model.</span></span>|[<span data-ttu-id="dcd9c-148">モデルを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-148">Delete a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="dcd9c-149">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="dcd9c-149">Related Content</span></span>  
  
-   [<span data-ttu-id="dcd9c-150">マスター データ サービス概要</span><span class="sxs-lookup"><span data-stu-id="dcd9c-150">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="dcd9c-151">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-151">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [<span data-ttu-id="dcd9c-152">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-152">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [<span data-ttu-id="dcd9c-153">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-153">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
-   [<span data-ttu-id="dcd9c-154">モデル オブジェクト権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="dcd9c-154">Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/model-object-permissions-master-data-services.md)  
  
  
