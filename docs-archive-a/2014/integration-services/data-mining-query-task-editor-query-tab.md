---
title: データマイニングクエリタスクエディター ([クエリ] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.query.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 72b1755d-d226-46c5-b862-0c9333196a10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6005c92d0d48850461c01353ddf94c61140d0f2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738520"
---
# <a name="data-mining-query-task-editor-query-tab"></a><span data-ttu-id="dda41-102">[データ マイニング クエリ タスク エディター] ([クエリ] タブ)</span><span class="sxs-lookup"><span data-stu-id="dda41-102">Data Mining Query Task Editor (Query Tab)</span></span>
  <span data-ttu-id="dda41-103">**[データ マイニング クエリ タスク]** ダイアログ ボックスの **[クエリ]** タブを使用すると、マイニング モデルに基づいて予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dda41-103">Use the **Query** tab of the **Data Mining Query Task** dialog box to create prediction queries based on a mining model.</span></span> <span data-ttu-id="dda41-104">このダイアログ ボックスでは、パラメーターおよび結果セットを変数にバインドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="dda41-104">In this dialog box you can also bind parameters and result sets to variables.</span></span>  
  
 <span data-ttu-id="dda41-105">パッケージでのデータ マイニングの実装の詳細については、「 [データ マイニング クエリ タスク](control-flow/data-mining-query-task.md) 」および「 [データ マイニング ソリューション](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dda41-105">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="dda41-106">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="dda41-106">General Options</span></span>  
 <span data-ttu-id="dda41-107">**名前**</span><span class="sxs-lookup"><span data-stu-id="dda41-107">**Name**</span></span>  
 <span data-ttu-id="dda41-108">データ マイニング クエリ タスクに固有の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dda41-108">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="dda41-109">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dda41-109">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dda41-110">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dda41-110">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="dda41-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="dda41-111">**Description**</span></span>  
 <span data-ttu-id="dda41-112">データ マイニング クエリ タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="dda41-112">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="build-query-tab-options"></a><span data-ttu-id="dda41-113">[クエリの作成] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="dda41-113">Build Query Tab Options</span></span>  
 <span data-ttu-id="dda41-114">**データマイニングクエリ**</span><span class="sxs-lookup"><span data-stu-id="dda41-114">**Data mining query**</span></span>  
 <span data-ttu-id="dda41-115">データ マイニング クエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="dda41-115">Type a data mining query.</span></span>  
  
 <span data-ttu-id="dda41-116">**関連項目:**  [データ マイニング拡張機能 (DMX) リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)</span><span class="sxs-lookup"><span data-stu-id="dda41-116">**Related Topics:**  [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference)</span></span>  
  
 <span data-ttu-id="dda41-117">**[新しいクエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="dda41-117">**Build New Query**</span></span>  
 <span data-ttu-id="dda41-118">グラフィカル ツールを使用してデータ マイニング クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dda41-118">Create the data mining query using a graphical tool.</span></span>  
  
 <span data-ttu-id="dda41-119">**関連項目:** [Data Mining Query](control-flow/data-mining-query.md)</span><span class="sxs-lookup"><span data-stu-id="dda41-119">**Related Topics:** [Data Mining Query](control-flow/data-mining-query.md)</span></span>  
  
## <a name="parameter-mapping-tab-options"></a><span data-ttu-id="dda41-120">[パラメーター マッピング] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="dda41-120">Parameter Mapping Tab Options</span></span>  
 <span data-ttu-id="dda41-121">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="dda41-121">**Parameter Name**</span></span>  
 <span data-ttu-id="dda41-122">オプションで、パラメーター名を更新します。</span><span class="sxs-lookup"><span data-stu-id="dda41-122">Optionally, update the parameter name.</span></span> <span data-ttu-id="dda41-123">**[変数名]** 一覧から変数を選択して、パラメーターを変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="dda41-123">Map the parameter to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="dda41-124">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="dda41-124">**Variable Name**</span></span>  
 <span data-ttu-id="dda41-125">パラメーターにマップする変数を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="dda41-125">Select a variable in the list to map it to the parameter.</span></span>  
  
 <span data-ttu-id="dda41-126">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="dda41-126">**Add**</span></span>  
 <span data-ttu-id="dda41-127">一覧にパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="dda41-127">Add to a parameter to the list.</span></span>  
  
 <span data-ttu-id="dda41-128">**削除**</span><span class="sxs-lookup"><span data-stu-id="dda41-128">**Remove**</span></span>  
 <span data-ttu-id="dda41-129">パラメーターを選択してから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dda41-129">Select a parameter, and then click **Remove**.</span></span>  
  
## <a name="result-set-tab-options"></a><span data-ttu-id="dda41-130">[結果セット] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="dda41-130">Result Set Tab Options</span></span>  
 <span data-ttu-id="dda41-131">**[結果名]**</span><span class="sxs-lookup"><span data-stu-id="dda41-131">**Result Name**</span></span>  
 <span data-ttu-id="dda41-132">オプションで、結果セット名を更新します。</span><span class="sxs-lookup"><span data-stu-id="dda41-132">Optionally, update the result set name.</span></span> <span data-ttu-id="dda41-133">**[変数名]** 一覧から変数を選択して、結果を変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="dda41-133">Map the result to a variable by selecting a variable in the **Variable Name** list.</span></span>  
  
 <span data-ttu-id="dda41-134">**[追加]** をクリックして結果を追加したら、結果の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dda41-134">After you have added a result by clicking **Add**, provide a unique name for the result.</span></span>  
  
 <span data-ttu-id="dda41-135">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="dda41-135">**Variable Name**</span></span>  
 <span data-ttu-id="dda41-136">結果セットにマップする変数を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="dda41-136">Select a variable in the list to map it to the result set.</span></span>  
  
 <span data-ttu-id="dda41-137">**結果の種類**</span><span class="sxs-lookup"><span data-stu-id="dda41-137">**Result Type**</span></span>  
 <span data-ttu-id="dda41-138">1 行だけを返すか、完全な結果セットを返すかを示します。</span><span class="sxs-lookup"><span data-stu-id="dda41-138">Indicate whether to return a single row or a full result set.</span></span>  
  
 <span data-ttu-id="dda41-139">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="dda41-139">**Add**</span></span>  
 <span data-ttu-id="dda41-140">一覧に結果セットを追加します。</span><span class="sxs-lookup"><span data-stu-id="dda41-140">Add a result set to the list.</span></span>  
  
 <span data-ttu-id="dda41-141">**削除**</span><span class="sxs-lookup"><span data-stu-id="dda41-141">**Remove**</span></span>  
 <span data-ttu-id="dda41-142">結果を選択してから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dda41-142">Select a result, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda41-143">参照</span><span class="sxs-lookup"><span data-stu-id="dda41-143">See Also</span></span>  
 <span data-ttu-id="dda41-144">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dda41-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dda41-145">[データマイニングクエリタスクエディター &#40;[マイニングモデル] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="dda41-145">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="dda41-146">[[データマイニングクエリタスクエディター] &#40;[出力] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="dda41-146">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="dda41-147">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="dda41-147">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
