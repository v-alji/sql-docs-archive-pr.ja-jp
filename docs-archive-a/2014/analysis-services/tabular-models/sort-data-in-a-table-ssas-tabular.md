---
title: テーブル内のデータの並べ替え (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9a6636c2c11fc571e8d4c1bcbc25c1e02d815fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711038"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a><span data-ttu-id="6e6fd-102">テーブル内のデータの並べ替え (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="6e6fd-102">Sort Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="6e6fd-103">データは、1 つ以上の列のテキスト (A から Z、または Z から A) または数値 (小さい数値から大きい数値、または大きい数値から小さい数値) の順で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-103">You can sort data by text (A to Z or Z to A) and numbers (smallest to largest or largest to smallest) in one or more columns.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a><span data-ttu-id="6e6fd-104">テキスト列を基準にテーブル データを並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="6e6fd-104">To sort the data in a table based on a text column</span></span>  
  
1.  <span data-ttu-id="6e6fd-105">モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-105">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="6e6fd-106">[オートフィルター] メニューで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-106">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="6e6fd-107">英数字の昇順で並べ替えるには、 **[昇順で並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-107">To sort in ascending alphanumeric order, click **Sort A to Z**.</span></span>  
  
    -   <span data-ttu-id="6e6fd-108">英数字の降順で並べ替えるには、 **[降順で並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-108">To sort in descending alphanumeric order, click **Sort Z to A**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e6fd-109">他のアプリケーションからインポートされたデータの場合、データの先頭にスペースが挿入されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-109">In some cases, data imported from another application might have leading spaces inserted before data.</span></span> <span data-ttu-id="6e6fd-110">データを正しく並べ替えるには、先頭のスペースを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-110">You must remove the leading spaces in order to correctly sort the data.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a><span data-ttu-id="6e6fd-111">数値列を基準にテーブル データを並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="6e6fd-111">To sort the data in a table based on a numeric column</span></span>  
  
1.  <span data-ttu-id="6e6fd-112">モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-112">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="6e6fd-113">[オートフィルター] メニューで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="6e6fd-114">小さい数値から順に並べ替えるには、 **[小さい順に並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-114">To sort from low numbers to high numbers, click **Sort Smallest to Largest**.</span></span>  
  
    -   <span data-ttu-id="6e6fd-115">大きい数値から順に並べ替えるには、 **[大きい順に並べ替え]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-115">To sort from high numbers to low numbers, click **Sort Largest to Smallest**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e6fd-116">期待した結果が得られない場合、列の数値が数値ではなくテキストとして格納されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-116">If the results are not what you expected, the column might contain numbers stored as text and not as numbers.</span></span> <span data-ttu-id="6e6fd-117">たとえば、何らかの会計システムからインポートされた負の数値や、先頭にアポストロフィ (') が入力されている数値は、テキストとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="6e6fd-117">For example, negative numbers imported from some accounting systems, or a number entered with a leading ' (apostrophe), are stored as text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6fd-118">参照</span><span class="sxs-lookup"><span data-stu-id="6e6fd-118">See Also</span></span>  
 <span data-ttu-id="6e6fd-119">[SSAS 表形式&#41;&#40;データのフィルター処理と並べ替え](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="6e6fd-119">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="6e6fd-120">[SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="6e6fd-120">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="6e6fd-121">ロール (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="6e6fd-121">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
