---
title: '[オブジェクトのバインド] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
ms.openlocfilehash: a10c91e0222b826066aeede96aa665cc22540637
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642352"
---
# <a name="object-binding-dialog-box"></a><span data-ttu-id="f298f-102">[オブジェクトのバインド] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="f298f-102">Object Binding Dialog Box</span></span>
  <span data-ttu-id="f298f-103">**の** [オブジェクトのバインド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのプロパティとデータ ソース ビューのテーブルまたは列の間のバインドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="f298f-103">Use the **Object Binding** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define bindings between the property of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object and a table or column in a data source view.</span></span> <span data-ttu-id="f298f-104">**[オブジェクトのバインド]** ダイアログ ボックスを表示するには、 **の** [プロパティ] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ウィンドウで **オブジェクトの次のプロパティの値に対して、ドロップダウン リストから** [(新規)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を選択します。</span><span class="sxs-lookup"><span data-stu-id="f298f-104">You can display the **Object Binding** dialog box by selecting **(new)** from the drop-down list for the value of the following properties of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   <span data-ttu-id="f298f-105">NameColumn</span><span class="sxs-lookup"><span data-stu-id="f298f-105">NameColumn</span></span>  
  
-   <span data-ttu-id="f298f-106">ValueColumn</span><span class="sxs-lookup"><span data-stu-id="f298f-106">ValueColumn</span></span>  
  
-   <span data-ttu-id="f298f-107">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="f298f-107">CustomRollupColumn</span></span>  
  
-   <span data-ttu-id="f298f-108">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="f298f-108">CustomRollupPropertiesColumn</span></span>  
  
-   <span data-ttu-id="f298f-109">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="f298f-109">UnaryOperatorColumn</span></span>  
  
## <a name="options"></a><span data-ttu-id="f298f-110">Options</span><span class="sxs-lookup"><span data-stu-id="f298f-110">Options</span></span>  
 <span data-ttu-id="f298f-111">**バインドの種類**</span><span class="sxs-lookup"><span data-stu-id="f298f-111">**Binding type**</span></span>  
 <span data-ttu-id="f298f-112">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトに対して使用するバインドを選択します。</span><span class="sxs-lookup"><span data-stu-id="f298f-112">Select the binding to use for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="f298f-113">次の種類のバインドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f298f-113">The following types of binding can be used:</span></span>  
  
 <span data-ttu-id="f298f-114">[列のバインド]</span><span class="sxs-lookup"><span data-stu-id="f298f-114">Column binding</span></span>  
 <span data-ttu-id="f298f-115">オブジェクトをデータ ソース ビュー内の既存のテーブルおよび列にバインドします。</span><span class="sxs-lookup"><span data-stu-id="f298f-115">Binds the object to an existing table and column within a data source view.</span></span>  
  
 <span data-ttu-id="f298f-116">[列の生成]</span><span class="sxs-lookup"><span data-stu-id="f298f-116">Generate column</span></span>  
 <span data-ttu-id="f298f-117">データ ソース ビュー内で新しい列を定義して、列のバインドを関連付けることを示します。</span><span class="sxs-lookup"><span data-stu-id="f298f-117">Indicates that a new column is to be defined in the data source view, and a column binding is then associated with it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f298f-118"> このオプションを選択した場合は、 **オブジェクトを配置する前に** スキーマ生成ウィザード [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f298f-118">If this option is selected, you must run the **Schema Generation Wizard** before deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="f298f-119">[行のバインド]</span><span class="sxs-lookup"><span data-stu-id="f298f-119">Row binding</span></span>  
 <span data-ttu-id="f298f-120">オブジェクトをファクト テーブルの行にバインドします。ファクト テーブルで処理される行の数に基づくカウント メジャーに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f298f-120">Binds the object to a row in a fact table and is used to facilitate count measures based on the number of rows processed in the fact table.</span></span>  
  
 <span data-ttu-id="f298f-121">**基になるテーブル**</span><span class="sxs-lookup"><span data-stu-id="f298f-121">**Source table**</span></span>  
 <span data-ttu-id="f298f-122">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトに関連付けられているデータ ソース ビュー内のテーブルの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f298f-122">Displays a list of tables in the data source view associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="f298f-123">**ソース列**</span><span class="sxs-lookup"><span data-stu-id="f298f-123">**Source column**</span></span>  
 <span data-ttu-id="f298f-124">**[基になるテーブル]** で選択されているテーブル内の列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f298f-124">Displays a list of columns in the table selected in **Source table**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f298f-125">参照</span><span class="sxs-lookup"><span data-stu-id="f298f-125">See Also</span></span>  
 [<span data-ttu-id="f298f-126">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="f298f-126">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
