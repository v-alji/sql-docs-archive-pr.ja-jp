---
title: レプリケーションの CHECK 制約の無効化 | Microsoft Docs
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
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98b6ca7c3525edeffdb47f294db568d3c115b2c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630864"
---
# <a name="disable-check-constraints-for-replication"></a><span data-ttu-id="623ab-102">レプリケーションの CHECK 制約の無効化</span><span class="sxs-lookup"><span data-stu-id="623ab-102">Disable Check Constraints for Replication</span></span>
  <span data-ttu-id="623ab-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して CHECK 制約を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="623ab-103">You can disable check constraints in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="623ab-104">CHECK 制約はレプリケーションに対して明示的に無効にすることもできます。これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのデータをパブリッシュする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="623ab-104">You can also explicitly disable check constraints for replication, which can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="623ab-105">レプリケーションを使用してテーブルをパブリッシュした場合、レプリケーション エージェントが実行する操作に対しては CHECK 制約が自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="623ab-105">If a table is published using replication, check constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="623ab-106">レプリケーション エージェントがサブスクライバー側で挿入、更新、または削除を実行した場合、制約のチェックは行われません。ユーザーが挿入、更新、または削除を実行した場合は、制約のチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="623ab-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="623ab-107">制約がレプリケーション エージェントに対して無効になるのは、データが最初に挿入、更新、または削除された際に、発行者側で既に制約がチェックされているためです。</span><span class="sxs-lookup"><span data-stu-id="623ab-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span> <span data-ttu-id="623ab-108">詳細については、「[スキーマ オプションの指定](../replication/publish/specify-schema-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="623ab-108">For more information, see [Specify Schema Options](../replication/publish/specify-schema-options.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="623ab-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="623ab-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="623ab-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="623ab-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="623ab-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="623ab-111">Permissions</span></span>  
 <span data-ttu-id="623ab-112">テーブルに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="623ab-112">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="623ab-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="623ab-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="623ab-114">レプリケーションに対して CHECK 制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="623ab-114">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="623ab-115">**オブジェクト エクスプローラー**で、変更する CHECK 制約が設定されているテーブルを展開し、 **[制約]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="623ab-115">In **Object Explorer**, expand the table with the check constraint you want to modify, and then expand the **Constraints** folder.</span></span>  
  
2.  <span data-ttu-id="623ab-116">変更する CHECK 制約を右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="623ab-116">Right-click the check constraint you wish to modify and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="623ab-117">**[CHECK 制約]** ダイアログ ボックスで、 **[テーブル デザイナー]** の **[レプリケーションに対して適用]** の値として **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="623ab-117">In the **Check Constraints** dialog box, under **Table Designer**, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="623ab-118">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="623ab-118">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="623ab-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="623ab-119">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-check-constraint-for-replication"></a><span data-ttu-id="623ab-120">レプリケーションに対して CHECK 制約を無効にするには</span><span class="sxs-lookup"><span data-stu-id="623ab-120">To disable a check constraint for replication</span></span>  
  
1.  <span data-ttu-id="623ab-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="623ab-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="623ab-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="623ab-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="623ab-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="623ab-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="623ab-124">最初の例では、IDENTITY 列を含むテーブルとテーブルに対する CHECK 制約を作成します。</span><span class="sxs-lookup"><span data-stu-id="623ab-124">The example creates a table with an IDENTITY column and a CHECK constraint on the table.</span></span> <span data-ttu-id="623ab-125">次に、制約を削除した後、NOT FOR REPLICATION 句を指定して制約を再作成します。</span><span class="sxs-lookup"><span data-stu-id="623ab-125">The example then drops the constraint and recreates it specifying the NOT FOR REPLICATION clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 <span data-ttu-id="623ab-126">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="623ab-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>   
## <a name="see-also"></a><span data-ttu-id="623ab-127">参照</span><span class="sxs-lookup"><span data-stu-id="623ab-127">See Also</span></span>  
 [<span data-ttu-id="623ab-128">スキーマ オプションの指定</span><span class="sxs-lookup"><span data-stu-id="623ab-128">Specify Schema Options</span></span>](../replication/publish/specify-schema-options.md)  
  
  
