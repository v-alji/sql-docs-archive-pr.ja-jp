---
title: Analysis Services 処理タスクエディター (Analysis Services] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aabcfe286b40f58b429227654107d58e8a4ee837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633981"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a><span data-ttu-id="57744-102">[Analysis Services 処理タスク エディター] ([Analysis Services] ページ)</span><span class="sxs-lookup"><span data-stu-id="57744-102">Analysis Services Processing Task Editor (Analysis Services Page)</span></span>
  <span data-ttu-id="57744-103">**[Analysis Services 処理タスク エディター]** ダイアログ ボックスの **[Analysis Services]** ページを使用すると、Analysis Services 接続マネージャーの指定、処理する分析オブジェクトの選択、処理およびエラー処理オプションの設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="57744-103">Use the **Analysis Services** page of the **Analysis Services Processing Task Editor** dialog box to specify an Analysis Services connection manager, select the analytic objects to process, and set processing and error handling options.</span></span>  
  
 <span data-ttu-id="57744-104">テーブル モデルを処理する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57744-104">When processing tabular models, keep the following in mind:</span></span>  
  
1.  <span data-ttu-id="57744-105">テーブル モデルでは影響分析を実行できません。</span><span class="sxs-lookup"><span data-stu-id="57744-105">You cannot perform impact analysis on tabular models.</span></span>  
  
2.  <span data-ttu-id="57744-106">テーブル モード用のいくつかの処理オプションが表示されません ([デフラグの処理] や [再計算の処理] など)。</span><span class="sxs-lookup"><span data-stu-id="57744-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="57744-107">これらの機能は DDL 実行タスクを使用すると実行できます。</span><span class="sxs-lookup"><span data-stu-id="57744-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
3.  <span data-ttu-id="57744-108">提供されているいくつかの処理オプション ([インデックスの処理] など) はテーブル モデルには適していないので、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="57744-108">Some processing options provided, such as process indexes, are not appropriate for tabular models and should not be used.</span></span>  
  
