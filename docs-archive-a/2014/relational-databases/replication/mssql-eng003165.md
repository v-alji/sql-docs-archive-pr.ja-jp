---
title: MSSQL_ENG003165 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003165 error
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1702588ba6ac1beeb33b87a7afc7fc330271559
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630937"
---
# <a name="mssql_eng003165"></a><span data-ttu-id="2ec74-102">MSSQL_ENG003165</span><span class="sxs-lookup"><span data-stu-id="2ec74-102">MSSQL_ENG003165</span></span>
    
## <a name="message-details"></a><span data-ttu-id="2ec74-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="2ec74-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ec74-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2ec74-104">Product Name</span></span>|<span data-ttu-id="2ec74-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2ec74-105">SQL Server</span></span>|  
|<span data-ttu-id="2ec74-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2ec74-106">Event ID</span></span>|<span data-ttu-id="2ec74-107">3165</span><span class="sxs-lookup"><span data-stu-id="2ec74-107">3165</span></span>|  
|<span data-ttu-id="2ec74-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2ec74-108">Event Source</span></span>|<span data-ttu-id="2ec74-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2ec74-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2ec74-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2ec74-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="2ec74-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2ec74-111">Symbolic Name</span></span>||  
|<span data-ttu-id="2ec74-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2ec74-112">Message Text</span></span>|<span data-ttu-id="2ec74-113">データベース '%ls' は復元されましたが、レプリケーションの復元または削除中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2ec74-113">Database '%ls' was restored; however, an error was encountered while replication was being restored/removed.</span></span> <span data-ttu-id="2ec74-114">データベースはオフラインのままです。</span><span class="sxs-lookup"><span data-stu-id="2ec74-114">The database has been left offline.</span></span> <span data-ttu-id="2ec74-115">SQL Server オンライン ブックのトピック「MSSQL_ENG003165」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ec74-115">See the topic MSSQL_ENG003165 in SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2ec74-116">説明</span><span class="sxs-lookup"><span data-stu-id="2ec74-116">Explanation</span></span>  
 <span data-ttu-id="2ec74-117">このエラーは、レプリケートされたデータベースのバックアップの復元で問題が生じた場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-117">This error is raised if a problem occurs restoring a backup of a replicated database:</span></span>  
  
-   <span data-ttu-id="2ec74-118">バックアップをその作成元と同じデータベースおよびサーバーに復元している場合、このエラーは、レプリケーション設定を適切に復元できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-118">If the backup is being restored to the same database and server on which it was taken, the error indicates that replication settings could not be restored properly.</span></span>  
  
-   <span data-ttu-id="2ec74-119">バックアップを異なるデータベースまたはサーバーに復元している場合、このエラーは、レプリケーション設定を適切に削除できなかったことを示します (既定では、データベースまたはサーバーが異なる場合、レプリケーション設定は削除されます)。</span><span class="sxs-lookup"><span data-stu-id="2ec74-119">If the backup is being restored to a different database or server, the error indicates that replication settings could not be removed properly (by default, replication settings are removed if the database or server is different).</span></span>  
  
 <span data-ttu-id="2ec74-120">このエラーは、復元されたデータベースと、レプリケーション メタデータを含む 1 つ以上のシステム データベース、つまり **msdb**、 **master**、またはディストリビューション データベースの間の状態の不一致が原因と考えられます。</span><span class="sxs-lookup"><span data-stu-id="2ec74-120">The error is probably the result of a mismatch between the state of the restored database and one or more system databases that contain replication metadata: **msdb**, **master**, or the distribution database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2ec74-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2ec74-121">User Action</span></span>  
 <span data-ttu-id="2ec74-122">この問題を解決するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-122">To resolve this issue:</span></span>  
  
1.  <span data-ttu-id="2ec74-123">ALTER DATABASE を実行し、データベースをオンラインにします。たとえば、「 `ALTER DATABASE AdventureWorks SET ONLINE`」と実行します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-123">Execute ALTER DATABASE to bring the database online; for example: `ALTER DATABASE AdventureWorks SET ONLINE`.</span></span> <span data-ttu-id="2ec74-124">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ec74-124">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span> <span data-ttu-id="2ec74-125">レプリケーションの設定を保存する場合は、手順 2. に進みます。</span><span class="sxs-lookup"><span data-stu-id="2ec74-125">If you want to preserve replication settings, go to step 2.</span></span> <span data-ttu-id="2ec74-126">それ以外の場合は、手順 3. に進みます。</span><span class="sxs-lookup"><span data-stu-id="2ec74-126">If not, go to step 3.</span></span>  
  
2.  <span data-ttu-id="2ec74-127">[sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-127">Execute [sp_restoredbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql).</span></span> <span data-ttu-id="2ec74-128">このストアド プロシージャの実行に成功した場合、復元は完了です。</span><span class="sxs-lookup"><span data-stu-id="2ec74-128">If this stored procedure executes successfully, the restore is complete.</span></span> <span data-ttu-id="2ec74-129">実行に失敗した場合は、手順 3. に進んでください。</span><span class="sxs-lookup"><span data-stu-id="2ec74-129">If it does not execute successfully, go to step 3.</span></span>  
  
3.  <span data-ttu-id="2ec74-130">[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、レプリケーションの設定をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-130">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove all replication settings.</span></span>  
  
     <span data-ttu-id="2ec74-131">必要に応じて、レプリケーションを再構成します。</span><span class="sxs-lookup"><span data-stu-id="2ec74-131">Reconfigure replication if necessary.</span></span> <span data-ttu-id="2ec74-132">推奨どおりにレプリケーション トポロジのスクリプトを作成している場合は、スクリプトを使用してトポロジを再構成してください。</span><span class="sxs-lookup"><span data-stu-id="2ec74-132">If you have scripted the replication topology as recommended, use scripts to reconfigure the topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec74-133">参照</span><span class="sxs-lookup"><span data-stu-id="2ec74-133">See Also</span></span>  
 <span data-ttu-id="2ec74-134">[SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="2ec74-134">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="2ec74-135">[レプリケートされたデータベースのバックアップと復元](administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="2ec74-135">[Back Up and Restore Replicated Databases](administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="2ec74-136">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="2ec74-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
