---
title: '[新しいメジャー] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.newmeasuredialog.f1
helpviewer_keywords:
- New Measure dialog box
ms.assetid: 86dc9146-cc6d-4cef-b178-9a6b4cf616e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1fb60bd598257d2de1f60900aafa43b085000fd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743533"
---
# <a name="new-measure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="486c1-102">[新しいメジャー] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="486c1-102">New Measure Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="486c1-103">**の** [新しいメジャー] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、キューブ デザイナーでメジャー グループに新しいメジャーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="486c1-103">Use the **New Measure** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a new measure to a measure group in Cube Designer.</span></span> <span data-ttu-id="486c1-104">**[新しいメジャー]** ダイアログ ボックスは次の方法で表示します。</span><span class="sxs-lookup"><span data-stu-id="486c1-104">You can display the **New Measure** dialog box by:</span></span>  
  
-   <span data-ttu-id="486c1-105">キューブ デザイナーの **[キューブ構造]** タブの **[ツール バー]** ペインで **[新しいメジャー]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="486c1-105">Clicking **New Measure** in the **Toolbar** pane on the **Cube Structure** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="486c1-106">**[キューブ構造]** タブの **[メジャー]** ペインでメジャー グループまたはメジャーを右クリックし、コンテキスト メニューの **[新しいメジャー]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="486c1-106">Right-clicking a measure group or measure in the **Measures** pane on the **Cube Structure** tab in Cube Designer and selecting **New Measure** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="486c1-107">Options</span><span class="sxs-lookup"><span data-stu-id="486c1-107">Options</span></span>  
 <span data-ttu-id="486c1-108">**使用方法**</span><span class="sxs-lookup"><span data-stu-id="486c1-108">**Usage**</span></span>  
 <span data-ttu-id="486c1-109">新しいメジャーによって使用される集計関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="486c1-109">Select the aggregation function to be used by the new measure.</span></span>  
  
 <span data-ttu-id="486c1-110">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="486c1-110">**Source table**</span></span>  
 <span data-ttu-id="486c1-111">新しいメジャーを作成するときに基になるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="486c1-111">Select the table from which the new measure is to be created.</span></span>  
  
 <span data-ttu-id="486c1-112">**ソース列**</span><span class="sxs-lookup"><span data-stu-id="486c1-112">**Source column**</span></span>  
 <span data-ttu-id="486c1-113">**[基になるテーブル]** で選択されたテーブルから新しいメジャーの基になる列を選択します。</span><span class="sxs-lookup"><span data-stu-id="486c1-113">Select the column in the table selected in **Source table** on which the new measure is to be based.</span></span>  
  
 <span data-ttu-id="486c1-114">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="486c1-114">**Show all columns**</span></span>  
 <span data-ttu-id="486c1-115">新しいメジャーが作成されるメジャー グループのファクト テーブル内のすべての列を表示することを選択します。</span><span class="sxs-lookup"><span data-stu-id="486c1-115">Select to display all columns in the fact table for the measure group in which the new measure is to be created.</span></span> <span data-ttu-id="486c1-116">選択しなかった場合、 **[基になる列]** には、論理プライマリ キーとして使用されずリレーションシップにも含まれない数値列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="486c1-116">If not selected, **Source column** only displays numeric columns that are not used as logical primary keys or involved in relationships.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486c1-117">参照</span><span class="sxs-lookup"><span data-stu-id="486c1-117">See Also</span></span>  
 <span data-ttu-id="486c1-118">[キューブ構造 &#40;キューブデザイナーの&#41; &#40;Analysis Services-多次元データ&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="486c1-118">[Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="486c1-119">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="486c1-119">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
