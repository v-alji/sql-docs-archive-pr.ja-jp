---
title: テーブル内のデータのフィルター処理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f4003457df4068713e75e6bb5c0ab78c15ac03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712518"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a><span data-ttu-id="7bd0c-102">テーブル内のデータのフィルター処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="7bd0c-102">Filter Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="7bd0c-103">テーブルに読み込む行を制御するには、データをインポートする際にフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-103">You can apply filters when you import data to control the rows that are loaded into a table.</span></span> <span data-ttu-id="7bd0c-104">データをインポートした後、行を個別に削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-104">After you have imported the data, you cannot delete individual rows.</span></span> <span data-ttu-id="7bd0c-105">ただし、カスタム フィルターを適用して行の表示方法を制御することは可能です。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-105">However, you can apply custom filters to control the way that rows are displayed.</span></span> <span data-ttu-id="7bd0c-106">フィルター条件を満たしていない行は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-106">Rows that do not meet the filtering criteria are hidden.</span></span> <span data-ttu-id="7bd0c-107">1 行以上の列を基準にしてフィルター処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-107">You can filter by one or more columns.</span></span> <span data-ttu-id="7bd0c-108">フィルター処理は追加型です。つまり、新しいフィルターによる処理は、前のフィルター処理の結果に対して行われます。したがって、フィルターを適用するごとにデータのサブセットは減っていきます。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-108">Filters are additive, which means that each additional filter is based on the current filter and further reduces the subset of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bd0c-109">フィルターのプレビュー ウィンドウでは、表示される異なる値の数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-109">The filter preview window limits the number of different values displayed.</span></span> <span data-ttu-id="7bd0c-110">制限を超えた場合は、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-110">If the limit is exceeded, a message is displayed.</span></span>  
  
### <a name="to-filter-data-based-on-column-values"></a><span data-ttu-id="7bd0c-111">列の値を基準にしてデータをフィルター処理するには</span><span class="sxs-lookup"><span data-stu-id="7bd0c-111">To filter data based on column values</span></span>  
  
1.  <span data-ttu-id="7bd0c-112">モデル デザイナーでテーブルを選択し、フィルター処理の基準にする列の見出しの矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-112">In the model designer, select a table, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="7bd0c-113">[オートフィルター] メニューで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="7bd0c-114">列の値の一覧で、フィルター処理の条件として1つ以上の値を選択または選択解除し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-114">In the list of column values, select or clear one or more values to filter by, and then click **OK**.</span></span>  
  
         <span data-ttu-id="7bd0c-115">値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-115">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="7bd0c-116">その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-116">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="7bd0c-117">[**数値フィルター** ] または [**テキストフィルター** ] (列の種類によって異なります) をクリックし、比較演算子コマンドのいずれかクリック ( **Equals**など) を選択するか、[**カスタムフィルター**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-117">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as **Equals**), or click **Custom Filter**.</span></span> <span data-ttu-id="7bd0c-118">**[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-118">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
### <a name="to-clear-a-filter-for-a-column"></a><span data-ttu-id="7bd0c-119">列のフィルターをクリアするには</span><span class="sxs-lookup"><span data-stu-id="7bd0c-119">To clear a filter for a column</span></span>  
  
1.  <span data-ttu-id="7bd0c-120">フィルターをクリアする列の見出しの矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-120">Click the arrow in the header of the column for which you want to clear a filter.</span></span>  
  
2.  <span data-ttu-id="7bd0c-121">[**フィルターをクリア \<Column Name> ] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-121">Click **Clear Filter from \<Column Name>**.</span></span>  
  
### <a name="to-clear-all-filters-for-a-table"></a><span data-ttu-id="7bd0c-122">テーブルのすべてのフィルターをクリアするには</span><span class="sxs-lookup"><span data-stu-id="7bd0c-122">To clear all filters for a table</span></span>  
  
1.  <span data-ttu-id="7bd0c-123">モデル デザイナーで、フィルターをクリアするテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-123">In the model designer, select the table for which you want to clear filters.</span></span>  
  
2.  <span data-ttu-id="7bd0c-124">**[列]** メニューをクリックし、 **[すべてのフィルターをクリア]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd0c-124">Click on the **Column** menu, and then click **Clear All Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd0c-125">参照</span><span class="sxs-lookup"><span data-stu-id="7bd0c-125">See Also</span></span>  
 <span data-ttu-id="7bd0c-126">[SSAS 表形式&#41;&#40;データのフィルター処理と並べ替え](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7bd0c-126">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="7bd0c-127">[SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7bd0c-127">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="7bd0c-128">ロール (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="7bd0c-128">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
