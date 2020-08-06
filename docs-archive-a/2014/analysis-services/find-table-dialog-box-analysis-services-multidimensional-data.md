---
title: '[テーブルの検索] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.findtabledialog.f1
helpviewer_keywords:
- Find Table dialog box
ms.assetid: 133d28e8-55eb-4783-bb8b-d3776a95ebda
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee22c912a3121841a7827e31d53f7b8baba72174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633442"
---
# <a name="find-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="24366-102">[テーブルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="24366-102">Find Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="24366-103">**の** [テーブルの検索] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、ディメンション、キューブ、またはマイニング構造に関連付けられているデータ ソース ビュー内のテーブルを検索できます。</span><span class="sxs-lookup"><span data-stu-id="24366-103">Use the **Find Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to locate a table in the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="24366-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でこのダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="24366-104">You can display this dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] by:</span></span>  
  
-   <span data-ttu-id="24366-105">**ディメンション デザイナー** の **[ディメンション構造]** ページの **[ツール バー]** ペインで **[テーブルの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24366-105">Clicking **Find Table** from the **Toolbar** pane on the **Dimension Structure** page of the **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="24366-106">**ディメンション デザイナー** の **[ディメンション構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの検索]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="24366-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of the **Dimension Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="24366-107">**キューブ デザイナー** の **[キューブ構造]** ページの **[ツール バー]** ペインで **[テーブルの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24366-107">Clicking **Find Table** from the **Toolbar** pane on the **Cube Structure** page of the **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="24366-108">**キューブ デザイナー** の **[キューブ構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの検索]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="24366-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of the **Cube Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="24366-109">**データ マイニング モデル デザイナー** の **[マイニング構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの検索]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="24366-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of the **Data Mining Model Designer** and selecting **Find Table**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="24366-110">Options</span><span class="sxs-lookup"><span data-stu-id="24366-110">Options</span></span>  
 <span data-ttu-id="24366-111">**[データ ソース ビューからテーブルを選択]**</span><span class="sxs-lookup"><span data-stu-id="24366-111">**Select a table from data source view**</span></span>  
 <span data-ttu-id="24366-112">検索するテーブルを **[データ ソース ビュー]** ペインで選択します。</span><span class="sxs-lookup"><span data-stu-id="24366-112">Select the table to find in the **Data Source View** pane.</span></span> <span data-ttu-id="24366-113">このオプションのグリッドには、 **[フィルター]** で設定したフィルターに一致する、現在のダイアグラムにまだ表示されていないオブジェクトとその種類が表示されます ( **[フィルター]** が設定されていない場合、すべてのテーブルが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="24366-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="24366-114">**Assert**</span><span class="sxs-lookup"><span data-stu-id="24366-114">**Filter**</span></span>  
 <span data-ttu-id="24366-115">表示するオブジェクトを限定するために使用するフィルターを入力した後、ボタンをクリックすると、 **[データ ソース ビューからテーブルを選択]** に表示されるテーブルがフィルター選択されます。</span><span class="sxs-lookup"><span data-stu-id="24366-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select a table from data source view**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24366-116">参照</span><span class="sxs-lookup"><span data-stu-id="24366-116">See Also</span></span>  
 <span data-ttu-id="24366-117">[[アセンブリのプロパティ] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="24366-117">[Assembly Properties Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="24366-118">[データソースビュー &#40;[ディメンション構造] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="24366-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="24366-119">[キューブデザイナーの [キューブ構造] タブの [データソースビュー &#40;&#41; &#40;Analysis Services-多次元データ&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="24366-119">[Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
