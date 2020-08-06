---
title: '[FTP タスクエディター] ([ファイル転送] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8094051e93c4165be6ae186bde394f9271d60669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633904"
---
# <a name="ftp-task-editor-file-transfer-page"></a><span data-ttu-id="1ade4-102">[FTP タスク エディター] ([ファイル転送] ページ)</span><span class="sxs-lookup"><span data-stu-id="1ade4-102">FTP Task Editor (File Transfer Page)</span></span>
  <span data-ttu-id="1ade4-103">**[FTP タスク エディター]** ダイアログ ボックスの **[ファイル転送]** ページを使用すると、タスクで実行される FTP 操作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-103">Use the **File Transfer** page of the **FTP Task Editor** dialog box to configure the FTP operation that the task performs.</span></span>  
  
 <span data-ttu-id="1ade4-104">このタスクの詳細については、「 [FTP タスク](control-flow/ftp-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ade4-104">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ade4-105">Options</span><span class="sxs-lookup"><span data-stu-id="1ade4-105">Options</span></span>  
 <span data-ttu-id="1ade4-106">**[IsRemotePathVariable]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-106">**IsRemotePathVariable**</span></span>  
 <span data-ttu-id="1ade4-107">リモート パスが変数に格納されているかどうかを表します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-107">Indicate whether the remote path is stored in a variable.</span></span> <span data-ttu-id="1ade4-108">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1ade4-109">値</span><span class="sxs-lookup"><span data-stu-id="1ade4-109">Value</span></span>|<span data-ttu-id="1ade4-110">説明</span><span class="sxs-lookup"><span data-stu-id="1ade4-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ade4-111">**True**</span><span class="sxs-lookup"><span data-stu-id="1ade4-111">**True**</span></span>|<span data-ttu-id="1ade4-112">対象になるパスは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-112">The destination path is stored in a variable.</span></span> <span data-ttu-id="1ade4-113">この値を選択すると、動的オプションの **[RemoteVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-113">Selecting the value displays the dynamic option, **RemoteVariable**.</span></span>|  
|<span data-ttu-id="1ade4-114">**False**</span><span class="sxs-lookup"><span data-stu-id="1ade4-114">**False**</span></span>|<span data-ttu-id="1ade4-115">対象になるパスは、ファイル接続マネージャーで指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-115">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="1ade4-116">この値を選択すると、動的オプションの **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-116">Selecting the value displays the dynamic option, **RemotePath**.</span></span>|  
  
 <span data-ttu-id="1ade4-117">**[OverwriteFileAtDestination]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-117">**OverwriteFileAtDestination**</span></span>  
 <span data-ttu-id="1ade4-118">転送先でファイルを上書きできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-118">Specify whether a file at the destination can be overwritten.</span></span>  
  
 <span data-ttu-id="1ade4-119">**[IsLocalPathVariable]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-119">**IsLocalPathVariable**</span></span>  
 <span data-ttu-id="1ade4-120">ローカル パスが変数に格納されているかどうかを表します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-120">Indicate whether the local path is stored in a variable.</span></span> <span data-ttu-id="1ade4-121">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-121">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1ade4-122">値</span><span class="sxs-lookup"><span data-stu-id="1ade4-122">Value</span></span>|<span data-ttu-id="1ade4-123">説明</span><span class="sxs-lookup"><span data-stu-id="1ade4-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ade4-124">**True**</span><span class="sxs-lookup"><span data-stu-id="1ade4-124">**True**</span></span>|<span data-ttu-id="1ade4-125">対象になるパスは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-125">The destination path is stored in a variable.</span></span> <span data-ttu-id="1ade4-126">この値を選択すると、動的オプションの **[LocalVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-126">Selecting the value displays the dynamic option, **LocalVariable**.</span></span>|  
|<span data-ttu-id="1ade4-127">**False**</span><span class="sxs-lookup"><span data-stu-id="1ade4-127">**False**</span></span>|<span data-ttu-id="1ade4-128">対象になるパスは、ファイル接続マネージャーで指定されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-128">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="1ade4-129">この値を選択すると、動的オプションの **[LocalPath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-129">Selecting the value displays the dynamic option, **LocalPath**.</span></span>|  
  
 <span data-ttu-id="1ade4-130">**操作**</span><span class="sxs-lookup"><span data-stu-id="1ade4-130">**Operation**</span></span>  
 <span data-ttu-id="1ade4-131">実行する FTP 操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-131">Select the FTP operation to perform.</span></span> <span data-ttu-id="1ade4-132">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1ade4-133">値</span><span class="sxs-lookup"><span data-stu-id="1ade4-133">Value</span></span>|<span data-ttu-id="1ade4-134">説明</span><span class="sxs-lookup"><span data-stu-id="1ade4-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ade4-135">**ファイルの送信**</span><span class="sxs-lookup"><span data-stu-id="1ade4-135">**Send files**</span></span>|<span data-ttu-id="1ade4-136">ファイルを送信します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-136">Send files.</span></span> <span data-ttu-id="1ade4-137">この値を選択すると、動的オプションの **[LocalVariable]** 、 **[LocalPathRemoteVariable]** 、 **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-137">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="1ade4-138">**ファイルの受信**</span><span class="sxs-lookup"><span data-stu-id="1ade4-138">**Receive files**</span></span>|<span data-ttu-id="1ade4-139">ファイルを受信します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-139">Receive files.</span></span> <span data-ttu-id="1ade4-140">この値を選択すると、動的オプションの **[LocalVariable]** 、 **[LocalPathRemoteVariable]** 、 **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-140">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="1ade4-141">**ローカル ディレクトリの作成**</span><span class="sxs-lookup"><span data-stu-id="1ade4-141">**Create local directory**</span></span>|<span data-ttu-id="1ade4-142">ローカル ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-142">Create a local directory.</span></span> <span data-ttu-id="1ade4-143">この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-143">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="1ade4-144">**リモート ディレクトリの作成**</span><span class="sxs-lookup"><span data-stu-id="1ade4-144">**Create remote directory**</span></span>|<span data-ttu-id="1ade4-145">リモート ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-145">Create a remote directory.</span></span> <span data-ttu-id="1ade4-146">この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-146">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotelPath**.</span></span>|  
|<span data-ttu-id="1ade4-147">**ローカル ディレクトリの削除**</span><span class="sxs-lookup"><span data-stu-id="1ade4-147">**Remove local directory**</span></span>|<span data-ttu-id="1ade4-148">ローカル ディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-148">Removes a local directory.</span></span> <span data-ttu-id="1ade4-149">この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-149">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="1ade4-150">**リモート ディレクトリの削除**</span><span class="sxs-lookup"><span data-stu-id="1ade4-150">**Remove remote directory**</span></span>|<span data-ttu-id="1ade4-151">リモート ディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-151">Remove a remote directory.</span></span> <span data-ttu-id="1ade4-152">この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-152">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="1ade4-153">**ローカル ファイルの削除**</span><span class="sxs-lookup"><span data-stu-id="1ade4-153">**Delete local files**</span></span>|<span data-ttu-id="1ade4-154">ローカル ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-154">Delete local files.</span></span> <span data-ttu-id="1ade4-155">この値を選択すると、動的オプションの **[LocalVariable]** および **[LocalPath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-155">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="1ade4-156">**リモート ファイルの削除**</span><span class="sxs-lookup"><span data-stu-id="1ade4-156">**Delete remote files**</span></span>|<span data-ttu-id="1ade4-157">リモート ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-157">Delete remote files.</span></span> <span data-ttu-id="1ade4-158">この値を選択すると、動的オプションの **[RemoteVariable]** および **[RemotePath]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ade4-158">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
  
 <span data-ttu-id="1ade4-159">**[IsTransferASCII]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-159">**IsTransferASCII**</span></span>  
 <span data-ttu-id="1ade4-160">リモート FTP サーバーへ転送されるファイル、およびリモート FTP サーバーから転送されるファイルを ASCII モードで転送するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-160">Indicate whether files transferred to and from the remote FTP server should be transferred in ASCII mode.</span></span>  
  
## <a name="isremotepathvariable-dynamic-options"></a><span data-ttu-id="1ade4-161">[IsRemotePathVariable] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="1ade4-161">IsRemotePathVariable Dynamic Options</span></span>  
  
### <a name="isremotepathvariable--true"></a><span data-ttu-id="1ade4-162">[IsRemotePathVariable] = [True]</span><span class="sxs-lookup"><span data-stu-id="1ade4-162">IsRemotePathVariable = True</span></span>  
 <span data-ttu-id="1ade4-163">**[RemoteVariable]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-163">**RemoteVariable**</span></span>  
 <span data-ttu-id="1ade4-164">既存のユーザー定義変数を選択するか、[\<**New variable...**>] をクリックしてユーザー定義変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-164">Select an existing user-defined variable, or click \<**New variable...**> to create a user-defined variable.</span></span>  
  
 <span data-ttu-id="1ade4-165">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、変数の追加</span><span class="sxs-lookup"><span data-stu-id="1ade4-165">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="isremotepathvariable--false"></a><span data-ttu-id="1ade4-166">[IsRemotePathVariable] = [False]</span><span class="sxs-lookup"><span data-stu-id="1ade4-166">IsRemotePathVariable = False</span></span>  
 <span data-ttu-id="1ade4-167">**[RemotePath]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-167">**RemotePath**</span></span>  
 <span data-ttu-id="1ade4-168">既存の FTP 接続マネージャーを選択するか、[\<**New connection...**>] をクリックして接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-168">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="1ade4-169">**関連トピック:** [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)、[FTP 接続マネージャー エディター](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1ade4-169">**Related Topics:** [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
## <a name="islocalpathvariable-dynamic-options"></a><span data-ttu-id="1ade4-170">[IsLocalPathVariable] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="1ade4-170">IsLocalPathVariable Dynamic Options</span></span>  
  
### <a name="islocalpathvariable--true"></a><span data-ttu-id="1ade4-171">[IsLocalPathVariable] = [True]</span><span class="sxs-lookup"><span data-stu-id="1ade4-171">IsLocalPathVariable = True</span></span>  
 <span data-ttu-id="1ade4-172">**[LocalVariable]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-172">**LocalVariable**</span></span>  
 <span data-ttu-id="1ade4-173">既存のユーザー定義変数を選択するか、[\<**New variable...**>] をクリックして変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-173">Select an existing user-defined variable, or click \<**New variable...**> to create a variable.</span></span>  
  
 <span data-ttu-id="1ade4-174">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、変数の追加</span><span class="sxs-lookup"><span data-stu-id="1ade4-174">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="islocalpathvariable--false"></a><span data-ttu-id="1ade4-175">[IsLocalPathVariable] = [False]</span><span class="sxs-lookup"><span data-stu-id="1ade4-175">IsLocalPathVariable = False</span></span>  
 <span data-ttu-id="1ade4-176">**[LocalPath]**</span><span class="sxs-lookup"><span data-stu-id="1ade4-176">**LocalPath**</span></span>  
 <span data-ttu-id="1ade4-177">既存のファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ade4-177">Select an existing File connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="1ade4-178">**関連トピック:**[フラット ファイル接続マネージャー](connection-manager/file-connection-manager.md)、 [ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1ade4-178">**Related Topics**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ade4-179">参照</span><span class="sxs-lookup"><span data-stu-id="1ade4-179">See Also</span></span>  
 <span data-ttu-id="1ade4-180">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1ade4-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1ade4-181">[FTP タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="1ade4-181">[FTP Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="1ade4-182">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="1ade4-182">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
