---
title: '[メンバーのフィルター選択] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.filtermembers.f1
helpviewer_keywords:
- Filter Members dialog box
ms.assetid: 52c6da1d-9fb5-4dbc-bffa-248d11cd337c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66980b1afe9d4eed353ae18c37ed1fdd052e62b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631315"
---
# <a name="filter-members-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="bfccd-102">[メンバーのフィルター選択] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="bfccd-102">Filter Members Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="bfccd-103">**の** [メンバーのフィルター選択] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 **ディメンション デザイナー** の **[ブラウザー]** タブでディメンションを参照しながら、現在のレベルのメンバー キャプション、メンバー名、メンバーの一意名、キー列値、または値列値でディメンション メンバーをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="bfccd-103">Use the **Filter Members** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to filter dimension members by member caption, member name, member unique name, key column value, or value column value for the current level while browsing a dimension in the **Browser** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfccd-104">Options</span><span class="sxs-lookup"><span data-stu-id="bfccd-104">Options</span></span>  
  
|<span data-ttu-id="bfccd-105">期間</span><span class="sxs-lookup"><span data-stu-id="bfccd-105">Term</span></span>|<span data-ttu-id="bfccd-106">定義</span><span class="sxs-lookup"><span data-stu-id="bfccd-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="bfccd-107">**フィルター式**</span><span class="sxs-lookup"><span data-stu-id="bfccd-107">**Filter expression**</span></span>|<span data-ttu-id="bfccd-108">フィルター式を作成するためのプロパティ、操作、および値のグリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="bfccd-108">Displays a grid of properties, operators, and values used to construct a filter expression.</span></span> <span data-ttu-id="bfccd-109">いったん追加した行は削除できません。</span><span class="sxs-lookup"><span data-stu-id="bfccd-109">Note that after a row is added, it cannot be removed.</span></span> <span data-ttu-id="bfccd-110">新しいフィルター式を指定するには、ダイアログ ボックスを閉じてから開き直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfccd-110">You must close and reopen the dialog box to specify a new filter expression.</span></span> <span data-ttu-id="bfccd-111">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bfccd-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="bfccd-112">[**プロパティ**]: フィルター式に使用するメンバーのプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="bfccd-112">**Property**: Select the property of the member to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="bfccd-113">**演算子**: フィルター式に使用する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="bfccd-113">**Operator**: Select the operator to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="bfccd-114">**値**: [**プロパティ**で選択されたプロパティの値を入力して、**演算子**に指定された演算子を使用して評価します。</span><span class="sxs-lookup"><span data-stu-id="bfccd-114">**Value**: Type the value of the property selected in **Property** to evaluate using the operator specified in **Operator**.</span></span>|  
|<span data-ttu-id="bfccd-115">**Test pane**</span><span class="sxs-lookup"><span data-stu-id="bfccd-115">**Test pane**</span></span>|<span data-ttu-id="bfccd-116">**[テスト]** をクリックすると、フィルター式から返されたメンバーがこのペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bfccd-116">When **Test** is clicked, this pane displays the members returned by the filter expression.</span></span> <span data-ttu-id="bfccd-117">**[フィルター式]** に指定した条件に従って返されるメンバーがない場合は、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bfccd-117">If no members are returned using the criteria specified in **Filter expression**, a warning is displayed.</span></span>|  
|<span data-ttu-id="bfccd-118">**テスト**</span><span class="sxs-lookup"><span data-stu-id="bfccd-118">**Test**</span></span>|<span data-ttu-id="bfccd-119">クリックすると、 **[フィルター式]** に指定した条件がテストされます。</span><span class="sxs-lookup"><span data-stu-id="bfccd-119">Click to test the criteria specified in **Filter expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfccd-120">参照</span><span class="sxs-lookup"><span data-stu-id="bfccd-120">See Also</span></span>  
 <span data-ttu-id="bfccd-121">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bfccd-121">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="bfccd-122">ブラウザー &#40;ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="bfccd-122">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
