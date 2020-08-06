---
title: '[作成方法の選択] (ディメンションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensiondefinition.f1
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6338a0bde7865482fb7a98d7ec36ba5a71feb806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712533"
---
# <a name="select-creation-method-dimension-wizard"></a><span data-ttu-id="f2fe1-102">[作成方法の選択] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="f2fe1-102">Select Creation Method (Dimension Wizard)</span></span>
  <span data-ttu-id="f2fe1-103">**[作成方法の選択]** ページを使用すると、ディメンションの作成方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-103">Use the **Select Creation Method** page to select how to create the dimension.</span></span>  
  
 <span data-ttu-id="f2fe1-104">**ディメンション ウィザードを開くには**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="f2fe1-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、 **プロジェクトの** [ディメンション] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2fe1-106">Options</span><span class="sxs-lookup"><span data-stu-id="f2fe1-106">Options</span></span>  
 <span data-ttu-id="f2fe1-107">**[既存のテーブルの使用]**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-107">**Use an existing table**</span></span>  
 <span data-ttu-id="f2fe1-108">データ ソース内の 1 つ以上のテーブルからディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-108">Create a dimension from one or more tables in a data source.</span></span> <span data-ttu-id="f2fe1-109">ディメンションに使用できる属性は、テーブル内のデータの構造によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-109">The attributes that are available for the dimension will depend on the structure of the data in the table.</span></span>  
  
 <span data-ttu-id="f2fe1-110">詳細については、「 [Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)」(既存のテーブルを使用したディメンションの作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-110">For more information, see [Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md).</span></span>  
  
 <span data-ttu-id="f2fe1-111">**[データ ソースに時間テーブルを生成]**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-111">**Generate a time table in the data source**</span></span>  
 <span data-ttu-id="f2fe1-112">基になるデータ ソースに時間テーブルを作成し、そのテーブルを使用して時間ディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-112">Create a time table in the underlying data source and then use that table to create a time dimension.</span></span> <span data-ttu-id="f2fe1-113">こうしたテーブルが存在せず、テーブルの作成にスクリプトを使用しない場合、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-113">Use this option when no such table exists and you do not want to use a script to create one.</span></span> <span data-ttu-id="f2fe1-114">新しい時間テーブルには、ウィザードで指定した日付範囲、属性、およびカレンダーのデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-114">The new time table will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2fe1-115">このオプションを使用するには、基になるデータ ソースにオブジェクトを作成する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-115">To use this option, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="f2fe1-116">データ ソースにオブジェクトを作成する権限がない場合は、代わりに **[サーバーに時間テーブルを生成]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-116">If you do not have permission to create objects on the data source, try to use the **Generate a time table on the server** option instead.</span></span>  
  
 <span data-ttu-id="f2fe1-117">詳細については、「 [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)」(時間テーブルを生成して時間ディメンションを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-117">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="f2fe1-118">**[サーバーに時間テーブルを生成]**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-118">**Generate a time table on the server**</span></span>  
 <span data-ttu-id="f2fe1-119">サーバーに直接時間テーブルを作成し、そのテーブルを使用して時間ディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-119">Create a time table directly on the server and then use that table to create a time dimension.</span></span> <span data-ttu-id="f2fe1-120">基になるデータ ソースにオブジェクトを作成する権限がない場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-120">Use this option if you do not have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="f2fe1-121">新しい時間ディメンションには、ウィザードで指定した日付範囲、属性、およびカレンダーのデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-121">The new time dimension will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
 <span data-ttu-id="f2fe1-122">詳細については、「 [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)」(時間テーブルを生成して時間ディメンションを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-122">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="f2fe1-123">**[データ ソースに時間テーブル以外のテーブルを生成]**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-123">**Generate a non-time table in the data source**</span></span>  
 <span data-ttu-id="f2fe1-124">基になるリレーショナル データ ソースを使用せずにディメンションをデザインし、データ ソースに必要なスキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-124">Design the dimension without an underlying relational data source, and then generate the necessary schema for the data source.</span></span> <span data-ttu-id="f2fe1-125">この方法は、トップダウンのモデリングと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-125">This approach is known as top-down modeling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2fe1-126">このオプションを使用するには、基になるデータ ソースにオブジェクトを作成する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-126">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="f2fe1-127">テンプレートを使用するかどうかにかかわらず、ディメンションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-127">You can build the dimension with or without a template.</span></span> <span data-ttu-id="f2fe1-128">テンプレートを使用してディメンションを構築するには、 **[テンプレート]** の一覧からテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-128">To build the dimension with a template, select the template from the **Template** list.</span></span>  
  
 <span data-ttu-id="f2fe1-129">詳細については、「 [Create a Dimension by Generating a Non-Time Table in the Data Source](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)」(データ ソースに時間テーブル以外のテーブルを生成することによるディメンションの作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-129">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md).</span></span>  
  
 <span data-ttu-id="f2fe1-130">**テンプレート**</span><span class="sxs-lookup"><span data-stu-id="f2fe1-130">**Template**</span></span>  
 <span data-ttu-id="f2fe1-131">ディメンションの作成に使用するテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-131">Select the template that you want to use to create the dimension.</span></span> <span data-ttu-id="f2fe1-132">テンプレートは、特定のビジネス用途向けの属性および階層定義の完全なセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-132">Templates provide a complete set of attribute and hierarchy definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2fe1-133">このオプションは、 **[データ ソースに時間テーブル以外のテーブルを生成]** オプションが選択された場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2fe1-133">This option is only available when the **Generate a non-time table in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fe1-134">参照</span><span class="sxs-lookup"><span data-stu-id="f2fe1-134">See Also</span></span>  
 <span data-ttu-id="f2fe1-135">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f2fe1-135">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="f2fe1-136">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2fe1-136">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f2fe1-137">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="f2fe1-137">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