4.  <span data-ttu-id="57744-109">テーブル モデルでは、バッチ設定が無視されます。</span><span class="sxs-lookup"><span data-stu-id="57744-109">Batch settings are ignored for tabular models.</span></span>  
  
 <span data-ttu-id="57744-110">このタスクの詳細については、「 [Analysis Services 処理タスク](control-flow/analysis-services-processing-task.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="57744-110">To learn about this task, see [Analysis Services Processing Task](control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="57744-111">Options</span><span class="sxs-lookup"><span data-stu-id="57744-111">Options</span></span>  
 <span data-ttu-id="57744-112">**Analysis Services 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="57744-112">**Analysis Services connection manager**</span></span>  
 <span data-ttu-id="57744-113">既存の Analysis Services 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="57744-113">Select an existing Analysis Services connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="57744-114">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="57744-114">**New**</span></span>  
 <span data-ttu-id="57744-115">新しい Analysis Services 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="57744-115">Create a new Analysis Services connection manager.</span></span>  
  
 <span data-ttu-id="57744-116">**関連トピック:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)、 [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="57744-116">**Related Topics:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="57744-117">**オブジェクトの一覧**</span><span class="sxs-lookup"><span data-stu-id="57744-117">**Object list**</span></span>  
 |<span data-ttu-id="57744-118">プロパティ</span><span class="sxs-lookup"><span data-stu-id="57744-118">Property</span></span>|<span data-ttu-id="57744-119">説明</span><span class="sxs-lookup"><span data-stu-id="57744-119">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="57744-120">**[オブジェクト名]**</span><span class="sxs-lookup"><span data-stu-id="57744-120">**Object Name**</span></span>|<span data-ttu-id="57744-121">指定されたオブジェクト名を表示します。</span><span class="sxs-lookup"><span data-stu-id="57744-121">Lists the specified object names.</span></span>|  
|<span data-ttu-id="57744-122">**Type**</span><span class="sxs-lookup"><span data-stu-id="57744-122">**Type**</span></span>|<span data-ttu-id="57744-123">指定されたオブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="57744-123">Lists the types of the specified objects.</span></span>|  
|<span data-ttu-id="57744-124">**[処理オプション]**</span><span class="sxs-lookup"><span data-stu-id="57744-124">**Process Options**</span></span>|<span data-ttu-id="57744-125">一覧から処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="57744-125">Select a processing option in the list.</span></span><br /><br /> <span data-ttu-id="57744-126">**関連トピック**:[多次元モデルオブジェクトの処理](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span><span class="sxs-lookup"><span data-stu-id="57744-126">**Related Topics**: [Multidimensional Model Object Processing](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services)</span></span>|  
|<span data-ttu-id="57744-127">**設定**</span><span class="sxs-lookup"><span data-stu-id="57744-127">**Settings**</span></span>|<span data-ttu-id="57744-128">指定されたオブジェクトの処理設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="57744-128">Lists processing settings for the specified objects.</span></span>|  
  
 <span data-ttu-id="57744-129">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="57744-129">**Add**</span></span>  
 <span data-ttu-id="57744-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="57744-130">Add an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object to the list.</span></span>  
  
 <span data-ttu-id="57744-131">**削除**</span><span class="sxs-lookup"><span data-stu-id="57744-131">**Remove**</span></span>  
 <span data-ttu-id="57744-132">オブジェクトを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57744-132">Select an object, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="57744-133">**[影響分析]**</span><span class="sxs-lookup"><span data-stu-id="57744-133">**Impact Analysis**</span></span>  
 <span data-ttu-id="57744-134">選択したオブジェクトに対して影響分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="57744-134">Perform impact analysis on the selected object.</span></span>  
  
 <span data-ttu-id="57744-135">**関連トピック:** [[影響分析] ダイアログ ボックス (Analysis Services - 多次元データ)](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="57744-135">**Related Topics:** [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
 <span data-ttu-id="57744-136">**[バッチ設定の概要]**</span><span class="sxs-lookup"><span data-stu-id="57744-136">**Batch Settings Summary**</span></span>  
 |<span data-ttu-id="57744-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="57744-137">Property</span></span>|<span data-ttu-id="57744-138">説明</span><span class="sxs-lookup"><span data-stu-id="57744-138">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="57744-139">**処理順序**</span><span class="sxs-lookup"><span data-stu-id="57744-139">**Processing order**</span></span>|<span data-ttu-id="57744-140">オブジェクトを順番に処理するか、一括して処理するかを指定します。並行処理を行う場合は、同時に処理するオブジェクトの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="57744-140">Specifies whether objects are processed sequentially or in a batch; if parallel processing is used, specifies the number of objects to process concurrently.</span></span>|  
|<span data-ttu-id="57744-141">**[トランザクション モード]**</span><span class="sxs-lookup"><span data-stu-id="57744-141">**Transaction mode**</span></span>|<span data-ttu-id="57744-142">順次処理のトランザクション モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="57744-142">Specifies the transaction mode for sequential processing.</span></span>|  
|<span data-ttu-id="57744-143">**[ディメンション エラー]**</span><span class="sxs-lookup"><span data-stu-id="57744-143">**Dimension errors**</span></span>|<span data-ttu-id="57744-144">エラーが発生したときのタスクの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="57744-144">Specifies the task behavior when errors occur.</span></span>|  
|<span data-ttu-id="57744-145">**[ディメンション キーのエラー ログのパス]**</span><span class="sxs-lookup"><span data-stu-id="57744-145">**Dimension key error log path**</span></span>|<span data-ttu-id="57744-146">エラーを記録するファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="57744-146">Specifies the path of the file to which errors are logged.</span></span>|  
|<span data-ttu-id="57744-147">**影響を受けるオブジェクトの処理**</span><span class="sxs-lookup"><span data-stu-id="57744-147">**Process affected objects**</span></span>|<span data-ttu-id="57744-148">依存オブジェクトまたは影響を受けたオブジェクトも処理するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="57744-148">Indicates whether dependent or affected objects are also processed.</span></span>|  
  
 <span data-ttu-id="57744-149">**設定の変更**</span><span class="sxs-lookup"><span data-stu-id="57744-149">**Change Settings**</span></span>  
 <span data-ttu-id="57744-150">処理オプションおよびディメンション キー内のエラー処理を変更します。</span><span class="sxs-lookup"><span data-stu-id="57744-150">Change the processing options and the handling of errors in dimension keys.</span></span>  
  
 <span data-ttu-id="57744-151">**関連トピック:** [[設定の変更] ダイアログ ボックス (Analysis Services - 多次元データ)](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="57744-151">**Related Topics:** [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57744-152">参照</span><span class="sxs-lookup"><span data-stu-id="57744-152">See Also</span></span>  
 <span data-ttu-id="57744-153">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="57744-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="57744-154">[Analysis Services 処理タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="57744-154">[Analysis Services Processing Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="57744-155">Analysis Services DDL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="57744-155">Analysis Services Execute DDL Task</span></span>](control-flow/analysis-services-execute-ddl-task.md)  
  
  
