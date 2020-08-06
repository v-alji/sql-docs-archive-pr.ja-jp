---
title: オペレーターの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75bea1c5c5fabff7ce55fe07a5181baa8f99e0fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632271"
---
# <a name="delete-an-operator"></a><span data-ttu-id="e6843-102">Delete an Operator</span><span class="sxs-lookup"><span data-stu-id="e6843-102">Delete an Operator</span></span>
  <span data-ttu-id="e6843-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] またはを使用して、でエージェントの警告通知が受信されないように、オペレーターを削除する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e6843-103">This topic describes how to remove an operator so they no longer receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e6843-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e6843-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e6843-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e6843-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e6843-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e6843-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e6843-107">Security</span><span class="sxs-lookup"><span data-stu-id="e6843-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e6843-108">**オペレーターを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="e6843-108">**To delete an operator, using:**</span></span>  
  
     [<span data-ttu-id="e6843-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6843-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e6843-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6843-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e6843-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e6843-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e6843-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e6843-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e6843-113">オペレーターを削除すると、そのオペレーターと関連するすべての通知も削除されます。</span><span class="sxs-lookup"><span data-stu-id="e6843-113">When an operator is removed, all the notifications associated with the operator are also removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e6843-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e6843-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e6843-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="e6843-115">Permissions</span></span>  
 <span data-ttu-id="e6843-116">オペレーターを削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="e6843-116">Members of the **sysadmin** fixed server role can delete operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e6843-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e6843-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="e6843-118">オペレーターを削除するには</span><span class="sxs-lookup"><span data-stu-id="e6843-118">To delete an operator</span></span>  
  
1.  <span data-ttu-id="e6843-119">**オブジェクト エクスプローラー**で、削除するオペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="e6843-119">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to delete.</span></span>  
  
2.  <span data-ttu-id="e6843-120">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="e6843-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="e6843-121">プラス記号をクリックして **[オペレーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e6843-121">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="e6843-122">削除するオペレーターを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6843-122">Right-click the operator that you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="e6843-123">**[オブジェクトの削除]** ダイアログ ボックスで、正しいオペレーターが選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6843-123">In the **Delete Object** dialog box, make sure that the correct operator is selected, and then click **OK**.</span></span> <span data-ttu-id="e6843-124">削除したオペレーターに送信されていた警告およびジョブが別のオペレーターに送信されるようにする場合は、 **[再割り当てするオペレーター]** をオンにし、一覧からオペレーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="e6843-124">If you want another operator to receive the alerts and jobs sent to the deleted operator, check **Reassign to** and select an operator in the list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e6843-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e6843-125">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="e6843-126">オペレーターを削除するには</span><span class="sxs-lookup"><span data-stu-id="e6843-126">To delete an operator</span></span>  
  
1.  <span data-ttu-id="e6843-127">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6843-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e6843-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6843-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e6843-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e6843-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'Fran??ois Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'Fran??ois Ajenstat';  
    GO  
    ```  
  
 <span data-ttu-id="e6843-130">詳細については、「 [sp_delete_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6843-130">For more information, see [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span></span>  
  
  
