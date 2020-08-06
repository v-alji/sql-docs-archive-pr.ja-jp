---
title: トレース ファイルの最大ファイル サイズの設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa990c610f7aa8bf82690c8c201c6643eb712191
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720618"
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="630a8-102">トレース ファイルの最大ファイル サイズの設定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="630a8-102">Set a Maximum File Size for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="630a8-103">トレース ファイルの最大ファイル サイズを設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="630a8-103">Use the following procedure to set the maximum file size for a trace file.</span></span>  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a><span data-ttu-id="630a8-104">トレース ファイルの最大ファイル サイズを設定するには</span><span class="sxs-lookup"><span data-stu-id="630a8-104">To set a maximum file size for a trace file</span></span>  
  
1.  <span data-ttu-id="630a8-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="630a8-105">On the **File** menu, click **New Trace**, and then connect to an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="630a8-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="630a8-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="630a8-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="630a8-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="630a8-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="630a8-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="630a8-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="630a8-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="630a8-110">**[テンプレート名]** ボックスの一覧で、トレース テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="630a8-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="630a8-111">**[ファイルに保存]** チェック ボックスをオンにし、トレース情報を格納するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="630a8-111">Select **Save to file**, and then specify a file to store the trace information.</span></span>  
  
5.  <span data-ttu-id="630a8-112">**[最大ファイル サイズの設定 (MB)]** ボックスで、トレースの最大ファイル サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="630a8-112">In the **Set maximum file size** check box, specify a maximum file size for the trace.</span></span> <span data-ttu-id="630a8-113">ファイル サイズが指定した最大値に達すると、このファイルにはトレース イベントが記録されなくなります。</span><span class="sxs-lookup"><span data-stu-id="630a8-113">When the file size reaches this maximum, trace events are no longer recorded in this file.</span></span> <span data-ttu-id="630a8-114">**[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにした場合 (既定でオンになっています)、次の動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="630a8-114">If you select **Enable file rollover** (which is selected by default),the following occurs:</span></span>  
  
     <span data-ttu-id="630a8-115">ファイルのロールオーバー オプションを使用すると、最大ファイル サイズに達したときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって現在のファイルが閉じられ、新しいファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="630a8-115">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="630a8-116">新しいファイルの名前は古いファイルと同一ですが、順序を表す整数がファイル名に付加されます。たとえば、元のトレース ファイルの名前を filename_1.trc とすると、次のトレース ファイルは filename_2.trc となり、以降同様に続きます。</span><span class="sxs-lookup"><span data-stu-id="630a8-116">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence; for example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="630a8-117">新しいロールオーバー ファイルに割り当てられた名前が既存のファイルで既に使用されている場合、その既存のファイルは、読み取り専用でない限り上書きされます。</span><span class="sxs-lookup"><span data-stu-id="630a8-117">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read-only.</span></span> <span data-ttu-id="630a8-118">トレース データをファイルに保存する場合、ファイルのロールオーバー オプションが既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="630a8-118">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
     <span data-ttu-id="630a8-119">ファイルのロールオーバー オプションを有効にすると、トレースは他の方法によって停止されるまで続行されます。</span><span class="sxs-lookup"><span data-stu-id="630a8-119">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="630a8-120">ファイル サイズの制限に達した後でトレースを停止するには、ファイルのロールオーバー オプションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="630a8-120">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="630a8-121">FAT32 ファイル システムでは、ファイル サイズが 4 GB 弱に制限されます。</span><span class="sxs-lookup"><span data-stu-id="630a8-121">The FAT32 file system limits files to slightly less than 4 gigabytes (GB).</span></span> <span data-ttu-id="630a8-122">トレース ファイルがそのサイズに達すると、"ディスク領域が不足しています" というエラーが発生してトレースが失敗します。</span><span class="sxs-lookup"><span data-stu-id="630a8-122">When the trace file reaches that size, the trace fails with the error "Not enough disk space."</span></span> <span data-ttu-id="630a8-123">これよりも大きなファイルを作成するには、NTFS ファイル システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="630a8-123">To create larger files, use the NTFS file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630a8-124">参照</span><span class="sxs-lookup"><span data-stu-id="630a8-124">See Also</span></span>  
 [<span data-ttu-id="630a8-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="630a8-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
