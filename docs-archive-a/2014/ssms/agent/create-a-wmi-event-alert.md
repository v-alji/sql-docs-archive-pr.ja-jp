---
title: WMI イベント警告の作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: stevestein
ms.author: sstein
ms.openlocfilehash: 737e7ccac9c92e663040e71339aa120f8db8b80b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642504"
---
# <a name="create-a-wmi-event-alert"></a><span data-ttu-id="305aa-102">Create a WMI Event Alert</span><span class="sxs-lookup"><span data-stu-id="305aa-102">Create a WMI Event Alert</span></span>
  <span data-ttu-id="305aa-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、WMI Provider for Server Events によって監視されている特定の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] イベントが発生したときに通知される [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェントの警告を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="305aa-103">This topic describes how to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] event occurs that is monitored by the WMI Provider for Server Events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="305aa-104">WMI プロバイダーを使用したイベントの監視の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [wmi Provider For Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="305aa-104">For information about the using the WMI Provider to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span> <span data-ttu-id="305aa-105">WMI イベント警告の通知を受信するために必要な権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="305aa-105">For information about the permissions necessary to receive WMI event alert notifications, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span> <span data-ttu-id="305aa-106">WQL の詳細については、「 [WMI Provider for Server Events と WQL の使用](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="305aa-106">For more information about WQL, see [Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).</span></span>  
  
 <span data-ttu-id="305aa-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="305aa-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="305aa-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="305aa-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="305aa-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="305aa-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="305aa-110">Security</span><span class="sxs-lookup"><span data-stu-id="305aa-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="305aa-111">**WMI イベント警告を作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="305aa-111">**To create a WMI event alert, using:**</span></span>  
  
     [<span data-ttu-id="305aa-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="305aa-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="305aa-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="305aa-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="305aa-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="305aa-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="305aa-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="305aa-115">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="305aa-116">は、警告システム全体を簡単に管理できるグラフィカルなツールです。警告の基本構成を設定するには、SQL Server Management Studio を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="305aa-116">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="305aa-117">**xp_logevent** で生成されたイベントは master データベースで発生します。</span><span class="sxs-lookup"><span data-stu-id="305aa-117">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="305aa-118">このため、 **xp_logevent** では、警告の **@database_name** が **'master'** または NULL になっていないと、警告が起動されません。</span><span class="sxs-lookup"><span data-stu-id="305aa-118">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="305aa-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されているコンピューター上の WMI 名前空間だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="305aa-119">Only WMI namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="305aa-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="305aa-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="305aa-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="305aa-121">Permissions</span></span>  
 <span data-ttu-id="305aa-122">既定では、 **sp_add_alert** を実行できるのは、 **sysadmin**固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="305aa-122">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="305aa-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="305aa-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="305aa-124">WMI イベント警告を作成するには</span><span class="sxs-lookup"><span data-stu-id="305aa-124">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="305aa-125">**オブジェクト エクスプローラー** で、プラス記号をクリックして、WMI イベントの警告を作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="305aa-125">In **Object Explorer,** click the plus sign to expand the server where you want to create a WMI event alert.</span></span>  
  
2.  <span data-ttu-id="305aa-126">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="305aa-126">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="305aa-127">**[警告]** を右クリックし、 **[新しい警告]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="305aa-127">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="305aa-128">**[新しい警告]** ダイアログ ボックスで、 **[名前]** ボックスに新しい警告の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="305aa-128">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="305aa-129">**[有効化]** チェック ボックスをオンにして、実行する警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="305aa-129">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="305aa-130">既定では、 **[有効化]** チェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="305aa-130">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="305aa-131">**[種類]** ボックスの一覧の **[WMI イベント警告]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="305aa-131">In the **Type** list, select **WMI event alert**.</span></span>  
  
7.  <span data-ttu-id="305aa-132">**[WMI イベント警告定義]** の **[名前空間]** ボックスで、この警告を発生させる WMI イベントを識別する WQL (WMI Query Language) ステートメントの WMI 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="305aa-132">Under **WMI event alert definition**, in the **Namespace** box, specify the WMI namespace for the WMI Query Language (WQL) statement that identifies which WMI event will trigger this alert.</span></span>  
  
8.  <span data-ttu-id="305aa-133">**[クエリ]** ボックスで、警告が応答するイベントを識別する WQL ステートメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="305aa-133">In the **Query** box, specify the WQL statement that identifies the event that this alert responds to.</span></span>  
  
9. <span data-ttu-id="305aa-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="305aa-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="305aa-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="305aa-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="305aa-136">WMI イベント警告を作成するには</span><span class="sxs-lookup"><span data-stu-id="305aa-136">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="305aa-137">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="305aa-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="305aa-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="305aa-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="305aa-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="305aa-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information...',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
 <span data-ttu-id="305aa-140">詳細については、「 [sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="305aa-140">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
