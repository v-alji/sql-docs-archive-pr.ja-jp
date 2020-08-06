---
title: MSSQL_REPL020011 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646f25740ebb007f8d04a89690d3b712781efcc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721350"
---
# <a name="mssql_repl020011"></a><span data-ttu-id="6e716-102">MSSQL_REPL020011</span><span class="sxs-lookup"><span data-stu-id="6e716-102">MSSQL_REPL020011</span></span>
    
## <a name="message-details"></a><span data-ttu-id="6e716-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="6e716-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e716-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6e716-104">Product Name</span></span>|<span data-ttu-id="6e716-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6e716-105">SQL Server</span></span>|  
|<span data-ttu-id="6e716-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6e716-106">Event ID</span></span>|<span data-ttu-id="6e716-107">20011</span><span class="sxs-lookup"><span data-stu-id="6e716-107">20011</span></span>|  
|<span data-ttu-id="6e716-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6e716-108">Event Source</span></span>|<span data-ttu-id="6e716-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e716-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e716-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e716-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="6e716-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6e716-111">Symbolic Name</span></span>||  
|<span data-ttu-id="6e716-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6e716-112">Message Text</span></span>|<span data-ttu-id="6e716-113">プロセスは、'%1' を '%2' で実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e716-113">The process could not execute '%1' on '%2'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e716-114">説明</span><span class="sxs-lookup"><span data-stu-id="6e716-114">Explanation</span></span>  
 <span data-ttu-id="6e716-115">このエラーは、ログ リーダー エージェントが **sp_replcmds** を実行したとき (プロセスは、'sp_replcmds' を \<ServerName> で実行できませんでした) や **sp_repldone** を実行したとき (プロセスは、'sp_repldone' を \<ServerName> で実行できませんでした) など、トランザクション レプリケーション処理中のさまざまな状況で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e716-115">This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp_replcmds** (The process could not execute 'sp_replcmds' on \<ServerName>) or **sp_repldone** (The process could not execute 'sp_repldone' on \<ServerName>).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e716-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6e716-116">User Action</span></span>  
 <span data-ttu-id="6e716-117">バックアップから復元したばかりのデータベースでこのエラーが発生した場合、 **sp_replrestart** の実行 (該当する場合) も含めて、バックアップおよび復元のマニュアルに概説されている手順に従っているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6e716-117">If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp_replrestart** if appropriate.</span></span> <span data-ttu-id="6e716-118">詳細については、「 [スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e716-118">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="6e716-119">このエラーは内部処理エラーであり、復元以外の状況で発生した場合は、一般的にレプリケーションを削除して再構成する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6e716-119">This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured.</span></span> <span data-ttu-id="6e716-120">レプリケーションを削除できない場合は、カスタマー サポートにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="6e716-120">If you cannot remove replication, contact customer support for assistance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e716-121">参照</span><span class="sxs-lookup"><span data-stu-id="6e716-121">See Also</span></span>  
 <span data-ttu-id="6e716-122">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6e716-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="6e716-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6e716-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span></span>  
 [<span data-ttu-id="6e716-124">sp_repldone &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6e716-124">sp_repldone &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
