---
title: データベース スナップショットの表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92c5c557656e87be562e9d5477f14f66b2c39e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741074"
---
# <a name="view-a-database-snapshot-sql-server"></a><span data-ttu-id="a4dd6-102">データベース スナップショットの表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a4dd6-102">View a Database Snapshot (SQL Server)</span></span>
  <span data-ttu-id="a4dd6-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベース スナップショットを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-103">This topic explains how to view a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4dd6-104">データベース スナップショットの作成、復元、削除には、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-104">To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a4dd6-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a4dd6-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a4dd6-106">**データベース スナップショットの確認に使用するツール:**</span><span class="sxs-lookup"><span data-stu-id="a4dd6-106">**To view a database snapshot, using:**</span></span>  
  
     [<span data-ttu-id="a4dd6-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a4dd6-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a4dd6-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a4dd6-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a4dd6-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a4dd6-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a4dd6-110">**データベース スナップショットを確認するには**</span><span class="sxs-lookup"><span data-stu-id="a4dd6-110">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="a4dd6-111">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-111">In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a4dd6-112">**[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-112">Expand **Databases.**</span></span>  
  
3.  <span data-ttu-id="a4dd6-113">**[データベース スナップショット]** を展開し、表示するスナップショットを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-113">Expand **Database Snapshots**, and select the snapshot you want to view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a4dd6-114">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a4dd6-114">Using Transact-SQL</span></span>  
 <span data-ttu-id="a4dd6-115">**データベース スナップショットを確認するには**</span><span class="sxs-lookup"><span data-stu-id="a4dd6-115">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="a4dd6-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a4dd6-117">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-117">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a4dd6-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのデータベース スナップショットの一覧を表示するには、 **sys.databases** カタログ ビューの [source_database_id](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列で NULL 以外の値に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-118">To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], query the **source_database_id** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view for non-NULL values.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a4dd6-119">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a4dd6-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a4dd6-120">データベース スナップショットの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4dd6-120">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="a4dd6-121">データベースをデータベース スナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="a4dd6-121">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="a4dd6-122">データベース スナップショットの削除 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4dd6-122">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4dd6-123">参照</span><span class="sxs-lookup"><span data-stu-id="a4dd6-123">See Also</span></span>  
 [<span data-ttu-id="a4dd6-124">Database Snapshots &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4dd6-124">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
