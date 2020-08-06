---
title: '[フィールド] ([データセットのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b9d315f85751c0f73896e809a522613fefece5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632993"
---
# <a name="dataset-properties-dialog-box-fields"></a><span data-ttu-id="bb9f5-102">[フィールド] ([データセットのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="bb9f5-102">Dataset Properties Dialog Box, Fields</span></span>
  <span data-ttu-id="bb9f5-103">**[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** を選択すると、レポート データセットのフィールド コレクションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="bb9f5-104">フィールドの一覧は自動的に作成されますが、 **[フィールド]** を使用してクエリ フィールドや計算フィールドを追加、編集、および削除することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bb9f5-105">Options</span><span class="sxs-lookup"><span data-stu-id="bb9f5-105">Options</span></span>  
 <span data-ttu-id="bb9f5-106">**追加**</span><span class="sxs-lookup"><span data-stu-id="bb9f5-106">**Add**</span></span>  
 <span data-ttu-id="bb9f5-107">新しいクエリフィールドまたは計算フィールドをデータセットに追加します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-107">Add a new query field or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="bb9f5-108">**削除**</span><span class="sxs-lookup"><span data-stu-id="bb9f5-108">**Delete**</span></span>  
 <span data-ttu-id="bb9f5-109">選択したフィールドをデータセットから削除します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-109">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="bb9f5-110">**フィールド名**</span><span class="sxs-lookup"><span data-stu-id="bb9f5-110">**Field Name**</span></span>  
 <span data-ttu-id="bb9f5-111">フィールドの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-111">Type a name for the field.</span></span> <span data-ttu-id="bb9f5-112">フィールドはデータセット内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-112">The field must be unique within the dataset.</span></span> <span data-ttu-id="bb9f5-113">データセット クエリ内にある既存の各フィールドの名前は、あらかじめ設定されています。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-113">For each existing field in the dataset query, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="bb9f5-114">**[フィールド ソース]**</span><span class="sxs-lookup"><span data-stu-id="bb9f5-114">**Field Source**</span></span>  
 <span data-ttu-id="bb9f5-115">フィールドの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-115">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="bb9f5-116">計算フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前か、ユーザーが作成した式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-116">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="bb9f5-117">たとえば、Sales クエリ フィールドの値の 10 倍を表すフィールドを作成する場合は、 `=10 * Fields!Sales.Value`という式を使用します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-117">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="bb9f5-118">クエリ フィールドの場合、フィールド ソースは、データセット クエリで取得した既存のフィールドの名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-118">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="bb9f5-119">**式 ([fx])**</span><span class="sxs-lookup"><span data-stu-id="bb9f5-119">**Expression (fx)**</span></span>  
 <span data-ttu-id="bb9f5-120">計算フィールドを表す式を追加または変更します。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-120">Add or change an expression for the calculated field.</span></span> <span data-ttu-id="bb9f5-121">このボタンは、 **[追加]** をクリックして **[計算フィールド]** を選択した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb9f5-121">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9f5-122">参照</span><span class="sxs-lookup"><span data-stu-id="bb9f5-122">See Also</span></span>  
 <span data-ttu-id="bb9f5-123">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bb9f5-123">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bb9f5-124">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bb9f5-124">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="bb9f5-125">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9f5-125">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
