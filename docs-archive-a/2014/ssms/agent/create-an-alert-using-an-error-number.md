---
title: エラー番号を使用して警告を作成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- alerts [SQL Server], error numbers
ms.assetid: 03dd7fac-5073-4f86-babd-37e45a86023c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a98f64bc5b9dffc3e2494a0c36c8fc04cdfb6fa2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641967"
---
# <a name="create-an-alert-using-an-error-number"></a><span data-ttu-id="fae29-102">エラー番号を使用して警告を作成する</span><span class="sxs-lookup"><span data-stu-id="fae29-102">Create an Alert Using an Error Number</span></span>
  <span data-ttu-id="fae29-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して特定の番号のエラーが発生した場合に発生するエージェント警告の作成方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fae29-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert occurs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that will be raised when an error of a specific number occurs by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fae29-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="fae29-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fae29-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="fae29-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fae29-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fae29-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fae29-107">Security</span><span class="sxs-lookup"><span data-stu-id="fae29-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fae29-108">**エラー番号を使用する警告を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="fae29-108">**To create an alert using an error number, using:**</span></span>  
  
     [<span data-ttu-id="fae29-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fae29-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fae29-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fae29-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fae29-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="fae29-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fae29-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fae29-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="fae29-113">は、警告システム全体を簡単に管理できるグラフィカルなツールです。警告の基本構成を設定するには、SQL Server Management Studio を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fae29-113">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="fae29-114">**xp_logevent** で生成されたイベントは master データベースで発生します。</span><span class="sxs-lookup"><span data-stu-id="fae29-114">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="fae29-115">このため、 **xp_logevent** では、警告の **@database_name** が **'master'** または NULL になっていないと、警告が起動されません。</span><span class="sxs-lookup"><span data-stu-id="fae29-115">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fae29-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fae29-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fae29-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="fae29-117">Permissions</span></span>  
 <span data-ttu-id="fae29-118">既定では、 **sp_add_alert** を実行できるのは、 **sysadmin**固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="fae29-118">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fae29-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="fae29-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-alert-using-an-error-number"></a><span data-ttu-id="fae29-120">エラー番号を使用して警告を作成するには</span><span class="sxs-lookup"><span data-stu-id="fae29-120">To create an alert using an error number</span></span>  
  
1.  <span data-ttu-id="fae29-121">**オブジェクト エクスプローラー** で、プラス記号をクリックして、エラー番号を使用する警告を作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="fae29-121">In **Object Explorer,** click the plus sign to expand the server where you want to create an alert using an error number.</span></span>  
  
2.  <span data-ttu-id="fae29-122">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="fae29-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="fae29-123">**[警告]** を右クリックし、 **[新しい警告]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fae29-123">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="fae29-124">**[新しい警告]** ダイアログ ボックスで、 **[名前]** ボックスに新しい警告の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fae29-124">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="fae29-125">**[有効化]** チェック ボックスをオンにして、実行する警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fae29-125">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="fae29-126">既定では、 **[有効化]** チェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="fae29-126">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="fae29-127">**[種類]** ボックスの一覧の **[SQL Server イベント警告]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fae29-127">In the **Type** list, select **SQL Server event alert**.</span></span>  
  
7.  <span data-ttu-id="fae29-128">**[イベント警告定義]** で、 **[データベース名]** ボックスの一覧からデータベースを選択して、警告を特定のデータベースに限定します。</span><span class="sxs-lookup"><span data-stu-id="fae29-128">Under **Event alert definition**, in the **Database name** list, select a database to restrict the alert to a specific database.</span></span>  
  
8.  <span data-ttu-id="fae29-129">**[警告が発生する条件]** の **[エラー番号]** をクリックし、その警告の有効なエラー番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="fae29-129">Under **Alerts will be raised based on**, click **Error number**, and then type a valid error number for the alert.</span></span> <span data-ttu-id="fae29-130">または、 **[重大度]** をクリックし、警告を発生させる重大度を選択します。</span><span class="sxs-lookup"><span data-stu-id="fae29-130">Alternately, click **Severity** and then select the specific severity that will raise the alert.</span></span>  
  
9. <span data-ttu-id="fae29-131">特定の文字列が含まれている場合のみ警告を生成するには、 **[メッセージに次の内容が含まれている場合に警告する]** チェック ボックスをオンにし、 **[メッセージ テキスト]** ボックスにキーワードまたは文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="fae29-131">Check the box corresponding to **Raise alert when message contains** check box to restrict the alert to a particular character sequence, and then enter a keyword or character string for the **Message text**.</span></span> <span data-ttu-id="fae29-132">最大文字数は 100 文字です。</span><span class="sxs-lookup"><span data-stu-id="fae29-132">The maximum number of characters is 100.</span></span>  
  
10. <span data-ttu-id="fae29-133">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fae29-133">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fae29-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fae29-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-alert-using-an-error-number"></a><span data-ttu-id="fae29-135">エラー番号を使用して警告を作成するには</span><span class="sxs-lookup"><span data-stu-id="fae29-135">To create an alert using an error number</span></span>  
  
1.  <span data-ttu-id="fae29-136">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fae29-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fae29-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fae29-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fae29-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fae29-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 <span data-ttu-id="fae29-139">詳細については、「 [sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fae29-139">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
