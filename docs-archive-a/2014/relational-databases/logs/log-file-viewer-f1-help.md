---
title: '[ログ ファイルの表示] の F1 ヘルプ | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.errorlog.f1
helpviewer_keywords:
- Log File Viewer
ms.assetid: 2243845c-4880-4aa0-9ee8-0a97a128996b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6eadb4baa4a47202b40a9cde1eca896022f31d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639503"
---
# <a name="log-file-viewer-f1-help"></a><span data-ttu-id="6a848-102">[ログ ファイルの表示] の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="6a848-102">Log File Viewer F1 Help</span></span>
  <span data-ttu-id="6a848-103">[ログ ファイルの表示] には、さまざまなコンポーネントのログ情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-103">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="6a848-104">[ログ ファイルの表示] が開いているときに **[ログの選択]** ペインを使用して、表示するログを選択します。</span><span class="sxs-lookup"><span data-stu-id="6a848-104">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="6a848-105">各ログには、そのログの種類に適した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-105">Each log displays columns appropriate to that kind of log.</span></span>  
  
 <span data-ttu-id="6a848-106">表示できるログ ファイルは、[ログ ファイルの表示] を開いたときの状況に応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="6a848-106">The logs that are available depend on how Log File Viewer is opened.</span></span> <span data-ttu-id="6a848-107">詳細については、「 [[ログ ファイルの表示] を開く](open-log-file-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a848-107">For more information, see [Open Log File Viewer](open-log-file-viewer.md).</span></span>  
  
 <span data-ttu-id="6a848-108">監査ログの表示行数は、 **[ツール] メニューから開く [オプション]** ダイアログ ボックスの **[SQL Server オブジェクト エクスプローラー]/[コマンド]** ページで構成できます。</span><span class="sxs-lookup"><span data-stu-id="6a848-108">The number of rows that are displayed for audit logs can be configured on the **SQL Server Object Explorer/Commands** page of the **Tools/Options** dialog box.</span></span> <span data-ttu-id="6a848-109">監査ログの表示列の詳細については、「[sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a848-109">For descriptions of the columns that are displayed for audit logs, see [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6a848-110">Options</span><span class="sxs-lookup"><span data-stu-id="6a848-110">Options</span></span>  
 <span data-ttu-id="6a848-111">**[ログの読み込み]**</span><span class="sxs-lookup"><span data-stu-id="6a848-111">**Load Log**</span></span>  
 <span data-ttu-id="6a848-112">読み込むログ ファイルを指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="6a848-112">Open a dialog box where you can specify a log file to load.</span></span>  
  
 <span data-ttu-id="6a848-113">**エクスポート**</span><span class="sxs-lookup"><span data-stu-id="6a848-113">**Export**</span></span>  
 <span data-ttu-id="6a848-114">**[ログ ファイルの概要]** グリッドに表示されている情報をテキスト ファイルとしてエクスポートするためのダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="6a848-114">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
 <span data-ttu-id="6a848-115">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="6a848-115">**Refresh**</span></span>  
 <span data-ttu-id="6a848-116">選択されたログの表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="6a848-116">Refresh the view of the selected logs.</span></span> <span data-ttu-id="6a848-117">**[更新]** ボタンをクリックすると、選択したログがターゲット サーバーから再度読み込まれ、それと同時にすべてのフィルター設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-117">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
 <span data-ttu-id="6a848-118">**Assert**</span><span class="sxs-lookup"><span data-stu-id="6a848-118">**Filter**</span></span>  
 <span data-ttu-id="6a848-119">**[接続]** や **[日付]** などの **[全般]** フィルター基準を含め、ログ ファイルのフィルター選択に使用する設定を指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="6a848-119">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
 <span data-ttu-id="6a848-120">**Search**</span><span class="sxs-lookup"><span data-stu-id="6a848-120">**Search**</span></span>  
 <span data-ttu-id="6a848-121">ログ ファイル内で特定のテキストを検索します。</span><span class="sxs-lookup"><span data-stu-id="6a848-121">Search the log file for specific text.</span></span> <span data-ttu-id="6a848-122">ワイルドカード文字を使用した検索はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6a848-122">Searching with wildcard characters is not supported.</span></span>  
  
 <span data-ttu-id="6a848-123">**Stop**</span><span class="sxs-lookup"><span data-stu-id="6a848-123">**Stop**</span></span>  
 <span data-ttu-id="6a848-124">ログ ファイル エントリの読み込みを停止します。</span><span class="sxs-lookup"><span data-stu-id="6a848-124">Stops loading the log file entries.</span></span> <span data-ttu-id="6a848-125">たとえば、最新のエントリのみを表示したい場合に、リモートまたはオフラインのログ ファイルの読み込みに長い時間がかかるときは、このオプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6a848-125">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
 <span data-ttu-id="6a848-126">**[ログ ファイルの概要]**</span><span class="sxs-lookup"><span data-stu-id="6a848-126">**Log file summary**</span></span>  
 <span data-ttu-id="6a848-127">この情報パネルには、ログ ファイルのフィルター選択の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-127">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="6a848-128">ファイルがフィルター選択されない場合、 **"フィルターが適用されていません"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-128">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="6a848-129">ログにフィルターが適用されている場合、"**ログ エントリのフィルター条件:** \<filter criteria>" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-129">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
 <span data-ttu-id="6a848-130">**[選択した行の詳細]**</span><span class="sxs-lookup"><span data-stu-id="6a848-130">**Selected row details**</span></span>  
 <span data-ttu-id="6a848-131">行を選択すると、選択されたイベント行の詳細情報がページの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-131">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="6a848-132">列をグリッド内の別の場所にドラッグすることで、列を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6a848-132">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="6a848-133">グリッドのヘッダーで列のセパレーター バーを左右にドラッグすると、列の幅を変更できます。</span><span class="sxs-lookup"><span data-stu-id="6a848-133">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="6a848-134">グリッドのヘッダーで列のセパレーター バーをダブルクリックすると、内容の長さに合わせて自動的に列の幅が調整されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-134">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
 <span data-ttu-id="6a848-135">**インスタンス**</span><span class="sxs-lookup"><span data-stu-id="6a848-135">**Instance**</span></span>  
 <span data-ttu-id="6a848-136">イベントが発生したインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="6a848-136">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="6a848-137">これは、 *computer name*\\*instance name*と表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-137">This is displayed as *computer name*\\*instance name*.</span></span>  
  
## <a name="frequently-displayed-columns"></a><span data-ttu-id="6a848-138">表示頻度の高い列</span><span class="sxs-lookup"><span data-stu-id="6a848-138">Frequently Displayed Columns</span></span>  
 <span data-ttu-id="6a848-139">**Date**</span><span class="sxs-lookup"><span data-stu-id="6a848-139">**Date**</span></span>  
 <span data-ttu-id="6a848-140">イベントの日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-140">Displays the date of the event.</span></span>  
  
 <span data-ttu-id="6a848-141">**ソース**</span><span class="sxs-lookup"><span data-stu-id="6a848-141">**Source**</span></span>  
 <span data-ttu-id="6a848-142">サービスの名前 (たとえば MSSQLSERVER) など、イベントの作成元のソース機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-142">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="6a848-143">ログの種類によっては表示されません。</span><span class="sxs-lookup"><span data-stu-id="6a848-143">This does not appear for all log types.</span></span>  
  
 <span data-ttu-id="6a848-144">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="6a848-144">**Message**</span></span>  
 <span data-ttu-id="6a848-145">イベントに関連付けられているメッセージがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-145">Displays any messages associated with the event.</span></span>  
  
 <span data-ttu-id="6a848-146">**[ログの種類]**</span><span class="sxs-lookup"><span data-stu-id="6a848-146">**Log Type**</span></span>  
 <span data-ttu-id="6a848-147">イベントが属するログの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-147">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="6a848-148">[ログ ファイルの概要] ウィンドウには、選択したログがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-148">All selected logs appear in the log file summary window.</span></span>  
  
 <span data-ttu-id="6a848-149">**[ログ ソース]**</span><span class="sxs-lookup"><span data-stu-id="6a848-149">**Log Source**</span></span>  
 <span data-ttu-id="6a848-150">イベントがキャプチャされているソース ログの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a848-150">Displays a description of the source log in which the event is captured.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="6a848-151">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="6a848-151">Permissions</span></span>  
 <span data-ttu-id="6a848-152">オンラインの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、securityadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6a848-152">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="6a848-153">オフラインの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間、およびログ ファイルの保存されているフォルダーの両方に対する読み取りアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="6a848-153">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="6a848-154">詳細については、「 [オフライン ログ ファイルの表示](view-offline-log-files.md)」トピックの「セキュリティ」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a848-154">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a848-155">参照</span><span class="sxs-lookup"><span data-stu-id="6a848-155">See Also</span></span>  
 <span data-ttu-id="6a848-156">[ログ ファイルの表示](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="6a848-156">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="6a848-157">[[ログ ファイルの表示] を開く](open-log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="6a848-157">[Open Log File Viewer](open-log-file-viewer.md) </span></span>  
 [<span data-ttu-id="6a848-158">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="6a848-158">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
