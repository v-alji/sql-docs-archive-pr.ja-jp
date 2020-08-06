---
title: FTP タスク | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.f1
helpviewer_keywords:
- FTP task [Integration Services]
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63ec58c1bff9894d0aa73112686c4b1fe9421b98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631198"
---
# <a name="ftp-task"></a><span data-ttu-id="bc30d-102">FTP タスク</span><span class="sxs-lookup"><span data-stu-id="bc30d-102">FTP Task</span></span>
  <span data-ttu-id="bc30d-103">FTP タスクは、データ ファイルをダウンロードまたはアップロードし、サーバー上のディレクトリを管理します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-103">The FTP task downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="bc30d-104">たとえば、パッケージは、リモート サーバーまたはインターネット サイトから、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ワークフローの一部としてデータ ファイルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-104">For example, a package can download data files from a remote server or an Internet location as part of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="bc30d-105">FTP タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-105">You can use the FTP task for the following purposes:</span></span>  
  
-   <span data-ttu-id="bc30d-106">データを移動し、変換をデータに適用する前または後で、あるディレクトリから別のディレクトリに、ディレクトリやデータ ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="bc30d-106">Copying directories and data files from one directory to another, before or after moving data, and applying transformations to the data.</span></span>  
  
-   <span data-ttu-id="bc30d-107">コピー元の FTP サイトにログインし、ファイルやパッケージをコピー先のディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="bc30d-107">Logging in to a source FTP location and copying files or packages to a destination directory.</span></span>  
  
