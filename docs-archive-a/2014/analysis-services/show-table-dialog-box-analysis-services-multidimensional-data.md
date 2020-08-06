---
title: '[テーブルの表示] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.showtabledialog.f1
helpviewer_keywords:
- Show Table dialog box
ms.assetid: 4c0bf4fa-5685-4269-bf7d-f0e9802ab4bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15d90ccc5773663baf9c780a920d80e4adc38927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736864"
---
# <a name="show-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="887ea-102">[テーブルの表示] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="887ea-102">Show Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="887ea-103">**の** [テーブルの表示] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、ディメンション、キューブ、またはマイニング構造に関連付けられているデータ ソース ビューのテーブルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="887ea-103">Use the **Show Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to include tables from the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="887ea-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でこのダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="887ea-104">You can display this dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="887ea-105">**ディメンション デザイナー** の **[ディメンション構造]** ページの **[ツール バー]** ペインで **[テーブルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="887ea-105">Clicking **Show Tables** from the **Toolbar** pane on the **Dimension Structure** page of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="887ea-106">**ディメンション デザイナー** の **[ディメンション構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="887ea-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of **Dimension Designer** and selecting **Show Tables**.</span></span>  
  
-   <span data-ttu-id="887ea-107">**キューブ デザイナー** の **[キューブ構造]** ページの **[ツール バー]** ペインで **[テーブルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="887ea-107">Clicking **Show Tables** from the **Toolbar** pane on the **Cube Structure** page of **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="887ea-108">**キューブ デザイナー** の **[キューブ構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="887ea-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of **Cube Designer** and selecting **Show Tables**.</span></span>  
  
-   <span data-ttu-id="887ea-109">**データ マイニング モデル デザイナー** の **[マイニング構造]** ページの **[データ ソース ビュー]** ペインで何もない部分を右クリックし、 **[テーブルの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="887ea-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of **Data Mining Model Designer** and selecting **Show Tables**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="887ea-110">Options</span><span class="sxs-lookup"><span data-stu-id="887ea-110">Options</span></span>  
 <span data-ttu-id="887ea-111">**[他に表示するテーブルを選択します。]**</span><span class="sxs-lookup"><span data-stu-id="887ea-111">**Select additional tables to be shown**</span></span>  
 <span data-ttu-id="887ea-112">**[データ ソース ビュー]** ペインに追加するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="887ea-112">Select the tables to add to the **Data Source View** pane.</span></span> <span data-ttu-id="887ea-113">このオプションのグリッドには、 **[フィルター]** で設定したフィルターに一致する、現在のダイアグラムにまだ表示されていないオブジェクトとその種類が表示されます ( **[フィルター]** が設定されていない場合、すべてのテーブルが表示されます)。</span><span class="sxs-lookup"><span data-stu-id="887ea-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="887ea-114">**Assert**</span><span class="sxs-lookup"><span data-stu-id="887ea-114">**Filter**</span></span>  
 <span data-ttu-id="887ea-115">表示するオブジェクトを限定するために使用するフィルターを入力した後、ボタンをクリックすると、 **[他に表示するテーブルを選択します。]** に表示されるテーブルがフィルター選択されます。</span><span class="sxs-lookup"><span data-stu-id="887ea-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select additional tables to be shown**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887ea-116">参照</span><span class="sxs-lookup"><span data-stu-id="887ea-116">See Also</span></span>  
 <span data-ttu-id="887ea-117">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="887ea-117">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="887ea-118">[データソースビュー &#40;[ディメンション構造] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="887ea-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="887ea-119">[キューブデザイナーの [キューブ構造] タブの [データソースビュー &#40;&#41; &#40;Analysis Services-多次元データ&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="887ea-119">[Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
