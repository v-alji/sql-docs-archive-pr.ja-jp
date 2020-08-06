---
title: ディメンション処理変換先エディター ([詳細設定] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5be80cbbfb6871594d7481ccc0f9444d014885e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644564"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a><span data-ttu-id="051e9-102">[ディメンション処理変換先エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="051e9-102">Dimension Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="051e9-103">**[ディメンション処理変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理を構成できます。</span><span class="sxs-lookup"><span data-stu-id="051e9-103">Use the **Advanced** page of the **Dimension Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="051e9-104">ディメンション処理変換先の詳細については、「 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="051e9-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="051e9-105">Options</span><span class="sxs-lookup"><span data-stu-id="051e9-105">Options</span></span>  
 <span data-ttu-id="051e9-106">**[既定のエラー構成を使用する]**</span><span class="sxs-lookup"><span data-stu-id="051e9-106">**Use default error configuration.**</span></span>  
 <span data-ttu-id="051e9-107">既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エラー処理を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-107">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="051e9-108">この値の既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="051e9-108">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="051e9-109">**[キー エラー アクション]**</span><span class="sxs-lookup"><span data-stu-id="051e9-109">**Key error action**</span></span>  
 <span data-ttu-id="051e9-110">許容されないキー値を持つレコードを処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-110">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="051e9-111">値</span><span class="sxs-lookup"><span data-stu-id="051e9-111">Value</span></span>|<span data-ttu-id="051e9-112">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-113">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="051e9-113">**ConvertToUnknown**</span></span>|<span data-ttu-id="051e9-114">許容できないキー値を `UnknownMember` 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="051e9-114">Convert the unacceptable key value to the `UnknownMember` value.</span></span>|  
|<span data-ttu-id="051e9-115">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="051e9-115">**DiscardRecord**</span></span>|<span data-ttu-id="051e9-116">レコードを破棄します。</span><span class="sxs-lookup"><span data-stu-id="051e9-116">Discard the record.</span></span>|  
  
 <span data-ttu-id="051e9-117">**[エラーを無視する]**</span><span class="sxs-lookup"><span data-stu-id="051e9-117">**Ignore errors**</span></span>  
 <span data-ttu-id="051e9-118">エラーを無視することを指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-118">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="051e9-119">**[エラー時に停止する]**</span><span class="sxs-lookup"><span data-stu-id="051e9-119">**Stop on error**</span></span>  
 <span data-ttu-id="051e9-120">エラーが発生した場合に処理を停止することを指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-120">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="051e9-121">**エラーの数**</span><span class="sxs-lookup"><span data-stu-id="051e9-121">**Number of errors**</span></span>  
 <span data-ttu-id="051e9-122">**[エラー時に停止する]** を選択した場合は、処理を停止するエラーのしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-122">Specify the error threshold at which processing should stop, if you have selected **Stop on errors**.</span></span>  
  
 <span data-ttu-id="051e9-123">**[エラー時のアクション]**</span><span class="sxs-lookup"><span data-stu-id="051e9-123">**On error action**</span></span>  
 <span data-ttu-id="051e9-124">**[エラー時に停止する]** を選択した場合は、エラーのしきい値に達した場合に実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-124">Specify the action to take when the error threshold is reached, if you have selected **Stop on errors**.</span></span>  
  
|<span data-ttu-id="051e9-125">値</span><span class="sxs-lookup"><span data-stu-id="051e9-125">Value</span></span>|<span data-ttu-id="051e9-126">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-127">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="051e9-127">**StopProcessing**</span></span>|<span data-ttu-id="051e9-128">処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-128">Stop processing.</span></span>|  
|<span data-ttu-id="051e9-129">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="051e9-129">**StopLogging**</span></span>|<span data-ttu-id="051e9-130">ログ記録エラーを停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-130">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="051e9-131">**[見つからないキー]**</span><span class="sxs-lookup"><span data-stu-id="051e9-131">**Key not found**</span></span>  
 <span data-ttu-id="051e9-132">見つからないキーのエラーに対する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-132">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="051e9-133">既定では、この値は **[ReportAndContinue]** です。</span><span class="sxs-lookup"><span data-stu-id="051e9-133">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="051e9-134">値</span><span class="sxs-lookup"><span data-stu-id="051e9-134">Value</span></span>|<span data-ttu-id="051e9-135">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-136">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="051e9-136">**IgnoreError**</span></span>|<span data-ttu-id="051e9-137">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-137">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-138">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="051e9-138">**ReportAndContinue**</span></span>|<span data-ttu-id="051e9-139">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-139">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-140">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="051e9-140">**ReportAndStop**</span></span>|<span data-ttu-id="051e9-141">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-141">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="051e9-142">**重複するキー**</span><span class="sxs-lookup"><span data-stu-id="051e9-142">**Duplicate key**</span></span>  
 <span data-ttu-id="051e9-143">重複キーのエラーに対する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-143">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="051e9-144">既定では、この値は **IgnoreError**です。</span><span class="sxs-lookup"><span data-stu-id="051e9-144">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="051e9-145">値</span><span class="sxs-lookup"><span data-stu-id="051e9-145">Value</span></span>|<span data-ttu-id="051e9-146">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-147">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="051e9-147">**IgnoreError**</span></span>|<span data-ttu-id="051e9-148">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-148">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-149">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="051e9-149">**ReportAndContinue**</span></span>|<span data-ttu-id="051e9-150">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-150">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-151">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="051e9-151">**ReportAndStop**</span></span>|<span data-ttu-id="051e9-152">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-152">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="051e9-153">**Null キーが不明な値に変換されました**</span><span class="sxs-lookup"><span data-stu-id="051e9-153">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="051e9-154">NULL キーが `UnknownMember` 値に変換された場合に実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-154">Specify the action to take when a null key has been converted to the `UnknownMember` value.</span></span> <span data-ttu-id="051e9-155">既定では、この値は **IgnoreError**です。</span><span class="sxs-lookup"><span data-stu-id="051e9-155">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="051e9-156">値</span><span class="sxs-lookup"><span data-stu-id="051e9-156">Value</span></span>|<span data-ttu-id="051e9-157">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-158">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="051e9-158">**IgnoreError**</span></span>|<span data-ttu-id="051e9-159">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-159">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-160">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="051e9-160">**ReportAndContinue**</span></span>|<span data-ttu-id="051e9-161">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-161">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-162">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="051e9-162">**ReportAndStop**</span></span>|<span data-ttu-id="051e9-163">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-163">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="051e9-164">**Null キーは使用できません**</span><span class="sxs-lookup"><span data-stu-id="051e9-164">**Null key not allowed**</span></span>  
 <span data-ttu-id="051e9-165">NULL キーが許可されていない場合に NULL キーが検出されたときに実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="051e9-165">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="051e9-166">既定では、この値は **[ReportAndContinue]** です。</span><span class="sxs-lookup"><span data-stu-id="051e9-166">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="051e9-167">値</span><span class="sxs-lookup"><span data-stu-id="051e9-167">Value</span></span>|<span data-ttu-id="051e9-168">説明</span><span class="sxs-lookup"><span data-stu-id="051e9-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="051e9-169">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="051e9-169">**IgnoreError**</span></span>|<span data-ttu-id="051e9-170">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-170">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-171">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="051e9-171">**ReportAndContinue**</span></span>|<span data-ttu-id="051e9-172">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="051e9-172">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="051e9-173">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="051e9-173">**ReportAndStop**</span></span>|<span data-ttu-id="051e9-174">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="051e9-174">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="051e9-175">**[エラー ログのパス]**</span><span class="sxs-lookup"><span data-stu-id="051e9-175">**Error log path**</span></span>  
 <span data-ttu-id="051e9-176">エラー ログのパスを入力するか、**[...]** ボタンをクリックしてログの保存先を選択します。</span><span class="sxs-lookup"><span data-stu-id="051e9-176">Type the path of the error log, or click the **browse(...)** button to select a destination.</span></span>  
  
 <span data-ttu-id="051e9-177">**[...]**</span><span class="sxs-lookup"><span data-stu-id="051e9-177">**Browse (...)**</span></span>  
 <span data-ttu-id="051e9-178">エラー ログのパスを選択します。</span><span class="sxs-lookup"><span data-stu-id="051e9-178">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051e9-179">参照</span><span class="sxs-lookup"><span data-stu-id="051e9-179">See Also</span></span>  
 <span data-ttu-id="051e9-180">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="051e9-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="051e9-181">[[ディメンション処理変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="051e9-181">[Dimension Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="051e9-182">[ディメンション処理変換先エディター ([マッピング] ページ)](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="051e9-182">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)</span></span>  
  
  
