---
title: '[パーティション処理変換先エディター] ([詳細設定] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12845ecd644eabd949ea37fbb18ba6cc9cf342f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632555"
---
# <a name="partition-processing-destination-editor-advanced-page"></a><span data-ttu-id="3caba-102">[パーティション処理変換先エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="3caba-102">Partition Processing Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="3caba-103">**[パーティション処理変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理を設定できます。</span><span class="sxs-lookup"><span data-stu-id="3caba-103">Use the **Advanced** page of the **Partition Processing Destination Editor** dialog box to configure error handling.</span></span>  
  
 <span data-ttu-id="3caba-104">パーティション処理変換先の詳細については、「 [Partition Processing Destination](data-flow/partition-processing-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3caba-104">To learn more about the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3caba-105">ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="3caba-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="3caba-106">テーブル モデルで入力列をパーティション列にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3caba-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="3caba-107">代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="3caba-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3caba-108">Options</span><span class="sxs-lookup"><span data-stu-id="3caba-108">Options</span></span>  
 <span data-ttu-id="3caba-109">**[既定のエラー構成を使用する]**</span><span class="sxs-lookup"><span data-stu-id="3caba-109">**Use default error configuration.**</span></span>  
 <span data-ttu-id="3caba-110">既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エラー処理を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-110">Specify whether to use the default [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] error handling.</span></span> <span data-ttu-id="3caba-111">この値の既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="3caba-111">By default, this value is `True`.</span></span>  
  
 <span data-ttu-id="3caba-112">**[キー エラー アクション]**</span><span class="sxs-lookup"><span data-stu-id="3caba-112">**Key error action**</span></span>  
 <span data-ttu-id="3caba-113">許容されないキー値を持つレコードを処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-113">Specify how to handle records that have unacceptable key values.</span></span>  
  
|<span data-ttu-id="3caba-114">値</span><span class="sxs-lookup"><span data-stu-id="3caba-114">Value</span></span>|<span data-ttu-id="3caba-115">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-116">**ConvertToUnknown**</span><span class="sxs-lookup"><span data-stu-id="3caba-116">**ConvertToUnknown**</span></span>|<span data-ttu-id="3caba-117">不正なキー値を不明な値に変換します。</span><span class="sxs-lookup"><span data-stu-id="3caba-117">Convert the unacceptable key value to the Unknown value.</span></span>|  
|<span data-ttu-id="3caba-118">**DiscardRecord**</span><span class="sxs-lookup"><span data-stu-id="3caba-118">**DiscardRecord**</span></span>|<span data-ttu-id="3caba-119">レコードを破棄します。</span><span class="sxs-lookup"><span data-stu-id="3caba-119">Discard the record.</span></span>|  
  
 <span data-ttu-id="3caba-120">**[エラーを無視する]**</span><span class="sxs-lookup"><span data-stu-id="3caba-120">**Ignore errors**</span></span>  
 <span data-ttu-id="3caba-121">エラーを無視することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-121">Specify that errors should be ignored.</span></span>  
  
 <span data-ttu-id="3caba-122">**[エラー時に停止する]**</span><span class="sxs-lookup"><span data-stu-id="3caba-122">**Stop on error**</span></span>  
 <span data-ttu-id="3caba-123">エラーが発生した場合に処理を停止することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-123">Specify that processing should stop when an error occurs.</span></span>  
  
 <span data-ttu-id="3caba-124">**エラーの数**</span><span class="sxs-lookup"><span data-stu-id="3caba-124">**Number of errors**</span></span>  
 <span data-ttu-id="3caba-125">**[エラー時に停止する]** を選択した場合は、処理を停止するエラーのしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-125">Specify the error threshold at which processing should stop, if you have selected **Stop on error**.</span></span>  
  
 <span data-ttu-id="3caba-126">**[エラー時のアクション]**</span><span class="sxs-lookup"><span data-stu-id="3caba-126">**On error action**</span></span>  
 <span data-ttu-id="3caba-127">**[エラー時に停止する]** を選択した場合は、エラーのしきい値に達した場合に実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-127">Specify the action to take when the error threshold is reached, if you have selected **Stop on error**.</span></span>  
  
|<span data-ttu-id="3caba-128">値</span><span class="sxs-lookup"><span data-stu-id="3caba-128">Value</span></span>|<span data-ttu-id="3caba-129">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-130">**StopProcessing**</span><span class="sxs-lookup"><span data-stu-id="3caba-130">**StopProcessing**</span></span>|<span data-ttu-id="3caba-131">処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-131">Stop processing.</span></span>|  
|<span data-ttu-id="3caba-132">**StopLogging**</span><span class="sxs-lookup"><span data-stu-id="3caba-132">**StopLogging**</span></span>|<span data-ttu-id="3caba-133">ログ記録エラーを停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-133">Stop logging errors.</span></span>|  
  
 <span data-ttu-id="3caba-134">**[見つからないキー]**</span><span class="sxs-lookup"><span data-stu-id="3caba-134">**Key not found**</span></span>  
 <span data-ttu-id="3caba-135">見つからないキーのエラーに対する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-135">Specify the action to take for a key not found error.</span></span> <span data-ttu-id="3caba-136">既定では、この値は **[ReportAndContinue]** です。</span><span class="sxs-lookup"><span data-stu-id="3caba-136">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="3caba-137">値</span><span class="sxs-lookup"><span data-stu-id="3caba-137">Value</span></span>|<span data-ttu-id="3caba-138">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-139">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="3caba-139">**IgnoreError**</span></span>|<span data-ttu-id="3caba-140">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-140">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-141">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="3caba-141">**ReportAndContinue**</span></span>|<span data-ttu-id="3caba-142">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-142">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-143">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="3caba-143">**ReportAndStop**</span></span>|<span data-ttu-id="3caba-144">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-144">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="3caba-145">**重複するキー**</span><span class="sxs-lookup"><span data-stu-id="3caba-145">**Duplicate key**</span></span>  
 <span data-ttu-id="3caba-146">重複キーのエラーに対する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-146">Specify the action to take for a duplicate key error.</span></span> <span data-ttu-id="3caba-147">既定では、この値は **IgnoreError**です。</span><span class="sxs-lookup"><span data-stu-id="3caba-147">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="3caba-148">値</span><span class="sxs-lookup"><span data-stu-id="3caba-148">Value</span></span>|<span data-ttu-id="3caba-149">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-150">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="3caba-150">**IgnoreError**</span></span>|<span data-ttu-id="3caba-151">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-151">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-152">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="3caba-152">**ReportAndContinue**</span></span>|<span data-ttu-id="3caba-153">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-153">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-154">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="3caba-154">**ReportAndStop**</span></span>|<span data-ttu-id="3caba-155">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-155">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="3caba-156">**Null キーが不明な値に変換されました**</span><span class="sxs-lookup"><span data-stu-id="3caba-156">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="3caba-157">NULL キーが不明な値に変換された場合に実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-157">Specify the action to take when a null key has been converted to the Unknown value.</span></span> <span data-ttu-id="3caba-158">既定では、この値は **IgnoreError**です。</span><span class="sxs-lookup"><span data-stu-id="3caba-158">By default, this value is **IgnoreError**.</span></span>  
  
|<span data-ttu-id="3caba-159">値</span><span class="sxs-lookup"><span data-stu-id="3caba-159">Value</span></span>|<span data-ttu-id="3caba-160">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-161">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="3caba-161">**IgnoreError**</span></span>|<span data-ttu-id="3caba-162">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-162">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-163">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="3caba-163">**ReportAndContinue**</span></span>|<span data-ttu-id="3caba-164">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-164">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-165">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="3caba-165">**ReportAndStop**</span></span>|<span data-ttu-id="3caba-166">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-166">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="3caba-167">**Null キーは使用できません**</span><span class="sxs-lookup"><span data-stu-id="3caba-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="3caba-168">NULL キーが許可されていない場合に NULL キーが検出されたときに実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="3caba-168">Specify the action to take when null keys are not allowed and a null key is encountered.</span></span> <span data-ttu-id="3caba-169">既定では、この値は **[ReportAndContinue]** です。</span><span class="sxs-lookup"><span data-stu-id="3caba-169">By default, this value is **ReportAndContinue**.</span></span>  
  
|<span data-ttu-id="3caba-170">値</span><span class="sxs-lookup"><span data-stu-id="3caba-170">Value</span></span>|<span data-ttu-id="3caba-171">説明</span><span class="sxs-lookup"><span data-stu-id="3caba-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3caba-172">**IgnoreError**</span><span class="sxs-lookup"><span data-stu-id="3caba-172">**IgnoreError**</span></span>|<span data-ttu-id="3caba-173">エラーを無視して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-173">Ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-174">**[ReportAndContinue]**</span><span class="sxs-lookup"><span data-stu-id="3caba-174">**ReportAndContinue**</span></span>|<span data-ttu-id="3caba-175">エラーを報告して処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="3caba-175">Report the error and continue processing.</span></span>|  
|<span data-ttu-id="3caba-176">**ReportAndStop**</span><span class="sxs-lookup"><span data-stu-id="3caba-176">**ReportAndStop**</span></span>|<span data-ttu-id="3caba-177">エラーを報告して処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="3caba-177">Report the error and stop processing.</span></span>|  
  
 <span data-ttu-id="3caba-178">**[エラー ログのパス]**</span><span class="sxs-lookup"><span data-stu-id="3caba-178">**Error log path**</span></span>  
 <span data-ttu-id="3caba-179">エラー ログのパスを入力するか、 **(...)** 参照ボタンを使用してログの保存先を選択します。</span><span class="sxs-lookup"><span data-stu-id="3caba-179">Type the path for the error log, or select a destination by using the browse **(...)** button.</span></span>  
  
 <span data-ttu-id="3caba-180">**[...]**</span><span class="sxs-lookup"><span data-stu-id="3caba-180">**Browse (...)**</span></span>  
 <span data-ttu-id="3caba-181">エラー ログのパスを選択します。</span><span class="sxs-lookup"><span data-stu-id="3caba-181">Select a path for the error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3caba-182">参照</span><span class="sxs-lookup"><span data-stu-id="3caba-182">See Also</span></span>  
 <span data-ttu-id="3caba-183">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3caba-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3caba-184">[パーティション処理変換先エディター ([マッピング] ページ)](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="3caba-184">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)</span></span>  
  
  
