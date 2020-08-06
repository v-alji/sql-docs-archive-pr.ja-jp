---
title: INSERT ステートメントまたは UPDATE ステートメントによる CHECK 制約の無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 780a2c1bfd9f21c71367ad61f200ec19ab44a608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640830"
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a><span data-ttu-id="50f63-102">INSERT ステートメントまたは UPDATE ステートメントによる CHECK 制約の無効化</span><span class="sxs-lookup"><span data-stu-id="50f63-102">Disable Check Constraints with INSERT and UPDATE Statements</span></span>
  <span data-ttu-id="50f63-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して INSERT および UPDATE トランザクションの CHECK 制約を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="50f63-103">You can disable a check constraint for INSERT and UPDATE transactions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="50f63-104">CHECK 制約を無効にすると、今後列に行われる挿入または更新は、制約条件に対して検証されません。</span><span class="sxs-lookup"><span data-stu-id="50f63-104">After you disable the check constraints, future inserts or updates to the column will not be validated against the constraint conditions.</span></span> <span data-ttu-id="50f63-105">新しいデータが既存の制約に違反することがわかっている場合、またはデータベース内の既存のデータのみに制約を適用する場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="50f63-105">Use this option if you know that new data will violate the existing constraint or if the constraint applies only to the data already in the database.</span></span>  
  
 <span data-ttu-id="50f63-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="50f63-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="50f63-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="50f63-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="50f63-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50f63-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="50f63-109">**INSERT ステートメントおよび UPDATE ステートメントの実行中に CHECK 制約を無効にする方法:**</span><span class="sxs-lookup"><span data-stu-id="50f63-109">**To disable a check constraint for INSERT and UPDATE statements, using:**</span></span>  
  
     [<span data-ttu-id="50f63-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="50f63-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="50f63-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="50f63-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="50f63-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="50f63-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="50f63-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50f63-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="50f63-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="50f63-114">Permissions</span></span>  
 <span data-ttu-id="50f63-115">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="50f63-115">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="50f63-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="50f63-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="50f63-117">INSERT ステートメントおよび UPDATE ステートメントの実行中に CHECK 制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="50f63-117">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="50f63-118">**オブジェクト エクスプローラー**で、制約が設定されているテーブルを展開し、 **[制約]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="50f63-118">In **Object Explorer**, expand the table with the constraint and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="50f63-119">制約を右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f63-119">Right-click the constraint and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="50f63-120">**テーブル デザイナー**の下にあるグリッドで、 **[INSERT および UPDATE に適用]** をクリックし、ドロップダウン メニューの **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f63-120">In the grid under **Table Designer**, click **Enforce For INSERTs And UPDATEs** and select **No** from the drop-down menu.</span></span>  
  
4.  <span data-ttu-id="50f63-121">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f63-121">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="50f63-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="50f63-122">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a><span data-ttu-id="50f63-123">INSERT ステートメントおよび UPDATE ステートメントの実行中に CHECK 制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="50f63-123">To disable a check constraint for INSERT and UPDATE statements</span></span>  
  
1.  <span data-ttu-id="50f63-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="50f63-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="50f63-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f63-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="50f63-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f63-126">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 <span data-ttu-id="50f63-127">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50f63-127">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
