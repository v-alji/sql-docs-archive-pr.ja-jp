---
title: スクリプト タスクの例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 920d2ee5cc2e64db1048d10522d9be644794e55b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716414"
---
# <a name="script-task-examples"></a><span data-ttu-id="e0c73-102">スクリプト タスクの例</span><span class="sxs-lookup"><span data-stu-id="e0c73-102">Script Task Examples</span></span>
  <span data-ttu-id="e0c73-103">スクリプト タスクは複数の用途を持つツールで、パッケージで使用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に組み込まれているタスクでは満たせないほとんどすべての要件を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="e0c73-103">The Script task is a multi-purpose tool that you can use in a package to fill almost any requirement that is not met by the tasks included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="e0c73-104">このトピックでは、使用できる機能の一部を示すスクリプト タスクのコード例について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-104">This topic lists Script task code samples that demonstrate some of the available functionality.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0c73-105">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、これらのスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="e0c73-105">If you want to create tasks that you can more easily reuse across multiple packages, consider using the code in these Script task samples as the starting point for custom tasks.</span></span> <span data-ttu-id="e0c73-106">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c73-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0c73-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e0c73-107">In This Section</span></span>  
  
### <a name="example-topics"></a><span data-ttu-id="e0c73-108">コード例のトピック</span><span class="sxs-lookup"><span data-stu-id="e0c73-108">Example Topics</span></span>  
 <span data-ttu-id="e0c73-109">このセクションに含まれるコード例では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] スクリプト タスクに組み込むことができる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] クラスのさまざまな使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-109">This section contains code examples that demonstrate various uses of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that you can incorporate into an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task:</span></span>  
  
 [<span data-ttu-id="e0c73-110">スクリプト タスクによる空のフラット ファイルの検出</span><span class="sxs-lookup"><span data-stu-id="e0c73-110">Detecting an Empty Flat File with the Script Task</span></span>](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 <span data-ttu-id="e0c73-111">フラット ファイルをチェックして、データ行が含まれているかどうかを判別し、結果を変数に保存して制御フローの分岐で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e0c73-111">Checks a flat file to determine whether it contains rows of data, and saves the result to a variable for use in control flow branching.</span></span>  
  
 [<span data-ttu-id="e0c73-112">スクリプト タスクによる ForEach ループの一覧の収集</span><span class="sxs-lookup"><span data-stu-id="e0c73-112">Gathering a List for the ForEach Loop with the Script Task</span></span>](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 <span data-ttu-id="e0c73-113">ユーザー指定条件に適合するファイルのリストを収集し、後に Foreach from Variable 列挙子で使用できるように変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-113">Gathers a list of files that meet user-specified criteria, and populates a variable for later use by the Foreach from Variable Enumerator.</span></span>  
  
 [<span data-ttu-id="e0c73-114">スクリプト タスクによる Active Directory へのクエリの実行</span><span class="sxs-lookup"><span data-stu-id="e0c73-114">Querying the Active Directory with the Script Task</span></span>](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 <span data-ttu-id="e0c73-115">System.DirectoryServices 名前空間のクラスを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変数の値に基づき、Active Directory からユーザー情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-115">Retrieves user information from Active Directory based on the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, by using classes in the System.DirectoryServices namespace.</span></span>  
  
 [<span data-ttu-id="e0c73-116">スクリプト タスクによるパフォーマンス カウンターの監視</span><span class="sxs-lookup"><span data-stu-id="e0c73-116">Monitoring Performance Counters with the Script Task</span></span>](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 <span data-ttu-id="e0c73-117">System.Diagnostics 名前空間のクラスを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ実行の進行状況を監視するときに使用できる、カスタム パフォーマンス カウンターを作成します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-117">Creates a custom performance counter that can be used to track the execution progress of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, by using classes in the System.Diagnostics namespace.</span></span>  
  
 [<span data-ttu-id="e0c73-118">スクリプト タスクによる画像の操作</span><span class="sxs-lookup"><span data-stu-id="e0c73-118">Working with Images with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 <span data-ttu-id="e0c73-119">System.Drawing 名前空間のクラスを使用して、画像を JPEG 形式に圧縮し、そこからサムネイル画像を作成します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-119">Compresses images into the JPEG format and creates thumbnail images from them, by using classes in the System.Drawing namespace.</span></span>  
  
 [<span data-ttu-id="e0c73-120">スクリプト タスクによるインストールされたプリンターの検索</span><span class="sxs-lookup"><span data-stu-id="e0c73-120">Finding Installed Printers with the Script Task</span></span>](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 <span data-ttu-id="e0c73-121">System.Drawing.Printing 名前空間のクラスを使用して、特定の用紙サイズをサポートするインストール済みのプリンターを探します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-121">Locates installed printers that support a specific paper size, by using classes in the System.Drawing.Printing namespace.</span></span>  
  
 [<span data-ttu-id="e0c73-122">スクリプト タスクによる HTML メール メッセージの送信</span><span class="sxs-lookup"><span data-stu-id="e0c73-122">Sending an HTML Mail Message with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 <span data-ttu-id="e0c73-123">プレーン テキスト形式の代わりに HTML 形式でメール メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-123">Sends a mail message in HTML format instead of plain text format.</span></span>  
  
 [<span data-ttu-id="e0c73-124">スクリプト タスクを使用した Excel ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="e0c73-124">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 <span data-ttu-id="e0c73-125">Excel ファイル内のワークシートを一覧表示し、特定のワークシートが存在するかどうかチェックします。</span><span class="sxs-lookup"><span data-stu-id="e0c73-125">Lists the worksheets in an Excel file and checks for the existence of a specific worksheet.</span></span>  
  
 [<span data-ttu-id="e0c73-126">スクリプト タスクによるリモート プライベート メッセージ キューへの送信</span><span class="sxs-lookup"><span data-stu-id="e0c73-126">Sending to a Remote Private Message Queue with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 <span data-ttu-id="e0c73-127">リモート プライベート メッセージ キューにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-127">Sends a message to a remote private message queue.</span></span>  
  
### <a name="other-examples"></a><span data-ttu-id="e0c73-128">その他の例</span><span class="sxs-lookup"><span data-stu-id="e0c73-128">Other Examples</span></span>  
 <span data-ttu-id="e0c73-129">以下のトピックでも、スクリプト タスクで使用するコード例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-129">The following topics also contain code examples for use with the Script task:</span></span>  
  
 [<span data-ttu-id="e0c73-130">スクリプト タスクでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="e0c73-130">Using Variables in the Script Task</span></span>](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 <span data-ttu-id="e0c73-131">パッケージ変数の値が別の変数で指定した制限を超える可能性がある場合、パッケージの実行を継続するかどうかをユーザーに確認します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-131">Asks the user for confirmation of whether the package should continue to run, based on the value of a package variable that may exceed the limit specified in another variable.</span></span>  
  
 [<span data-ttu-id="e0c73-132">スクリプト タスクでのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="e0c73-132">Connecting to Data Sources in the Script Task</span></span>](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="e0c73-133">パッケージで定義された接続マネージャーから、接続または接続情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-133">Retrieves a connection or connection information from connection managers defined in the package.</span></span>  
  
 [<span data-ttu-id="e0c73-134">スクリプト タスクでのイベントの発生</span><span class="sxs-lookup"><span data-stu-id="e0c73-134">Raising Events in the Script Task</span></span>](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 <span data-ttu-id="e0c73-135">サーバー上のインターネット接続の状態に基づき、エラー、警告、または情報メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-135">Raises an error, a warning, or an informational message based on the status of the Internet connection on the server.</span></span>  
  
 [<span data-ttu-id="e0c73-136">スクリプト タスクでのログ記録</span><span class="sxs-lookup"><span data-stu-id="e0c73-136">Logging in the Script Task</span></span>](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 <span data-ttu-id="e0c73-137">タスクによって処理されたアイテム数を、有効なログ プロバイダーに記録します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-137">Logs the number of items processed by the task to enabled log providers.</span></span>  
  
<span data-ttu-id="e0c73-138">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="e0c73-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0c73-139">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c73-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0c73-140">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="e0c73-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0c73-141">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="e0c73-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
