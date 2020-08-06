---
title: '[ファイルシステムタスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e893f667c2a32fbc667c375dc57647d1aff1b806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741137"
---
# <a name="file-system-task-editor-general-page"></a><span data-ttu-id="b8bcd-102">[ファイル システム タスク エディター] \([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-102">File System Task Editor (General Page)</span></span>
  <span data-ttu-id="b8bcd-103">**[ファイル システム タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクで実行するファイル システム操作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-103">Use the **General** page of the **File System Task Editor** dialog to configure the file system operation that the task performs.</span></span>  
  
 <span data-ttu-id="b8bcd-104">このタスクの詳細については、「 [File System Task](control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-104">To learn about this task, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="b8bcd-105">SourceConnection プロパティと DestinationConnection プロパティを設定して、ソースとターゲットの接続マネージャーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-105">You must specify a source and destination connection manager by setting the SourceConnection and DestinationConnection properties.</span></span> <span data-ttu-id="b8bcd-106">タスクでソースまたはターゲットとして使用されるファイルを指すファイル接続マネージャーの名前を指定することも、ファイルのパスが変数に格納されていれば変数の名前を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-106">You can either provide the names of File connection managers that point to the files that the task uses as a source or destination, or if the paths of the files are stored in variables, you can provide the names of the variables.</span></span> <span data-ttu-id="b8bcd-107">変数を使用してファイル パスを保存するには、最初に、IsSourcePathVariable オプション (ソース接続) および IsDestinationPatheVariable オプション (ターゲット接続) を **True**に設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-107">To use variables to store the file paths, you must set first set the IsSourcePathVariable option for the source connection and the IsDestinationPatheVariable option for the destination connection to **True**.</span></span> <span data-ttu-id="b8bcd-108">その後で、既存のシステム変数またはユーザー定義変数を選択するか、新しい変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-108">You can then choose the existing system or user-defined variables to use, or you can create new variables.</span></span> <span data-ttu-id="b8bcd-109">変数のスコープは、 **[変数の追加]** ダイアログ ボックスで構成および指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-109">In the **Add Variable** dialog box, you can configure and specify the scope of the variables.</span></span> <span data-ttu-id="b8bcd-110">スコープは、ファイル システム タスクまたは親コンテナーにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-110">The scope must be the File System task or a parent container.</span></span> <span data-ttu-id="b8bcd-111">詳細については、「[Integration Services (SSIS) Variables](integration-services-ssis-variables.md)」(Integration Services (SSIS) の変数) と「[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)」(パッケージで変数を使用する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-111">For more information see, [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8bcd-112">プロパティとプロパティに対して選択した変数をオーバーライドするには、 `SourceConnection` `DestinationConnection` **Source**プロパティと**Destination**プロパティに式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-112">To override the variables you selected for the `SourceConnection` and `DestinationConnection` properties, enter an expression for the **Source** and **Destination** properties.</span></span> <span data-ttu-id="b8bcd-113">式は、 **ファイル システム タスク エディター** の **[式]** ページで入力します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-113">You enter expressions on the **Expressions** page of the **File System Task Editor**.</span></span> <span data-ttu-id="b8bcd-114">たとえば、タスクで変換先として使用するファイルのパスを設定するには、特定の状況下では変数 A、別の状況下では変数 B を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-114">For example, to set the path of the files that the task uses as a destination, you may want to use variable A under certain conditions and use variable B under other conditions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8bcd-115">ファイル システム タスクは、1 つのファイルまたはディレクトリのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-115">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="b8bcd-116">したがって、このタスクでは、ワイルドカード文字を使用して複数のファイルまたはディレクトリに同じ処理を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-116">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files or directories.</span></span> <span data-ttu-id="b8bcd-117">ファイル システム タスクが複数のファイルやディレクトリに対して同じ処理を繰り返し行うようにするには、ファイル システム タスクを Foreach ループ コンテナー内に配置します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-117">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container.</span></span> <span data-ttu-id="b8bcd-118">詳細については、「 [File System Task](control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-118">For more information, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="b8bcd-119">さまざまな変数を使用する式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-119">You can use expressions to use different variables for the</span></span>  
  
## <a name="options"></a><span data-ttu-id="b8bcd-120">Options</span><span class="sxs-lookup"><span data-stu-id="b8bcd-120">Options</span></span>  
 <span data-ttu-id="b8bcd-121">**[IsDestinationPathVariable]**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-121">**IsDestinationPathVariable**</span></span>  
 <span data-ttu-id="b8bcd-122">対象になるパスを変数に格納するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-122">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="b8bcd-123">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-123">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b8bcd-124">値</span><span class="sxs-lookup"><span data-stu-id="b8bcd-124">Value</span></span>|<span data-ttu-id="b8bcd-125">説明</span><span class="sxs-lookup"><span data-stu-id="b8bcd-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8bcd-126">**True**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-126">**True**</span></span>|<span data-ttu-id="b8bcd-127">対象になるパスは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-127">The destination path is stored in a variable.</span></span> <span data-ttu-id="b8bcd-128">この値を選択すると、動的オプション **[DestinationVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-128">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
|<span data-ttu-id="b8bcd-129">**False**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-129">**False**</span></span>|<span data-ttu-id="b8bcd-130">対象になるパスは、ファイル接続マネージャーで指定されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-130">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="b8bcd-131">この値を選択すると、動的オプションの [] が表示され `DestinationConnection` ます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-131">Selecting this value displays the dynamic option, `DestinationConnection`.</span></span>|  
  
 <span data-ttu-id="b8bcd-132">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-132">**OverwriteDestination**</span></span>  
 <span data-ttu-id="b8bcd-133">操作によって対象になるディレクトリ内のファイルを上書きできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-133">Specify whether the operation can overwrite files in the destination directory.</span></span>  
  
 <span data-ttu-id="b8bcd-134">**名前**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-134">**Name**</span></span>  
 <span data-ttu-id="b8bcd-135">ファイル システム タスクの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-135">Provide a unique name for the File System task.</span></span> <span data-ttu-id="b8bcd-136">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-136">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8bcd-137">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-137">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="b8bcd-138">**説明**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-138">**Description**</span></span>  
 <span data-ttu-id="b8bcd-139">ファイル システム タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-139">Type a description of the File System task.</span></span>  
  
 <span data-ttu-id="b8bcd-140">**操作**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-140">**Operation**</span></span>  
 <span data-ttu-id="b8bcd-141">実行するファイル システム操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-141">Select the file-system operation to perform.</span></span> <span data-ttu-id="b8bcd-142">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-142">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b8bcd-143">値</span><span class="sxs-lookup"><span data-stu-id="b8bcd-143">Value</span></span>|<span data-ttu-id="b8bcd-144">説明</span><span class="sxs-lookup"><span data-stu-id="b8bcd-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8bcd-145">**ディレクトリのコピー**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-145">**Copy directory**</span></span>|<span data-ttu-id="b8bcd-146">ディレクトリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-146">Copy a directory.</span></span> <span data-ttu-id="b8bcd-147">この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-147">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="b8bcd-148">**ファイルのコピー**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-148">**Copy file**</span></span>|<span data-ttu-id="b8bcd-149">ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-149">Copy a file.</span></span> <span data-ttu-id="b8bcd-150">この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-150">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="b8bcd-151">**ディレクトリの作成**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-151">**Create directory**</span></span>|<span data-ttu-id="b8bcd-152">ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-152">Create a directory.</span></span> <span data-ttu-id="b8bcd-153">この値を選択すると、ソース ディレクトリとターゲット ディレクトリを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-153">Selecting this value displays the dynamic options for a source and a destination directory.</span></span>|  
|<span data-ttu-id="b8bcd-154">**ディレクトリの削除**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-154">**Delete directory**</span></span>|<span data-ttu-id="b8bcd-155">ディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-155">Delete a directory.</span></span> <span data-ttu-id="b8bcd-156">この値を選択すると、ソースを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-156">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="b8bcd-157">**ディレクトリ コンテンツの削除**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-157">**Delete directory content**</span></span>|<span data-ttu-id="b8bcd-158">ディレクトリのコンテンツを削除します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-158">Delete the content of a directory.</span></span> <span data-ttu-id="b8bcd-159">この値を選択すると、ソースを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-159">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="b8bcd-160">**ファイルの削除**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-160">**Delete file**</span></span>|<span data-ttu-id="b8bcd-161">ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-161">Delete a file.</span></span> <span data-ttu-id="b8bcd-162">この値を選択すると、ソースを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-162">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="b8bcd-163">**ディレクトリの移動**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-163">**Move directory**</span></span>|<span data-ttu-id="b8bcd-164">ディレクトリを移動します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-164">Move a directory.</span></span> <span data-ttu-id="b8bcd-165">この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-165">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="b8bcd-166">**ファイルの移動**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-166">**Move file**</span></span>|<span data-ttu-id="b8bcd-167">ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-167">Move a file.</span></span> <span data-ttu-id="b8bcd-168">この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-168">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="b8bcd-169">注: ファイルを移動する場合は、保存先として指定するディレクトリパスにファイル名を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-169">Note: When moving a file, do not include a file name in the directory path that you provide as the destination.</span></span>|  
|<span data-ttu-id="b8bcd-170">**ファイル名の変更**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-170">**Rename file**</span></span>|<span data-ttu-id="b8bcd-171">ファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-171">Rename a file.</span></span> <span data-ttu-id="b8bcd-172">この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-172">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="b8bcd-173">注: ファイルの名前を変更する場合は、変換先に指定するディレクトリパスに新しいファイル名を含めます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-173">Note: When renaming a file, include the new file name in the directory path that you provide for the destination.</span></span>|  
|<span data-ttu-id="b8bcd-174">**属性の設定**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-174">**Set attributes**</span></span>|<span data-ttu-id="b8bcd-175">ファイルまたはディレクトリの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-175">Set the attributes of a file or directory.</span></span> <span data-ttu-id="b8bcd-176">この値を選択すると、ソースと操作を指定するための動的オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-176">Selecting this value displays the dynamic options for a source and operation.</span></span>|  
  
 `IsSourcePathVariable`  
 <span data-ttu-id="b8bcd-177">対象になるパスを変数に格納するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-177">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="b8bcd-178">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-178">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b8bcd-179">値</span><span class="sxs-lookup"><span data-stu-id="b8bcd-179">Value</span></span>||  
|-----------|-|  
|<span data-ttu-id="b8bcd-180">**True**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-180">**True**</span></span>|<span data-ttu-id="b8bcd-181">対象になるパスは変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-181">The destination path is stored in a variable.</span></span> <span data-ttu-id="b8bcd-182">この値を選択すると、動的オプション **[SourceVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-182">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
|<span data-ttu-id="b8bcd-183">**False**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-183">**False**</span></span>|<span data-ttu-id="b8bcd-184">対象になるパスは、ファイル接続マネージャーで指定されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-184">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="b8bcd-185">この値を選択すると、動的オプション **[DestinationVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-185">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a><span data-ttu-id="b8bcd-186">[IsDestinationPathVariable] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="b8bcd-186">IsDestinationPathVariable Dynamic Options</span></span>  
  
### <a name="isdestinationpathvariable--true"></a><span data-ttu-id="b8bcd-187">[IsDestinationPathVariable] = [True]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-187">IsDestinationPathVariable = True</span></span>  
 <span data-ttu-id="b8bcd-188">**[DestinationVariable]**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-188">**DestinationVariable**</span></span>  
 <span data-ttu-id="b8bcd-189">一覧から変数名を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-189">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b8bcd-190">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-190">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="isdestinationpathvariable--false"></a><span data-ttu-id="b8bcd-191">[IsDestinationPathVariable] = [False]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-191">IsDestinationPathVariable = False</span></span>  
 `DestinationConnection`  
 <span data-ttu-id="b8bcd-192">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-192">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b8bcd-193">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-193">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="issourcepathvariable-dynamic-options"></a><span data-ttu-id="b8bcd-194">[IsSourcePathVariable] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="b8bcd-194">IsSourcePathVariable Dynamic Options</span></span>  
  
### <a name="issourcepathvariable--true"></a><span data-ttu-id="b8bcd-195">[IsSourcePathVariable] = [True]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-195">IsSourcePathVariable = True</span></span>  
 <span data-ttu-id="b8bcd-196">**[SourceVariable]**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-196">**SourceVariable**</span></span>  
 <span data-ttu-id="b8bcd-197">一覧から変数名を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-197">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b8bcd-198">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-198">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="issourcepathvariable--false"></a><span data-ttu-id="b8bcd-199">[IsSourcePathVariable] = [False]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-199">IsSourcePathVariable = False</span></span>  
 `SourceConnection`  
 <span data-ttu-id="b8bcd-200">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-200">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b8bcd-201">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-201">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="operation-dynamic-options"></a><span data-ttu-id="b8bcd-202">[Operation] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="b8bcd-202">Operation Dynamic Options</span></span>  
  
### <a name="operation--set-attributes"></a><span data-ttu-id="b8bcd-203">[Operation] = [属性の設定]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-203">Operation = Set Attributes</span></span>  
 <span data-ttu-id="b8bcd-204">**[非表示]**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-204">**Hidden**</span></span>  
 <span data-ttu-id="b8bcd-205">ファイルまたはディレクトリを表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-205">Indicate whether the file or directory is visible.</span></span>  
  
 <span data-ttu-id="b8bcd-206">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-206">**ReadOnly**</span></span>  
 <span data-ttu-id="b8bcd-207">ファイルが読み取り専用かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-207">Indicate whether the file is read-only.</span></span>  
  
 <span data-ttu-id="b8bcd-208">**Archive**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-208">**Archive**</span></span>  
 <span data-ttu-id="b8bcd-209">ファイルまたはディレクトリをアーカイブするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-209">Indicate whether the file or directory is ready for archiving.</span></span>  
  
 <span data-ttu-id="b8bcd-210">**システム**</span><span class="sxs-lookup"><span data-stu-id="b8bcd-210">**System**</span></span>  
 <span data-ttu-id="b8bcd-211">ファイルがオペレーティング システム ファイルかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-211">Indicate whether the file is an operating system file.</span></span>  
  
### <a name="operation--create-directory"></a><span data-ttu-id="b8bcd-212">[Operation] = [ディレクトリの作成]</span><span class="sxs-lookup"><span data-stu-id="b8bcd-212">Operation = Create directory</span></span>  
 `UseDirectoryIfExists`  
 <span data-ttu-id="b8bcd-213">**[ディレクトリの作成]** 操作で、新しいディレクトリを作成せずに、指定された名前の既存のディレクトリを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8bcd-213">Indicates whether the **Create directory** operation uses an existing directory with the specified name instead of creating a new directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8bcd-214">参照</span><span class="sxs-lookup"><span data-stu-id="b8bcd-214">See Also</span></span>  
 <span data-ttu-id="b8bcd-215">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8bcd-215">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b8bcd-216">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="b8bcd-216">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
