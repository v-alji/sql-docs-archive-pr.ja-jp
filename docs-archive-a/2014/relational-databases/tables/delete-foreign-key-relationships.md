---
title: 外部キーのリレーションシップの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], deleting
- removing foreign keys
- deleting foreign keys
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ae466b9fce53073bfc0645c753246023ff3269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640837"
---
# <a name="delete-foreign-key-relationships"></a><span data-ttu-id="c129d-102">外部キーのリレーションシップの削除</span><span class="sxs-lookup"><span data-stu-id="c129d-102">Delete Foreign Key Relationships</span></span>
  <span data-ttu-id="c129d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して外部キー制約を削除できます。</span><span class="sxs-lookup"><span data-stu-id="c129d-103">You can delete a foreign key constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c129d-104">外部キー制約を削除すると、参照整合性の適用要件が解除されます。</span><span class="sxs-lookup"><span data-stu-id="c129d-104">Deleting a foreign key constraint removes the requirement to enforce referential integrity.</span></span>  
  
 <span data-ttu-id="c129d-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c129d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c129d-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c129d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c129d-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c129d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c129d-108">**以下を使用して外部キーの制約を削除するには:**</span><span class="sxs-lookup"><span data-stu-id="c129d-108">**To delete a foreign key constraint, using:**</span></span>  
  
     [<span data-ttu-id="c129d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c129d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c129d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c129d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c129d-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="c129d-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c129d-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c129d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c129d-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="c129d-113">Permissions</span></span>  
 <span data-ttu-id="c129d-114">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c129d-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c129d-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c129d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="c129d-116">外部キーの制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="c129d-116">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="c129d-117">**オブジェクト エクスプローラー**で、制約が含まれているテーブルを展開し、 **[キー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="c129d-117">In **Object Explorer**, expand the table with the constraint and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="c129d-118">制約を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c129d-118">Right-click the constraint and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="c129d-119">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c129d-119">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c129d-120">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c129d-120">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="c129d-121">外部キーの制約を削除するには</span><span class="sxs-lookup"><span data-stu-id="c129d-121">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="c129d-122">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c129d-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c129d-123">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c129d-123">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c129d-124">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c129d-124">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 <span data-ttu-id="c129d-125">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c129d-125">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
