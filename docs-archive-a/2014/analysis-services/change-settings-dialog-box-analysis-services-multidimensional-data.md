---
title: '[設定の変更] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2649195e3aff4e17d378e54c4b1d656361dfe3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634164"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="45455-102">[設定の変更] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="45455-102">Change Settings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="45455-103">**および** の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] [設定の変更] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 **[処理]** ダイアログ ボックスに示されているオブジェクトの処理を制御する設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="45455-103">Use the **Change Settings** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to change the settings that govern the processing of objects listed in the **Process** dialog box.</span></span> <span data-ttu-id="45455-104">**[設定の変更]** ダイアログ ボックスを表示するには、 **[処理]** ダイアログ ボックスの **[設定の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45455-104">You can display the **Change Settings** dialog box by clicking **Change Settings** on the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45455-105">このダイアログ ボックスで指定された  設定は、**[処理]** ダイアログ ボックスに一覧表示されたオブジェクトの、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースから継承された既定の設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="45455-105">Settings specified in this dialog box override default settings inherited from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database for the objects listed in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="45455-106">Options</span><span class="sxs-lookup"><span data-stu-id="45455-106">Options</span></span>  
 <span data-ttu-id="45455-107">**処理オプション**</span><span class="sxs-lookup"><span data-stu-id="45455-107">**Processing options**</span></span>  
 <span data-ttu-id="45455-108">このタブを使用して、処理中の操作の処理順序、書き戻しテーブル、および影響を受けたオブジェクトに関連する設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="45455-108">Use this tab to modify settings related to the processing order, writeback table, and affected objects for the processing operation.</span></span> <span data-ttu-id="45455-109">このタブには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="45455-109">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="45455-110">**Parallel**</span><span class="sxs-lookup"><span data-stu-id="45455-110">**Parallel**</span></span>  
 <span data-ttu-id="45455-111">オブジェクトを並列に処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-111">Click to process the objects in parallel.</span></span>  
  
 <span data-ttu-id="45455-112">**[最大並列タスク]**</span><span class="sxs-lookup"><span data-stu-id="45455-112">**Maximum parallel tasks**</span></span>  
 <span data-ttu-id="45455-113">処理中の操作で並列に実行されるタスクの最大数を選択するか、 **[サーバーの決定]** を選択し、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が並列タスクの最適数を選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-113">Select the maximum number of tasks to execute in parallel by the processing operation, or choose **Let the server decide** to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to select an optimal number of parallel tasks.</span></span>  
  
 <span data-ttu-id="45455-114">**逐次**</span><span class="sxs-lookup"><span data-stu-id="45455-114">**Sequential**</span></span>  
 <span data-ttu-id="45455-115">オブジェクトを順番に処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-115">Click to process the objects sequentially.</span></span>  
  
 <span data-ttu-id="45455-116">**[トランザクション モード]**</span><span class="sxs-lookup"><span data-stu-id="45455-116">**Transaction mode**</span></span>  
 <span data-ttu-id="45455-117">オブジェクトが順番に処理される際に使用するトランザクション モードを次から選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-117">Choose the transaction mode that is used when objects are processed in sequential order:</span></span>  
  
-   <span data-ttu-id="45455-118">**[1 つのトランザクション]** は、同じトランザクションのすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-118">**One Transaction** processes all objects in the same transaction.</span></span>  
  
-   <span data-ttu-id="45455-119">**[個別のトランザクション]** は、依存オブジェクトを含む、個別のトランザクションのすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-119">**Separate Transactions** processes all objects, including dependent objects, in separate transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45455-120"> このオプションは、 **[シーケンシャル]** が選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="45455-120">This option is enabled only if **Sequential** is selected.</span></span>  
  
 <span data-ttu-id="45455-121">**[書き戻しテーブル オプション]**</span><span class="sxs-lookup"><span data-stu-id="45455-121">**Writeback table option**</span></span>  
 <span data-ttu-id="45455-122">書き戻しテーブルの管理に使用するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-122">Choose the option used to manage a writeback table:</span></span>  
  
