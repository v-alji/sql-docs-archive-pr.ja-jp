---
title: 警告への応答の定義 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
ms.openlocfilehash: c14e5adf43602b57697483b9ce4c2cdf20ff8e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715033"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a><span data-ttu-id="74b18-102">Define the Response to an Alert (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="74b18-102">Define the Response to an Alert (SQL Server Management Studio)</span></span>
  <span data-ttu-id="74b18-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] またはを使用して、でエージェントの警告に応答する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方法を定義する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="74b18-103">This topic describes how to define how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] responds to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="74b18-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="74b18-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="74b18-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="74b18-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="74b18-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="74b18-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="74b18-107">Security</span><span class="sxs-lookup"><span data-stu-id="74b18-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="74b18-108">**警告に対する応答を定義する方法:**</span><span class="sxs-lookup"><span data-stu-id="74b18-108">**To define the response to an alert, using:**</span></span>  
  
     [<span data-ttu-id="74b18-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="74b18-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="74b18-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="74b18-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="74b18-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="74b18-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="74b18-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="74b18-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="74b18-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからポケットベル オプションと **net send** オプションが削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="74b18-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74b18-114">新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="74b18-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="74b18-115">SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74b18-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="74b18-116">詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b18-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="74b18-117">は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="74b18-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="74b18-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="74b18-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="74b18-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="74b18-119">Permissions</span></span>  
 <span data-ttu-id="74b18-120">警告に対する応答を定義できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="74b18-120">Only members of the **sysadmin** fixed server role can define the response to an alert.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="74b18-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="74b18-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="74b18-122">警告に対する応答を定義するには</span><span class="sxs-lookup"><span data-stu-id="74b18-122">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="74b18-123">**オブジェクト エクスプローラー**で、応答を定義する警告を格納するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="74b18-123">In **Object Explorer**, click the plus sign to expand the server that contains the alert on which you want to define a response.</span></span>  
  
2.  <span data-ttu-id="74b18-124">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="74b18-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="74b18-125">プラス記号をクリックして **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="74b18-125">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="74b18-126">応答を定義する警告を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74b18-126">Right-click the alert on which you want to define a response and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="74b18-127">[_alert_name_**警告のプロパティ**] ダイアログ ボックスで、**[ページの選択]** から **[応答]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74b18-127">In the _alert_name_**alert properties** dialog box, under **Select a page**, select **Response**.</span></span>  
  
6.  <span data-ttu-id="74b18-128">**[ジョブの実行]** チェック ボックスをオンにし、 **[ジョブの実行]** チェック ボックスの下に表示されている一覧から、警告の発生時に実行するジョブを選択します。</span><span class="sxs-lookup"><span data-stu-id="74b18-128">Select the **Execute job** check box and, from the list below the **Execute job** check box, select a job to execute when the alert occurs.</span></span> <span data-ttu-id="74b18-129">**[新しいジョブ]** をクリックすることで、新しいジョブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="74b18-129">You can create a new job by clicking **New Job**.</span></span> <span data-ttu-id="74b18-130">**[ジョブの表示]** をクリックすると、ジョブに関するより詳しい情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="74b18-130">You can view more information about the job by clicking **View Job**.</span></span> <span data-ttu-id="74b18-131">**[新しいジョブ]** ダイアログ ボックスと [**ジョブのプロパティ**_job_name_] ダイアログ ボックスで使用できるオプションの詳細については、「[ジョブの作成](create-a-job.md)」と「[ジョブの表示](view-a-job.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b18-131">For more information about the available options in the **New Job** and **Job Properties**_job_name_ dialog boxes, see [Create a Job](create-a-job.md) and [View a Job](view-a-job.md).</span></span>  
  
7.  <span data-ttu-id="74b18-132">警告がアクティブになったときにオペレーターに通知する場合は、 **[オペレーターに通知する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="74b18-132">Select the **Notify Operators** check box if you want to notify operators when the alert is activated.</span></span> <span data-ttu-id="74b18-133">**[オペレーター一覧]** の **[電子メール]**、 **[ポケットベル]**、 **[Net Send]** から、オペレーターに通知する方法を選択します (複数選択可)。</span><span class="sxs-lookup"><span data-stu-id="74b18-133">In the **Operator list**, select one or more of the following methods for notifying the operator or operators: **E-mail**, **Pager**, or **Net Send**.</span></span> <span data-ttu-id="74b18-134">**[新しいオペレーター]** をクリックすることで、新しいオペレーターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="74b18-134">You can create a new operator by clicking **New Operator**.</span></span> <span data-ttu-id="74b18-135">**[オペレーターの表示]** をクリックすることで、オペレーターに関するより詳しい情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="74b18-135">You can view more information about an operator by clicking **View Operator**.</span></span> <span data-ttu-id="74b18-136">**[新しいオペレーター]** ダイアログ ボックスと **[オペレーターのプロパティの表示]** ダイアログ ボックスで使用できるオプションの詳細については、「 [Create an Operator](create-an-operator.md) 」と「 [View Information About an Operator](view-information-about-an-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b18-136">For more information about the available options in the **New Operator** and **View Operator Properties** dialog boxes, see [Create an Operator](create-an-operator.md) and [View Information About an Operator](view-information-about-an-operator.md).</span></span>  
  
8.  <span data-ttu-id="74b18-137">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b18-137">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="74b18-138">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="74b18-138">Using Transact-SQL</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="74b18-139">警告に対する応答を定義するには</span><span class="sxs-lookup"><span data-stu-id="74b18-139">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="74b18-140">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="74b18-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="74b18-141">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b18-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="74b18-142">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74b18-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="74b18-143">詳細については、「 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b18-143">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
