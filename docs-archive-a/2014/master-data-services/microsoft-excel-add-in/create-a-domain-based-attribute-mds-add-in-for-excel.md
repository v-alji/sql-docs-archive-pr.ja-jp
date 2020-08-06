---
title: ドメイン ベースの属性の作成 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bda0c7f63ad380aaea5d980d2e729822ec9a3d22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631131"
---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a><span data-ttu-id="8b114-102">ドメイン ベースの属性の作成 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="8b114-102">Create a Domain-based Attribute (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8b114-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の管理者は、列内の値を特定の一連の値に制約する場合に、ドメイン ベースの属性を作成できます。</span><span class="sxs-lookup"><span data-stu-id="8b114-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create a domain-based attribute when they want to constrain the values in a column to a specific set of values.</span></span>  
  
 <span data-ttu-id="8b114-104">使用できるのは、既にワークシート内にある値か、既存のエンティティの値です。</span><span class="sxs-lookup"><span data-stu-id="8b114-104">The values can already be in the worksheet or they can come from an existing entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b114-105">制約された列の値を、一覧から選択せずにユーザーが入力すると、パブリッシュ時に **[$InputStatus$]** 列にエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b114-105">If users type a value in the constrained column, rather than selecting from the list, errors are displayed in the **$InputStatus$** column when they publish.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b114-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="8b114-106">Prerequisites</span></span>  
 <span data-ttu-id="8b114-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8b114-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8b114-108">**[システム管理]** および **[エクスプローラー]** 機能領域に対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8b114-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="8b114-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b114-109">You must be a model administrator.</span></span> <span data-ttu-id="8b114-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b114-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8b114-111">モデルとエンティティが既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b114-111">The model and entity must already exist.</span></span>  
  
### <a name="to-perform-this-procedure"></a><span data-ttu-id="8b114-112">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8b114-112">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="8b114-113">Excel で、制約する列 (属性) を含むエンティティを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8b114-113">In Excel, load the entity that contains the column (attribute) you want to constrain.</span></span> <span data-ttu-id="8b114-114">詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b114-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="8b114-115">制約する列の任意のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b114-115">Click any cell in the column you want to constrain.</span></span>  
  
3.  <span data-ttu-id="8b114-116">**[モデルの構築]** グループの **[属性プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b114-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="8b114-117">**[属性プロパティ]** ダイアログ ボックスで、 **[属性の型]** ボックスの一覧の **[制約付き一覧 (ドメイン ベース)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b114-117">In the **Attribute Properties** dialog box, in the **Attribute type** list, choose **Constrained list (domain-based)**.</span></span>  
  
5.  <span data-ttu-id="8b114-118">**[属性に次の値を設定]** ボックスの一覧で、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b114-118">In the **Populate the attribute with values from** list:</span></span>  
  
    -   <span data-ttu-id="8b114-119">ワークシートの値を使用するには、[ **選択した列**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b114-119">To use values from the worksheet, choose **the selected column**.</span></span> <span data-ttu-id="8b114-120">選択した列の値を使用して、新しいエンティティと新しいステージング テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8b114-120">A new entity and new staging table will be created with the values from the selected column.</span></span>  
  
    -   <span data-ttu-id="8b114-121">既存のエンティティの値を使用するには、エンティティの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b114-121">To use values from an existing entity, choose the name of the entity.</span></span>  
  
6.  <span data-ttu-id="8b114-122">前の手順で **[選択した列]** をクリックした場合は、 **[新しいエンティティ名]** ボックスに新しいエンティティの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8b114-122">If you chose **the selected column** in the previous step, in the **New entity name** box, type a name for the new entity.</span></span> <span data-ttu-id="8b114-123">列 (属性) と同じ名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b114-123">This can be the same as the column (attribute) name.</span></span>  
  
7.  <span data-ttu-id="8b114-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b114-124">Click **OK**.</span></span> <span data-ttu-id="8b114-125">これで、列内の各セルに、ユーザーが選択する値の一覧が設定されます。</span><span class="sxs-lookup"><span data-stu-id="8b114-125">Each cell in the column now has a list of values for users to choose from.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b114-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="8b114-126">Next Steps</span></span>  
  
-   <span data-ttu-id="8b114-127">制約された一覧の値を追加および削除するには、その属性が基づいているエンティティを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8b114-127">To add and delete values in the constrained list, load the entity that the attribute is based on.</span></span> <span data-ttu-id="8b114-128">エンティティの読み込みの詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b114-128">For more information on loading entities, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b114-129">参照</span><span class="sxs-lookup"><span data-stu-id="8b114-129">See Also</span></span>  
 <span data-ttu-id="8b114-130">[ドメインベースの属性 &#40;マスターデータサービス&#41;](../domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8b114-130">[Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="8b114-131">[エンティティ &#40;Excel 用 MDS アドインを作成し&#41;](create-an-entity-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8b114-131">[Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="8b114-132">モデルの構築 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="8b114-132">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