-   <span data-ttu-id="45455-123">**[作成]** は、書き戻しテーブルが存在しない場合に作成します。</span><span class="sxs-lookup"><span data-stu-id="45455-123">**Create** creates a writeback table if it does not exist.</span></span> <span data-ttu-id="45455-124">書き戻しテーブルが既に存在する場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="45455-124">An error occurs if a writeback table already exists.</span></span>  
  
-   <span data-ttu-id="45455-125">**[常に作成]** は、書き戻しテーブルが存在しない場合に作成するか、既存の書き戻しテーブルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="45455-125">**Create always** creates a writeback table if it does not exist, or overwrites the existing writeback table if it does exist.</span></span>  
  
-   <span data-ttu-id="45455-126">**[既存のデータを使用する]** は、書き戻しテーブルが存在する場合にそれを使用します。</span><span class="sxs-lookup"><span data-stu-id="45455-126">**Use existing** uses the existing writeback table if it exists.</span></span> <span data-ttu-id="45455-127">書き戻しテーブルが存在しない場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="45455-127">An error occurs if a writeback table does not exist.</span></span>  
  
 <span data-ttu-id="45455-128">**影響を受けるオブジェクトの処理**</span><span class="sxs-lookup"><span data-stu-id="45455-128">**Process affected objects**</span></span>  
 <span data-ttu-id="45455-129">処理中の操作に含まれているオブジェクトに依存するオブジェクトを、処理対象に含めて処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-129">Select to include and process objects that depend on objects included in the processing operation.</span></span>  
  
 <span data-ttu-id="45455-130">**ディメンションキーのエラー**</span><span class="sxs-lookup"><span data-stu-id="45455-130">**Dimension key errors**</span></span>  
 <span data-ttu-id="45455-131">このタブを使用して、処理中の操作のエラー構成に関連する設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="45455-131">Use this tab to modify settings related to the error configuration for the processing operation.</span></span> <span data-ttu-id="45455-132">このタブには次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="45455-132">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="45455-133">**既定のエラー構成を使用する**</span><span class="sxs-lookup"><span data-stu-id="45455-133">**Use default error configuration**</span></span>  
 <span data-ttu-id="45455-134">処理操作でオブジェクトに対して既定のエラー構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="45455-134">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="45455-135">**[カスタム エラー構成を使用する]**</span><span class="sxs-lookup"><span data-stu-id="45455-135">**Use custom error configuration**</span></span>  
 <span data-ttu-id="45455-136">処理操作でオブジェクトに対してエラー構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="45455-136">Select to define the error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="45455-137">**[キー エラー アクション]**</span><span class="sxs-lookup"><span data-stu-id="45455-137">**Key error action**</span></span>  
 <span data-ttu-id="45455-138">参照できない処理の間に新しいキーが検出されたとき、発生するアクションを次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-138">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="45455-139">**[不明な種類に変換]** は、レコードの情報を不明なメンバーに集計します。</span><span class="sxs-lookup"><span data-stu-id="45455-139">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="45455-140">**[レコードの破棄]** は、レコードの情報をオブジェクトでの処理から除外します。</span><span class="sxs-lookup"><span data-stu-id="45455-140">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="45455-141">**エラー数を無視する**</span><span class="sxs-lookup"><span data-stu-id="45455-141">**Ignore errors count**</span></span>  
 <span data-ttu-id="45455-142">処理中に発生するエラーは、すべて無視します。</span><span class="sxs-lookup"><span data-stu-id="45455-142">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="45455-143">**[エラー時に停止する]**</span><span class="sxs-lookup"><span data-stu-id="45455-143">**Stop on error**</span></span>  
 <span data-ttu-id="45455-144">エラーが発生した場合、処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="45455-144">Click to stop processing when errors occur.</span></span> <span data-ttu-id="45455-145">このオプションによって、 **[エラー数]** オプションおよび **[エラー時のアクション]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="45455-145">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="45455-146">**エラーの数**</span><span class="sxs-lookup"><span data-stu-id="45455-146">**Number of errors**</span></span>  
 <span data-ttu-id="45455-147">処理が停止される前に無視できるエラーの数を入力します。</span><span class="sxs-lookup"><span data-stu-id="45455-147">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="45455-148">**[エラー時のアクション]**</span><span class="sxs-lookup"><span data-stu-id="45455-148">**On error action**</span></span>  
 <span data-ttu-id="45455-149">エラー数が **[エラー数]** の値を超えたときに行うアクションを次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-149">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="45455-150">**[処理の停止]** は、処理中の操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="45455-150">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="45455-151">**[ログ記録の停止]** は、エラーのログ記録を停止しますが、処理中の操作は続行します。</span><span class="sxs-lookup"><span data-stu-id="45455-151">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="45455-152">**[見つからないキー]**</span><span class="sxs-lookup"><span data-stu-id="45455-152">**Key not found**</span></span>  
 <span data-ttu-id="45455-153">オブジェクトの処理の際にキーが見つからなかった場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="45455-153">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="45455-154">[**エラーを無視**する] エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="45455-154">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="45455-155">[**レポートと続行**] はエラーを報告し、処理操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="45455-155">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="45455-156">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="45455-156">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="45455-157">**重複するキー**</span><span class="sxs-lookup"><span data-stu-id="45455-157">**Duplicate key**</span></span>  
 <span data-ttu-id="45455-158">オブジェクトの処理の際に重複キーが見つかった場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="45455-158">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="45455-159">[**エラーを無視**する] エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="45455-159">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="45455-160">[**レポートと続行**] はエラーを報告し、処理操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="45455-160">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="45455-161">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="45455-161">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="45455-162">**Null キーが不明な値に変換されました**</span><span class="sxs-lookup"><span data-stu-id="45455-162">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="45455-163">オブジェクトの処理の際に NULL メンバー キーが不明なメンバーに追加された場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="45455-163">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed:</span></span>  
  
