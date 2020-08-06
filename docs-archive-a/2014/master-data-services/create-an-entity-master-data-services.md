---
title: エンティティを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7cefdedd07ee248f12b3b17337878934a2b1aa84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645151"
---
# <a name="create-an-entity-master-data-services"></a><span data-ttu-id="64dde-102">エンティティを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="64dde-102">Create an Entity (Master Data Services)</span></span>
  <span data-ttu-id="64dde-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でエンティティを作成して、メンバーおよびその属性を含めます。</span><span class="sxs-lookup"><span data-stu-id="64dde-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an entity to contain members and their attributes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="64dde-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="64dde-104">Prerequisites</span></span>  
 <span data-ttu-id="64dde-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="64dde-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="64dde-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="64dde-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="64dde-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="64dde-107">You must be a model administrator.</span></span> <span data-ttu-id="64dde-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64dde-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="64dde-109">モデルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64dde-109">A model must exist.</span></span> <span data-ttu-id="64dde-110">詳細については、「[モデルを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-model-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64dde-110">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-an-entity"></a><span data-ttu-id="64dde-111">エンティティを作成するには</span><span class="sxs-lookup"><span data-stu-id="64dde-111">To create an entity</span></span>  
  
1.  <span data-ttu-id="64dde-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64dde-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="64dde-113">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64dde-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="64dde-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="64dde-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="64dde-115">[**エンティティの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64dde-115">Click **Add entity**.</span></span>  
  
5.  <span data-ttu-id="64dde-116">[**エンティティ名**] ボックスに、エンティティの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="64dde-116">In the **Entity name** box, type the name of the entity.</span></span>  
  
6.  <span data-ttu-id="64dde-117">[**ステージングテーブルの名前**] ボックスに、ステージングテーブルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="64dde-117">In the **Name for staging tables** box, type a name for the staging table.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="64dde-118">ステージング テーブルの名前の一部にはモデル名を使用します。たとえば、 *Modelname_Entityname*のようにします。</span><span class="sxs-lookup"><span data-stu-id="64dde-118">Use the model name as part of the staging table name, for example *Modelname_Entityname*.</span></span> <span data-ttu-id="64dde-119">こうすることで、データベースからテーブルを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="64dde-119">This makes the tables easier to find in the database.</span></span> <span data-ttu-id="64dde-120">ステージングテーブルの詳細については、「[データのインポート &#40;マスターデータサービス&#41;](overview-importing-data-from-tables-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64dde-120">For more information about the staging tables, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
7.  <span data-ttu-id="64dde-121">省略可能。</span><span class="sxs-lookup"><span data-stu-id="64dde-121">Optional.</span></span> <span data-ttu-id="64dde-122">**[コード値を自動的に作成する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="64dde-122">Select the **Create Code values automatically** check box.</span></span> <span data-ttu-id="64dde-123">詳細については、「[自動コード作成 &#40;マスターデータサービス&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64dde-123">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="64dde-124">[**明示的階層とコレクションを有効にする**] の一覧で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="64dde-124">From the **Enable explicit hierarchies and collections** list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="64dde-125">**[いいえ]** 。</span><span class="sxs-lookup"><span data-stu-id="64dde-125">**No**.</span></span> <span data-ttu-id="64dde-126">明示的階層およびコレクションに対してエンティティを有効にする必要がない場合、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="64dde-126">Select this option if you do not need to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="64dde-127">これは、必要に応じて後で変更できます。</span><span class="sxs-lookup"><span data-stu-id="64dde-127">You can change this later if needed.</span></span>  
  
    -   <span data-ttu-id="64dde-128">**はい**。</span><span class="sxs-lookup"><span data-stu-id="64dde-128">**Yes**.</span></span> <span data-ttu-id="64dde-129">明示的階層およびコレクションに対してエンティティを有効にする場合、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="64dde-129">Select this option when you want to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="64dde-130">[**明示的階層名**] ボックスに、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="64dde-130">In the **Explicit hierarchy name** box, type a name.</span></span> <span data-ttu-id="64dde-131">必要に応じて、[必須階層] を選択します (明示的階層を必須階層にするに**は、すべてのリーフメンバーが含ま**れます)。</span><span class="sxs-lookup"><span data-stu-id="64dde-131">Optionally, select **Mandatory hierarchy (all leaf members are included** to make the explicit hierarchy a mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="64dde-132">[**エンティティの保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64dde-132">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="64dde-133">次の手順</span><span class="sxs-lookup"><span data-stu-id="64dde-133">Next Steps</span></span>  
  
-   [<span data-ttu-id="64dde-134">テキスト属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="64dde-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="64dde-135">ドメイン ベースの属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="64dde-135">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="64dde-136">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="64dde-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="64dde-137">参照</span><span class="sxs-lookup"><span data-stu-id="64dde-137">See Also</span></span>  
 <span data-ttu-id="64dde-138">[エンティティ &#40;マスターデータサービス&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="64dde-138">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="64dde-139">[明示的階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="64dde-139">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="64dde-140">[エンティティ名を変更する &#40;マスターデータサービス&#41;](edit-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="64dde-140">[Change an Entity Name &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="64dde-141">エンティティを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="64dde-141">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
