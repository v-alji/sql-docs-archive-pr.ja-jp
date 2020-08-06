---
title: INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にする方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
- UPDATE statement [SQL Server], foreign key constraints
- INSERT statement [SQL Server], foreign key constraints
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: e91328f4f12f2a0a27f397c7bd95390a505f3998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639924"
---
# <a name="disable-foreign-key-constraints-with-insert-and-update-statements"></a><span data-ttu-id="38da2-102">INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にする方法</span><span class="sxs-lookup"><span data-stu-id="38da2-102">Disable Foreign Key Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="38da2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、INSERT トランザクションまたは UPDATE トランザクションの実行中に外部キー制約を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="38da2-103">You can disable a foreign key constraint during INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="38da2-104">新しいデータが既存の制約に違反することがわかっている場合、またはデータベース内の既存のデータのみに制約を適用する場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="38da2-104">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="38da2-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="38da2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="38da2-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="38da2-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="38da2-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="38da2-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="38da2-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="38da2-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="38da2-109">**以下を使用して INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには:**</span><span class="sxs-lookup"><span data-stu-id="38da2-109">**To disable a foreign key constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="38da2-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38da2-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="38da2-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38da2-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38da2-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="38da2-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38da2-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="38da2-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="38da2-114">これらの制約を無効にすると、今後列に行われる挿入または更新は、制約条件に対して検証されません。</span><span class="sxs-lookup"><span data-stu-id="38da2-114">After you disable these constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38da2-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="38da2-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38da2-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="38da2-116">Permissions</span></span>  
 <span data-ttu-id="38da2-117">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="38da2-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38da2-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="38da2-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="38da2-119">INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="38da2-119">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="38da2-120">**オブジェクト エクスプローラー**で、制約が含まれているテーブルを展開し、 **[キー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="38da2-120">In **Object Explorer**, expand the table with the constraint and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="38da2-121">制約を右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38da2-121">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="38da2-122">**[テーブル デザイナー]** の下のグリッドで、 **[外部キーの制約を適用]** をクリックし、ドロップダウン ボックスの一覧の **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38da2-122">In the grid under **Table Designer**, click **Enforce Foreign Key Constraint** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="38da2-123">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38da2-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38da2-124">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="38da2-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-insert-and-update-statements"></a><span data-ttu-id="38da2-125">INSERT ステートメントまたは UPDATE ステートメントに対して外部キー制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="38da2-125">To disable a foreign key constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="38da2-126">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="38da2-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="38da2-127">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38da2-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="38da2-128">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38da2-128">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 <span data-ttu-id="38da2-129">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38da2-129">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
