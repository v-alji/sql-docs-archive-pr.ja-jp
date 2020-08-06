---
title: オブジェクト エクスプローラーでのイベント セッションの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 16849e38-d3fb-414d-8dcb-797b5ffce6ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 1aa33a97137f63348898e6b1fcb7b19b2d218573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631921"
---
# <a name="manage-event-sessions-in-the-object-explorer"></a><span data-ttu-id="a8b01-102">オブジェクト エクスプローラーでのイベント セッションの管理</span><span class="sxs-lookup"><span data-stu-id="a8b01-102">Manage Event Sessions in the Object Explorer</span></span>
  <span data-ttu-id="a8b01-103">このトピックでは、拡張イベントに影響する **オブジェクト エクスプローラー** で実行できる操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-103">This topic discusses the actions you can take in **Object Explorer** that affect Extended Events:</span></span>  
  
-   <span data-ttu-id="a8b01-104">拡張イベント セッションの作成</span><span class="sxs-lookup"><span data-stu-id="a8b01-104">Create an Extended Events Session</span></span>  
  
-   <span data-ttu-id="a8b01-105">拡張イベント セッションの開始または停止</span><span class="sxs-lookup"><span data-stu-id="a8b01-105">Starting or Stopping an Extended Events Session</span></span>  
  
-   <span data-ttu-id="a8b01-106">拡張イベント セッションのエクスポート</span><span class="sxs-lookup"><span data-stu-id="a8b01-106">Export an Extended Events Session</span></span>  
  
-   <span data-ttu-id="a8b01-107">拡張イベント セッション テンプレートのインポート</span><span class="sxs-lookup"><span data-stu-id="a8b01-107">Import an Extended Events Session Template</span></span>  
  
-   <span data-ttu-id="a8b01-108">拡張イベント セッションの編集</span><span class="sxs-lookup"><span data-stu-id="a8b01-108">Edit an Extended Events Session</span></span>  
  
-   <span data-ttu-id="a8b01-109">拡張イベント セッションの削除</span><span class="sxs-lookup"><span data-stu-id="a8b01-109">Delete an Extended Events Session</span></span>  
  
