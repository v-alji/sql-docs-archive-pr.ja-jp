---
title: '[エラーの構成] ([マイニング構造] ダイアログボックス) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5eb41da36400271a9b058ecf275d26bd22d3ee53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645889"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6ed8f-102">[エラーの構成] ([マイニング構造] ダイアログ ボックス) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="6ed8f-102">Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6ed8f-103">**SQL Server Management Studio** で **[マイニング構造のプロパティ]** ダイアログ ボックスの **[エラーの構成]** ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内のマイニング構造のエラー構成プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-103">Use the **Error Configuration** page of the **Mining Structure Properties** dialog box in **SQL Server Management Studio** to set the error configuration properties of a mining structure in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ed8f-104">Options</span><span class="sxs-lookup"><span data-stu-id="6ed8f-104">Options</span></span>  
 <span data-ttu-id="6ed8f-105">**既定のエラー構成を使用する**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-105">**Use default error configuration**</span></span>  
 <span data-ttu-id="6ed8f-106">処理操作でオブジェクトに対して既定のエラー構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-106">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-107">**[キー エラー アクション]**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-107">**Key error action**</span></span>  
 <span data-ttu-id="6ed8f-108">参照できない処理の間に新しいキーが検出されたとき、発生するアクションを次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-108">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="6ed8f-109">**[不明な種類に変換]** は、レコードの情報を不明なメンバーに集計します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-109">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="6ed8f-110">**[レコードの破棄]** は、レコードの情報をオブジェクトでの処理から除外します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-110">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="6ed8f-111">**エラー数を無視する**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-111">**Ignore errors count**</span></span>  
 <span data-ttu-id="6ed8f-112">処理中に発生するエラーは、すべて無視します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-112">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="6ed8f-113">**[エラー時に停止する]**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-113">**Stop on error**</span></span>  
 <span data-ttu-id="6ed8f-114">エラーが発生した場合、処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-114">Click to stop processing when errors occur.</span></span> <span data-ttu-id="6ed8f-115">このオプションによって、 **[エラー数]** オプションおよび **[エラー時のアクション]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-115">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="6ed8f-116">**エラーの数**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-116">**Number of errors**</span></span>  
 <span data-ttu-id="6ed8f-117">処理が停止される前に無視できるエラーの数を入力します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-117">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="6ed8f-118">**[エラー時のアクション]**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-118">**On error action**</span></span>  
 <span data-ttu-id="6ed8f-119">エラー数が **[エラー数]** の値を超えたときに行うアクションを次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-119">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="6ed8f-120">**[処理の停止]** は、処理中の操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-120">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="6ed8f-121">**[ログ記録の停止]** は、エラーのログ記録を停止しますが、処理中の操作は続行します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-121">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-122">**[見つからないキー]**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-122">**Key not found**</span></span>  
 <span data-ttu-id="6ed8f-123">オブジェクトの処理の際にキーが見つからなかった場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-123">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="6ed8f-124">**[エラーを無視する]** は、エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-124">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="6ed8f-125">**[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-125">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="6ed8f-126">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-126">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-127">**重複するキー**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-127">**Duplicate key**</span></span>  
 <span data-ttu-id="6ed8f-128">オブジェクトの処理の際に重複キーが見つかった場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-128">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="6ed8f-129">**[エラーを無視する]** は、エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-129">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="6ed8f-130">**[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-130">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="6ed8f-131">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-131">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-132">**Null キーが不明な値に変換されました**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-132">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="6ed8f-133">オブジェクトの処理の際に NULL メンバー キーが不明なメンバーに追加された場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-133">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed.</span></span>  
  
-   <span data-ttu-id="6ed8f-134">**[エラーを無視する]** は、エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-134">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="6ed8f-135">**[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-135">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="6ed8f-136">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-136">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-137">**Null キーは使用できません**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-137">**Null key not allowed**</span></span>  
 <span data-ttu-id="6ed8f-138">オブジェクトの処理の際に NULL キーが見つかったが許可されていない場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-138">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed.</span></span>  
  
-   <span data-ttu-id="6ed8f-139">**[エラーを無視する]** は、エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-139">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="6ed8f-140">**[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-140">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="6ed8f-141">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-141">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6ed8f-142">**[エラー ログのパス]**</span><span class="sxs-lookup"><span data-stu-id="6ed8f-142">**Error log path**</span></span>  
 <span data-ttu-id="6ed8f-143">エラー ログ ファイルの完全なパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="6ed8f-143">Type the full path and file name for the error log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed8f-144">参照</span><span class="sxs-lookup"><span data-stu-id="6ed8f-144">See Also</span></span>  
 <span data-ttu-id="6ed8f-145">[Analysis Services データマイニング&#41;&#40;マイニング構造のプロパティ] ダイアログボックス](mining-structure-properties-dialog-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6ed8f-145">[Mining Structure Properties Dialog &#40;Analysis Services - Data Mining&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6ed8f-146">[[全般 &#40;[マイニング構造] ダイアログボックス&#41; &#40;Analysis Services-データマイニング&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="6ed8f-146">[General &#40;Mining Structure Dialog Box&#41; &#40;Analysis Services - Data Mining&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)</span></span>  
  
  
