---
title: MSSQLSERVER_601 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 459a983d72a91e628e8cc33636d3abd81998f1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645116"
---
# <a name="mssqlserver_601"></a><span data-ttu-id="93476-102">MSSQLSERVER_601</span><span class="sxs-lookup"><span data-stu-id="93476-102">MSSQLSERVER_601</span></span>
    
## <a name="details"></a><span data-ttu-id="93476-103">詳細</span><span class="sxs-lookup"><span data-stu-id="93476-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93476-104">製品名</span><span class="sxs-lookup"><span data-stu-id="93476-104">Product Name</span></span>|<span data-ttu-id="93476-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="93476-105">SQL Server</span></span>|  
|<span data-ttu-id="93476-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="93476-106">Event ID</span></span>|<span data-ttu-id="93476-107">601</span><span class="sxs-lookup"><span data-stu-id="93476-107">601</span></span>|  
|<span data-ttu-id="93476-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="93476-108">Event Source</span></span>|<span data-ttu-id="93476-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="93476-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="93476-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="93476-110">Component</span></span>|<span data-ttu-id="93476-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="93476-111">SQLEngine</span></span>|  
|<span data-ttu-id="93476-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="93476-112">Symbolic Name</span></span>||  
|<span data-ttu-id="93476-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="93476-113">Message Text</span></span>|<span data-ttu-id="93476-114">データが移動されたので NOLOCK を使用したスキャンは続行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="93476-114">Could not continue scan with NOLOCK due to data movement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="93476-115">説明</span><span class="sxs-lookup"><span data-stu-id="93476-115">Explanation</span></span>  
 <span data-ttu-id="93476-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]が別のトランザクションによって更新または削除されたデータを読み取ろうとしているため、クエリの実行を続行できません。</span><span class="sxs-lookup"><span data-stu-id="93476-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot continue executing the query because it is trying to read data that was updated or deleted by another transaction.</span></span> <span data-ttu-id="93476-117">このクエリでは、NOLOCK ロック ヒントまたは READ UNCOMMITTED トランザクション分離レベルのいずれかが使用されています。</span><span class="sxs-lookup"><span data-stu-id="93476-117">The query is using either the NOLOCK locking hint or the READ UNCOMMITTED transaction isolation level.</span></span>  
  
 <span data-ttu-id="93476-118">通常、別のトランザクションによって変更されているデータへのアクセスは、データがロックされているために拒否されます。</span><span class="sxs-lookup"><span data-stu-id="93476-118">Typically, access to data that is being changed by another transaction is denied because of locks put on the data.</span></span> <span data-ttu-id="93476-119">しかし、NOLOCK ロック ヒントや READ UNCOMMITTED トランザクション分離レベルを使用すると、別のトランザクションによってロックされているデータをクエリで読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="93476-119">However, the NOLOCK locking hint and READ UNCOMMITTED transaction isolation level let a query read data that is locked by another transaction.</span></span> <span data-ttu-id="93476-120">まだコミットされておらず変更される可能性がある値を読み取ることができるため、この操作はダーティ リードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="93476-120">This is referred to as a dirty read because you can read values that have not yet been committed and that are subject to change.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="93476-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="93476-121">User Action</span></span>  
 <span data-ttu-id="93476-122">このエラーが発生するとクエリは取り消されます。</span><span class="sxs-lookup"><span data-stu-id="93476-122">This error cancels the query.</span></span> <span data-ttu-id="93476-123">クエリを再送信するか、NOLOCK ロック ヒントを削除します。</span><span class="sxs-lookup"><span data-stu-id="93476-123">Either resubmit the query or remove the NOLOCK locking hint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93476-124">参照</span><span class="sxs-lookup"><span data-stu-id="93476-124">See Also</span></span>  
 <span data-ttu-id="93476-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="93476-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span></span>  
 <span data-ttu-id="93476-126">[テーブル ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="93476-126">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 <span data-ttu-id="93476-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="93476-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="93476-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93476-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
