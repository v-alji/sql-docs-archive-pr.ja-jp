---
title: オペレーターへの警告の割り当て | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cc238b952c03595035856f377b6fdbb9eaf5e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640332"
---
# <a name="assign-alerts-to-an-operator"></a><span data-ttu-id="eb42a-102">オペレーターへの警告の割り当て</span><span class="sxs-lookup"><span data-stu-id="eb42a-102">Assign Alerts to an Operator</span></span>
  <span data-ttu-id="eb42a-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、エージェントの警告をオペレーターに割り当てて、でジョブに関する通知を受信できるようにする方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="eb42a-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts to operators so they can receive notifications about jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb42a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="eb42a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb42a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="eb42a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb42a-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eb42a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eb42a-107">Security</span><span class="sxs-lookup"><span data-stu-id="eb42a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eb42a-108">**オペレーターに警告を割り当てる方法:**</span><span class="sxs-lookup"><span data-stu-id="eb42a-108">**To assign alerts to an operator, using:**</span></span>  
  
     [<span data-ttu-id="eb42a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb42a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb42a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb42a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb42a-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="eb42a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eb42a-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eb42a-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="eb42a-113">は、警告システム全体を簡単に管理できるグラフィカルなツールです。</span><span class="sxs-lookup"><span data-stu-id="eb42a-113">provides an easy, graphical way to manage the entire alerting system.</span></span> <span data-ttu-id="eb42a-114">警告システムを構成するときには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eb42a-114">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is the recommended way to configure your alert infrastructure.</span></span>  
  
-   <span data-ttu-id="eb42a-115">警告に対応して通知を送るには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがメールを送れるようにあらかじめ構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb42a-115">To send a notification in response to an alert, you must first configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send mail.</span></span> <span data-ttu-id="eb42a-116">詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb42a-116">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
-   <span data-ttu-id="eb42a-117">電子メールのメッセージやポケットベルによる通知に失敗した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス エラー ログに失敗がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="eb42a-117">If a failure occurs when sending an e-mail message or pager notification, the failure is reported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service error log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb42a-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eb42a-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb42a-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="eb42a-119">Permissions</span></span>  
 <span data-ttu-id="eb42a-120">オペレーターに警告を割り当てることができるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="eb42a-120">Only members of the **sysadmin** fixed server role can assign alerts to operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb42a-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="eb42a-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="eb42a-122">オペレーターに警告を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="eb42a-122">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="eb42a-123">**オブジェクト エクスプローラー**で、警告を割り当てるオペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator to which you want to assign an alert.</span></span>  
  
2.  <span data-ttu-id="eb42a-124">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="eb42a-125">プラス記号をクリックして **[オペレーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="eb42a-126">警告を割り当てるオペレーターを右クリックし、 **[プロパティ]** を選択して、 **[通知]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-126">Right-click the operator to which you want to assign an alert and select **Properties**, and select the **Notifications** page.</span></span>  
  
5.  <span data-ttu-id="eb42a-127">[_operator_name_**のプロパティ]** ダイアログ ボックスで、**[ページの選択]** の **[通知]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-127">In the _operator_name_**Properties** dialog box, under **Select a page**, select **Notifications**.</span></span>  
  
6.  <span data-ttu-id="eb42a-128">**[このユーザーに送信された通知の表示方法]** で、 **[警告]** を選択してこのオペレーターに送信する警告の一覧を表示するか、または **[ジョブ]** を選択してこのオペレーターに通知を送信するジョブの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-128">Under **View notifications sent to this user by**, select **Alerts** to view a list of alerts sent to this operator or select **Jobs** to view a list of jobs that send notifications to this operator.</span></span> <span data-ttu-id="eb42a-129">**[電子メール]**、 **[ポケットベル]**、 **[Net Send]** のチェック ボックスの中から 1 つ以上を選択し、必要に応じて通知ごとに通知方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-129">Select one or more of the following checkboxes to define the notification method for each notification as necessary: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="eb42a-130">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb42a-130">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb42a-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="eb42a-131">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="eb42a-132">オペレーターに警告を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="eb42a-132">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="eb42a-133">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eb42a-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb42a-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb42a-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb42a-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb42a-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="eb42a-136">詳細については、「 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb42a-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
