---
title: エンティティの作成 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d354abb3-88fe-4b40-a374-f6256b84ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87ad67f7347da87c67afc11590df6775af4cf3d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631129"
---
# <a name="create-an-entity-mds-add-in-for-excel"></a><span data-ttu-id="4960a-102">エンティティの作成 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="4960a-102">Create an Entity (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="4960a-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の管理者は、新しいエンティティを作成してデータを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="4960a-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create new entities to store data.</span></span> <span data-ttu-id="4960a-104">エンティティを作成する場合、少なくとも、格納するデータのサンプリングを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4960a-104">When you create an entity you should load at least a sampling of the data you want to store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4960a-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="4960a-105">Prerequisites</span></span>  
 <span data-ttu-id="4960a-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="4960a-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="4960a-107">**[システム管理]** および **[エクスプローラー]** 機能領域に対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4960a-107">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="4960a-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4960a-108">You must be a model administrator.</span></span> <span data-ttu-id="4960a-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4960a-109">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="4960a-110">エンティティの作成先となる既存のモデルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4960a-110">You must have an existing model to create the entity in.</span></span> <span data-ttu-id="4960a-111">詳細については、「[モデルを作成する (マスター データ サービス)](../create-a-model-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4960a-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../create-a-model-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="4960a-112">データが次の要件を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4960a-112">Ensure that your data meets the following requirements:</span></span>  
  
    -   <span data-ttu-id="4960a-113">データにはヘッダー行が必要です。</span><span class="sxs-lookup"><span data-stu-id="4960a-113">The data should have a header row.</span></span>  
  
    -   <span data-ttu-id="4960a-114">**[名前]** 列と **[コード]** 列があると便利です。</span><span class="sxs-lookup"><span data-stu-id="4960a-114">It is helpful to have **Name** and **Code** columns.</span></span> <span data-ttu-id="4960a-115">**[コード]** は、各行の一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="4960a-115">**Code** is a unique identifier for each row.</span></span>  
  
    -   <span data-ttu-id="4960a-116">ヘッダー以外に、少なくとも 1 行のデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="4960a-116">You should have at least one row of data other than the header.</span></span> <span data-ttu-id="4960a-117">すべての列が値を持つ必要はありませんが、そのデータはエンティティに含まれるデータを代表するものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4960a-117">All columns do not need values, but the data should be representative of the data that will be in the entity.</span></span>  
  
    -   <span data-ttu-id="4960a-118">一意の識別子 (MDS の場合は " **コード**") を含む列がある場合は、その値が一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4960a-118">If you have a column that contains a unique identifier (known in MDS as **Code**), ensure that the values are unique.</span></span> <span data-ttu-id="4960a-119">識別子を含む列がない場合は、エンティティを作成するときに自動的にこれらの列を生成できます。</span><span class="sxs-lookup"><span data-stu-id="4960a-119">If no column contains identifiers, you can have them generated automatically when you create the entity.</span></span>  
  
    -   <span data-ttu-id="4960a-120">式を含むセルがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4960a-120">Ensure that no cells contain formulas.</span></span>  
  
    -   <span data-ttu-id="4960a-121">時刻の値を含むセルがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4960a-121">Ensure that no cells contain time values.</span></span> <span data-ttu-id="4960a-122">MDS では日付の値は保存できますが、時刻の値は保存できません。</span><span class="sxs-lookup"><span data-stu-id="4960a-122">Date values can be saved in MDS but time values cannot.</span></span>  
  
### <a name="to-create-an-entity-and-load-data"></a><span data-ttu-id="4960a-123">エンティティを作成してデータを読み込むには</span><span class="sxs-lookup"><span data-stu-id="4960a-123">To create an entity and load data</span></span>  
  
1.  <span data-ttu-id="4960a-124">読み込むデータを含む Excel ワークシートを開くか、作成します。</span><span class="sxs-lookup"><span data-stu-id="4960a-124">Open or create an Excel worksheet that contains data you want to load.</span></span>  
  
2.  <span data-ttu-id="4960a-125">新しいエンティティに読み込むセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4960a-125">Select the cells you want to load into the new entity.</span></span>  
  
3.  <span data-ttu-id="4960a-126">**[マスター データ]** タブで、 **[モデルの構築]** グループの **[エンティティの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4960a-126">On the **Master Data** tab, in the **Build Model** group, click **Create Entity**.</span></span>  
  
4.  <span data-ttu-id="4960a-127">MDS リポジトリへの接続を求めるメッセージが表示された場合は、接続します。</span><span class="sxs-lookup"><span data-stu-id="4960a-127">If you are prompted to connect to an MDS repository, connect.</span></span>  
  
5.  <span data-ttu-id="4960a-128">**[エンティティの作成]** ダイアログ ボックスで、既定の範囲のままにするか、読み込むデータに合うように範囲を変更します。</span><span class="sxs-lookup"><span data-stu-id="4960a-128">In the **Create Entity** dialog box, leave the default range or change it to apply to the data you want to load.</span></span>  
  
6.  <span data-ttu-id="4960a-129">**[データにヘッダーが含まれている]** チェック ボックスはオフにしないでください。</span><span class="sxs-lookup"><span data-stu-id="4960a-129">Do not clear the **My data has headers** check box.</span></span>  
  
7.  <span data-ttu-id="4960a-130">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4960a-130">From the **Model** list, select a model.</span></span>  
  
8.  <span data-ttu-id="4960a-131">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4960a-131">From the **Version** list, select a version.</span></span>  
  
9. <span data-ttu-id="4960a-132">**[新しいエンティティ名]** ボックスに、エンティティの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4960a-132">In the **New entity name** box, type a name for the entity.</span></span>  
  
10. <span data-ttu-id="4960a-133">**[コード]** ボックスの一覧から、一意の識別子または自動的に生成されたコードを含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="4960a-133">From the **Code** list, select the column that contains unique identifiers or have codes generated automatically.</span></span>  
  
11. <span data-ttu-id="4960a-134">省略可能。</span><span class="sxs-lookup"><span data-stu-id="4960a-134">Optional.</span></span> <span data-ttu-id="4960a-135">**[名前]** ボックスの一覧から、各メンバーの名前を含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="4960a-135">From the **Name** list, select a column that contains names for each member.</span></span>  
  
12. <span data-ttu-id="4960a-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4960a-136">Click **OK**.</span></span> <span data-ttu-id="4960a-137">エンティティが正常に作成されると、新しいヘッダー行が表示され、セルが強調表示されます。シート名は、エンティティ名と一致するように更新されます。</span><span class="sxs-lookup"><span data-stu-id="4960a-137">When the entity has been created successfully, a new header row is displayed, the cells are highlighted, and the sheet name is updated to match the entity name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4960a-138">次の手順</span><span class="sxs-lookup"><span data-stu-id="4960a-138">Next Steps</span></span>  
  
-   <span data-ttu-id="4960a-139">発生したエラーを確認するには、 **[パブリッシュと検証]** グループの **[状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4960a-139">To view errors that occurred, in the **Publish and Validate** group, click **Show Status**.</span></span> <span data-ttu-id="4960a-140">ValidationStatus 列と InputStatus 列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4960a-140">ValidationStatus and InputStatus columns are displayed.</span></span> <span data-ttu-id="4960a-141">詳細については、「[データの検証 (Excel 用 MDS アドイン)](validating-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4960a-141">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
-   <span data-ttu-id="4960a-142">想定していたデータ型として属性が作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4960a-142">Confirm that the attributes were created as the data type you expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4960a-143">参照</span><span class="sxs-lookup"><span data-stu-id="4960a-143">See Also</span></span>  
 [<span data-ttu-id="4960a-144">ドメイン ベースの属性の作成 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="4960a-144">Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;</span></span>](create-a-domain-based-attribute-mds-add-in-for-excel.md)  
  
  
