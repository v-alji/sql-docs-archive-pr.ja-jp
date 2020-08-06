---
title: オペレーターの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfe07042f9a4b8ac595ada8b86e7bad131032700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715058"
---
# <a name="create-an-operator"></a><span data-ttu-id="84081-102">オペレーターの作成</span><span class="sxs-lookup"><span data-stu-id="84081-102">Create an Operator</span></span>
  <span data-ttu-id="84081-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントジョブに関する通知を受信するようにユーザーを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="84081-103">This topic describes how to configure a user to receive notifications about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="84081-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="84081-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="84081-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="84081-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84081-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="84081-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="84081-107">Security</span><span class="sxs-lookup"><span data-stu-id="84081-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="84081-108">**オペレーターを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="84081-108">**To create an operator, using:**</span></span>  
  
     [<span data-ttu-id="84081-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84081-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="84081-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84081-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84081-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="84081-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="84081-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="84081-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="84081-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからポケットベル オプションと **net send** オプションが削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="84081-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="84081-114">新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="84081-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="84081-115">SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84081-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="84081-116">詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84081-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="84081-117">は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="84081-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84081-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="84081-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="84081-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="84081-119">Permissions</span></span>  
 <span data-ttu-id="84081-120">オペレーターを作成できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="84081-120">Only members of the **sysadmin** fixed server role can create operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="84081-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="84081-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="84081-122">オペレーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="84081-122">To create an operator</span></span>  
  
1.  <span data-ttu-id="84081-123">**オブジェクト エクスプ ローラー**で、SQL Server エージェント オペレーターを作成するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="84081-123">In **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent operator.</span></span>  
  
2.  <span data-ttu-id="84081-124">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="84081-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="84081-125">**[オペレーター]** フォルダーを右クリックし、 **[新しいオペレーター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="84081-125">Right-click the **Operators** folder and select **New Operator**.</span></span>  
  
     <span data-ttu-id="84081-126">**[新しいオペレーター]** ダイアログ ボックスの **[全般]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="84081-126">The following options are available on the **General** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="84081-127">**名前**</span><span class="sxs-lookup"><span data-stu-id="84081-127">**Name**</span></span>  
     <span data-ttu-id="84081-128">オペレーターの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="84081-128">Change the name of the operator.</span></span>  
  
     <span data-ttu-id="84081-129">**有効**</span><span class="sxs-lookup"><span data-stu-id="84081-129">**Enabled**</span></span>  
     <span data-ttu-id="84081-130">オペレーターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="84081-130">Enable the operator.</span></span> <span data-ttu-id="84081-131">有効になっていない場合は、オペレーターに通知が送信されません。</span><span class="sxs-lookup"><span data-stu-id="84081-131">When not enabled, no notifications are sent to the operator.</span></span>  
  
     <span data-ttu-id="84081-132">**[電子メール名]**</span><span class="sxs-lookup"><span data-stu-id="84081-132">**E-mail name**</span></span>  
     <span data-ttu-id="84081-133">オペレーターの電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="84081-133">Specifies the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="84081-134">**[Net Send アドレス]**</span><span class="sxs-lookup"><span data-stu-id="84081-134">**Net send address**</span></span>  
     <span data-ttu-id="84081-135">**net send**に使用するアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="84081-135">Specify the address to use for **net send**.</span></span>  
  
     <span data-ttu-id="84081-136">**[ポケットベル用電子メール ログイン名]**</span><span class="sxs-lookup"><span data-stu-id="84081-136">**Pager e-mail name**</span></span>  
     <span data-ttu-id="84081-137">オペレーターのポケットベルに使用する電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="84081-137">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
     <span data-ttu-id="84081-138">**[ポケットベルの受信スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="84081-138">**Pager on duty schedule**</span></span>  
     <span data-ttu-id="84081-139">ポケットベルをアクティブにする時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="84081-139">Sets the times at which the pager is active.</span></span>  
  
     <span data-ttu-id="84081-140">**[月曜日] ～ [日曜日]**</span><span class="sxs-lookup"><span data-stu-id="84081-140">**Monday - Sunday**</span></span>  
     <span data-ttu-id="84081-141">ポケットベルをアクティブにする日を選択します。</span><span class="sxs-lookup"><span data-stu-id="84081-141">Select the days that the pager is active.</span></span>  
  
     <span data-ttu-id="84081-142">**[始業時刻]**</span><span class="sxs-lookup"><span data-stu-id="84081-142">**Workday begin**</span></span>  
     <span data-ttu-id="84081-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがポケットベルへのメッセージ送信を開始する時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="84081-143">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
     <span data-ttu-id="84081-144">**[終業時刻]**</span><span class="sxs-lookup"><span data-stu-id="84081-144">**Workday end**</span></span>  
     <span data-ttu-id="84081-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがポケットベルへのメッセージ送信を終了する時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="84081-145">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
     <span data-ttu-id="84081-146">**[新しいオペレーター]** ダイアログ ボックスの **[通知]** ページでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="84081-146">The following options are available on the **Notifications** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="84081-147">**アラート**</span><span class="sxs-lookup"><span data-stu-id="84081-147">**Alerts**</span></span>  
     <span data-ttu-id="84081-148">インスタンス内の警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="84081-148">View the alerts in the instance.</span></span>  
  
     <span data-ttu-id="84081-149">**ジョブ**</span><span class="sxs-lookup"><span data-stu-id="84081-149">**Jobs**</span></span>  
     <span data-ttu-id="84081-150">インスタンス内のジョブを表示します。</span><span class="sxs-lookup"><span data-stu-id="84081-150">View the jobs in the instance.</span></span>  
  
     <span data-ttu-id="84081-151">**アラートの一覧**</span><span class="sxs-lookup"><span data-stu-id="84081-151">**Alert list**</span></span>  
     <span data-ttu-id="84081-152">インスタンス内の警告を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="84081-152">Lists the alerts in the instance.</span></span>  
  
     <span data-ttu-id="84081-153">**ジョブ一覧**</span><span class="sxs-lookup"><span data-stu-id="84081-153">**Job list**</span></span>  
     <span data-ttu-id="84081-154">インスタンス内のジョブを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="84081-154">Lists the jobs in the instance.</span></span>  
  
     <span data-ttu-id="84081-155">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="84081-155">**E-mail**</span></span>  
     <span data-ttu-id="84081-156">電子メールを使用してこのオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="84081-156">Notify this operator using e-mail.</span></span>  
  
     <span data-ttu-id="84081-157">**ポケットベル**</span><span class="sxs-lookup"><span data-stu-id="84081-157">**Pager**</span></span>  
     <span data-ttu-id="84081-158">電子メールをポケット ベルに送信することによって、このオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="84081-158">Notify this operator by sending e-mail to the pager address.</span></span>  
  
     <span data-ttu-id="84081-159">**Net send**</span><span class="sxs-lookup"><span data-stu-id="84081-159">**Net send**</span></span>  
     <span data-ttu-id="84081-160">**net send**を使用してこのオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="84081-160">Notify this operator using **net send**.</span></span>  
  
4.  <span data-ttu-id="84081-161">新しいオペレーターの作成が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84081-161">When finished creating the new operator, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="84081-162">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="84081-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="84081-163">オペレーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="84081-163">To create an operator</span></span>  
  
1.  <span data-ttu-id="84081-164">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="84081-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="84081-165">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84081-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="84081-166">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84081-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 <span data-ttu-id="84081-167">詳細については、「 [sp_add_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84081-167">For more information, see [sp_add_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).</span></span>  
  
  