-   <span data-ttu-id="45455-164">[**エラーを無視**する] エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="45455-164">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="45455-165">[**レポートと続行**] はエラーを報告し、処理操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="45455-165">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="45455-166">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="45455-166">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="45455-167">**Null キーは使用できません**</span><span class="sxs-lookup"><span data-stu-id="45455-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="45455-168">オブジェクトの処理の際に NULL キーが見つかったが許可されていない場合に行うアクションを次の中から 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="45455-168">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed:</span></span>  
  
-   <span data-ttu-id="45455-169">[**エラーを無視**する] エラーを無視します。</span><span class="sxs-lookup"><span data-stu-id="45455-169">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="45455-170">[**レポートと続行**] はエラーを報告し、処理操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="45455-170">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="45455-171">**[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="45455-171">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="45455-172">**[エラー ログのパス]**</span><span class="sxs-lookup"><span data-stu-id="45455-172">**Error log path**</span></span>  
 <span data-ttu-id="45455-173">エラー ログ ファイルの完全なパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="45455-173">Type the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="45455-174">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="45455-174">**Browse**</span></span>  
 <span data-ttu-id="45455-175">**[開く]** ダイアログ ボックスを表示し、エラー ログ ファイルの完全なパスおよびファイル名を選択します。</span><span class="sxs-lookup"><span data-stu-id="45455-175">Click to open the **Open** dialog box and select the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="45455-176">**影響を受けるオブジェクトの処理**</span><span class="sxs-lookup"><span data-stu-id="45455-176">**Process affected objects**</span></span>  
 <span data-ttu-id="45455-177">**[処理]** ダイアログ ボックスで選択されたオブジェクトに依存するオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="45455-177">Click to process the objects that have a dependency on the objects selected in the **Process** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45455-178">参照</span><span class="sxs-lookup"><span data-stu-id="45455-178">See Also</span></span>  
 <span data-ttu-id="45455-179">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="45455-179">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="45455-180">[[処理] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="45455-180">[Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](process-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
