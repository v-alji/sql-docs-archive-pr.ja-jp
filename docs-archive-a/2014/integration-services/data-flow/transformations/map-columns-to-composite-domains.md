---
title: 複合ドメインへの列のマップ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a665b2096579c9da35a1b69be46c4ba6103610f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644056"
---
# <a name="map-columns-to-composite-domains"></a><span data-ttu-id="a8ae9-102">複合ドメインへの列のマップ</span><span class="sxs-lookup"><span data-stu-id="a8ae9-102">Map Columns to Composite Domains</span></span>
  <span data-ttu-id="a8ae9-103">複合ドメインは 2 つ以上の単一ドメインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-103">A composite domain consists of two or more single domains.</span></span> <span data-ttu-id="a8ae9-104">ドメインに複数の列をマップすることも、区切られた値を含む単一の列をドメインにマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-104">You can map multiple columns to the domain, or you can map a single column with delimited values to the domain.</span></span>  
  
 <span data-ttu-id="a8ae9-105">複数の列がある場合は、複合ドメインの各単一ドメインに列をマップして、データ クレンジングに複合ドメイン ルールを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-105">When you have multiple columns, you must map a column to each single domain in the composite domain to apply the composite domain rules to data cleansing.</span></span> <span data-ttu-id="a8ae9-106">Data Quality Client の複合ドメインに含まれる単一ドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-106">You select the single domains contained in the composite domain, in the Data Quality Client.</span></span> <span data-ttu-id="a8ae9-107">詳細については、「 [複合ドメインの作成](../../../data-quality-services/create-a-composite-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-107">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="a8ae9-108">区切られた値を含む単一の列がある場合は、その単一の列を複合ドメインにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-108">When you have a single column with delimited values, you must map the single column to the composite domain.</span></span> <span data-ttu-id="a8ae9-109">値は、単一ドメインが複合ドメインに表示されるのと同じ順序で表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-109">The values must appear in the same order as the single domains appear in the composite domain.</span></span> <span data-ttu-id="a8ae9-110">データ ソースの区切り記号は、複合ドメインの値の解析に使用される区切り記号と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-110">The delimiter in the data source must match the delimiter that is used to parse the composite domain values.</span></span> <span data-ttu-id="a8ae9-111">複合ドメインの区切り記号を選択し、Data Quality Client で他のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-111">You select the delimiter for the composite domain, as well as set other properties, in the Data Quality Client.</span></span> <span data-ttu-id="a8ae9-112">詳細については、「 [複合ドメインの作成](../../../data-quality-services/create-a-composite-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-112">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a><span data-ttu-id="a8ae9-113">複数の列を複合ドメインにマップするには</span><span class="sxs-lookup"><span data-stu-id="a8ae9-113">To map multiple columns to a composite domain</span></span>  
  
1.  <span data-ttu-id="a8ae9-114">DQS クレンジング変換を右クリックして、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-114">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="a8ae9-115">**[接続マネージャー]** タブで、複合ドメインが使用可能なドメインの一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-115">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="a8ae9-116">**[マッピング]** タブの **[使用できる入力列]** 領域で列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-116">On the **Mapping** tab, select the columns in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="a8ae9-117">**[入力列]** フィールドにリストされている列ごとに、 **[ドメイン]** フィールドで単一ドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-117">For each column listed in the **Input Column** field, select a single domain in the **Domain** field.</span></span> <span data-ttu-id="a8ae9-118">複合ドメイン内の単一ドメインのみ選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-118">Select only single domains that are in the composite domain.</span></span>  
  
5.  <span data-ttu-id="a8ae9-119">必要に応じて、 **[ソースの別名]** 、 **[出力の別名]** 、および **[状態の別名]** の各フィールドに表示される名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-119">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="a8ae9-120">必要に応じて、 **[詳細設定]** タブでプロパティを設定します。プロパティの詳細については、「 [[DQS クレンジング変換エディター] ダイアログ ボックス](../../dqs-cleansing-transformation-editor-dialog-box.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-120">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a><span data-ttu-id="a8ae9-121">区切られた値を含む列を複合ドメインにマップするには</span><span class="sxs-lookup"><span data-stu-id="a8ae9-121">To map a column with delimited values to a composite domain</span></span>  
  
1.  <span data-ttu-id="a8ae9-122">DQS クレンジング変換を右クリックして、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-122">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="a8ae9-123">**[接続マネージャー]** タブで、複合ドメインが使用可能なドメインの一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-123">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="a8ae9-124">**[マッピング]** タブの **[使用できる入力列]** 領域で列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-124">On the **Mapping** tab, select the column in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="a8ae9-125">**[入力列]** フィールドに表示されている列に対して、 **[ドメイン]** フィールドで複合ドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-125">For the column listed in the **Input Column** field, select the composite domain in the **Domain** field.</span></span>  
  
5.  <span data-ttu-id="a8ae9-126">必要に応じて、 **[ソースの別名]** 、 **[出力の別名]** 、および **[状態の別名]** の各フィールドに表示される名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-126">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="a8ae9-127">必要に応じて、 **[詳細設定]** タブでプロパティを設定します。プロパティの詳細については、「 [[DQS クレンジング変換エディター] ダイアログ ボックス](../../dqs-cleansing-transformation-editor-dialog-box.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a8ae9-127">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ae9-128">参照</span><span class="sxs-lookup"><span data-stu-id="a8ae9-128">See Also</span></span>  
 [<span data-ttu-id="a8ae9-129">DQS クレンジング変換</span><span class="sxs-lookup"><span data-stu-id="a8ae9-129">DQS Cleansing Transformation</span></span>](dqs-cleansing-transformation.md)  
  
  
