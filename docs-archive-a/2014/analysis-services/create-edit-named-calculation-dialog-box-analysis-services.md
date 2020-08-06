---
title: '[作成-名前付き計算の編集] ダイアログボックス (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b6777feb47a1ce6b601d0190e413b4baae35f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631363"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a><span data-ttu-id="a1ef0-102">[作成-名前付き計算の編集] ダイアログボックス (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a1ef0-102">Create-Edit Named Calculation Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="a1ef0-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の **[名前付き計算の作成]/[名前付き計算の編集]** ダイアログ ボックスを使用すると、データ ソース ビューにあるテーブルの名前付き計算を定義または変更できます。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-103">Use the **Create/Edit Named Calculation** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a named calculation for a table in a data source view.</span></span> <span data-ttu-id="a1ef0-104">**[名前付き計算の作成]/[名前付き計算の編集]** ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-104">You can display the **Create/Edit Named Calculation** dialog box by:</span></span>  
  
-   <span data-ttu-id="a1ef0-105">**データ ソース ビュー デザイナー**の **[ツール バー]** ペインにある **[新しい名前付き計算]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-105">Clicking **New Named Calculation** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="a1ef0-106">**データ ソース ビュー デザイナー**の **[テーブル]** ペインまたは **[ダイアグラム]** ペインにあるテーブルを右クリックして、**[新しい名前付き計算]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Named Calculation**.</span></span>  
  
-   <span data-ttu-id="a1ef0-107">**データ ソース ビュー デザイナー**の **[ダイアグラム]** ペインで、名前付き計算の名前を右クリックして、**[名前付き計算の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-107">Right-clicking the name of a named calculation in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Named Calculation**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a1ef0-108">Options</span><span class="sxs-lookup"><span data-stu-id="a1ef0-108">Options</span></span>  
 <span data-ttu-id="a1ef0-109">**列名**</span><span class="sxs-lookup"><span data-stu-id="a1ef0-109">**Column Name**</span></span>  
 <span data-ttu-id="a1ef0-110">名前付き計算の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-110">Type the name of the named calculation.</span></span>  
  
 <span data-ttu-id="a1ef0-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="a1ef0-111">**Description**</span></span>  
 <span data-ttu-id="a1ef0-112">名前付き計算の説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-112">Type the optional description of the named calculation.</span></span>  
  
 <span data-ttu-id="a1ef0-113">**[式]**</span><span class="sxs-lookup"><span data-stu-id="a1ef0-113">**Expression**</span></span>  
 <span data-ttu-id="a1ef0-114">スカラー値を返す有効な SQL 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-114">Type a valid SQL expression that returns a scalar value.</span></span> <span data-ttu-id="a1ef0-115">この式はプロバイダーに送られ、次の式により検証されます。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-115">The expression is sent to the provider, and validated in the following expression:</span></span>  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 <span data-ttu-id="a1ef0-116">式では、下位選択ステートメントを使用して他のテーブルへの参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a1ef0-116">The expression can contain references to other tables, by means of a sub-select statement.</span></span> <span data-ttu-id="a1ef0-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span><span class="sxs-lookup"><span data-stu-id="a1ef0-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ef0-118">参照</span><span class="sxs-lookup"><span data-stu-id="a1ef0-118">See Also</span></span>  
 <span data-ttu-id="a1ef0-119">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a1ef0-119">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a1ef0-120">データ ソース ビュー デザイナー (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="a1ef0-120">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