## <a name="create-an-extended-events-session"></a><span data-ttu-id="a8b01-110">拡張イベント セッションの作成</span><span class="sxs-lookup"><span data-stu-id="a8b01-110">Create an Extended Events Session</span></span>  
 <span data-ttu-id="a8b01-111">拡張イベント セッションの作成の詳細については、「 [拡張イベント セッションの作成](../../database-engine/create-an-extended-events-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8b01-111">For more information about creating an Extended Events session, see [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md).</span></span>  
  
## <a name="starting-or-stopping-an-extended-events-session"></a><span data-ttu-id="a8b01-112">拡張イベント セッションの開始または停止</span><span class="sxs-lookup"><span data-stu-id="a8b01-112">Starting or Stopping an Extended Events Session</span></span>  
 <span data-ttu-id="a8b01-113">拡張イベントセッションを開始または停止するには、**クエリエディター**でステートメントを使用する `ALTER EVENT SESSION` か、**オブジェクトエクスプローラー**の [**拡張イベント**] ノードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-113">You can start or stop an Extended Events session through the **Query Editor** using the `ALTER EVENT SESSION` statement, or by using the **Extended Events** node of **Object Explorer**.</span></span>  
  
 <span data-ttu-id="a8b01-114">イベント セッションを停止すると、以後そのセッションは、sys.dm_xe_sessions 動的管理ビュー (DMV) にアクティブなセッションとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="a8b01-114">When you stop an event session, the session is no longer listed as an active session in the sys.dm_xe_sessions dynamic management view (DMV).</span></span> <span data-ttu-id="a8b01-115">ただし、セッションの定義は一切変更されず、セッションを再開することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-115">However, the session definition remains intact, and you can restart the session.</span></span> <span data-ttu-id="a8b01-116">セッションの定義を完全に削除するには、セッションを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8b01-116">To completely remove a session definition, you must delete the session.</span></span>  
  
 <span data-ttu-id="a8b01-117">拡張イベント セッションを開始または停止するには、ALTER ANY EVENT SESSION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8b01-117">To start or stop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="a8b01-118">リング バッファー、バケット、イベント ペアリング ターゲット、同期イベント カウンター ターゲットなど、メモリ内ターゲットを使用するセッションを停止すると、セッションのバッファーに格納されるすべての情報 (sys.dm_xe_session_targets DMV の target_data 列) が失われます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-118">When you stop a session that uses an in-memory target, such as the ring buffer, bucketing, event pairing, or synchronous event counter targets, all the information stored in the session's buffer (the target_data column of the sys.dm_xe_session_targets DMV) will be lost.</span></span> <span data-ttu-id="a8b01-119">セッションを停止した後にイベント データにアクセスするには、ファイル ターゲットを使用するようにセッションを構成するか、セッションを停止する前にデータを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8b01-119">To access event data after you stop the session, you should either save the data before you stop the session, or configure the session to use the file target.</span></span>  
  
### <a name="start-or-stop-an-extended-events-session-using-query-editor"></a><span data-ttu-id="a8b01-120">クエリ エディターを使用した拡張イベント セッションの開始または停止</span><span class="sxs-lookup"><span data-stu-id="a8b01-120">Start or Stop an Extended Events Session Using Query Editor</span></span>  
 <span data-ttu-id="a8b01-121">セッションを開始するには、次のステートメントを発行します。 *session_name* の部分は、拡張イベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="a8b01-121">To start a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = START  
```  
  
 <span data-ttu-id="a8b01-122">セッションを停止するには、次のステートメントを発行します。 *session_name* の部分は、拡張イベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="a8b01-122">To stop a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = STOP  
```  
  
### <a name="start-or-stop-an-extended-events-session-in-object-explorer"></a><span data-ttu-id="a8b01-123">オブジェクト エクスプローラーでの拡張イベント セッションの開始または停止</span><span class="sxs-lookup"><span data-stu-id="a8b01-123">Start or Stop an Extended Events Session in Object Explorer</span></span>  
 <span data-ttu-id="a8b01-124">**オブジェクト エクスプローラー**で拡張イベント セッションを開始または停止するには、 **[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開し、セッションを右クリックして、 **[セッションの開始]** または **[セッションの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-124">To start or stop an Extended Events session in **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes and right click on a session and then click **Start Session** or **Stop Session**.</span></span>  
  
## <a name="export-an-extended-events-session-template"></a><span data-ttu-id="a8b01-125">拡張イベント セッション テンプレートのエクスポート</span><span class="sxs-lookup"><span data-stu-id="a8b01-125">Export an Extended Events Session Template</span></span>  
 <span data-ttu-id="a8b01-126">**オブジェクト エクスプローラー**を使用して拡張イベント セッションをエクスポートし、.xml テンプレート ファイルとして保存することができます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-126">You can export an Extended Events session using **Object Explorer**, and save it as an .xml template file.</span></span> <span data-ttu-id="a8b01-127">たとえば、セッションをエクスポートした後、 **新規セッション ウィザード** または **新規セッション** ウィザードを使用して、そのテンプレートを新しいイベント セッションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-127">For example, you may want to export a session and then apply the template to a new event session using the **New Session Wizard** or the **New Session** wizard.</span></span>  
  
 <span data-ttu-id="a8b01-128">セッションをエクスポートする際は、NTFS ファイル システムが使用されている場所にテンプレート ファイルを保存し、その情報を表示する権限を持つユーザーのみにアクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8b01-128">When you export a session, make sure that you save the template file to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="a8b01-129">**オブジェクト エクスプローラー**で拡張イベント セッションをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="a8b01-129">To export an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="a8b01-130">**[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-130">Expand the **Management**, **Extended Events**, and then **Sessions** nodes</span></span>  
  
2.  <span data-ttu-id="a8b01-131">エクスポートするセッションを右クリックし、 **[セッションのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-131">Right-click the session that you want to export, and select **Export Session**.</span></span>  
  
3.  <span data-ttu-id="a8b01-132">**[名前を付けて保存]** ダイアログ ボックスで、ファイルの保存場所を選択し、 **[ファイル名]** ボックスにファイル名を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-132">In the **Save As** dialog box, select a location to save the file, type the file name in the **File name** box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="a8b01-133">ファイルを既定の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] テンプレートの場所に保存すると、 **新規セッション ウィザード** および **[新しいセッション]** ダイアログを使用するときに事前定義されたテンプレートのドロップダウン リストにテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-133">If you save the file to the default [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] template location, the template will appear in the dropdown list of predefined templates when you use the **New Session Wizard** and **New Session** dialog.</span></span>  
  
## <a name="import-an-extended-events-session-template"></a><span data-ttu-id="a8b01-134">拡張イベント セッション テンプレートのインポート</span><span class="sxs-lookup"><span data-stu-id="a8b01-134">Import an Extended Events Session Template</span></span>  
 <span data-ttu-id="a8b01-135">**オブジェクト エクスプローラー**を使用して、拡張イベント セッションのテンプレートをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-135">Using **Object Explorer**, you can import a template for an Extended Events session.</span></span> <span data-ttu-id="a8b01-136">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の別のインスタンスからエクスポートされたテンプレートからセッションを作成する場合に、この操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-136">For example, you may want to do this to create a session from a template that was exported from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a8b01-137">拡張イベント セッションをインポートするには、`ALTER ANY EVENT SESSION` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8b01-137">To import an Extended Events session, you must have the necessary `ALTER ANY EVENT SESSION` permissions.</span></span>  
  
 <span data-ttu-id="a8b01-138">テンプレート ファイルをインポートする前に、ファイルが信頼できるソースからであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-138">Before you import a template file, make sure that the file is from a trusted source.</span></span> <span data-ttu-id="a8b01-139">テンプレート ファイルは、NTFS ファイル システムを使用し、その情報を表示する権限を持つユーザーのみにアクセスが制限されている場所に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8b01-139">Template files should be saved to a location that uses the NTFS file system and where access is restricted to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="a8b01-140">拡張イベント セッションをインポートするには</span><span class="sxs-lookup"><span data-stu-id="a8b01-140">To import an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="a8b01-141">**オブジェクト エクスプローラー**で **[管理]** ノードを展開し、 **[拡張イベント]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-141">In **Object Explorer**, expand the **Management**, and then **Extended Events** nodes.</span></span>  
  
2.  <span data-ttu-id="a8b01-142">**[セッション]** を右クリックし、 **[新しいセッション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-142">Right-click **Sessions** and select **New Session**.</span></span>  
  
3.  <span data-ttu-id="a8b01-143">セッションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-143">Specify a name for the session.</span></span>  
  
4.  <span data-ttu-id="a8b01-144">**[テンプレート]** ボックスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-144">Expand the **Template** drop down box.</span></span>  
  
5.  <span data-ttu-id="a8b01-145">**[\<File From ...>Open]** をクリックし、インポートするセッション (XML ファイル) を参照します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-145">Click **\<File From ...>Open** and browse for the session (XML file) you want to import.</span></span>  
  
 <span data-ttu-id="a8b01-146">**[セッション]** ノードにセッションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-146">The session appears under the **Sessions** node.</span></span> <span data-ttu-id="a8b01-147">既定では、セッションは開始されていません。</span><span class="sxs-lookup"><span data-stu-id="a8b01-147">By default, the session is not started.</span></span>  
  
## <a name="edit-an-extended-events-session"></a><span data-ttu-id="a8b01-148">拡張イベント セッションの編集</span><span class="sxs-lookup"><span data-stu-id="a8b01-148">Edit an Extended Events Session</span></span>  
 <span data-ttu-id="a8b01-149">オブジェクト エクスプローラーで拡張イベント セッションを編集できます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-149">You can edit an Extended Events session in Object Explorer.</span></span>  
  
 <span data-ttu-id="a8b01-150">拡張イベント セッションを編集するには</span><span class="sxs-lookup"><span data-stu-id="a8b01-150">To edit an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="a8b01-151">**オブジェクト エクスプローラー**で **[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-151">In **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="a8b01-152">セッションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-152">Right-click a session and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="a8b01-153">**[ページの選択]** セクションで、編集するページを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-153">In the **Select a page** section, select the page or pages you want to edit.</span></span>  
  
4.  <span data-ttu-id="a8b01-154">イベント セッションの編集が終了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-154">After you finish revising the event session, click **OK**.</span></span>  
  
## <a name="script-an-event-session-definition-using-tsql"></a><span data-ttu-id="a8b01-155">を使用したイベント セッション定義のスクリプト化 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8b01-155">Script an Event Session Definition Using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
 <span data-ttu-id="a8b01-156">新規セッション ウィザードおよび [新しいセッション] ダイアログの両方に、拡張イベント セッションを定義する [!INCLUDE[tsql](../../includes/tsql-md.md)] を生成するスクリプト オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="a8b01-156">Both the New Session Wizard and the New Session dialog have a Script option that generates the [!INCLUDE[tsql](../../includes/tsql-md.md)] that defines the Extended Events session.</span></span>  
  
 <span data-ttu-id="a8b01-157">セッション名を右クリックし、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [セッションをスクリプト化] **をポイントし、** [CREATE] **をクリックして、既存の拡張イベント セッションの**にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-157">You can access the [!INCLUDE[tsql](../../includes/tsql-md.md)] for an existing Extended Events session by right clicking the session name, selecting **Script Session as**, and then selecting **Create to**.</span></span>  
  
## <a name="delete-an-extended-events-session"></a><span data-ttu-id="a8b01-158">拡張イベント セッションの削除</span><span class="sxs-lookup"><span data-stu-id="a8b01-158">Delete an Extended Events Session</span></span>  
 <span data-ttu-id="a8b01-159">次の方法で拡張イベント セッションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-159">You can delete an Extended Events session:</span></span>  
  
-   <span data-ttu-id="a8b01-160">クエリ エディターで、`DROP EVENT SESSION` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-160">In Query Editor using `DROP EVENT SESSION`.</span></span>  
  
-   <span data-ttu-id="a8b01-161">**オブジェクト エクスプローラー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-161">In **Object Explorer**.</span></span>  
  
 <span data-ttu-id="a8b01-162">イベント セッションを削除すると、すべての構成情報が削除され、以後、セッションの定義は sys.server_event_sessions カタログ ビューに表示されません。</span><span class="sxs-lookup"><span data-stu-id="a8b01-162">When you delete an event session, all configuration information is removed and the session definition no longer appears in the sys.server_event_sessions catalog view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8b01-163">system_health と AlwaysOn_health はに含まれています。削除しないで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a8b01-163">system_health and AlwaysOn_health are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; do not delete them.</span></span> <span data-ttu-id="a8b01-164">system_health は既定で有効です (詳細については、「 [system_health セッションの使用](use-the-ssms-xe-profiler.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="a8b01-164">system_health is enabled by default (for more information, see [Use the system_health Session](use-the-ssms-xe-profiler.md)).</span></span> <span data-ttu-id="a8b01-165">既定では、AlwaysOn_health はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="a8b01-165">AlwaysOn_health is off by default.</span></span> <span data-ttu-id="a8b01-166">パフォーマンスの問題を診断する際に役立つデータがこれらのセッションによって収集されます。</span><span class="sxs-lookup"><span data-stu-id="a8b01-166">These sessions collect data that can be useful for diagnosing performance issues.</span></span>  
  
 <span data-ttu-id="a8b01-167">拡張イベント セッションを削除するには、ALTER ANY EVENT SESSION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8b01-167">To delete an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="a8b01-168">**オブジェクト エクスプローラー**で拡張イベント セッションを削除するには</span><span class="sxs-lookup"><span data-stu-id="a8b01-168">To delete an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="a8b01-169">**[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="a8b01-169">Expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="a8b01-170">セッションを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-170">Right-click a session and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="a8b01-171">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-171">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="a8b01-172">イベント セッションの編集が終了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8b01-172">After you finish revising the event session, click **OK**.</span></span>  
  
 <span data-ttu-id="a8b01-173">拡張イベント セッションを **クエリ エディター**で削除するには、次のステートメントを発行します。 *session_name* の部分は、削除する拡張イベント セッションの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="a8b01-173">To delete an Extended Events session in the **Query Editor**, Issue the following statements, replacing *session_name* with the name of the Extended Events session that you want to delete:</span></span>  
  
```  
DROP EVENT SESSION [session_name]  
ON SERVER  
```  
  
  
