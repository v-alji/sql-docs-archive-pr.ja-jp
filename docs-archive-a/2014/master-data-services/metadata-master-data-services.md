---
title: メタデータ (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714490"
---
# <a name="metadata-master-data-services"></a><span data-ttu-id="19560-102">メタデータ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="19560-102">Metadata (Master Data Services)</span></span>
  <span data-ttu-id="19560-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] におけるユーザー定義メタデータは、モデル オブジェクトを説明するために使用する情報です。</span><span class="sxs-lookup"><span data-stu-id="19560-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], user-defined metadata is information that you use to describe model objects.</span></span> <span data-ttu-id="19560-104">たとえば、特定のモデルまたはエンティティの所有者を追跡する場合や、エンティティにデータを提供するソース システムを追跡する場合があります。</span><span class="sxs-lookup"><span data-stu-id="19560-104">For example, you may want to track the owners of a particular model or entity, or track the source systems that supply data to an entity.</span></span>  
  
 <span data-ttu-id="19560-105">ユーザー定義メタデータは、**メタデータ**と呼ばれるモデルによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="19560-105">User-defined metadata is managed by a model called **Metadata**.</span></span> <span data-ttu-id="19560-106">このモデルは、のインストール時に自動的に含まれ、その [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 他のすべての MDS モデルに似ています。ただし、バージョンを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="19560-106">This model is automatically included when [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed, and it is similar to all other MDS models, except that you cannot create versions of it.</span></span>  
  
 <span data-ttu-id="19560-107">メタデータ モデルにユーザー定義のメタデータを投入した後は、それをサブスクリプション ビューに追加することで、サブスクライブ システムから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="19560-107">After you populate the Metadata model with user-defined metadata, you can include it in subscription views, so it can be consumed by subscribing systems.</span></span>  
  
## <a name="metadata-entities"></a><span data-ttu-id="19560-108">メタデータ エンティティ</span><span class="sxs-lookup"><span data-stu-id="19560-108">Metadata Entities</span></span>  
 <span data-ttu-id="19560-109">メタデータ モデルには 5 つのエンティティが含まれます。各エンティティはユーザー定義メタデータをサポートするマスター データ モデル オブジェクトの種類を表します。</span><span class="sxs-lookup"><span data-stu-id="19560-109">The Metadata model includes five entities, each of which represents a type of master data model object that supports user-defined metadata.</span></span> <span data-ttu-id="19560-110">たとえば、**モデルメタデータ定義**エンティティには、モデルを表すメンバーが含まれています。また、**属性メタデータ定義**エンティティには、すべてのモデルのすべての属性を表すメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="19560-110">For example, the **Model Metadata Definition** entity contains members that represent models, and the **Attribute Metadata Definition** entity has members that represent all attributes in all models.</span></span>  
  
 <span data-ttu-id="19560-111">モデル オブジェクトのメタデータを定義するには、こうしたメンバーのいずれかの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="19560-111">To define metadata for a model object, you populate one of these member's attributes.</span></span> <span data-ttu-id="19560-112">たとえば、**エンティティメタデータ定義**エンティティでは、価格メンバーの Description 属性に、"**顧客に販売された場合の製品価格**" というテキストを入力できます。</span><span class="sxs-lookup"><span data-stu-id="19560-112">For example, in the **Entity Metadata Definition** entity, you can populate the Price member's Description attribute with the text: **The product price when sold to a customer**.</span></span>  
  
 <span data-ttu-id="19560-113">メタデータ モデルのメンバーは、ユーザー定義メタデータをサポートするモデル オブジェクトが追加または削除されると自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="19560-113">The members in the Metadata model are automatically updated whenever model objects that support user-defined metadata are added or deleted.</span></span>  
  
 <span data-ttu-id="19560-114">メタデータ モデルでは、バージョン管理、バージョン フラグの追加または変更を行うことができません。また、メタデータ モデルをモデルの配置パッケージとして保存することもできません。</span><span class="sxs-lookup"><span data-stu-id="19560-114">The Metadata model cannot be versioned, have version flags added or changed, or be saved as a model deployment package.</span></span> <span data-ttu-id="19560-115">ただし、他のマスター データ モデルで使用できるその他の機能はすべて備えています。</span><span class="sxs-lookup"><span data-stu-id="19560-115">However, it has all the same other functionality available to other master data models.</span></span> <span data-ttu-id="19560-116">たとえば、ビジネス ルールのセットをメタデータ モデルに実装して、データ ポリシーを強制することができます。</span><span class="sxs-lookup"><span data-stu-id="19560-116">For example, you might implement a set of business rules on the Metadata model to enforce data policies.</span></span>  
  
## <a name="customizing-your-metadata-model"></a><span data-ttu-id="19560-117">メタデータ モデルのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="19560-117">Customizing Your Metadata Model</span></span>  
 <span data-ttu-id="19560-118">各メタデータ定義エンティティには、Name、Code、および Description の属性があります。</span><span class="sxs-lookup"><span data-stu-id="19560-118">Each metadata definition entity includes Name, Code, and Description attributes.</span></span> <span data-ttu-id="19560-119">また、追加の属性を作成して、モデル オブジェクトを詳細に説明することができます。</span><span class="sxs-lookup"><span data-stu-id="19560-119">You may want to create additional attributes to further describe your model objects.</span></span>  
  
 <span data-ttu-id="19560-120">たとえば、以下の属性を作成できます。</span><span class="sxs-lookup"><span data-stu-id="19560-120">For example, you might create:</span></span>  
  
-   <span data-ttu-id="19560-121">Owner という名前のドメイン ベースの属性。各モデル オブジェクトの所有者を追跡するために使用します。</span><span class="sxs-lookup"><span data-stu-id="19560-121">A domain-based attribute named Owner, which you use to track the owner of each model object.</span></span>  
  
-   <span data-ttu-id="19560-122">Last Review Date という名前の自由形式の属性。所有者によってオブジェクトが最後に確認された日付を追跡するために使用します。</span><span class="sxs-lookup"><span data-stu-id="19560-122">A free-form attribute named Last Review Date, which you use to track the date that an object was last reviewed by the owner.</span></span>  
  
-   <span data-ttu-id="19560-123">ソースという名前のドメインベースの属性。インスタンスと対話するソースシステムを追跡および管理するために使用し [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="19560-123">A domain-based attribute named Sources, which you use to track and manage the source systems that interact with the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] instance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="19560-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="19560-124">Related Tasks</span></span>  
  
|<span data-ttu-id="19560-125">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="19560-125">Task Description</span></span>|<span data-ttu-id="19560-126">トピック</span><span class="sxs-lookup"><span data-stu-id="19560-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="19560-127">モデル オブジェクトにメタデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="19560-127">Add metadata to a model object.</span></span>|[<span data-ttu-id="19560-128">メタデータの追加 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="19560-128">Add Metadata &#40;Master Data Services&#41;</span></span>](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a><span data-ttu-id="19560-129">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="19560-129">Related Content</span></span>  
  
-   [<span data-ttu-id="19560-130">データのエクスポート &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="19560-130">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
