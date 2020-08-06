---
title: '[メジャーグループ] (キューブデザイナーの [パーティション] タブ) (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b73b77bd62c38881be20450f0b7506917014461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741469"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="853c9-102">[メジャー グループ] (キューブ デザイナーの [パーティション] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="853c9-102">Measure Groups (Partitions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="853c9-103">キューブ デザイナーの **[パーティション]** タブの **[メジャー グループ]** ペインを使用すると、キューブ内の各メジャー グループに関連付けられたパーティションを管理できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-103">Use the **Measure Groups** pane on the **Partitions** tab in Cube Designer to manage the partitions associated with each measure group in the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="853c9-104">Options</span><span class="sxs-lookup"><span data-stu-id="853c9-104">Options</span></span>  
 <span data-ttu-id="853c9-105">**パーティション**</span><span class="sxs-lookup"><span data-stu-id="853c9-105">**Partitions**</span></span>  
 <span data-ttu-id="853c9-106">選択されたメジャー グループをサポートするパーティションの一覧が示されたグリッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="853c9-106">Displays a grid containing the list of partitions that support the selected measure group.</span></span> <span data-ttu-id="853c9-107">このグリッドには次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="853c9-107">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="853c9-108">**数値**</span><span class="sxs-lookup"><span data-stu-id="853c9-108">**(Ordinal)**</span></span>  
 <span data-ttu-id="853c9-109">メジャー グループ内のパーティションの序数の位置を表示します。</span><span class="sxs-lookup"><span data-stu-id="853c9-109">Displays the ordinal position of the partition within the measure group.</span></span>  
  
 <span data-ttu-id="853c9-110">クリックすると、パーティションの行全体が選択されます。</span><span class="sxs-lookup"><span data-stu-id="853c9-110">Click to select the entire row for the partition.</span></span>  
  
 <span data-ttu-id="853c9-111">**[パーティション名]**</span><span class="sxs-lookup"><span data-stu-id="853c9-111">**Partition Name**</span></span>  
 <span data-ttu-id="853c9-112">選択したパーティションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="853c9-112">Type the name of the selected partition.</span></span>  
  
 <span data-ttu-id="853c9-113">**ソース**</span><span class="sxs-lookup"><span data-stu-id="853c9-113">**Source**</span></span>  
 <span data-ttu-id="853c9-114">選択したパーティションのファクト テーブル データを提供するテーブル名 (テーブル バインドの場合) またはクエリ (クエリ バインドの場合) を入力します。</span><span class="sxs-lookup"><span data-stu-id="853c9-114">Type the table name (for table binding) or query (for query binding) that provides the fact table data for the selected partition.</span></span>  
  
 <span data-ttu-id="853c9-115">**[...]** ボタンをクリックすると、 **[パーティション ソース]** ダイアログ ボックスが表示され、選択したパーティションのソースを定義できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-115">Click the **...** button to display the **Partition Source** dialog box and define the source for the selected partition.</span></span>  
  
 <span data-ttu-id="853c9-116">**集計**</span><span class="sxs-lookup"><span data-stu-id="853c9-116">**Aggregation**</span></span>  
 <span data-ttu-id="853c9-117">パーティションの集計モードおよびストレージ モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="853c9-117">Displays the aggregation mode and the storage mode of the partition.</span></span> <span data-ttu-id="853c9-118">最初にストレージ モードが表示されます。ストレージ モードは、リレーショナル オンライン分析処理 (ROLAP)、多次元オンライン分析処理 (MOLAP)、またはハイブリッド オンライン分析処理 (HOLAP) です。</span><span class="sxs-lookup"><span data-stu-id="853c9-118">The storage mode is displayed first: relational online analytical processing (ROLAP), multidimensional online analytical processing (MOLAP), or hybrid online analytical processing (HOLAP).</span></span> <span data-ttu-id="853c9-119">集計モードは、要求された最適化の比率として、要求または使用された領域のメジャーとして、または作成された集計の数として表示されます。</span><span class="sxs-lookup"><span data-stu-id="853c9-119">The aggregation mode is displayed as a percentage of optimization requested, as a measure of space requested or used, or as the number of aggregations created.</span></span> <span data-ttu-id="853c9-120">**[...]** ボタンをクリックすると、 **集計のデザイン ウィザード** が表示され、指定したパーティションの集計のデザインを定義できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-120">Click the **...** button to display the **Aggregation Design Wizard** and define the aggregation design for the specified partition.</span></span>  
  
 <span data-ttu-id="853c9-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="853c9-121">**Description**</span></span>  
 <span data-ttu-id="853c9-122">パーティションの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="853c9-122">Type the optional description of the partition.</span></span>  
  
 <span data-ttu-id="853c9-123">**[新しいパーティション]**</span><span class="sxs-lookup"><span data-stu-id="853c9-123">**New Partition...**</span></span>  
 <span data-ttu-id="853c9-124">クリックすると、 **パーティション ウィザード** が表示され、選択したメジャー グループ内に新しいパーティションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-124">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>  
  
 <span data-ttu-id="853c9-125">**ストレージの設定...**</span><span class="sxs-lookup"><span data-stu-id="853c9-125">**Storage settings...**</span></span>  
 <span data-ttu-id="853c9-126">クリックすると、 **[ストレージ設定]** ダイアログ ボックスが表示され、選択したパーティションのストレージ モード、プロアクティブ キャッシュ、および通知の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-126">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="853c9-127">このオプションは、選択したメジャー グループの **[パーティション]** グリッドでパーティションのセルが選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-127">This option is enabled only if any cell of a partition is selected in the **Partitions** grid of the selected measure group.</span></span>  
  
 <span data-ttu-id="853c9-128">**[書き戻しの設定]**</span><span class="sxs-lookup"><span data-stu-id="853c9-128">**Writeback settings...**</span></span>  
 <span data-ttu-id="853c9-129">クリックすると、 **[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスが表示され、選択したメジャー グループの書き戻し設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-129">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the selected measure group.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="853c9-130">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="853c9-130">Context Menu</span></span>  
 <span data-ttu-id="853c9-131">選択したメジャー グループの **[パーティション]** グリッドの行を右クリックすると、コンテキスト メニューが表示され、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-131">The following options are available in the context menu displayed by right-clicking a row in the **Partitions** grid of a selected measure group:</span></span>  
  
|<span data-ttu-id="853c9-132">オプション</span><span class="sxs-lookup"><span data-stu-id="853c9-132">Option</span></span>|<span data-ttu-id="853c9-133">定義</span><span class="sxs-lookup"><span data-stu-id="853c9-133">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="853c9-134">**[ビジネス インテリジェンスの追加]**</span><span class="sxs-lookup"><span data-stu-id="853c9-134">**Add Business Intelligence**</span></span>|<span data-ttu-id="853c9-135">クリックすると、 **ビジネス インテリジェンス ウィザード** が表示され、ビジネス インテリジェンス機能をキューブに追加できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-135">Click to display the **Business Intelligence Wizard** and add business intelligence features to the cube.</span></span> <span data-ttu-id="853c9-136">**ビジネス インテリジェンス ウィザード**の詳細については、「 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="853c9-136">For more information about the **Business Intelligence Wizard**, see [Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="853c9-137">**新しいパーティション**</span><span class="sxs-lookup"><span data-stu-id="853c9-137">**New Partition**</span></span>|<span data-ttu-id="853c9-138">クリックすると、 **パーティション ウィザード** が表示され、選択したメジャー グループ内に新しいパーティションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-138">Click to display the **Partition Wizard** and create a new partition in the selected measure group.</span></span>|  
|<span data-ttu-id="853c9-139">**[パーティション名の変更]**</span><span class="sxs-lookup"><span data-stu-id="853c9-139">**Rename Partition**</span></span>|<span data-ttu-id="853c9-140">選択したパーティションの名前を変更する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="853c9-140">Select to rename the selected partition.</span></span>|  
|<span data-ttu-id="853c9-141">**削除**</span><span class="sxs-lookup"><span data-stu-id="853c9-141">**Delete**</span></span>|<span data-ttu-id="853c9-142">クリックすると、 **[オブジェクトの削除]** ダイアログ ボックスが表示され、選択したアクションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-142">Click to display the **Delete Objects** dialog box and delete the selected action.</span></span><br /><br /> <span data-ttu-id="853c9-143">注: このオプションは、書き戻しパーティションが選択されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-143">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="853c9-144">**[集計のデザイン]**</span><span class="sxs-lookup"><span data-stu-id="853c9-144">**Design Aggregations**</span></span>|<span data-ttu-id="853c9-145">クリックすると、 **集計のデザイン ウィザード** が表示され、選択したパーティションの集計デザインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-145">Click to display the **Aggregation Design Wizard** and create an aggregation design for the selected partition.</span></span><br /><br /> <span data-ttu-id="853c9-146">注: このオプションは、書き戻しパーティションが選択されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-146">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="853c9-147">**ストレージの設定**</span><span class="sxs-lookup"><span data-stu-id="853c9-147">**Storage Settings**</span></span>|<span data-ttu-id="853c9-148">クリックすると、 **[ストレージ設定]** ダイアログ ボックスが表示され、選択したパーティションのストレージ モード、プロアクティブ キャッシュ、および通知の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-148">Click to display the **Storage Settings** dialog box and specify storage mode, proactive caching, and notification settings for the selected partition.</span></span>|  
|<span data-ttu-id="853c9-149">**書き戻しの設定**</span><span class="sxs-lookup"><span data-stu-id="853c9-149">**Writeback Settings**</span></span>|<span data-ttu-id="853c9-150">クリックすると、 **[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスが表示され、選択したパーティションを含むメジャー グループの書き戻し設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-150">Click to display the **Enable/Disable Writeback** dialog box and specify writeback settings for the measure group containing the selected partition.</span></span>|  
|<span data-ttu-id="853c9-151">**[使用法に基づく最適化]**</span><span class="sxs-lookup"><span data-stu-id="853c9-151">**Usage Based Optimization**</span></span>|<span data-ttu-id="853c9-152">クリックすると、 **使用法に基づく最適化ウィザード** が表示され、選択したパーティションの既存の使用パターンに基づいた集計デザインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-152">Click to display the **Usage-Based Optimization Wizard** and create an aggregation design based on existing usage patterns for the selected partition.</span></span><br /><br /> <span data-ttu-id="853c9-153">注: このオプションは、書き戻しパーティションが選択されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-153">Note: This option is disabled if a writeback partition is selected.</span></span>|  
|<span data-ttu-id="853c9-154">**処理**</span><span class="sxs-lookup"><span data-stu-id="853c9-154">**Process**</span></span>|<span data-ttu-id="853c9-155">クリックすると、 **[処理]** ダイアログ ボックスが表示され、選択したパーティションを処理できます。</span><span class="sxs-lookup"><span data-stu-id="853c9-155">Click to display the **Process** dialog box and process the selected partition.</span></span>|  
|<span data-ttu-id="853c9-156">**コピー**</span><span class="sxs-lookup"><span data-stu-id="853c9-156">**Copy**</span></span>|<span data-ttu-id="853c9-157">このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-157">This option is disabled.</span></span>|  
|<span data-ttu-id="853c9-158">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="853c9-158">**Paste**</span></span>|<span data-ttu-id="853c9-159">このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="853c9-159">This option is disabled.</span></span>|  
|<span data-ttu-id="853c9-160">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="853c9-160">**Properties**</span></span>|<span data-ttu-id="853c9-161">**で選択したパーティションの** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウを表示する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="853c9-161">Select to display the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected partition.</span></span>|  
  
  
