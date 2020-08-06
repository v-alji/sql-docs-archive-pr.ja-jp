---
title: '[トレースのプロパティ] ([全般] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30de30c88db35a41f8f118b6545d56a78b2dec79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741217"
---
# <a name="trace-properties-general-tab"></a><span data-ttu-id="86e5a-102">[トレースのプロパティ] ([全般] タブ)</span><span class="sxs-lookup"><span data-stu-id="86e5a-102">Trace Properties (General Tab)</span></span>
  <span data-ttu-id="86e5a-103">**[トレースのプロパティ]** ダイアログ ボックスの **[全般]** タブを使用すると、トレースのプロパティを表示したり指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-103">Use the **General** tab of the **Trace Properties** dialog box to view or specify properties of a trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86e5a-104">Options</span><span class="sxs-lookup"><span data-stu-id="86e5a-104">Options</span></span>  
 <span data-ttu-id="86e5a-105">**[トレース名]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-105">**Trace name**</span></span>  
 <span data-ttu-id="86e5a-106">トレース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-106">Specify the name of the trace.</span></span>  
  
 <span data-ttu-id="86e5a-107">**[トレース プロバイダー名]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-107">**Trace provider name**</span></span>  
 <span data-ttu-id="86e5a-108">トレースされる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-108">Shows the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that will be traced.</span></span> <span data-ttu-id="86e5a-109">このフィールドには、接続時に指定したサーバーの名前が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-109">This field is populated automatically with the name of the server that you specified when you connected.</span></span> <span data-ttu-id="86e5a-110">トレース プロバイダーの名前を変更するには、 **[キャンセル]** をクリックしてダイアログ ボックスを閉じ、新しいトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-110">To change the name of the trace provider, click **Cancel** to close the dialog box, and start a new trace.</span></span>  
  
 <span data-ttu-id="86e5a-111">**[トレース プロバイダーの種類]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-111">**Trace provider type**</span></span>  
 <span data-ttu-id="86e5a-112">トレースを提供しているサーバーの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-112">Shows the server type that is providing the trace.</span></span> <span data-ttu-id="86e5a-113">トレース定義ファイルの **[トレース プロバイダーの種類]** フィールドは自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-113">The trace definition file populates the **Trace provider type** field automatically.</span></span> <span data-ttu-id="86e5a-114">このフィールドは変更できません。</span><span class="sxs-lookup"><span data-stu-id="86e5a-114">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="86e5a-115">**version**</span><span class="sxs-lookup"><span data-stu-id="86e5a-115">**version**</span></span>  
 <span data-ttu-id="86e5a-116">トレースを提供しているサーバーのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-116">Shows the version of the server that is providing the trace.</span></span> <span data-ttu-id="86e5a-117">トレース定義ファイルの **[バージョン]** フィールドは自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-117">The trace definition file populates the **Version** field automatically.</span></span> <span data-ttu-id="86e5a-118">このフィールドは変更できません。</span><span class="sxs-lookup"><span data-stu-id="86e5a-118">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="86e5a-119">**テンプレートを使用する**</span><span class="sxs-lookup"><span data-stu-id="86e5a-119">**Use the template**</span></span>  
 <span data-ttu-id="86e5a-120">テンプレート ディレクトリからテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-120">Select a template from the template directory.</span></span> <span data-ttu-id="86e5a-121">ディレクトリには、既定のテンプレート、および現在のトレース プロバイダーの種類に対して作成されたユーザー定義テンプレートが入力されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-121">The directory is populated with the default templates and any user-defined templates created for the current trace provider type.</span></span>  
  
 <span data-ttu-id="86e5a-122">**[ファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-122">**Save to file**</span></span>  
 <span data-ttu-id="86e5a-123">トレース データを .trc ファイルにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="86e5a-123">Capture the trace data to a .trc file.</span></span> <span data-ttu-id="86e5a-124">トレース データを保存しておくと、後でチェックしたり分析したりするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="86e5a-124">Saving trace data is useful for later review and analysis.</span></span>  
  
 <span data-ttu-id="86e5a-125">**[最大ファイル サイズの設定 (MB)]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-125">**Set maximum file size (MB)**</span></span>  
 <span data-ttu-id="86e5a-126">トレース データのファイルへの保存を選択する場合は、トレース ファイルの最大サイズを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86e5a-126">If you choose to save the trace data to a file, you must specify the maximum size of the trace file.</span></span> <span data-ttu-id="86e5a-127">既定の容量は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="86e5a-127">The default is 5 megabytes (MB).</span></span> <span data-ttu-id="86e5a-128">最大サイズは、ファイルが保存されているファイル システム (NTFS、FAT) によってのみ制限されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-128">The maximum size is limited only by the file system (NTFS, FAT) where the file is saved.</span></span>  
  
 <span data-ttu-id="86e5a-129">\<Graphic>**名前を付けて保存**</span><span class="sxs-lookup"><span data-stu-id="86e5a-129">\<Graphic> **Save As**</span></span>  
 <span data-ttu-id="86e5a-130">保存を選択した後で、このアイコンをクリックしてファイル名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-130">After you have selected to save, you can select this icon to change the file name.</span></span>  
  
 <span data-ttu-id="86e5a-131">**[ファイル ロールオーバーを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-131">**Enable file rollover**</span></span>  
 <span data-ttu-id="86e5a-132">選択した場合、最大ファイル サイズに達したときに追加ファイルを作成して、トレース データを受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-132">Select to enable the creation of additional files to accept the trace data when the maximum file size is reached.</span></span> <span data-ttu-id="86e5a-133">新しいファイル名は元の .trc  ファイル名で構成され、それぞれ順に番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-133">Each new file name consists of the original .trc file name, numbered sequentially.</span></span> <span data-ttu-id="86e5a-134">たとえば、最大ファイル サイズに達したときに、 **NewTrace.trc** が閉じ、新しいファイルの **NewTrace_1.trc**が開きます。次に **NewTrace_2.trc**が開いて、以降も順に同様のファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-134">For example, once it reaches maximum file size, **NewTrace.trc** closes, and a new file, **NewTrace_1.trc**, opens, followed by **NewTrace_2.trc**, and so on.</span></span> <span data-ttu-id="86e5a-135">トレースをファイルに保存する場合、特に指定しない限り、ファイル ロールオーバーはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="86e5a-135">File rollover is enabled by default when you save a trace to a file.</span></span>  
  
 <span data-ttu-id="86e5a-136">**[サーバーがトレース データを処理する]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-136">**Server processes trace data**</span></span>  
 <span data-ttu-id="86e5a-137">トレースを実行中のサーバーがトレース データを処理するように指定します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-137">Specify that the server running the trace should process the trace data.</span></span> <span data-ttu-id="86e5a-138">このオプションを使用すると、トレースによって起こるパフォーマンス オーバーヘッドを低減できます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-138">Using this option reduces the performance overhead incurred by tracing.</span></span> <span data-ttu-id="86e5a-139">オンにすると、ストレス条件下でもイベントはスキップされません。</span><span class="sxs-lookup"><span data-stu-id="86e5a-139">If selected, no events are skipped even under stress conditions.</span></span> <span data-ttu-id="86e5a-140">このチェック ボックスがオフの場合、処理は SQL Server Profiler によって実行され、ストレス条件下の一部のイベントがトレースされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86e5a-140">If this check box is cleared, processing is performed by SQL Server Profiler, and there is a possibility that some events are not traced under stress conditions.</span></span>  
  
 <span data-ttu-id="86e5a-141">**[テーブルに保存]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-141">**Save to table**</span></span>  
 <span data-ttu-id="86e5a-142">トレース データをデータベース テーブルにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="86e5a-142">Capture the trace data to a database table.</span></span> <span data-ttu-id="86e5a-143">トレース データを保存しておくと、後でチェックしたり分析したりするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="86e5a-143">Saving trace data is useful for later review and analysis.</span></span> <span data-ttu-id="86e5a-144">ただし、トレース データをテーブルに保存すると、保存先となるサーバーに大きなオーバーヘッドが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86e5a-144">However, saving trace data to a table can incur significant overhead on the server where the trace is being saved.</span></span> <span data-ttu-id="86e5a-145">可能な限り、トレースしているサーバーと同じサーバーにトレース テーブルを保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="86e5a-145">If possible, do not save the trace table on the same server that is being traced.</span></span>  
  
 <span data-ttu-id="86e5a-146">\<Graphic>**変換先テーブル**</span><span class="sxs-lookup"><span data-stu-id="86e5a-146">\<Graphic> **Destination Table**</span></span>  
 <span data-ttu-id="86e5a-147">トレース データをデータベース テーブルに保存することを選択した後で、このアイコンをクリックしてテーブル名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="86e5a-147">After you have selected to save the trace data to a database table, you can select this icon to change the table name.</span></span>  
  
 <span data-ttu-id="86e5a-148">**[最大行数の設定 (1000 行単位)]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-148">**Set maximum rows (in thousands)**</span></span>  
 <span data-ttu-id="86e5a-149">データを保存する最大行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-149">Specify the largest number of rows in which to save data.</span></span> <span data-ttu-id="86e5a-150">既定値は 1000 行です。</span><span class="sxs-lookup"><span data-stu-id="86e5a-150">The default is 1000 rows.</span></span>  
  
 <span data-ttu-id="86e5a-151">**[トレース停止時刻を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="86e5a-151">**Enable trace stop time**</span></span>  
 <span data-ttu-id="86e5a-152">トレースを終了して閉じる日時を設定します。</span><span class="sxs-lookup"><span data-stu-id="86e5a-152">Set the date and time for the trace to end and close itself.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e5a-153">参照</span><span class="sxs-lookup"><span data-stu-id="86e5a-153">See Also</span></span>  
 [<span data-ttu-id="86e5a-154">トレースの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="86e5a-154">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
