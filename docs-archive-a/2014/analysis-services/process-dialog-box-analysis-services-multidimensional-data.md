---
title: '[処理] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 369c121713894bba9b2ce6c40aa2869de49eaa72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741361"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="908bd-102">[処理] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="908bd-102">Process Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="908bd-103">**と** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [処理] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを処理できます。</span><span class="sxs-lookup"><span data-stu-id="908bd-103">Use the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to process [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="908bd-104">**で** [処理] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="908bd-104">You can display the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="908bd-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ソリューション エクスプローラー **で** プロジェクト、キューブ、ディメンション、またはマイニング構造を右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="908bd-105">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, cube, dimension, or mining structure in **Solution Explorer** and selecting **Process**.</span></span>  
  
-   <span data-ttu-id="908bd-106">**キューブ デザイナー** の各ページ、 **ディメンション デザイナー**の各ページ、または **マイニング モデル デザイナー**の **[マイニング構造]** ページおよび **[マイニング モデル]** ページでツール バーの **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="908bd-106">Selecting **Process** from the toolbar on every page of **Cube Designer**, every page of **Dimension Designer**, or the **Mining Structure** and **Mining Models** pages of **Data Mining Model Designer**.</span></span>  
  
-   <span data-ttu-id="908bd-107">**マイニング モデル デザイナー** の **[マイニング モデル]** ページでマイニング モデルを右クリックし、 **[マイニング構造および全モデルの処理]** または **[モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="908bd-107">Right-clicking a mining model in the **Mining Models** page of **Data Mining Model Designer** and selecting **Process Mining Structure and All Models** or **Process Model**.</span></span>  
  
 <span data-ttu-id="908bd-108">**SQL Server Management Studio** で **[処理]** ダイアログ ボックスを表示するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="908bd-108">You can display the **Process** dialog box in **SQL Server Management Studio** by:</span></span>  
  
-   <span data-ttu-id="908bd-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクト エクスプローラー **で** データベース、キューブ、メジャー グループ、パーティション、ディメンション、マイニング構造、またはマイニング モデルを右クリックし、 **[処理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="908bd-109">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, cube, measure group, partition, dimension, mining structure, or mining model in **Object Explorer** and selecting **Process**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="908bd-110">Options</span><span class="sxs-lookup"><span data-stu-id="908bd-110">Options</span></span>  
 <span data-ttu-id="908bd-111">**オブジェクトの一覧**</span><span class="sxs-lookup"><span data-stu-id="908bd-111">**Object list**</span></span>  
 <span data-ttu-id="908bd-112">処理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクト、および適用する処理オプションと設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="908bd-112">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects to be processed and the processing options and settings to be applied.</span></span> <span data-ttu-id="908bd-113">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="908bd-113">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="908bd-114">**[オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="908bd-114">**Object Name**</span></span>  
 <span data-ttu-id="908bd-115">処理するオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="908bd-115">Displays the name of the object to be processed.</span></span> <span data-ttu-id="908bd-116">名前の左にあるアイコンはオブジェクトの種類を示しています。</span><span class="sxs-lookup"><span data-stu-id="908bd-116">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="908bd-117">**Type**</span><span class="sxs-lookup"><span data-stu-id="908bd-117">**Type**</span></span>  
 <span data-ttu-id="908bd-118">処理するオブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="908bd-118">Displays the type of the object to be processed.</span></span>  
  
 <span data-ttu-id="908bd-119">**[処理オプション]**</span><span class="sxs-lookup"><span data-stu-id="908bd-119">**Process Options**</span></span>  
 <span data-ttu-id="908bd-120">選択されたオブジェクトに対して実行する処理の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="908bd-120">Select the type of processing to perform on the selected object.</span></span> <span data-ttu-id="908bd-121">使用可能な処理オプションの詳細については、「[多次元モデルオブジェクトの処理](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="908bd-121">For more information about available processing options, see [Multidimensional Model Object Processing](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
 <span data-ttu-id="908bd-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="908bd-122">**Settings**</span></span>  
 <span data-ttu-id="908bd-123">キューブ、メジャー グループ、またはパーティションの **[処理オプション]** で **[増分処理]** を選択するときに、 **[構成]** ハイパーリンクを表示します。</span><span class="sxs-lookup"><span data-stu-id="908bd-123">Displays the **Configure** hyperlink when you choose **Process Incremental** in **Process Options** for cubes, measure groups, or partitions.</span></span> <span data-ttu-id="908bd-124">**[構成]** をクリックし、 **[増分更新]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="908bd-124">Click **Configure** to launch the **Incremental Update** dialog box.</span></span> <span data-ttu-id="908bd-125">**[増分更新]** ダイアログ ボックスの詳細については、[「[増分更新] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="908bd-125">For more information about the **Incremental Update** dialog box, see [Incremental Update Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="908bd-126">**削除**</span><span class="sxs-lookup"><span data-stu-id="908bd-126">**Remove**</span></span>  
 <span data-ttu-id="908bd-127">**[オブジェクト一覧]** から選択された項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="908bd-127">Click to remove the selected items from **Object list**.</span></span>  
  
 <span data-ttu-id="908bd-128">**[影響分析]**</span><span class="sxs-lookup"><span data-stu-id="908bd-128">**Impact Analysis**</span></span>  
 <span data-ttu-id="908bd-129">**[影響分析]** ダイアログ ボックスを開き、処理タスクによって影響を受けるオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="908bd-129">Click to open the **Impact Analysis** dialog box and display the objects that will be affected by the processing task.</span></span> <span data-ttu-id="908bd-130">**[影響分析]** ダイアログ ボックスの詳細については、「[[影響分析] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="908bd-130">For more information about the **Impact Analysis** dialog box, see [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="908bd-131">**[設定の変更]** ダイアログ ボックスで **[影響を受けたオブジェクトを処理する]** オプションがオンの場合は、このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="908bd-131">This option is disabled when the **Process affected objects** option is selected in the **Change Settings** dialog box.</span></span>  
  
 <span data-ttu-id="908bd-132">**設定の変更**</span><span class="sxs-lookup"><span data-stu-id="908bd-132">**Change Settings**</span></span>  
 <span data-ttu-id="908bd-133">**[設定の変更]** ダイアログ ボックスを表示し、バッチ処理設定、書き戻し設定、およびディメンション キー エラー設定を含め、選択されたオブジェクトの処理を制御する設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="908bd-133">Click to open the **Change Settings** dialog box and change the settings that govern processing of the selected objects, including batch processing settings, writeback settings, and dimension key error settings.</span></span> <span data-ttu-id="908bd-134">**[設定の変更]** ダイアログ ボックスの詳細については、「[[設定の変更] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="908bd-134">For more information about the **Change Settings** dialog box, see [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="908bd-135">**実行**</span><span class="sxs-lookup"><span data-stu-id="908bd-135">**Run**</span></span>  
 <span data-ttu-id="908bd-136">オブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="908bd-136">Click to process the objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908bd-137">参照</span><span class="sxs-lookup"><span data-stu-id="908bd-137">See Also</span></span>  
 <span data-ttu-id="908bd-138">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="908bd-138">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="908bd-139">[[処理の進行状況] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="908bd-139">[Process Progress Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
