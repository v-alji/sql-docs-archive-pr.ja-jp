---
title: 警告を無効化または再有効化する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], reactivating
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- alerts [SQL Server], disabling
- reactivating alerts
- removing alerts
ms.assetid: 4cb37dc6-1134-405d-8590-58b44dcf63b2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3eec4ea7288f4847c0e9b861d80f23eb9c9ddba8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719419"
---
# <a name="disable-or-reactivate-an-alert"></a><span data-ttu-id="9d9e5-102">Disable or Reactivate an Alert</span><span class="sxs-lookup"><span data-stu-id="9d9e5-102">Disable or Reactivate an Alert</span></span>
  <span data-ttu-id="9d9e5-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントの警告を無効化または再アクティブ化する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-103">This topic describes how to disable or reactivate a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9d9e5-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9d9e5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9d9e5-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9d9e5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9d9e5-106">Security</span><span class="sxs-lookup"><span data-stu-id="9d9e5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9d9e5-107">**警告を無効化または再有効化する方法:**</span><span class="sxs-lookup"><span data-stu-id="9d9e5-107">**To disable or reactivate an alert, using:**</span></span>  
  
     [<span data-ttu-id="9d9e5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9d9e5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9d9e5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9d9e5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9d9e5-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="9d9e5-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9d9e5-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9d9e5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9d9e5-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="9d9e5-112">Permissions</span></span>  
 <span data-ttu-id="9d9e5-113">既定では、警告の情報を編集できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="9d9e5-114">それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9d9e5-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9d9e5-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="9d9e5-116">警告を無効にしたり、再び有効にするには</span><span class="sxs-lookup"><span data-stu-id="9d9e5-116">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="9d9e5-117">**オブジェクト エクスプローラー**で、無効化または再有効化する警告を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-117">In **Object Explorer**, click the plus sign to expand server that contains the alert you wish to disable or reactivate.</span></span>  
  
2.  <span data-ttu-id="9d9e5-118">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9d9e5-119">プラス記号をクリックして **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="9d9e5-120">有効化する警告を右クリックし、 **[有効化]** を選択します。警告を無効化するには、無効化する警告を右クリックし、 **[無効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-120">Right-click the alert you wish to enable and select **Enable** To disable an alert, right-click the alert you want to disable and select **Disable**.</span></span>  
  
5.  <span data-ttu-id="9d9e5-121">**[警告の有効化]** または **[警告の無効化]** ダイアログ ボックスが表示され、プロセスの状態が示されます。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-121">The **Disable Alert** or **Enable Alert** dialog box displays showing the status of the process.</span></span> <span data-ttu-id="9d9e5-122">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-122">When finished, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9d9e5-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9d9e5-123">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="9d9e5-124">警告を無効にしたり、再び有効にするには</span><span class="sxs-lookup"><span data-stu-id="9d9e5-124">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="9d9e5-125">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9d9e5-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9d9e5-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="9d9e5-128">詳細については、「 [sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d9e5-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
