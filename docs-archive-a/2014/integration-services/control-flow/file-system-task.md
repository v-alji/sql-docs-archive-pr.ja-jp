---
title: ファイル システム タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce3d31ceb720704fb61c33043a4c7319607caff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631205"
---
# <a name="file-system-task"></a><span data-ttu-id="75594-102">ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="75594-102">File System Task</span></span>
  <span data-ttu-id="75594-103">ファイル システム タスクは、ファイル システム内のファイルとディレクトリの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="75594-103">The File System task performs operations on files and directories in the file system.</span></span> <span data-ttu-id="75594-104">たとえば、ファイル システム タスクを使用すると、パッケージはディレクトリやファイルの作成、移動、または削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="75594-104">For example, by using the File System task, a package can create, move, or delete directories and files.</span></span> <span data-ttu-id="75594-105">また、ファイル システム タスクを使用して、ファイルやディレクトリの属性を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="75594-105">You can also use the File System task to set attributes on files and directories.</span></span> <span data-ttu-id="75594-106">たとえば、ファイル システム タスクを使用すると、ファイルを非表示にしたり読み取り専用にできます。</span><span class="sxs-lookup"><span data-stu-id="75594-106">For example, the File System task can make files hidden or read-only.</span></span>  
  
 <span data-ttu-id="75594-107">ファイル システム タスクのすべての操作では、ファイルまたはディレクトリをソースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="75594-107">All File System task operations use a source, which can be a file or a directory.</span></span> <span data-ttu-id="75594-108">たとえば、タスクによりコピーされるファイルや、タスクにより削除されるディレクトリは、ソースと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="75594-108">For example, the file that the task copies or the directory it deletes is a source.</span></span> <span data-ttu-id="75594-109">ソースを指定するには、ファイル接続マネージャーを使用してディレクトリまたはファイルをポイントするか、ソースへのパスが含まれる変数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="75594-109">The source can be specified by using a File connection manager that points to the directory or file or by providing the name of a variable that contains the source path.</span></span> <span data-ttu-id="75594-110">詳細については、「[ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」および「[Integration Services (SSIS) の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75594-110">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="75594-111">ファイルやディレクトリをコピーまたは移動する操作、およびファイルの名前を変更する操作では、その操作の出力先となるファイルまたはディレクトリと、基になるファイルまたはディレクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="75594-111">The operations that copy and move file and directories and rename files use a destination and a source.</span></span> <span data-ttu-id="75594-112">操作の出力先となるファイルまたはディレクトリは、ファイル接続マネージャーまたは変数を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="75594-112">The destination is specified by using a File connection manager or a variable.</span></span> <span data-ttu-id="75594-113">ファイル システム タスクの操作は、出力先のファイルやディレクトリの上書きを許可するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="75594-113">File system task operations can be configured to permit overwriting of destination files and directories.</span></span> <span data-ttu-id="75594-114">新しいディレクトリを作成する操作は、そのディレクトリが既に存在していても失敗するのではなく、指定した名前の既存のディレクトリが使用されるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="75594-114">The operation that creates a new directory can be configured to use an existing directory that has the specified name instead of failing when the directory already exists.</span></span>  
  
## <a name="predefined-file-system-operations"></a><span data-ttu-id="75594-115">定義済みのファイル システム操作</span><span class="sxs-lookup"><span data-stu-id="75594-115">Predefined File System Operations</span></span>  
 <span data-ttu-id="75594-116">ファイル システム タスクには、定義済みの操作のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="75594-116">The File System task includes a predefined set of operations.</span></span> <span data-ttu-id="75594-117">次の表では、これらの操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="75594-117">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="75594-118">Operation</span><span class="sxs-lookup"><span data-stu-id="75594-118">Operation</span></span>|<span data-ttu-id="75594-119">説明</span><span class="sxs-lookup"><span data-stu-id="75594-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75594-120">ディレクトリのコピー</span><span class="sxs-lookup"><span data-stu-id="75594-120">Copy directory</span></span>|<span data-ttu-id="75594-121">ある場所から別の場所にフォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="75594-121">Copies a folder from one location to another.</span></span>|  
|<span data-ttu-id="75594-122">ファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="75594-122">Copy file</span></span>|<span data-ttu-id="75594-123">ある場所から別の場所にファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="75594-123">Copies a file from one location to another.</span></span>|  
|<span data-ttu-id="75594-124">ディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="75594-124">Create directory</span></span>|<span data-ttu-id="75594-125">指定した場所にフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="75594-125">Creates a folder in a specified location.</span></span>|  
|<span data-ttu-id="75594-126">ディレクトリの削除</span><span class="sxs-lookup"><span data-stu-id="75594-126">Delete directory</span></span>|<span data-ttu-id="75594-127">指定した場所のフォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="75594-127">Deletes a folder in a specified location.</span></span>|  
|<span data-ttu-id="75594-128">ディレクトリ コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="75594-128">Delete directory content</span></span>|<span data-ttu-id="75594-129">フォルダー内のすべてのファイルおよびフォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="75594-129">Deletes all files and folders in a folder.</span></span>|  
|<span data-ttu-id="75594-130">ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="75594-130">Delete file</span></span>|<span data-ttu-id="75594-131">指定した場所のファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="75594-131">Deletes a file in a specified location.</span></span>|  
|<span data-ttu-id="75594-132">ディレクトリの移動</span><span class="sxs-lookup"><span data-stu-id="75594-132">Move directory</span></span>|<span data-ttu-id="75594-133">ある場所から別の場所にフォルダーを移動します。</span><span class="sxs-lookup"><span data-stu-id="75594-133">Moves a folder from one location to another.</span></span>|  
|<span data-ttu-id="75594-134">ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="75594-134">Move file</span></span>|<span data-ttu-id="75594-135">ある場所から別の場所にファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="75594-135">Moves a file from one location to another.</span></span>|  
|<span data-ttu-id="75594-136">ファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="75594-136">Rename file</span></span>|<span data-ttu-id="75594-137">指定した場所にあるファイル名を変更します。</span><span class="sxs-lookup"><span data-stu-id="75594-137">Renames a file in a specified location.</span></span>|  
|<span data-ttu-id="75594-138">属性の設定</span><span class="sxs-lookup"><span data-stu-id="75594-138">Set attributes</span></span>|<span data-ttu-id="75594-139">ファイルやディレクトリの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="75594-139">Sets attributes on files and folders.</span></span> <span data-ttu-id="75594-140">属性には、アーカイブ、非表示、標準、読み取り専用、およびシステムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="75594-140">Attributes include Archive, Hidden, Normal, ReadOnly, and System.</span></span> <span data-ttu-id="75594-141">標準には属性がなく、他の属性と組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="75594-141">Normal is the lack of attributes, and it cannot be combined with other attributes.</span></span> <span data-ttu-id="75594-142">他のすべての属性は、組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="75594-142">All other attributes can be used in combination.</span></span>|  
  
 <span data-ttu-id="75594-143">ファイル システム タスクは、1 つのファイルまたはディレクトリのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="75594-143">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="75594-144">したがって、このタスクでは、ワイルドカード文字を使用して複数のファイルに同じ処理を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="75594-144">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files.</span></span> <span data-ttu-id="75594-145">ファイル システム タスクが複数のファイルやディレクトリに対して同じ処理を繰り返し行うようにするには、次の手順に示すように、ファイル システム タスクを Foreach ループ コンテナー内に配置します。</span><span class="sxs-lookup"><span data-stu-id="75594-145">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container, as described in the following steps:</span></span>  
  
-   <span data-ttu-id="75594-146">**Foreach ループ コンテナーの構成** [Foreach ループ エディター] の **[コレクション]** ページで **[Foreach File 列挙子]** に列挙子を設定して、 **[ファイル]** の列挙子の構成としてワイルドカード式を入力します。</span><span class="sxs-lookup"><span data-stu-id="75594-146">**Configure the Foreach Loop container** On the **Collection** page of the Foreach Loop Editor, set the enumerator to **Foreach File Enumerator** and enter the wildcard expression as the enumerator configuration for **Files**.</span></span> <span data-ttu-id="75594-147">[Foreach ループ エディター] の **[変数のマッピング]** ページで、ファイル名を一度に 1 つずつファイル システム タスクに渡すために使用する変数をマップします。</span><span class="sxs-lookup"><span data-stu-id="75594-147">On the **Variable Mappings** page of the Foreach Loop Editor, map a variable that you want to use to pass the file names one at a time to the File System task.</span></span>  
  
-   <span data-ttu-id="75594-148">**ファイル システム タスクの追加と構成** ファイル システム タスクを Foreach ループ コンテナーに追加します。</span><span class="sxs-lookup"><span data-stu-id="75594-148">**Add and configure a File System task** Add a File System task to the Foreach Loop container.</span></span> <span data-ttu-id="75594-149">[ファイル システム タスク エディター] の **[全般]** ページで、 **SourceVariable** プロパティまたは **DestinationVariable** プロパティに、Foreach ループ コンテナーで定義した変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="75594-149">On the **General** page of the File System Task Editor, set the **SourceVariable** or **DestinationVariable** property to the variable that you defined in the Foreach Loop container.</span></span>  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a><span data-ttu-id="75594-150">ファイル システム タスクで使用できるカスタム ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="75594-150">Custom Log Entries Available on the File System Task</span></span>  
 <span data-ttu-id="75594-151">次の表では、ファイル システム タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="75594-151">The following table describes the custom log entry for the File System task.</span></span> <span data-ttu-id="75594-152">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75594-152">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="75594-153">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="75594-153">Log entry</span></span>|<span data-ttu-id="75594-154">説明</span><span class="sxs-lookup"><span data-stu-id="75594-154">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="75594-155">タスクで実行される操作を報告します。</span><span class="sxs-lookup"><span data-stu-id="75594-155">Reports the operation that the task performs.</span></span> <span data-ttu-id="75594-156">ログ エントリは、ファイル システム操作の開始時に書き込まれます。これには、操作の基になるファイルと操作対象のファイルに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="75594-156">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
## <a name="configuring-the-file-system-task"></a><span data-ttu-id="75594-157">ファイル システム タスクの構成</span><span class="sxs-lookup"><span data-stu-id="75594-157">Configuring the File System Task</span></span>  
 <span data-ttu-id="75594-158">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="75594-158">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="75594-159">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75594-159">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   <span data-ttu-id="75594-160">[[ファイル システム タスク エディター]\([全般] ページ)](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="75594-160">[File System Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="75594-161">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="75594-161">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="75594-162">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75594-162">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="75594-163">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="75594-163">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
 <span data-ttu-id="75594-164">プログラムでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75594-164">For more information about how to set these properties programmatically, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="75594-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="75594-165">Related Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="75594-166">には、データ ファイルをダウンロードまたはアップロードし、サーバー上のディレクトリを管理するタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="75594-166">includes a task that downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="75594-167">詳細については、「 [FTP タスク](ftp-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75594-167">For more information, see [FTP Task](ftp-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75594-168">参照</span><span class="sxs-lookup"><span data-stu-id="75594-168">See Also</span></span>  
 <span data-ttu-id="75594-169">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="75594-169">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="75594-170">制御フロー</span><span class="sxs-lookup"><span data-stu-id="75594-170">Control Flow</span></span>](control-flow.md)  
  
  
