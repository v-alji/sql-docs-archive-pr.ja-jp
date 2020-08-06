---
title: オペレーターの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45ffb520e240dfd97002060370ff6dcf7c60d083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631477"
---
# <a name="edit-an-operator"></a><span data-ttu-id="c6bcc-102">Edit an Operator</span><span class="sxs-lookup"><span data-stu-id="c6bcc-102">Edit an Operator</span></span>
  <span data-ttu-id="c6bcc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、通知の受信や通知用の電子メール アドレス、ポケットベル アドレス、Net SEND アドレスなど、オペレーターの可用性を編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-103">This topic describes how to edit an operators' availability for receiving notifications and their e-mail, pager, and net send addresses in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c6bcc-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c6bcc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c6bcc-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c6bcc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c6bcc-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c6bcc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c6bcc-107">Security</span><span class="sxs-lookup"><span data-stu-id="c6bcc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c6bcc-108">**オペレーターを編集する方法:**</span><span class="sxs-lookup"><span data-stu-id="c6bcc-108">**To edit an operator, using:**</span></span>  
  
     [<span data-ttu-id="c6bcc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c6bcc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c6bcc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c6bcc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c6bcc-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="c6bcc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c6bcc-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c6bcc-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c6bcc-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからポケットベル オプションと **net send** オプションが削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c6bcc-114">新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="c6bcc-115">SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="c6bcc-116">詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c6bcc-117">は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c6bcc-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c6bcc-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c6bcc-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="c6bcc-119">Permissions</span></span>  
 <span data-ttu-id="c6bcc-120">オペレーターを編集できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-120">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c6bcc-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c6bcc-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="c6bcc-122">オペレーターを編集するには</span><span class="sxs-lookup"><span data-stu-id="c6bcc-122">To edit an operator</span></span>  
  
1.  <span data-ttu-id="c6bcc-123">**オブジェクト エクスプローラー**で、編集するオペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to edit.</span></span>  
  
2.  <span data-ttu-id="c6bcc-124">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="c6bcc-125">プラス記号をクリックして **[オペレーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="c6bcc-126">編集するオペレーターを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-126">Right-click the operator that you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="c6bcc-127">[ _Operator_name_の**プロパティ**] ダイアログボックスに表示される使用可能なオプションの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-127">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   <span data-ttu-id="c6bcc-128">[[オペレーターのプロパティ] と [新しいオペレーター] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="c6bcc-128">[Operator Properties and New Operator &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
    -   [<span data-ttu-id="c6bcc-129">オペレーターのプロパティ: 新しいオペレーター &#40;通知ページ&#41;</span><span class="sxs-lookup"><span data-stu-id="c6bcc-129">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   <span data-ttu-id="c6bcc-130">[[オペレーターのプロパティ] ([履歴] ページ)](operator-properties-history-page.md)</span><span class="sxs-lookup"><span data-stu-id="c6bcc-130">[Operator Properties &#40;History Page&#41;](operator-properties-history-page.md)</span></span>  
  
5.  <span data-ttu-id="c6bcc-131">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c6bcc-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c6bcc-132">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="c6bcc-133">オペレーターを編集するには</span><span class="sxs-lookup"><span data-stu-id="c6bcc-133">To edit an operator</span></span>  
  
1.  <span data-ttu-id="c6bcc-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6bcc-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c6bcc-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.) when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 1,  
        @email_address = N'fran??oisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
 <span data-ttu-id="c6bcc-137">詳細については、「 [sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6bcc-137">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
