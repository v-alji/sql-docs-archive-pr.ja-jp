---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 592c788b563046e5949217c94006de2d4755f049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714181"
---
# <a name="mssql_eng021286"></a><span data-ttu-id="489cb-102">MSSQL_ENG021286</span><span class="sxs-lookup"><span data-stu-id="489cb-102">MSSQL_ENG021286</span></span>
    
## <a name="message-details"></a><span data-ttu-id="489cb-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="489cb-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="489cb-104">製品名</span><span class="sxs-lookup"><span data-stu-id="489cb-104">Product Name</span></span>|<span data-ttu-id="489cb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="489cb-105">SQL Server</span></span>|  
|<span data-ttu-id="489cb-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="489cb-106">Event ID</span></span>|<span data-ttu-id="489cb-107">21286</span><span class="sxs-lookup"><span data-stu-id="489cb-107">21286</span></span>|  
|<span data-ttu-id="489cb-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="489cb-108">Event Source</span></span>|<span data-ttu-id="489cb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="489cb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="489cb-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="489cb-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="489cb-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="489cb-111">Symbolic Name</span></span>||  
|<span data-ttu-id="489cb-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="489cb-112">Message Text</span></span>|<span data-ttu-id="489cb-113">競合テーブル '%s' が存在しません。</span><span class="sxs-lookup"><span data-stu-id="489cb-113">Conflict table '%s' does not exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="489cb-114">説明</span><span class="sxs-lookup"><span data-stu-id="489cb-114">Explanation</span></span>  
 <span data-ttu-id="489cb-115">このエラーは、[sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) にリストされているアーティクルの競合テーブルが実際には存在しない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="489cb-115">This error is raised if the conflict table for an article listed in [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) does not actually exist.</span></span> <span data-ttu-id="489cb-116">このエラーは、マージ レプリケーション用にパブリッシュされたテーブルへの列の追加または削除を試みたときに発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="489cb-116">The error can occur when you attempt to add a column to or drop a column from a table published for merge replication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="489cb-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="489cb-117">User Action</span></span>  
 <span data-ttu-id="489cb-118">競合テーブルが見つからないデータベース上で [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、データの一貫性の問題がないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="489cb-118">Execute [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database with the missing conflict table to verify there are no data consistency issues.</span></span>  
  
 <span data-ttu-id="489cb-119">サブスクライバーに競合テーブルがない場合は、サブスクリプションを削除し、再作成します。</span><span class="sxs-lookup"><span data-stu-id="489cb-119">If the conflict table is missing on a Subscriber, drop the subscription and recreate it.</span></span> <span data-ttu-id="489cb-120">パブリッシャーに競合テーブルがない場合は、すべてのサブスクリプションを削除し、パブリケーションを削除してから、パブリケーションおよびすべてのサブスクリプションを再作成します。</span><span class="sxs-lookup"><span data-stu-id="489cb-120">If the conflict table is missing on a Publisher, drop all subscriptions, drop the publication, and then recreate the publication and all subscriptions.</span></span> <span data-ttu-id="489cb-121">詳細については、「[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)」および「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="489cb-121">For more information, see [Publish Data and Database Objects](publish/publish-data-and-database-objects.md) and [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489cb-122">参照</span><span class="sxs-lookup"><span data-stu-id="489cb-122">See Also</span></span>  
 [<span data-ttu-id="489cb-123">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="489cb-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
