---
title: データベース スナップショットの削除 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0d9d912a092e581fad7d3d53504309f63ba1806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631075"
---
# <a name="drop-a-database-snapshot-transact-sql"></a><span data-ttu-id="1f241-102">データベース スナップショットの削除 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1f241-102">Drop a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="1f241-103">データベース スナップショットを削除すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータベース スナップショットが削除され、そのスナップショットで使用されていたスパース ファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1f241-103">Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and deletes the sparse files that are used by the snapshot.</span></span> <span data-ttu-id="1f241-104">データベース スナップショットを削除すると、そのデータベース スナップショットに対するすべてのユーザー接続が終了します。</span><span class="sxs-lookup"><span data-stu-id="1f241-104">When you drop a database snapshot, all user connections to it are terminated.</span></span>  
  
## <a name="security"></a><span data-ttu-id="1f241-105">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1f241-105">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f241-106">Permissions</span><span class="sxs-lookup"><span data-stu-id="1f241-106">Permissions</span></span>  
 <span data-ttu-id="1f241-107">DROP DATABASE 権限を持つすべてのユーザーが、データベース スナップショットを削除できます。</span><span class="sxs-lookup"><span data-stu-id="1f241-107">Any user with DROP DATABASE permissions can drop a database snapshot.</span></span>  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f241-108">データベース スナップショットを削除する方法 (Transact-SQL の使用)</span><span class="sxs-lookup"><span data-stu-id="1f241-108">How to Drop a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="1f241-109">**データベース スナップショットを削除するには**</span><span class="sxs-lookup"><span data-stu-id="1f241-109">**To drop a database snapshot**</span></span>  
  
1.  <span data-ttu-id="1f241-110">削除するデータベース スナップショットを特定します。</span><span class="sxs-lookup"><span data-stu-id="1f241-110">Identify the database snapshot that you want to drop.</span></span> <span data-ttu-id="1f241-111">データベース内のスナップショットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1f241-111">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1f241-112">詳細については、「 [データベース スナップショットの表示 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1f241-112">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1f241-113">削除するデータベース スナップショットの名前を指定して [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1f241-113">Issue a [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) statement, specifying the name of the database snapshot to be dropped.</span></span> <span data-ttu-id="1f241-114">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f241-114">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="1f241-115">DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="1f241-115">DROP DATABASE *database_snapshot_name* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="1f241-116">ここで、 *database_snapshot_name* は、削除するデータベース スナップショットの名前です。</span><span class="sxs-lookup"><span data-stu-id="1f241-116">Where *database_snapshot_name* is the name of the database snapshot to be dropped.</span></span>  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1f241-117">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1f241-117">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1f241-118">この例では、データベース スナップショット SalesSnapshot0600 を削除します。これは元のデータベースには影響しません。</span><span class="sxs-lookup"><span data-stu-id="1f241-118">This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.</span></span>  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 <span data-ttu-id="1f241-119">SalesSnapshot0600 へのユーザー接続がすべて終了し、スナップショットで使用される NTFS ファイル システムのスパース ファイルがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="1f241-119">Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f241-120">データベース スナップショットによるスパース ファイルの使用の詳細については、「 [データベース スナップショット &#40;SQL Server&#41;](database-snapshots-sql-server.md)で参照できます。</span><span class="sxs-lookup"><span data-stu-id="1f241-120">For information about the use of sparse files by database snapshots, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1f241-121">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1f241-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1f241-122">データベース スナップショットの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1f241-122">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="1f241-123">データベース スナップショットの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1f241-123">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="1f241-124">データベースをデータベース スナップショットに戻す</span><span class="sxs-lookup"><span data-stu-id="1f241-124">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="1f241-125">参照</span><span class="sxs-lookup"><span data-stu-id="1f241-125">See Also</span></span>  
 <span data-ttu-id="1f241-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1f241-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 [<span data-ttu-id="1f241-127">Database Snapshots &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1f241-127">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
