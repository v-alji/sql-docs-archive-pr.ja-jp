---
title: 基になる情報の指定 (ディメンションウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 99bbaac0bdf24a18dcde455e779f056b98106dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643511"
---
# <a name="specify-source-information-dimension-wizard"></a><span data-ttu-id="ffa0a-102">[基になる情報の指定] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="ffa0a-102">Specify Source Information (Dimension Wizard)</span></span>
  <span data-ttu-id="ffa0a-103">**[メイン ディメンション テーブルの選択]** ページを使用すると、作成するディメンションのデータ ソース ビュー、メイン ディメンション テーブル、キー列、およびメンバー名列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-103">Use the **Select the Main Dimension Table** page to select the data source view, main dimension table, key columns, and member name column for the dimension to be created.</span></span>  
  
 <span data-ttu-id="ffa0a-104">**ディメンション ウィザードを開くには**</span><span class="sxs-lookup"><span data-stu-id="ffa0a-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="ffa0a-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、 **プロジェクトの** [ディメンション] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ffa0a-106">Options</span><span class="sxs-lookup"><span data-stu-id="ffa0a-106">Options</span></span>  
 <span data-ttu-id="ffa0a-107">**データソースビュー**</span><span class="sxs-lookup"><span data-stu-id="ffa0a-107">**Data source view**</span></span>  
 <span data-ttu-id="ffa0a-108">データ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-108">Select a data source view.</span></span>  
  
 <span data-ttu-id="ffa0a-109">**[メイン テーブル]**</span><span class="sxs-lookup"><span data-stu-id="ffa0a-109">**Main table**</span></span>  
 <span data-ttu-id="ffa0a-110">選択したデータ ソース ビューから、ディメンションのメイン テーブルとして使用するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-110">Select a table from the selected data source view to use as the main table for the dimension.</span></span>  
  
 <span data-ttu-id="ffa0a-111">**キー列**</span><span class="sxs-lookup"><span data-stu-id="ffa0a-111">**Key columns**</span></span>  
 <span data-ttu-id="ffa0a-112">**[メイン テーブル]** で指定したテーブルから、ディメンションのキー属性に使用するキー列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-112">Select the key columns from the table specified in **Main table** for the key attribute of the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffa0a-113">列は 1 つ以上選択できます。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-113">More than one column can be selected.</span></span> <span data-ttu-id="ffa0a-114">テーブルに複合主キーが含まれている場合は、複合主キーに含まれる列をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-114">If the table contains a composite primary key, select all the columns included in the composite primary key.</span></span> <span data-ttu-id="ffa0a-115">キー列の順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-115">The order of the key columns is important.</span></span>  
  
 <span data-ttu-id="ffa0a-116">**名前列**</span><span class="sxs-lookup"><span data-stu-id="ffa0a-116">**Name column**</span></span>  
 <span data-ttu-id="ffa0a-117">**[メイン テーブル]** で指定したテーブルから、ディメンションのメンバー名を含んでいる列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-117">Select the column from the table specified in **Main table** that provides the member names for the dimension.</span></span> <span data-ttu-id="ffa0a-118">名前列は、複合キーを使用する場合に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-118">A name column must be specified when a composite key is used.</span></span> <span data-ttu-id="ffa0a-119">複合キーの名前列を作成するには、指定されたキー列を連結する名前付き計算をデータ ソース ビューで作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-119">To create a name column for a composite key, we recommend that you create a named calculation in the data source view that concatenates the specified key columns.</span></span> <span data-ttu-id="ffa0a-120">1 つのキーを使用する場合、名前列は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ffa0a-120">When a single key is used, the name column is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa0a-121">参照</span><span class="sxs-lookup"><span data-stu-id="ffa0a-121">See Also</span></span>  
 <span data-ttu-id="ffa0a-122">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ffa0a-122">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="ffa0a-123">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ffa0a-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="ffa0a-124">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="ffa0a-124">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
