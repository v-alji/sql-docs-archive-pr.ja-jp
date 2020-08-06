---
title: CHECK 制約の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28a7f72993cbf2ed0a8cc76534380090ef0d0a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640839"
---
# <a name="delete-check-constraints"></a><span data-ttu-id="b35b3-102">CHECK 制約の削除</span><span class="sxs-lookup"><span data-stu-id="b35b3-102">Delete Check Constraints</span></span>
  <span data-ttu-id="b35b3-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して CHECK 制約を削除できます。</span><span class="sxs-lookup"><span data-stu-id="b35b3-103">You can delete a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b35b3-104">CHECK 制約を削除すると、制約式に含まれる 1 つ以上の列に入力できるデータ値に対する制限が取り除かれます。</span><span class="sxs-lookup"><span data-stu-id="b35b3-104">Deleting check constraints removes the limitations on data values that are accepted in the column or columns included in the constraint expression.</span></span>  
  
 <span data-ttu-id="b35b3-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b35b3-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b35b3-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b35b3-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b35b3-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b35b3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b35b3-108">**CHECK 制約を削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="b35b3-108">**To delete a check constraint, using:**</span></span>  
  
     [<span data-ttu-id="b35b3-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b35b3-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b35b3-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b35b3-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b35b3-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="b35b3-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b35b3-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b35b3-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b35b3-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="b35b3-113">Permissions</span></span>  
 <span data-ttu-id="b35b3-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b35b3-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b35b3-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b35b3-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="b35b3-116">CHECK 制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="b35b3-116">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="b35b3-117">**オブジェクト エクスプローラー**で、CHECK 制約が設定されたテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="b35b3-117">In **Object Explorer**, expand the table with the check constraint.</span></span>  
  
2.  <span data-ttu-id="b35b3-118">**[制約]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b35b3-118">Expand  **Constraints**.</span></span>  
  
3.  <span data-ttu-id="b35b3-119">制約を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b35b3-119">Right-click the constraint and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="b35b3-120">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b35b3-120">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b35b3-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b35b3-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="b35b3-122">CHECK 制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="b35b3-122">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="b35b3-123">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="b35b3-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b35b3-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b35b3-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b35b3-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b35b3-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="b35b3-126">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b35b3-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
