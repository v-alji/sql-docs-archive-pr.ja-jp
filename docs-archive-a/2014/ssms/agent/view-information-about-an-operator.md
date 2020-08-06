---
title: オペレーターに関する情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 680b90401f800a9c435bdae33b8e55385541cc4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634775"
---
# <a name="view-information-about-an-operator"></a><span data-ttu-id="1ffb8-102">View Information About an Operator</span><span class="sxs-lookup"><span data-stu-id="1ffb8-102">View Information About an Operator</span></span>
  <span data-ttu-id="1ffb8-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] またはを使用して、エージェントオペレーターに関する情報を表示する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-103">This topic describes how to view information about a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1ffb8-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1ffb8-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1ffb8-106">Security</span><span class="sxs-lookup"><span data-stu-id="1ffb8-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1ffb8-107">**オペレーターに関する情報を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-107">**To view information about an operator, using:**</span></span>  
  
     [<span data-ttu-id="1ffb8-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1ffb8-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1ffb8-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ffb8-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ffb8-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="1ffb8-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ffb8-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1ffb8-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ffb8-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="1ffb8-112">Permissions</span></span>  
 <span data-ttu-id="1ffb8-113">既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-113">By default, members of the **sysadmin** fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="1ffb8-114">他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-114">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="1ffb8-115">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-115">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="1ffb8-116">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-116">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="1ffb8-117">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="1ffb8-117">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="1ffb8-118">これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-118">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1ffb8-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1ffb8-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="1ffb8-120">オペレーターに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="1ffb8-120">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="1ffb8-121">**オブジェクト エクスプローラー**で、表示するオペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-121">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to view.</span></span>  
  
2.  <span data-ttu-id="1ffb8-122">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1ffb8-123">プラス記号をクリックして **[オペレーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-123">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="1ffb8-124">表示するオペレーターを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-124">Right-click the operator that you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="1ffb8-125">[ _Operator_name_の**プロパティ**] ダイアログボックスに表示される使用可能なオプションの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-125">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   <span data-ttu-id="1ffb8-126">[[オペレーターのプロパティ] と [新しいオペレーター] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="1ffb8-126">[Operator Properties and New Operator &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
    -   [<span data-ttu-id="1ffb8-127">オペレーターのプロパティ: 新しいオペレーター &#40;通知ページ&#41;</span><span class="sxs-lookup"><span data-stu-id="1ffb8-127">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   <span data-ttu-id="1ffb8-128">[[オペレーターのプロパティ] ([履歴] ページ)](operator-properties-history-page.md)</span><span class="sxs-lookup"><span data-stu-id="1ffb8-128">[Operator Properties &#40;History Page&#41;](operator-properties-history-page.md)</span></span>  
  
5.  <span data-ttu-id="1ffb8-129">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1ffb8-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1ffb8-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="1ffb8-131">オペレーターに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="1ffb8-131">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="1ffb8-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ffb8-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1ffb8-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about operator Fran??ois Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'Fran??ois Ajenstat' ;  
    GO  
    ```  
  
 <span data-ttu-id="1ffb8-135">詳細については、「 [sp_help_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ffb8-135">For more information, see [sp_help_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql).</span></span>  
  
  
