---
title: Transact-SQL ジョブ ステップのオプションを定義する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc1d6412e52e74ce0c6d987d6189c0c72ffd7df7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712690"
---
# <a name="define-transact-sql-job-step-options"></a><span data-ttu-id="4bd34-102">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="4bd34-102">Define Transact-SQL Job Step Options</span></span>
  <span data-ttu-id="4bd34-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、または SQL Server 管理オブジェクトを使用して、でエージェントのジョブステップのオプションを定義する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-103">This topic describes how to define options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="4bd34-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4bd34-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4bd34-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4bd34-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4bd34-106">Security</span><span class="sxs-lookup"><span data-stu-id="4bd34-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4bd34-107">**Transact-SQL ジョブ ステップのオプションを定義する方法:**</span><span class="sxs-lookup"><span data-stu-id="4bd34-107">**To define Transact-SQL job step options, using:** ,</span></span>  
  
     [<span data-ttu-id="4bd34-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4bd34-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="4bd34-109">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4bd34-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4bd34-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="4bd34-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4bd34-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4bd34-111">Security</span></span>  
 <span data-ttu-id="4bd34-112">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4bd34-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="4bd34-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4bd34-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-transact-sql-job-step-options"></a><span data-ttu-id="4bd34-114">Transact-SQL ジョブ ステップのオプションを定義するには</span><span class="sxs-lookup"><span data-stu-id="4bd34-114">To define Transact-SQL job step options</span></span>  
  
1.  <span data-ttu-id="4bd34-115">**オブジェクト エクスプローラー**で、 **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、編集するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-115">In **Object Explorer**, expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4bd34-116">**[ステップ]** ページをクリックし、ジョブ ステップをクリックして、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-116">Click the **Steps** page, click a job step, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="4bd34-117">**[ジョブ ステップのプロパティ]** ダイアログ ボックスで、ジョブの種類が **[Transact-SQL スクリプト (T-SQL)]** であることを確認し、 **[詳細設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-117">On the **Job Step Properties** dialog, confirm that the job type is **Transact-SQL script (TSQL)**, and then select the **Advanced** page.</span></span>  
  
4.  <span data-ttu-id="4bd34-118">**[成功した場合のアクション]** ボックスで、ジョブが成功した場合に実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-118">Specify an action to take if the job is successful by selecting from the **On success action** list.</span></span>  
  
5.  <span data-ttu-id="4bd34-119">**[再試行回数]** ボックスに 0 ～ 9999 の数値を入力して、再試行回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-119">Specify a number of retry attempts by entering a number from 0 to 9999 into the **Retry attempts** box.</span></span>  
  
6.  <span data-ttu-id="4bd34-120">**[再試行間隔]** ボックスに 0 ～ 9999 の数 (分) を入力して、再試行間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-120">Specify a retry interval by entering a number of minutes from 0 to 9999 into the **Retry interval** box.</span></span>  
  
7.  <span data-ttu-id="4bd34-121">**[失敗した場合のアクション]** ボックスで、ジョブが失敗した場合に実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-121">Specify an action to take if the job fails by choosing from the **On failure action** list.</span></span>  
  
8.  <span data-ttu-id="4bd34-122">ジョブが [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの場合は、以下の方法から選択できます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-122">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="4bd34-123">**[出力ファイル]** ボックスに、出力ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-123">Enter the name of an **Output file**.</span></span> <span data-ttu-id="4bd34-124">既定では、ジョブ ステップの実行ごとに出力ファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-124">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="4bd34-125">出力ファイルを上書きしない場合は、 **[既存のファイルに出力を追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-125">If you do not want the output file overwritten, check **Append output to existing file**.</span></span> <span data-ttu-id="4bd34-126">このオプションは、 **sysadmin** 固定サーバー ロールのメンバーだけが使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-126">This option is only available to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="4bd34-127">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、ユーザーはファイル システム上の任意のファイルを表示できないので、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、ファイル システムに書き込まれたジョブ ステップのログを表示できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4bd34-127">Note that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not allow users to view arbitrary files on the file system, so you cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view job step logs that are written to the file system.</span></span>  
  
    -   <span data-ttu-id="4bd34-128">ジョブ ステップのログをデータベース テーブルに記録する場合は、 **[テーブルにログ記録する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-128">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="4bd34-129">既定では、ジョブ ステップの実行ごとにテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-129">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="4bd34-130">テーブルの内容を上書きしない場合は、 **[テーブル内の既存のエントリに出力を追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-130">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="4bd34-131">ジョブ ステップの実行後にこのテーブルのコンテンツを表示するには、 **[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-131">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="4bd34-132">ステップの履歴に出力を含める場合は、 **[履歴にステップ出力を含める]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4bd34-132">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="4bd34-133">エラーがない場合にのみ、出力は表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bd34-133">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="4bd34-134">また、出力が切り捨てられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bd34-134">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="4bd34-135">**sysadmin** 固定サーバー ロールのメンバーで、このジョブ ステップを別の SQL ログインで実行する場合は、 **[実行時のユーザー]** ボックスで SQL ログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-135">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="4bd34-136">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="4bd34-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="4bd34-137">**Transact-SQL ジョブ ステップのオプションを定義するには**</span><span class="sxs-lookup"><span data-stu-id="4bd34-137">**To define Transact-SQL job step options**</span></span>  
  
 <span data-ttu-id="4bd34-138">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4bd34-138">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
