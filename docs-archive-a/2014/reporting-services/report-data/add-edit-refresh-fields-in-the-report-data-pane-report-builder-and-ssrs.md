---
title: レポート データ ペインでのフィールドの追加、編集、更新 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a20880b84383fc5d9f96c5611419a08facb9ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631594"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a><span data-ttu-id="fe343-102">レポート データ ペインでのフィールドの追加、編集、更新 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="fe343-102">Add, Edit, Refresh Fields in the Report Data Pane (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fe343-103">データセット フィールドは、外部データ ソースにデータセット クエリを実行するときに返されるデータを表すフィールド名の組み込みのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="fe343-103">Dataset fields are the built-in collection of field names that represent the data that is returned when a dataset query runs on an external data source.</span></span>  
  
 <span data-ttu-id="fe343-104">埋め込みデータセットのデータセット フィールドには、クエリの作成が完了してクエリ デザイナー ペインを閉じた後に作成されたフィールドと、作成された計算フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="fe343-104">For an embedded dataset, the dataset fields are the fields that are created after you finish building a query and close the Query Designer pane, and calculated fields that you create.</span></span>  
  
 <span data-ttu-id="fe343-105">共有データセットのデータセット フィールドは、レポートに共有データセット定義を追加した際に共有データセット定義から取得されるフィールドです。</span><span class="sxs-lookup"><span data-stu-id="fe343-105">For a shared dataset, the dataset fields are the fields from the shared dataset definition when you added it to your report.</span></span> <span data-ttu-id="fe343-106">レポート サーバー上の共有データセットからのクエリは、レポートの実行時に常に使用されますが、レポート内のデータセット フィールドの一覧は静的です。</span><span class="sxs-lookup"><span data-stu-id="fe343-106">Although the query from the shared dataset on the report server is always used when you run the report, the list of dataset fields in the report is static.</span></span>  
  
 <span data-ttu-id="fe343-107">レポート内のフィールドの一覧を更新して共有データセット クエリからのフィールドの現在の一覧に一致させるには、 **[フィールドの更新]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe343-107">Use **Refresh Fields** to update the list of fields in the report to match the current list of fields from the shared dataset query.</span></span> <span data-ttu-id="fe343-108">フィールドの一覧を更新しても、レポート内で定義された計算フィールドには影響しません。</span><span class="sxs-lookup"><span data-stu-id="fe343-108">Refreshing the field list does not affect the calculated fields that you define in your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a><span data-ttu-id="fe343-109">クエリ フィールドを追加するには</span><span class="sxs-lookup"><span data-stu-id="fe343-109">To add a query field</span></span>  
  
1.  <span data-ttu-id="fe343-110">レポート データ ペインでデータセットを右クリックし、 **[クエリ フィールドの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-110">In the Report Data pane, right-click the dataset, and then click **Add Query Field**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe343-111">レポート データ ペインを表示できない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-111">If you cannot see the Report Data pane, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="fe343-112">**[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** ページで **[追加]** をクリックし、 **[クエリ フィールド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-112">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Query Field**.</span></span> <span data-ttu-id="fe343-113">グリッドの下部に、新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fe343-113">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="fe343-114">**[フィールド名]** ボックスに、フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe343-114">In the **Field Name** text box, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe343-115">名前は、データセット内で一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="fe343-115">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="fe343-116">**[フィールド ソース]** ボックスに、データ ソースの既存のフィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe343-116">In the **Field Source** text box, type the name of an existing field on the data source.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a><span data-ttu-id="fe343-117">計算フィールドを追加するには</span><span class="sxs-lookup"><span data-stu-id="fe343-117">To add a calculated field</span></span>  
  
1.  <span data-ttu-id="fe343-118">レポート データ ペインでデータセットを右クリックし、 **[計算フィールドの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-118">In the Report Data pane, right-click the dataset, and then click **Add Calculated Field**.</span></span>  
  
2.  <span data-ttu-id="fe343-119">**[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** ページで、 **[追加]** をクリックし、 **[計算フィールド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-119">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Calculated Field**.</span></span> <span data-ttu-id="fe343-120">グリッドの下部に、新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fe343-120">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="fe343-121">**[フィールド名]** ボックスに、フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe343-121">In the **Field Name** text bo, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe343-122">名前は、データセット内で一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="fe343-122">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="fe343-123">**[フィールド ソース]** ボックスに、フィールドの式を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe343-123">In the **Field Source** text box, type the expression for the field.</span></span> <span data-ttu-id="fe343-124">式を作成するには、式 ( **[fx]** ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-124">Click the expression (**fx**) button to build an expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe343-125">計算フィールドの式に、レポート アイテムに対する集計または参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fe343-125">The expression for a calculated field cannot contain aggregates or references to report items.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a><span data-ttu-id="fe343-126">クエリ フィールドまたはデータセット フィールドを編集するには</span><span class="sxs-lookup"><span data-stu-id="fe343-126">To edit a query field or a dataset field</span></span>  
  
1.  <span data-ttu-id="fe343-127">レポート データ ペインでフィールドを右クリックし、 **[フィールドのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-127">In the Report Data pane, right-click the field, and then click **Field Properties**.</span></span>  
  
2.  <span data-ttu-id="fe343-128">**[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** ページで、既存のフィールドをクリックして行を選択します。</span><span class="sxs-lookup"><span data-stu-id="fe343-128">In the **Fields** page of the **Dataset Properties** dialog box, click an existing field to select the row.</span></span>  
  
3.  <span data-ttu-id="fe343-129">フィールドの名前またはフィールドの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="fe343-129">Change the name of the field or the value of the field.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a><span data-ttu-id="fe343-130">クエリ フィールドまたは計算フィールドを削除するには</span><span class="sxs-lookup"><span data-stu-id="fe343-130">To delete a query field or a calculated field</span></span>  
  
1.  <span data-ttu-id="fe343-131">レポート データ ペインでデータセットを展開して、フィールド コレクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="fe343-131">In the Report Data pane, expand the dataset to display the field collection.</span></span>  
  
2.  <span data-ttu-id="fe343-132">削除するフィールドを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-132">Right-click the field you want to remove, and then click **Delete**.</span></span>  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a><span data-ttu-id="fe343-133">共有データセットのレポート データ ペインのフィールド コレクションを更新するには</span><span class="sxs-lookup"><span data-stu-id="fe343-133">To refresh the field collection in the Report Data Pane for a shared dataset</span></span>  
  
1.  <span data-ttu-id="fe343-134">レポート データ ペインでデータセットを右クリックし、 **[クエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-134">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
2.  <span data-ttu-id="fe343-135">**[フィールドの更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe343-135">Click **Refresh Fields**.</span></span>  
  
     <span data-ttu-id="fe343-136">レポート サーバーで、共有データセット クエリを実行し、現在のフィールド コレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="fe343-136">On the report server, the shared dataset query runs and returns the current field collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe343-137">参照</span><span class="sxs-lookup"><span data-stu-id="fe343-137">See Also</span></span>  
 <span data-ttu-id="fe343-138">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe343-138">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fe343-139">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe343-139">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="fe343-140">[レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fe343-140">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fe343-141">[Reporting Services クエリ デザイナー](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="fe343-141">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 [<span data-ttu-id="fe343-142">クエリ デザイナー &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="fe343-142">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
