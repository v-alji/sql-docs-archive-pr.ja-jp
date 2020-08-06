---
title: '[フィールド] ([データセットのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b766aa23cce390bc3ffdcf10efdb38efc91f3e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632994"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a><span data-ttu-id="dcad9-102">[フィールド] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="dcad9-102">Dataset Properties Dialog Box, Fields (Report Builder)</span></span>
  <span data-ttu-id="dcad9-103">**[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** を選択すると、レポート データセットのフィールド コレクションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="dcad9-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="dcad9-104">フィールドの一覧は自動的に作成されますが、 **[フィールド]** を使用してクエリ フィールドや計算フィールドを追加、編集、および削除することができます。</span><span class="sxs-lookup"><span data-stu-id="dcad9-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
 <span data-ttu-id="dcad9-105">計算フィールドは埋め込みデータセットでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="dcad9-105">Calculated fields are supported only on embedded datasets.</span></span> <span data-ttu-id="dcad9-106">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="dcad9-106">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcad9-107">Options</span><span class="sxs-lookup"><span data-stu-id="dcad9-107">Options</span></span>  
 <span data-ttu-id="dcad9-108">**追加**</span><span class="sxs-lookup"><span data-stu-id="dcad9-108">**Add**</span></span>  
 <span data-ttu-id="dcad9-109">データセットに新しいクエリ フィールドまたは計算フィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-109">Add a new query or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="dcad9-110">**削除**</span><span class="sxs-lookup"><span data-stu-id="dcad9-110">**Delete**</span></span>  
 <span data-ttu-id="dcad9-111">選択したフィールドをデータセットから削除します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-111">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="dcad9-112">**フィールド名**</span><span class="sxs-lookup"><span data-stu-id="dcad9-112">**Field Name**</span></span>  
 <span data-ttu-id="dcad9-113">フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-113">Type a name for the field.</span></span> <span data-ttu-id="dcad9-114">フィールドはデータセット内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcad9-114">The field must be unique within the dataset.</span></span> <span data-ttu-id="dcad9-115">データセット内の既存の各フィールドの名前はあらかじめ設定されています。</span><span class="sxs-lookup"><span data-stu-id="dcad9-115">For each existing field in the dataset, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="dcad9-116">**[フィールド ソース]**</span><span class="sxs-lookup"><span data-stu-id="dcad9-116">**Field Source**</span></span>  
 <span data-ttu-id="dcad9-117">フィールドの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-117">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="dcad9-118">計算フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前か、ユーザーが作成した式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcad9-118">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="dcad9-119">たとえば、Sales クエリ フィールドの値の 10 倍を表すフィールドを作成する場合は、 `=10 * Fields!Sales.Value`という式を使用します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-119">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="dcad9-120">クエリ フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcad9-120">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="dcad9-121">**式 ([fx])**</span><span class="sxs-lookup"><span data-stu-id="dcad9-121">**Expression (fx)**</span></span>  
 <span data-ttu-id="dcad9-122">新しい計算フィールドを表す式を追加または変更します。</span><span class="sxs-lookup"><span data-stu-id="dcad9-122">Add or change an expression for the new calculated field.</span></span> <span data-ttu-id="dcad9-123">このボタンは、 **[追加]** をクリックして **[計算フィールド]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="dcad9-123">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcad9-124">参照</span><span class="sxs-lookup"><span data-stu-id="dcad9-124">See Also</span></span>  
 <span data-ttu-id="dcad9-125">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-125">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dcad9-126">[レポートビルダーおよび SSRS を &#40;共有データセットまたは埋め込みデータセットを作成&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-126">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dcad9-127">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-127">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="dcad9-128">[[オプション] ([データセットのプロパティ] ダイアログボックス &#40;レポートビルダー&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-128">[Dataset Properties Dialog Box, Options &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span></span>  
 <span data-ttu-id="dcad9-129">[[フィルター] ([データセットのプロパティ] ダイアログボックス) &#40;レポートビルダー&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-129">[Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span></span>  
 <span data-ttu-id="dcad9-130">[[パラメーター] ([データセットのプロパティ] ダイアログボックス &#40;レポートビルダー&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-130">[Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span></span>  
 <span data-ttu-id="dcad9-131">[[クエリ &#40;レポートビルダー] ([データセットのプロパティ] ダイアログボックス)&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-131">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="dcad9-132">[式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dcad9-132">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dcad9-133">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="dcad9-133">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
