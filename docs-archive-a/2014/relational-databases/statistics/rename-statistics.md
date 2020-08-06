---
title: 統計名の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- renaming statistics
- statistics [SQL Server], renaming
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1528dcec50a662524531065d597b004fe7f59e5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644375"
---
# <a name="rename-statistics"></a><span data-ttu-id="f066a-102">統計名の変更</span><span class="sxs-lookup"><span data-stu-id="f066a-102">Rename Statistics</span></span>
  <span data-ttu-id="f066a-103">を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で統計オブジェクトの名前を変更できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f066a-103">You can rename a statistics object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="f066a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f066a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f066a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f066a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f066a-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f066a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f066a-107">Security</span><span class="sxs-lookup"><span data-stu-id="f066a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f066a-108">**統計オブジェクトの名前を変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="f066a-108">**To rename a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="f066a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f066a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f066a-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="f066a-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f066a-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f066a-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f066a-112">既定では、インデックスの作成によって、インデックスのキー列に統計が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f066a-112">By default, creating an index creates a statistic on the key columns of that index.</span></span> <span data-ttu-id="f066a-113">そのため、インデックスの名前を変更すると、統計オブジェクトの名前も自動的に変更されます。逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="f066a-113">Therefore, renaming the index automatically renames the statistics object, and vice versa.</span></span>  
  
 <span data-ttu-id="f066a-114">オブジェクト名の一部または全部を変更すると、スクリプトおよびストアド プロシージャが壊れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f066a-114">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="f066a-115">名前を変更するのではなく、統計オブジェクトを削除してから新しい名前で作成し直すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f066a-115">Instead of renaming, we recommend that you drop the statistics object and re-create it with the new name.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f066a-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f066a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f066a-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="f066a-117">Permissions</span></span>  
 <span data-ttu-id="f066a-118">テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f066a-118">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f066a-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f066a-119">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-statistics-object"></a><span data-ttu-id="f066a-120">統計オブジェクトの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="f066a-120">To rename a statistics object</span></span>  
  
1.  <span data-ttu-id="f066a-121">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f066a-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f066a-122">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f066a-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f066a-123">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f066a-123">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 <span data-ttu-id="f066a-124">詳細については、「[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f066a-124">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
