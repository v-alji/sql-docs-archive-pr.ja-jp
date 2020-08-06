---
title: データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b958b280c358a8aeb752600dee1c2aee31d14db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634557"
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a><span data-ttu-id="921b9-102">データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="921b9-102">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>
  <span data-ttu-id="921b9-103">データベース メール メッセージと添付ファイルのコピーは、データベース メール イベント ログに記録されると同時に、 **msdb** のテーブルに保持されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-103">Copies of Database Mail messages and their attachments are retained in **msdb** tables along with the Database Mail event log.</span></span> <span data-ttu-id="921b9-104">このテーブルのサイズを縮小するためには、不要になったメッセージやイベントを定期的にアーカイブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="921b9-104">Periodically you might want to reduce the size of the tables and archive messages and events that are no longer needed.</span></span> <span data-ttu-id="921b9-105">次の手順では、この処理を自動化する SQL Server エージェント ジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="921b9-105">The following procedures create a SQL Server Agent job to automate the process.</span></span>  
  
-   <span data-ttu-id="921b9-106">**作業を開始する準備:**  、 [前提条件](#Prerequisites)、 [推奨事項](#Recommendations)、 [権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="921b9-106">**Before you begin:**  , [Prerequisites](#Prerequisites), [Recommendations](#Recommendations), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="921b9-107">**データベース メール メッセージおよびログをアーカイブする方法:** [SQL Server エージェント](#Process_Overview)</span><span class="sxs-lookup"><span data-stu-id="921b9-107">**To Archive Database Mail messages and logs using :**  [SQL Server Agent](#Process_Overview)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="921b9-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="921b9-108">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="921b9-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="921b9-109">Prerequisites</span></span>  
 <span data-ttu-id="921b9-110">アーカイブ データを格納する新しいテーブルが、特別なアーカイブ データベース内にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="921b9-110">The new tables to store the archive data might be located in a special archive database.</span></span> <span data-ttu-id="921b9-111">代わりに、行をテキスト ファイルにエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="921b9-111">Alternatively the rows could be exported to a text file.</span></span>  
 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="921b9-112">推奨事項</span><span class="sxs-lookup"><span data-stu-id="921b9-112">Recommendations</span></span>  
 <span data-ttu-id="921b9-113">運用環境では、詳細なエラー チェックを追加したり、ジョブが失敗した場合には電子メール メッセージをオペレーターに送信したりする必要があるでしょう。</span><span class="sxs-lookup"><span data-stu-id="921b9-113">In your production environment, you might want to add additional error checking and send an e-mail message to operators if the job fails.</span></span>  
  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="921b9-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="921b9-114">Permissions</span></span>  
 <span data-ttu-id="921b9-115">このトピックで説明したストアド プロシージャを実行するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="921b9-115">You must be a member of the **sysadmin** fixed server role to execute the stored procedures described in this topic.</span></span>  
  
  
###  <a name="overview-of-the-process"></a><a name="Process_Overview"></a> <span data-ttu-id="921b9-116">プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="921b9-116">Overview of the Process</span></span>  
  
-   <span data-ttu-id="921b9-117">まず、次のステップから構成される "データベース メールのアーカイブ" という名前のジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="921b9-117">The first procedure creates a job named Archive Database Mail with the following steps.</span></span>  
  
    1.  <span data-ttu-id="921b9-118">すべてのメッセージをデータベース メールのテーブルから新しいテーブルにコピーします。新しいテーブルには、**DBMailArchive_** _<年_月>_ の形式で、前の月を表す文字列を付加した名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="921b9-118">Copy all messages from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_**_<year_month>_.</span></span>  
  
    2.  <span data-ttu-id="921b9-119">最初のステップでコピーしたメッセージに関連する添付ファイルをデータベース メールのテーブルから新しいテーブルにコピーします。新しいテーブルには、**DBMailArchive_Attachments_** _<年_月>_ の形式で、前の月を表す文字列を付加した名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="921b9-119">Copy the attachments related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Attachments_**_<year_month>_.</span></span>  
  
    3.  <span data-ttu-id="921b9-120">最初のステップでコピーしたメッセージに関連するデータベース メール イベント ログからのイベントを、データベース メールのテーブルから新しいテーブルにコピーします。新しいテーブルには、**DBMailArchive_Log_** _<年_月>_ の形式で、前の月を表す文字列を付加した名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="921b9-120">Copy the events from the Database Mail event log that are related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Log_**_<year_month>_.</span></span>  
  
    4.  <span data-ttu-id="921b9-121">移し変えたメール アイテムのレコードをデータベース メールのテーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="921b9-121">Delete the records of the transferred mail items from the Database Mail tables.</span></span>  
  
    5.  <span data-ttu-id="921b9-122">移し変えたメール アイテムに関連するイベントをデータベース メールのイベント ログから削除します。</span><span class="sxs-lookup"><span data-stu-id="921b9-122">Delete the events related to the transferred mail items from the Database Mail event log.</span></span>  
  
-   <span data-ttu-id="921b9-123">ジョブが定期的に実行されるようにスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="921b9-123">Schedule the job to run periodically.</span></span>  
 
  
## <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="921b9-124">SQL Server エージェントのジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-124">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="921b9-125">オブジェクト エクスプローラーで [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント] を展開し、 **[ジョブ]** を右クリックして、 **[新しいジョブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-125">In Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, and then click **New Job**.</span></span>  
  
2.  <span data-ttu-id="921b9-126">**[新しいジョブ]** ダイアログ ボックスで、 **[名前]** ボックスに「 **データベース メールのアーカイブ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-126">In the **New Job** dialog box, in the **Name** box, type **Archive Database Mail**.</span></span>  
  
3.  <span data-ttu-id="921b9-127">**[所有者]** ボックスで、所有者が **sysadmin** 固定サーバー ロールのメンバーであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="921b9-127">In the **Owner** box, confirm that the owner is a member of the **sysadmin** fixed server role.</span></span>  
  
4.  <span data-ttu-id="921b9-128">**[カテゴリ]** ボックスで **[データベースのメンテナンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-128">In the **Category** box, click the **Database Maintenance**.</span></span>  
  
5.  <span data-ttu-id="921b9-129">**[説明]** ボックスに「 **データベース メール メッセージのアーカイブ**」と入力し、 **[ステップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-129">In the **Description** box, type **Archive Database Mail messages**, and then click **Steps**.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a><span data-ttu-id="921b9-130">データベース メールのメッセージをアーカイブするステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-130">To create a step to archive the Database Mail messages</span></span>  
  
1.  <span data-ttu-id="921b9-131">**[ステップ]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-131">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="921b9-132">**[ステップ名]** ボックスに「 **データベース メール アイテムのコピー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-132">In the **Step name** box, type **Copy Database Mail Items**.</span></span>  
  
3.  <span data-ttu-id="921b9-133">**[種類]** ボックスで **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-133">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="921b9-134">**[データベース]** ボックスで **[msdb]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-134">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="921b9-135">**[コマンド]** ボックスに次のステートメントを入力します。このステートメントでは、前の月を表す文字列を付加した名前のテーブルが作成されます。このテーブルには、今月の開始日以前の行が格納されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-135">In the **Command** box, type the following statement to create a table named after the previous month, containing rows older than the start of the current month:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="921b9-136">**[OK]** をクリックしてステップを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-136">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a><span data-ttu-id="921b9-137">データベース メールの添付ファイルをアーカイブするステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-137">To create a step to archive the Database Mail attachments</span></span>  
  
1.  <span data-ttu-id="921b9-138">**[ステップ]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-138">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="921b9-139">**[ステップ名]** ボックスに「 **データベース メール添付ファイルのコピー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-139">In the **Step name** box, type **Copy Database Mail Attachments**.</span></span>  
  
3.  <span data-ttu-id="921b9-140">**[種類]** ボックスで **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-140">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="921b9-141">**[データベース]** ボックスで **[msdb]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-141">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="921b9-142">**[コマンド]** ボックスに次のステートメントを入力します。このステートメントでは、前の月を表す文字列を付加した名前の添付ファイル テーブルが作成されます。このテーブルには、前のステップでコピーされたメッセージに対応する添付ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-142">In the **Command** box, type the following statement to create an attachments table named after the previous month, containing the attachments that correspond to the messages transferred in the previous step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="921b9-143">**[OK]** をクリックしてステップを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-143">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a><span data-ttu-id="921b9-144">データベース メールのログをアーカイブするステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-144">To create a step to archive the Database Mail log</span></span>  
  
1.  <span data-ttu-id="921b9-145">**[ステップ]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-145">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="921b9-146">**[ステップ名]** ボックスに「 **データベース メール ログのコピー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-146">In the **Step name** box, type **Copy Database Mail Log**.</span></span>  
  
3.  <span data-ttu-id="921b9-147">**[種類]** ボックスで **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-147">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="921b9-148">**[データベース]** ボックスで **[msdb]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-148">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="921b9-149">**[コマンド]** ボックスに次のステートメントを入力します。このステートメントでは、前の月を表す文字列を付加した名前のログ テーブルが作成されます。このテーブルには、前半のステップでコピーされたメッセージに対応するログ エントリが格納されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-149">In the **Command** box, type the following statement to create a log table named after the previous month, containing the log entries that correspond to the messages transferred in the earlier step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="921b9-150">**[OK]** をクリックしてステップを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-150">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a><span data-ttu-id="921b9-151">データベース メールからアーカイブされた行を削除するステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-151">To create a step to remove the archived rows from Database Mail</span></span>  
  
1.  <span data-ttu-id="921b9-152">**[ステップ]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-152">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="921b9-153">**[ステップ名]** ボックスに「 **データベース メールからの行の削除**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-153">In the **Step name** box, type **Remove rows from Database Mail**.</span></span>  
  
3.  <span data-ttu-id="921b9-154">**[種類]** ボックスで **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-154">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="921b9-155">**[データベース]** ボックスで **[msdb]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-155">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="921b9-156">**[コマンド]** ボックスに次のステートメントを入力します。このステートメントでは、データベース メールのテーブルから今月よりも古い行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-156">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail tables:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  <span data-ttu-id="921b9-157">**[OK]** をクリックしてステップを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-157">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a><span data-ttu-id="921b9-158">データベース メール イベント ログからアーカイブされたアイテムを削除するステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="921b9-158">To create a step to remove the archived items from Database Mail event log</span></span>  
  
1.  <span data-ttu-id="921b9-159">**[ステップ]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-159">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="921b9-160">**[ステップ名]** ボックスに「 **データベース メール イベント ログからの行の削除**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-160">In the **Step Name** box type **Remove rows from Database Mail event log**.</span></span>  
  
3.  <span data-ttu-id="921b9-161">**[種類]** ボックスで **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-161">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="921b9-162">**[コマンド]** ボックスに次のステートメントを入力します。このステートメントでは、データベース メールのイベント ログから今月よりも古い行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="921b9-162">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail event log:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  <span data-ttu-id="921b9-163">**[OK]** をクリックしてステップを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-163">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-schedule-the-job-to-run-periodically"></a><span data-ttu-id="921b9-164">ジョブが定期的に実行されるようにスケジュールを設定するには</span><span class="sxs-lookup"><span data-stu-id="921b9-164">To schedule the job to run periodically</span></span>  
  
1.  <span data-ttu-id="921b9-165">**[新しいジョブ]** ダイアログ ボックスで **[スケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-165">In the **New Job** dialog box, click **Schedules**.</span></span>  
  
2.  <span data-ttu-id="921b9-166">**[スケジュール]** ページで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-166">On the **Schedules** page, click **New**.</span></span>  
  
3.  <span data-ttu-id="921b9-167">**[名前]** ボックスに「 **データベース メールのアーカイブ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="921b9-167">In the **Name** box, type **Archive Database Mail**.</span></span>  
  
4.  <span data-ttu-id="921b9-168">**[スケジュールの種類]** ボックスで **[定期的]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="921b9-168">In the **Schedule type** box, select **Recurring**.</span></span>  
  
5.  <span data-ttu-id="921b9-169">**[頻度]** 領域で、たとえば毎月 1 回など、定期的にジョブを実行するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="921b9-169">In the **Frequency** area, select the options to run the job periodically, for example once every month.</span></span>  
  
6.  <span data-ttu-id="921b9-170">**[一日のうちの頻度]** 領域で、 **[1 回: \<time>]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="921b9-170">In the **Daily frequency** area, select **Occurs once at \<time>**.</span></span>  
  
7.  <span data-ttu-id="921b9-171">その他のオプションが目的どおりに構成されていることを確認し、 **[OK]** をクリックしてスケジュールを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-171">Verify that the other options are configured as you wish, and then click **OK** to save the schedule.</span></span>  
  
8.  <span data-ttu-id="921b9-172">**[OK]** をクリックしてジョブを保存します。</span><span class="sxs-lookup"><span data-stu-id="921b9-172">Click **OK** to save the job.</span></span>  
  
  
  
  
