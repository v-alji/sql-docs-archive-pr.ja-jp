---
title: 警告の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], deleting
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- removing alerts
ms.assetid: c982b208-e2d1-4d34-8cee-940b9baf6586
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15fdae19b150a5a06a32e91ec1947a0acfa5f900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643071"
---
# <a name="delete-an-alert"></a><span data-ttu-id="b40d2-102">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="b40d2-102">Delete an Alert</span></span>
  <span data-ttu-id="b40d2-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントの警告を削除する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b40d2-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b40d2-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b40d2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b40d2-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b40d2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b40d2-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b40d2-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b40d2-107">Security</span><span class="sxs-lookup"><span data-stu-id="b40d2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b40d2-108">**警告を削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="b40d2-108">**To delete an alert, using:**</span></span>  
  
     [<span data-ttu-id="b40d2-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b40d2-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b40d2-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b40d2-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b40d2-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="b40d2-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b40d2-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b40d2-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b40d2-113">警告を削除すると、この警告に関連するすべての通知も削除されます。</span><span class="sxs-lookup"><span data-stu-id="b40d2-113">Removing an alert also removes any notifications associated with the alert.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b40d2-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b40d2-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b40d2-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="b40d2-115">Permissions</span></span>  
 <span data-ttu-id="b40d2-116">既定では、警告を削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="b40d2-116">By default, only members of the **sysadmin** fixed server role can delete alerts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b40d2-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b40d2-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="b40d2-118">警告を削除するには</span><span class="sxs-lookup"><span data-stu-id="b40d2-118">To delete an alert</span></span>  
  
1.  <span data-ttu-id="b40d2-119">**オブジェクト エクスプローラー** で、削除する SQL Server エージェントの警告を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="b40d2-119">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent alert that you want to delete.</span></span>  
  
2.  <span data-ttu-id="b40d2-120">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b40d2-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b40d2-121">プラス記号をクリックして **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b40d2-121">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="b40d2-122">削除する警告を右クリックして、 **[削除]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b40d2-122">Right-click the alert you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="b40d2-123">**[オブジェクトの削除]** ダイアログ ボックスで、正しい警告が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b40d2-123">In the **Delete Object** dialog box, confirm that the correct alert is selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b40d2-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b40d2-124">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="b40d2-125">警告を削除するには</span><span class="sxs-lookup"><span data-stu-id="b40d2-125">To delete an alert</span></span>  
  
1.  <span data-ttu-id="b40d2-126">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="b40d2-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b40d2-127">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b40d2-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b40d2-128">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b40d2-128">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the SQL Server Agent alert called 'Test Alert.'  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_alert  
       @name = N'Test Alert' ;  
    GO  
    ```  
  
 <span data-ttu-id="b40d2-129">詳細については、「s[sp_delete_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b40d2-129">For more information, see s[sp_delete_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql).</span></span>  
  
  
