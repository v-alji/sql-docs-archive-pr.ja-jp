---
title: 警告の編集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], modifying
- modifying alerts
ms.assetid: f518e528-cc8f-446a-b37d-98505b86e430
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1eae606b3c2ca4c18d088e650e774986d4e31387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641958"
---
# <a name="edit-an-alert"></a><span data-ttu-id="63fbf-102">Edit an Alert</span><span class="sxs-lookup"><span data-stu-id="63fbf-102">Edit an Alert</span></span>
  <span data-ttu-id="63fbf-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントの警告を編集する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="63fbf-103">This topic describes how to edit a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="63fbf-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="63fbf-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63fbf-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="63fbf-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63fbf-106">Security</span><span class="sxs-lookup"><span data-stu-id="63fbf-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="63fbf-107">**警告定義を編集する方法:**</span><span class="sxs-lookup"><span data-stu-id="63fbf-107">**To edit an alert, using:**</span></span>  
  
     [<span data-ttu-id="63fbf-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63fbf-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="63fbf-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63fbf-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63fbf-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="63fbf-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63fbf-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="63fbf-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63fbf-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="63fbf-112">Permissions</span></span>  
 <span data-ttu-id="63fbf-113">既定では、警告の情報を編集できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="63fbf-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="63fbf-114">それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="63fbf-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63fbf-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="63fbf-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="63fbf-116">警告を編集するには</span><span class="sxs-lookup"><span data-stu-id="63fbf-116">To edit an alert</span></span>  
  
1.  <span data-ttu-id="63fbf-117">**オブジェクト エクスプローラー** で、編集する警告を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="63fbf-117">In **Object Explorer,** click the plus sign to expand the server containing the alert you want to edit.</span></span>  
  
2.  <span data-ttu-id="63fbf-118">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="63fbf-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="63fbf-119">プラス記号をクリックして **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="63fbf-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="63fbf-120">編集する警告を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fbf-120">Right-click the alert you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="63fbf-121">**[全般]**、 **[応答]**、および **[オプション]** の各ページで、警告のプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="63fbf-121">Update the alert properties on the **General**, **Response**, and **Options** pages.</span></span>  
  
6.  <span data-ttu-id="63fbf-122">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fbf-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="63fbf-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="63fbf-123">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="63fbf-124">警告を編集するには</span><span class="sxs-lookup"><span data-stu-id="63fbf-124">To edit an alert</span></span>  
  
1.  <span data-ttu-id="63fbf-125">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="63fbf-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63fbf-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fbf-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63fbf-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fbf-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="63fbf-128">詳細については、「 [sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63fbf-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
