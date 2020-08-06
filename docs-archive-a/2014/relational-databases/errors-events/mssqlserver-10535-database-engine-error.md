---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 439d282f18490a4353d6528276eaf7e4231c503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715374"
---
# <a name="mssqlserver_10535"></a><span data-ttu-id="23c84-102">MSSQLSERVER_10535</span><span class="sxs-lookup"><span data-stu-id="23c84-102">MSSQLSERVER_10535</span></span>
    
## <a name="details"></a><span data-ttu-id="23c84-103">詳細</span><span class="sxs-lookup"><span data-stu-id="23c84-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23c84-104">製品名</span><span class="sxs-lookup"><span data-stu-id="23c84-104">Product Name</span></span>|<span data-ttu-id="23c84-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23c84-105">SQL Server</span></span>|  
|<span data-ttu-id="23c84-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="23c84-106">Event ID</span></span>|<span data-ttu-id="23c84-107">10535</span><span class="sxs-lookup"><span data-stu-id="23c84-107">10535</span></span>|  
|<span data-ttu-id="23c84-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="23c84-108">Event Source</span></span>|<span data-ttu-id="23c84-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23c84-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23c84-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="23c84-110">Component</span></span>|<span data-ttu-id="23c84-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23c84-111">SQLEngine</span></span>|  
|<span data-ttu-id="23c84-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="23c84-112">Symbolic Name</span></span>|<span data-ttu-id="23c84-113">PG_NO_PLAN</span><span class="sxs-lookup"><span data-stu-id="23c84-113">PG_NO_PLAN</span></span>|  
|<span data-ttu-id="23c84-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="23c84-114">Message Text</span></span>|<span data-ttu-id="23c84-115">プラン ガイド '%.\*ls' を作成できません。指定されたプラン ハンドルに対応するプラン キャッシュでプランが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="23c84-115">Cannot create plan guide '%.\*ls' because a plan was not found in the plan cache that corresponds to the specified plan handle.</span></span> <span data-ttu-id="23c84-116">キャッシュされたプラン ハンドルを指定します。</span><span class="sxs-lookup"><span data-stu-id="23c84-116">Specify a cached plan handle.</span></span> <span data-ttu-id="23c84-117">キャッシュされたプラン ハンドルの一覧を取得するには、sys.dm_exec_query_stats 動的管理ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="23c84-117">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23c84-118">説明</span><span class="sxs-lookup"><span data-stu-id="23c84-118">Explanation</span></span>  
 <span data-ttu-id="23c84-119">指定されたプラン ハンドルに対応するプラン キャッシュ内にプランが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="23c84-119">A plan was not found in the plan cache that corresponds to the specified plan handle.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23c84-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="23c84-120">User Action</span></span>  
 <span data-ttu-id="23c84-121">キャッシュされたプラン ハンドルを指定します。</span><span class="sxs-lookup"><span data-stu-id="23c84-121">Specify a cached plan handle.</span></span> <span data-ttu-id="23c84-122">キャッシュされたプラン ハンドルの一覧を取得するには、sys.dm_exec_query_stats 動的管理ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="23c84-122">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c84-123">参照</span><span class="sxs-lookup"><span data-stu-id="23c84-123">See Also</span></span>  
 <span data-ttu-id="23c84-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="23c84-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 [<span data-ttu-id="23c84-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="23c84-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
