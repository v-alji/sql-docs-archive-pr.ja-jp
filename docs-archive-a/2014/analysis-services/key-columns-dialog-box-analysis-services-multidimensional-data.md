---
title: '[キー列] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a72a9e137700ddee822e68901bfde971637d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633412"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="3c9a6-102">[キー列] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="3c9a6-102">Key Columns Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3c9a6-103">属性の **KeyColumns** プロパティを変更するには、 **[キー列]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-103">Use the **Key Columns** dialog box to change the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="3c9a6-104">詳細については、「 [属性の KeyColumn プロパティの変更](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-104">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
 <span data-ttu-id="3c9a6-105">**[キー列] ダイアログ ボックスを表示するには**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-105">**To display the Key Columns dialog box**</span></span>  
  
-   <span data-ttu-id="3c9a6-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、属性を選択し、 **[プロパティ]** ウィンドウで、その属性の**KeyColumns**プロパティに関連付けられた省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-106">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select an attribute, and in the **Properties** window, click the ellipsis button (**...**) associated with the **KeyColumns** property of that attribute.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c9a6-107">Options</span><span class="sxs-lookup"><span data-stu-id="3c9a6-107">Options</span></span>  
 <span data-ttu-id="3c9a6-108">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-108">**Source table**</span></span>  
 <span data-ttu-id="3c9a6-109">選択するキー列を含む、基になるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-109">Select the source table for which you want to select its key columns.</span></span> <span data-ttu-id="3c9a6-110">基になるテーブルは、データ ソース ビュー内のすべてのテーブルの一覧から選択できます。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-110">You can select the source table from a list of all tables in the Data Source View.</span></span>  
  
 <span data-ttu-id="3c9a6-111">**使用できる列**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-111">**Available Columns**</span></span>  
 <span data-ttu-id="3c9a6-112">キー列として使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-112">Select the columns that you want to use as key columns.</span></span> <span data-ttu-id="3c9a6-113">指定した **[基になるテーブル]** 内の列の一覧から、まだキー列として選択されていない列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-113">You can select the columns from a list of columns in the specified **Source table** that have not yet been selected as key columns.</span></span>  
  
 <span data-ttu-id="3c9a6-114">選択した列を **[キー列]** の一覧に追加するには、**[>]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-114">To add the selected columns to the **Key Columns** list, click the **>** button.</span></span>  
  
 <span data-ttu-id="3c9a6-115">**[キー列]**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-115">**Key Columns**</span></span>  
 <span data-ttu-id="3c9a6-116">選択したキー列の順序を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-116">Define the order of the selected key columns.</span></span> <span data-ttu-id="3c9a6-117">キー列の順序は、適切な複合キーを定義する際に重要です。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-117">The order of the key columns is important in defining the correct composite key.</span></span> <span data-ttu-id="3c9a6-118">キー列の一覧の順序を設定または変更するには、列を選択し、**[上へ]** または **[下へ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-118">To order or reorder the list of key columns, select a column, and then click the **Up** or **Down** buttons.</span></span>  
  
 <span data-ttu-id="3c9a6-119">**[キー列]** の一覧から列を削除するには、列を選択し、**[\<]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-119">To remove a column from the **Key Columns** list, select the column and click the **\<** button.</span></span>  
  
 <span data-ttu-id="3c9a6-120">**設定**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-120">**Up**</span></span>  
 <span data-ttu-id="3c9a6-121">**[キー列]** で選択した列を 1 つ上の位置に移動する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-121">Click to move the column selected in **Key Columns** up one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c9a6-122">このオプションは、一覧に複数の列が含まれ、列が選択されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-122">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 <span data-ttu-id="3c9a6-123">**[下へ]**</span><span class="sxs-lookup"><span data-stu-id="3c9a6-123">**Down**</span></span>  
 <span data-ttu-id="3c9a6-124">**[キー列]** で選択した列を 1 つ下の位置に移動する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-124">Click to move the column selected in **Key Columns** down one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c9a6-125">このオプションは、一覧に複数の列が含まれ、列が選択されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-125">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 **>**  
 <span data-ttu-id="3c9a6-126">新しい列を **[キー列]** の一覧に表示される列の末尾に追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-126">Click to add a new column to the end of the columns listed in **Key Columns**.</span></span>  
  
 **<**  
 <span data-ttu-id="3c9a6-127">選択した列を **[キー列]** の一覧に表示される列から削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c9a6-127">Click to remove the selected column from the columns listed in **Key Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9a6-128">参照</span><span class="sxs-lookup"><span data-stu-id="3c9a6-128">See Also</span></span>  
 [<span data-ttu-id="3c9a6-129">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="3c9a6-129">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