-   <span data-ttu-id="bc30d-108">データをデータベースに読み込む前に、FTP サイトからファイルをダウンロードし、変換を列データに適用します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-108">Downloading files from an FTP location and applying transformations to column data before loading the data into a database.</span></span>  
  
 <span data-ttu-id="bc30d-109">実行時には、FTP タスクは FTP 接続マネージャーを使用してサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-109">At run time, the FTP task connects to a server by using an FTP connection manager.</span></span> <span data-ttu-id="bc30d-110">FTP 接続マネージャーは、FTP タスクとは別に構成され、FTP タスク内で参照されます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-110">The FTP connection manager is configured separately from the FTP task, and then is referenced in the FTP task.</span></span> <span data-ttu-id="bc30d-111">FTP 接続マネージャーには、サーバーの設定、FTP サーバーへのアクセス資格情報、および、サーバーへの接続のタイムアウトや再試行回数などのオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc30d-111">The FTP connection manager includes the server settings, the credentials for accessing the FTP server, and options such as the time-out and the number of retries for connecting to the server.</span></span> <span data-ttu-id="bc30d-112">詳細については、「 [FTP 接続マネージャー](../connection-manager/ftp-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-112">For more information, see [FTP Connection Manager](../connection-manager/ftp-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc30d-113">FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bc30d-113">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="bc30d-114">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bc30d-114">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="bc30d-115">ローカル ファイルまたはローカル ディレクトリにアクセスする場合、FTP タスクは、ファイル接続マネージャー、または変数に格納されたパス情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-115">When accessing a local file or a local directory, the FTP task uses a File connection manager or path information stored in a variable.</span></span> <span data-ttu-id="bc30d-116">それに対し、リモート ファイルまたはリモート ディレクトリにアクセスする場合、FTP タスクは、FTP 接続マネージャーで直接指定されたリモート サーバーのパス、または変数に格納されたパス情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-116">In contrast, when accessing a remote file or a remote directory, the FTP task uses a directly specified path on the remote server, as specified in the FTP connection manager, or path information stored in a variable.</span></span> <span data-ttu-id="bc30d-117">詳細については、「[ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」および「[Integration Services (SSIS) の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-117">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="bc30d-118">したがって、FTP タスクは複数のファイルを受信し、複数のリモート ファイルを削除できます。ただし、FTP タスクが接続マネージャーを使用している場合には、1 つのファイルのみを送信し、1 つのローカル ファイルのみを削除できます。ファイル接続マネージャーがアクセスできるのは 1 ファイルのみであるためです。</span><span class="sxs-lookup"><span data-stu-id="bc30d-118">This means that the FTP task can receive multiple files and delete multiple remote files; but the task can send only one file and delete only one local file if it uses a connection manager, because a File connection manager can access only one file.</span></span> <span data-ttu-id="bc30d-119">複数のローカル ファイルにアクセスするには、FTP タスクで変数を使用してパス情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc30d-119">To access multiple local files, the FTP task must use a variable to provide the path information.</span></span> <span data-ttu-id="bc30d-120">たとえば、"C:\Test\\*.txt" を含む変数は、Test ディレクトリ内で .txt 拡張子を持つすべてのファイルの削除または送信をサポートするパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-120">For example, a variable that contains "C:\Test\\*.txt" provides a path that supports deleting or sending all the files that have a .txt extension in the Test directory.</span></span>  
  
 <span data-ttu-id="bc30d-121">複数のファイルを送信したり、複数のローカル ファイルまたはディレクトリにアクセスするには、Foreach ループに FTP タスクを含めて、複数回実行する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="bc30d-121">To send multiple files and access multiple local files and directories, you can also execute the FTP task multiple times by including the task in a Foreach Loop.</span></span> <span data-ttu-id="bc30d-122">Foreach ループは、For Each File 列挙子を使用して、ディレクトリ内のファイル全体を列挙します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-122">The Foreach Loop can enumerate across files in a directory using the For Each File enumerator.</span></span> <span data-ttu-id="bc30d-123">詳細については、「 [Foreach ループ コンテナー](foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-123">For more information, see [Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="bc30d-124">FTP タスクでは、パス内で *?*</span><span class="sxs-lookup"><span data-stu-id="bc30d-124">The FTP task supports the *?*</span></span> <span data-ttu-id="bc30d-125">および *\** ワイルドカード文字がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-125">and *\** wildcard characters in paths.</span></span> <span data-ttu-id="bc30d-126">これによってタスクは複数のファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-126">This lets the task access multiple files.</span></span> <span data-ttu-id="bc30d-127">ただし、ワイルドカードが使用できるのは、パスのファイル名を指定する部分のみです。</span><span class="sxs-lookup"><span data-stu-id="bc30d-127">However, you can use wildcard characters only in the part of the path that specifies the file name.</span></span> <span data-ttu-id="bc30d-128">たとえば、C:\MyDirectory\\*.txt は有効なパスですが、C:\\\*\MyText.txt は無効なパスです。</span><span class="sxs-lookup"><span data-stu-id="bc30d-128">For example, C:\MyDirectory\\*.txt is a valid path, but C:\\\*\MyText.txt is not.</span></span>  
  
 <span data-ttu-id="bc30d-129">操作に失敗した場合にファイル システムに関するタスクを停止したり、ファイルを ASCII モードで転送するように FTP 操作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-129">The FTP operations can be configured to stop the File System task when the operation fails, or to transfer files in ASCII mode.</span></span> <span data-ttu-id="bc30d-130">ファイルのコピーを送受信する操作は、コピー先のファイルおよびディレクトリを上書きするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="bc30d-130">The operations that send and receive files copy can be configured to overwrite destination files and directories.</span></span>  
  
## <a name="predefined-ftp-operations"></a><span data-ttu-id="bc30d-131">定義済みの FTP 操作</span><span class="sxs-lookup"><span data-stu-id="bc30d-131">Predefined FTP Operations</span></span>  
 <span data-ttu-id="bc30d-132">FTP タスクには、定義済みの操作のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc30d-132">The FTP task includes a predefined set of operations.</span></span> <span data-ttu-id="bc30d-133">次の表では、これらの操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-133">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="bc30d-134">Operation</span><span class="sxs-lookup"><span data-stu-id="bc30d-134">Operation</span></span>|<span data-ttu-id="bc30d-135">説明</span><span class="sxs-lookup"><span data-stu-id="bc30d-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc30d-136">ファイルの送信</span><span class="sxs-lookup"><span data-stu-id="bc30d-136">Send files</span></span>|<span data-ttu-id="bc30d-137">ローカル コンピューターのファイルを FTP サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-137">Sends a file from the local computer to the FTP server.</span></span>|  
|<span data-ttu-id="bc30d-138">ファイルの受信</span><span class="sxs-lookup"><span data-stu-id="bc30d-138">Receive files</span></span>|<span data-ttu-id="bc30d-139">FTP サーバーのファイルをローカル コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-139">Saves a file from the FTP server to the local computer.</span></span>|  
|<span data-ttu-id="bc30d-140">ローカル ディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="bc30d-140">Create local directory</span></span>|<span data-ttu-id="bc30d-141">ローカル コンピューター上にフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-141">Creates a folder on the local computer.</span></span>|  
|<span data-ttu-id="bc30d-142">リモート ディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="bc30d-142">Create remote directory</span></span>|<span data-ttu-id="bc30d-143">FTP サーバー上にフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-143">Creates a folder on the FTP server.</span></span>|  
|<span data-ttu-id="bc30d-144">ローカル ディレクトリの削除</span><span class="sxs-lookup"><span data-stu-id="bc30d-144">Remove local directory</span></span>|<span data-ttu-id="bc30d-145">ローカル コンピューター上のフォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-145">Deletes a folder on the local computer.</span></span>|  
|<span data-ttu-id="bc30d-146">リモート ディレクトリの削除</span><span class="sxs-lookup"><span data-stu-id="bc30d-146">Remove remote directory</span></span>|<span data-ttu-id="bc30d-147">FTP サーバー上のフォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-147">Deletes a folder on the FTP server.</span></span>|  
|<span data-ttu-id="bc30d-148">ローカル ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="bc30d-148">Delete local files</span></span>|<span data-ttu-id="bc30d-149">ローカル コンピューターのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-149">Deletes a file on the local computer.</span></span>|  
|<span data-ttu-id="bc30d-150">リモート ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="bc30d-150">Delete remote files</span></span>|<span data-ttu-id="bc30d-151">FTP サーバーのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-151">Deletes a file on the FTP server.</span></span>|  
  
## <a name="custom-log-entries-available-on-the-ftp-task"></a><span data-ttu-id="bc30d-152">FTP タスクで使用できるカスタム ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="bc30d-152">Custom Log Entries Available on the FTP Task</span></span>  
 <span data-ttu-id="bc30d-153">次の表は、FTP タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="bc30d-153">The following table lists the custom log entries for the FTP task.</span></span> <span data-ttu-id="bc30d-154">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-154">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="bc30d-155">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="bc30d-155">Log entry</span></span>|<span data-ttu-id="bc30d-156">説明</span><span class="sxs-lookup"><span data-stu-id="bc30d-156">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="bc30d-157">タスクで FTP サーバーへの接続が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-157">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="bc30d-158">タスクで実行された FTP 操作の開始および種類を報告します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-158">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="bc30d-159">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bc30d-159">Related Tasks</span></span>  
 <span data-ttu-id="bc30d-160">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="bc30d-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bc30d-161">これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-161">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="bc30d-162">プログラムによってこれらのプロパティを設定する方法の詳細については、「 <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc30d-162">For more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc30d-163">参照</span><span class="sxs-lookup"><span data-stu-id="bc30d-163">See Also</span></span>  
 <span data-ttu-id="bc30d-164">[FTP タスクエディター &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bc30d-164">[FTP Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bc30d-165">[FTP タスクエディター &#40;ファイル転送ページ&#41;](../ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="bc30d-165">[FTP Task Editor &#40;File Transfer Page&#41;](../ftp-task-editor-file-transfer-page.md) </span></span>  
 <span data-ttu-id="bc30d-166">[Integration Services タスク](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bc30d-166">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="bc30d-167">制御フロー</span><span class="sxs-lookup"><span data-stu-id="bc30d-167">Control Flow</span></span>](control-flow.md)  
  
  
