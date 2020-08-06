---
title: SQL Server エージェントのエラー ログの表示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: b88214a158a970a754c5f313bde3d53f2652ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719388"
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="adb2f-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="adb2f-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="adb2f-103">このトピックでは、  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェントのエラー ログを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-103">This topic describes how to view the  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="adb2f-104">[ログ ファイルの表示] には、さまざまなコンポーネントのログ情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-104">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="adb2f-105">[ログ ファイルの表示] が開いているときに **[ログの選択]** ペインを使用して、表示するログを選択します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-105">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="adb2f-106">各ログには、そのログの種類に適した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-106">Each log displays columns appropriate to that kind of log.</span></span> <span data-ttu-id="adb2f-107">表示できるログ ファイルは、[ログ ファイルの表示] を開いたときの状況に応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="adb2f-107">The logs that are available depend on how Log File Viewer is opened.</span></span>  
  
 <span data-ttu-id="adb2f-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="adb2f-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="adb2f-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="adb2f-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="adb2f-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="adb2f-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="adb2f-111">Security</span><span class="sxs-lookup"><span data-stu-id="adb2f-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="adb2f-112">SQL Server Management Studio を使用して SQL Server エージェントのエラー ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="adb2f-112">To view the SQL Server Agent error log, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="adb2f-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="adb2f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="adb2f-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="adb2f-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="adb2f-115">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="adb2f-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="adb2f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="adb2f-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="adb2f-117">Permissions</span></span>  
 <span data-ttu-id="adb2f-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb2f-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="adb2f-119">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="adb2f-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="adb2f-120">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="adb2f-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="adb2f-121">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="adb2f-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="adb2f-122">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="adb2f-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="adb2f-123">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="adb2f-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="adb2f-124">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adb2f-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="adb2f-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="adb2f-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-ssnoversion-agent-error-log"></a><span data-ttu-id="adb2f-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="adb2f-126">To view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log</span></span>  
  
1.  <span data-ttu-id="adb2f-127">**オブジェクト エクスプローラー**で、表示する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-127">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to view.</span></span>  
  
