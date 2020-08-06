---
title: トレース結果のファイルへの保存 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9644751cda3689cf7b7cb00ec25310bc700ca1c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737219"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a><span data-ttu-id="44409-102">トレース結果のファイルへの保存 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="44409-102">Save Trace Results to a File (SQL Server Profiler)</span></span>
  <span data-ttu-id="44409-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース結果をファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="44409-103">This topic describes how to save trace results to a file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-file"></a><span data-ttu-id="44409-104">トレース結果をファイルに保存するには</span><span class="sxs-lookup"><span data-stu-id="44409-104">To save trace results to a file</span></span>  
  
1.  <span data-ttu-id="44409-105">**[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="44409-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="44409-106">**[トレースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44409-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44409-107">**[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="44409-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="44409-108">この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="44409-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="44409-109">**[トレース名]** ボックスに、トレースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="44409-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="44409-110">**[ファイルに保存する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="44409-110">Select the **Save to file** check box.</span></span>  
  
     <span data-ttu-id="44409-111">**[名前を付けて保存]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44409-111">The **Save As**dialog box appears.</span></span>  
  
4.  <span data-ttu-id="44409-112">**[名前を付けて保存]** ダイアログ ボックスでパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="44409-112">Specify a path and filename in the **Save As**dialog box.</span></span> <span data-ttu-id="44409-113">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44409-113">Click **Save.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44409-114">SQL Server サービスに、指定したディレクトリのファイルに対して書き込めるアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="44409-114">Ensure that the SQL Server service has sufficient permissions to write to a file in the directory specified.</span></span>  
  
5.  <span data-ttu-id="44409-115">**[トレースのプロパティ]** ダイアログ ボックスの **[最大ファイル サイズの設定 (MB)]** ボックスに、ファイルの最大サイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="44409-115">In the **Trace Properties** dialog box, enter the maximum file size in the **Set maximum file size (MB)** text box.</span></span> <span data-ttu-id="44409-116">既定値は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="44409-116">The default value is 5 megabytes (MB).</span></span>  
  
6.  <span data-ttu-id="44409-117">必要に応じて、次のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="44409-117">Optionally, specify the following options:</span></span>  
  
    -   <span data-ttu-id="44409-118">**[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにすると、最大ファイル サイズに達したとき、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によりトレース データ用の新しいファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="44409-118">Select the **Enable file rollover** check box to have [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] create new files for trace data once the maximum file size is reached.</span></span> <span data-ttu-id="44409-119">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="44409-119">This option is selected by default.</span></span>  
  
    -   <span data-ttu-id="44409-120">**[サーバーがトレース データを処理する]** チェック ボックスをオンにすると、サーバーにより、すべてのトレース イベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="44409-120">Select the **Server processes trace data** check box to ensure that the server records each trace event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="44409-121">**[サーバーがトレース データを処理する]** チェック ボックスをオフにすると、イベントを記録することが原因でパフォーマンスが大幅に低下する場合、イベントは記録されなくなります。</span><span class="sxs-lookup"><span data-stu-id="44409-121">When **Server processes trace data**is cleared, the server does not record events if recording events significantly degrades performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44409-122">参照</span><span class="sxs-lookup"><span data-stu-id="44409-122">See Also</span></span>  
 [<span data-ttu-id="44409-123">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="44409-123">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
