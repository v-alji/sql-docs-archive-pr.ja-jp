---
title: '[メッセージキュータスクエディター] ([受信] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f45aa579d37d1fdd3a3124eea972014ce839fdc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743357"
---
# <a name="message-queue-task-editor-receive-page"></a><span data-ttu-id="cd0e0-102">[メッセージ キュー タスク エディター] ([受信] ページ)</span><span class="sxs-lookup"><span data-stu-id="cd0e0-102">Message Queue Task Editor (Receive Page)</span></span>
  <span data-ttu-id="cd0e0-103">**[メッセージ キュー タスク エディター]** ダイアログ ボックスの **[受信]** ページを使用して、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) メッセージを受信するためのメッセージ キュー タスクを構成します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-103">Use the **Receive** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to receive [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) messages.</span></span>  
  
 <span data-ttu-id="cd0e0-104">このタスクの詳細については、「 [Message Queue Task](control-flow/message-queue-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cd0e0-105">Options</span><span class="sxs-lookup"><span data-stu-id="cd0e0-105">Options</span></span>  
 <span data-ttu-id="cd0e0-106">**[RemoveFromMessageQueue]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-106">**RemoveFromMessageQueue**</span></span>  
 <span data-ttu-id="cd0e0-107">メッセージが受信された後にキューからメッセージを削除するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-107">Indicate whether to remove the message from the queue after it is received.</span></span> <span data-ttu-id="cd0e0-108">既定では、この値は `False` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-108">By default, this value is set to `False`.</span></span>  
  
 <span data-ttu-id="cd0e0-109">**[ErrorIfMessageTimeOut]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-109">**ErrorIfMessageTimeOut**</span></span>  
 <span data-ttu-id="cd0e0-110">メッセージがタイムアウトになったときに、エラー メッセージを表示してタスクを中止するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-110">Indicate whether the task fails when the message times out, displaying an error message.</span></span> <span data-ttu-id="cd0e0-111">既定では、 `False`です。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-111">The default is `False`.</span></span>  
  
 <span data-ttu-id="cd0e0-112">**[TimeoutAfter]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-112">**TimeoutAfter**</span></span>  
 <span data-ttu-id="cd0e0-113">タスクが失敗したときにエラー メッセージを表示するように指定した場合、タイムアウト メッセージが表示されるまでの待機時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-113">If you choose to display an error message on task failure, specify the number of seconds to wait before displaying the time-out message.</span></span>  
  
 <span data-ttu-id="cd0e0-114">**[MessageType]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-114">**MessageType**</span></span>  
 <span data-ttu-id="cd0e0-115">メッセージ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-115">Select the message type.</span></span> <span data-ttu-id="cd0e0-116">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-116">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd0e0-117">値</span><span class="sxs-lookup"><span data-stu-id="cd0e0-117">Value</span></span>|<span data-ttu-id="cd0e0-118">説明</span><span class="sxs-lookup"><span data-stu-id="cd0e0-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0e0-119">**[データ ファイル メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-119">**Data file message**</span></span>|<span data-ttu-id="cd0e0-120">メッセージはファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-120">The message is stored in a file.</span></span> <span data-ttu-id="cd0e0-121">この値を選択すると、動的オプションの **[DataFileMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-121">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="cd0e0-122">**[変数メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-122">**Variable message**</span></span>|<span data-ttu-id="cd0e0-123">メッセージは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-123">The message is stored in a variable.</span></span> <span data-ttu-id="cd0e0-124">この値を選択すると、動的オプションの **[VariableMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-124">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="cd0e0-125">**[文字列メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-125">**String message**</span></span>|<span data-ttu-id="cd0e0-126">メッセージはメッセージ キュー タスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-126">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="cd0e0-127">この値を選択すると、動的オプションの **[StringMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-127">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
|<span data-ttu-id="cd0e0-128">**[文字列メッセージを変数に指定]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-128">**String message to variable**</span></span>|<span data-ttu-id="cd0e0-129">メッセージです。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-129">The message</span></span><br /><br /> <span data-ttu-id="cd0e0-130">この値を選択すると、動的オプションの **[StringMessage]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-130">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="cd0e0-131">[MessageType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="cd0e0-131">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="cd0e0-132">[MessageType] = [データ ファイル メッセージ]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-132">MessageType = Data file message</span></span>  
 <span data-ttu-id="cd0e0-133">**[SaveFileAs]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-133">**SaveFileAs**</span></span>  
 <span data-ttu-id="cd0e0-134">使用するファイルのパスを入力します。または、省略記号ボタン ( **[...]** ) をクリックし、ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-134">Type the path of the file to use, or click the ellipsis button **(...)** and then locate the file.</span></span>  
  
 <span data-ttu-id="cd0e0-135">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-135">**Overwrite**</span></span>  
 <span data-ttu-id="cd0e0-136">データ ファイル メッセージの内容を保存するとき、既存のファイルのデータを上書きするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-136">Indicate whether to overwrite the data in an existing file when saving the contents of a data file message.</span></span> <span data-ttu-id="cd0e0-137">既定では、 `False`です。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-137">The default is `False`.</span></span>  
  
 <span data-ttu-id="cd0e0-138">**Assert**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-138">**Filter**</span></span>  
 <span data-ttu-id="cd0e0-139">メッセージにフィルターを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-139">Specify whether to apply a filter to the message.</span></span> <span data-ttu-id="cd0e0-140">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd0e0-141">値</span><span class="sxs-lookup"><span data-stu-id="cd0e0-141">Value</span></span>|<span data-ttu-id="cd0e0-142">説明</span><span class="sxs-lookup"><span data-stu-id="cd0e0-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0e0-143">**[フィルターなし]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-143">**No filter**</span></span>|<span data-ttu-id="cd0e0-144">メッセージにフィルターは適用されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-144">The task does not filter messages.</span></span> <span data-ttu-id="cd0e0-145">この値を選択すると、動的オプションの **[IdentifierReadOnly]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-145">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="cd0e0-146">**[パッケージから]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-146">**From package**</span></span>|<span data-ttu-id="cd0e0-147">指定したパッケージからのメッセージのみが受信されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-147">The message receives only messages from the specified package.</span></span> <span data-ttu-id="cd0e0-148">この値を選択すると、動的オプションの **[Identifier]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-148">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="cd0e0-149">[Filter] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="cd0e0-149">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="cd0e0-150">[Filter] = [フィルターなし]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-150">Filter = No filter</span></span>  
 <span data-ttu-id="cd0e0-151">**[IdentifierReadOnly]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-151">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="cd0e0-152">このオプションは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-152">This option is read-only.</span></span> <span data-ttu-id="cd0e0-153">[Filter] プロパティが以前に設定された場合、パッケージの GUID が表示されます。それ以外の場合は空です。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-153">It may be blank or contain the GUID of a package when the Filter property was previously set.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="cd0e0-154">[Filter] = [パッケージから]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-154">Filter = From package</span></span>  
 <span data-ttu-id="cd0e0-155">**識別子**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-155">**Identifier**</span></span>  
 <span data-ttu-id="cd0e0-156">フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-156">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="cd0e0-157">**関連トピック:** [パッケージの選択](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="cd0e0-157">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="cd0e0-158">[MessageType] = [変数メッセージ]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-158">MessageType = Variable message</span></span>  
 <span data-ttu-id="cd0e0-159">**Assert**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-159">**Filter**</span></span>  
 <span data-ttu-id="cd0e0-160">メッセージにフィルターを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-160">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="cd0e0-161">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-161">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd0e0-162">値</span><span class="sxs-lookup"><span data-stu-id="cd0e0-162">Value</span></span>|<span data-ttu-id="cd0e0-163">説明</span><span class="sxs-lookup"><span data-stu-id="cd0e0-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0e0-164">**[フィルターなし]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-164">**No filter**</span></span>|<span data-ttu-id="cd0e0-165">メッセージにフィルターは適用されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-165">The task does not filter messages.</span></span> <span data-ttu-id="cd0e0-166">この値を選択すると、動的オプションの **[IdentifierReadOnly]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-166">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="cd0e0-167">**[パッケージから]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-167">**From package**</span></span>|<span data-ttu-id="cd0e0-168">指定したパッケージからのメッセージのみが受信されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-168">The message receives only messages from the specified package.</span></span> <span data-ttu-id="cd0e0-169">この値を選択すると、動的オプションの **[Identifier]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-169">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
 <span data-ttu-id="cd0e0-170">**変数**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-170">**Variable**</span></span>  
 <span data-ttu-id="cd0e0-171">変数の名前を入力するか、[\<**New variable...**>] をクリックして新しい変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-171">Type the variable name, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="cd0e0-172">**関連トピック:** [変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="cd0e0-172">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="cd0e0-173">[Filter] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="cd0e0-173">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="cd0e0-174">[Filter] = [フィルターなし]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-174">Filter = No filter</span></span>  
 <span data-ttu-id="cd0e0-175">**[IdentifierReadOnly]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-175">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="cd0e0-176">このオプションは空白です。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-176">This option is blank.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="cd0e0-177">[Filter] = [パッケージから]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-177">Filter = From package</span></span>  
 <span data-ttu-id="cd0e0-178">**識別子**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-178">**Identifier**</span></span>  
 <span data-ttu-id="cd0e0-179">フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-179">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="cd0e0-180">**関連トピック:** [パッケージの選択](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="cd0e0-180">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="cd0e0-181">[MessageType] = [文字列メッセージ]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-181">MessageType = String message</span></span>  
 <span data-ttu-id="cd0e0-182">**比較**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-182">**Compare**</span></span>  
 <span data-ttu-id="cd0e0-183">メッセージにフィルターを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-183">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="cd0e0-184">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-184">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd0e0-185">値</span><span class="sxs-lookup"><span data-stu-id="cd0e0-185">Value</span></span>|<span data-ttu-id="cd0e0-186">説明</span><span class="sxs-lookup"><span data-stu-id="cd0e0-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0e0-187">**なし**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-187">**None**</span></span>|<span data-ttu-id="cd0e0-188">メッセージは比較されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-188">Messages are not compared.</span></span>|  
|<span data-ttu-id="cd0e0-189">**完全一致**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-189">**Exact match**</span></span>|<span data-ttu-id="cd0e0-190">メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-190">Messages must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="cd0e0-191">**大文字と小文字を区別しない**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-191">**Ignore case**</span></span>|<span data-ttu-id="cd0e0-192">メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-192">Message must match the string in the **CompareString** option, but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="cd0e0-193">**[含まれる文字列]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-193">**Containing**</span></span>|<span data-ttu-id="cd0e0-194">メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-194">Message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="cd0e0-195">**[CompareString]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-195">**CompareString**</span></span>  
 <span data-ttu-id="cd0e0-196">**[Compare]** オプションが **[なし]** に設定されていない場合、メッセージと比較する文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-196">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
### <a name="messagetype--string-message-to-variable"></a><span data-ttu-id="cd0e0-197">[MessageType] = [文字列メッセージを変数に指定]</span><span class="sxs-lookup"><span data-stu-id="cd0e0-197">MessageType = String message to variable</span></span>  
 <span data-ttu-id="cd0e0-198">**比較**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-198">**Compare**</span></span>  
 <span data-ttu-id="cd0e0-199">メッセージにフィルターを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-199">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="cd0e0-200">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-200">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd0e0-201">値</span><span class="sxs-lookup"><span data-stu-id="cd0e0-201">Value</span></span>|<span data-ttu-id="cd0e0-202">説明</span><span class="sxs-lookup"><span data-stu-id="cd0e0-202">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd0e0-203">**なし**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-203">**None**</span></span>|<span data-ttu-id="cd0e0-204">メッセージは比較されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-204">Messages are not compared.</span></span>|  
|<span data-ttu-id="cd0e0-205">**完全一致**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-205">**Exact match**</span></span>|<span data-ttu-id="cd0e0-206">メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-206">The message must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="cd0e0-207">**大文字と小文字を区別しない**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-207">**Ignore case**</span></span>|<span data-ttu-id="cd0e0-208">メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-208">The message must match the string in the **CompareString** option but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="cd0e0-209">**[含まれる文字列]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-209">**Containing**</span></span>|<span data-ttu-id="cd0e0-210">メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-210">The message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="cd0e0-211">**[CompareString]**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-211">**CompareString**</span></span>  
 <span data-ttu-id="cd0e0-212">**[Compare]** オプションが **[なし]** に設定されていない場合、メッセージと比較する文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-212">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
 <span data-ttu-id="cd0e0-213">**変数**</span><span class="sxs-lookup"><span data-stu-id="cd0e0-213">**Variable**</span></span>  
 <span data-ttu-id="cd0e0-214">受信したメッセージを格納する変数の名前を入力するか、[\<**New variable...**>] をクリックして新しい変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="cd0e0-214">Type the name of the variable to hold the received message, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="cd0e0-215">**関連トピック:** [変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="cd0e0-215">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0e0-216">参照</span><span class="sxs-lookup"><span data-stu-id="cd0e0-216">See Also</span></span>  
 <span data-ttu-id="cd0e0-217">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cd0e0-217">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cd0e0-218">[メッセージキュータスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cd0e0-218">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="cd0e0-219">[メッセージキュータスクエディター &#40;送信ページ&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd0e0-219">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 <span data-ttu-id="cd0e0-220">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd0e0-220">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="cd0e0-221">メッセージ キュー タスク</span><span class="sxs-lookup"><span data-stu-id="cd0e0-221">Message Queue Task</span></span>](control-flow/message-queue-task.md)  
  
  