2.  <span data-ttu-id="adb2f-128">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="adb2f-129">プラス記号をクリックして **[エラー ログ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-129">Click the plus sign to expand the **Error Logs** folder.</span></span>  
  
4.  <span data-ttu-id="adb2f-130">表示するエラー ログを右クリックし、 **[エージェント ログの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-130">Right-click the error log you want to view and select **View Agent Log**.</span></span>  
  
     <span data-ttu-id="adb2f-131">**[ログ ファイルの表示 -**_サーバー名_] ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-131">The following options are available in the **Log File Viewer -**_server_name_ dialog box:</span></span>  
  
     <span data-ttu-id="adb2f-132">**[ログの読み込み]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-132">**Load Log**</span></span>  
     <span data-ttu-id="adb2f-133">読み込むログ ファイルを指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-133">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="adb2f-134">**エクスポート**</span><span class="sxs-lookup"><span data-stu-id="adb2f-134">**Export**</span></span>  
     <span data-ttu-id="adb2f-135">**[ログ ファイルの概要]** グリッドに表示されている情報をテキスト ファイルとしてエクスポートするためのダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-135">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="adb2f-136">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-136">**Refresh**</span></span>  
     <span data-ttu-id="adb2f-137">選択されたログの表示を更新します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-137">Refresh the view of the selected logs.</span></span> <span data-ttu-id="adb2f-138">**[更新]** ボタンをクリックすると、選択したログがターゲット サーバーから再度読み込まれ、それと同時にすべてのフィルター設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-138">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="adb2f-139">**Assert**</span><span class="sxs-lookup"><span data-stu-id="adb2f-139">**Filter**</span></span>  
     <span data-ttu-id="adb2f-140">**[接続]** や **[日付]** などの **[全般]** フィルター基準を含め、ログ ファイルのフィルター選択に使用する設定を指定できるダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-140">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="adb2f-141">**Search**</span><span class="sxs-lookup"><span data-stu-id="adb2f-141">**Search**</span></span>  
     <span data-ttu-id="adb2f-142">ログ ファイル内で特定のテキストを検索します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-142">Search the log file for specific text.</span></span> <span data-ttu-id="adb2f-143">ワイルドカード文字を使用した検索はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="adb2f-143">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="adb2f-144">**Stop**</span><span class="sxs-lookup"><span data-stu-id="adb2f-144">**Stop**</span></span>  
     <span data-ttu-id="adb2f-145">ログ ファイル エントリの読み込みを停止します。</span><span class="sxs-lookup"><span data-stu-id="adb2f-145">Stops loading the log file entries.</span></span> <span data-ttu-id="adb2f-146">たとえば、最新のエントリのみを表示したい場合に、リモートまたはオフラインのログ ファイルの読み込みに長い時間がかかるときは、このオプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="adb2f-146">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="adb2f-147">**[ログ ファイルの概要]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-147">**Log file summary**</span></span>  
     <span data-ttu-id="adb2f-148">この情報パネルには、ログ ファイルのフィルター選択の概要が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-148">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="adb2f-149">ファイルがフィルター選択されない場合、 **"フィルターが適用されていません"** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-149">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="adb2f-150">ログにフィルターが適用されている場合、"**ログ エントリのフィルター条件:** \<filter criteria>" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-150">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="adb2f-151">**[選択した行の詳細]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-151">**Selected row details**</span></span>  
     <span data-ttu-id="adb2f-152">行を選択すると、選択されたイベント行の詳細情報がページの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-152">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="adb2f-153">列をグリッド内の別の場所にドラッグすることで、列を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-153">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="adb2f-154">グリッドのヘッダーで列のセパレーター バーを左右にドラッグすると、列の幅を変更できます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-154">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="adb2f-155">グリッドのヘッダーで列のセパレーター バーをダブルクリックすると、内容の長さに合わせて自動的に列の幅が調整されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-155">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="adb2f-156">**インスタンス**</span><span class="sxs-lookup"><span data-stu-id="adb2f-156">**Instance**</span></span>  
     <span data-ttu-id="adb2f-157">イベントが発生したインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="adb2f-157">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="adb2f-158">これは、 *computer name*\\*instance name*と表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-158">This is displayed as *computer name*\\*instance name*.</span></span>  
  
     <span data-ttu-id="adb2f-159">**Date**</span><span class="sxs-lookup"><span data-stu-id="adb2f-159">**Date**</span></span>  
     <span data-ttu-id="adb2f-160">イベントの日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-160">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="adb2f-161">**ソース**</span><span class="sxs-lookup"><span data-stu-id="adb2f-161">**Source**</span></span>  
     <span data-ttu-id="adb2f-162">サービスの名前 (たとえば MSSQLSERVER) など、イベントの作成元のソース機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-162">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="adb2f-163">ログの種類によっては表示されません。</span><span class="sxs-lookup"><span data-stu-id="adb2f-163">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="adb2f-164">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="adb2f-164">**Message**</span></span>  
     <span data-ttu-id="adb2f-165">イベントに関連付けられているメッセージがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-165">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="adb2f-166">**[ログの種類]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-166">**Log Type**</span></span>  
     <span data-ttu-id="adb2f-167">イベントが属するログの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-167">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="adb2f-168">[ログ ファイルの概要] ウィンドウには、選択したログがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-168">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="adb2f-169">**[ログ ソース]**</span><span class="sxs-lookup"><span data-stu-id="adb2f-169">**Log Source**</span></span>  
     <span data-ttu-id="adb2f-170">イベントがキャプチャされているソース ログの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adb2f-170">Displays a description of the source log in which the event is captured.</span></span>  
  
5.  <span data-ttu-id="adb2f-171">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="adb2f-171">When finished, click **Close**.</span></span>  
  
  
