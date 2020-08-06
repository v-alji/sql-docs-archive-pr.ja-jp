---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0b9c71ea620174f993ae87befed8a21bb3d0bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640994"
---
# <a name="mssqlserver_30089"></a><span data-ttu-id="5f48c-102">MSSQLSERVER_30089</span><span class="sxs-lookup"><span data-stu-id="5f48c-102">MSSQLSERVER_30089</span></span>
    
## <a name="details"></a><span data-ttu-id="5f48c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="5f48c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f48c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="5f48c-104">Product Name</span></span>|<span data-ttu-id="5f48c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5f48c-105">SQL Server</span></span>|  
|<span data-ttu-id="5f48c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5f48c-106">Event ID</span></span>|<span data-ttu-id="5f48c-107">30089</span><span class="sxs-lookup"><span data-stu-id="5f48c-107">30089</span></span>|  
|<span data-ttu-id="5f48c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="5f48c-108">Event Source</span></span>|<span data-ttu-id="5f48c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5f48c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5f48c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5f48c-110">Component</span></span>|<span data-ttu-id="5f48c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5f48c-111">SQLEngine</span></span>|  
|<span data-ttu-id="5f48c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="5f48c-112">Symbolic Name</span></span>|<span data-ttu-id="5f48c-113">IFTS_FDHOST_TERMINATEDABNORMAL</span><span class="sxs-lookup"><span data-stu-id="5f48c-113">IFTS_FDHOST_TERMINATEDABNORMAL</span></span>|  
|<span data-ttu-id="5f48c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="5f48c-114">Message Text</span></span>|<span data-ttu-id="5f48c-115">フルテキスト フィルター デーモン ホスト (FDHost) プロセスが異常停止しました。</span><span class="sxs-lookup"><span data-stu-id="5f48c-115">The fulltext filter daemon host (FDHost) process has stopped abnormally.</span></span> <span data-ttu-id="5f48c-116">この問題は、ワード ブレーカー、ステマー、フィルターなどの言語コンポーネントの不適切な構成または誤動作が原因で、フルテキスト インデックスの作成中またはクエリの処理中に回復不可能なエラーが生じた場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="5f48c-116">This can occur if an incorrectly configured or malfunctioning linguistic component, such as a wordbreaker, stemmer or filter has caused an irrecoverable error during full-text indexing or query processing.</span></span> <span data-ttu-id="5f48c-117">プロセスは自動的に再開されます。</span><span class="sxs-lookup"><span data-stu-id="5f48c-117">The process will be restarted automatically.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f48c-118">説明</span><span class="sxs-lookup"><span data-stu-id="5f48c-118">Explanation</span></span>  
 <span data-ttu-id="5f48c-119">何らかの問題が発生したため、フルテキスト フィルター デーモン ホストが異常停止しました。</span><span class="sxs-lookup"><span data-stu-id="5f48c-119">The full-text filter daemon host has encountered some problem that has forced it to stop abnormally.</span></span> <span data-ttu-id="5f48c-120">問題の原因として、不適切な形式のドキュメント、フィルターやワード ブレーカーのバグ、フィルター デーモンの問題などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="5f48c-120">The cause of the problem could be a badly formatted document, a bug in the filter or word-breaker, or a problem in filter daemon.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f48c-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="5f48c-121">User Action</span></span>  
 <span data-ttu-id="5f48c-122">通常、デーモンはエラーから回復します。</span><span class="sxs-lookup"><span data-stu-id="5f48c-122">Typically, the daemon will recover from the error.</span></span> <span data-ttu-id="5f48c-123">デーモンのエラーが継続する場合は、トラブルシューティングが必要になります。</span><span class="sxs-lookup"><span data-stu-id="5f48c-123">If it is consistently failing, troubleshooting is necessary.</span></span> <span data-ttu-id="5f48c-124">問題を切り離すために、次の操作を試みてください。</span><span class="sxs-lookup"><span data-stu-id="5f48c-124">Try the following to isolate the issue:</span></span>  
  
1.  <span data-ttu-id="5f48c-125">新しい言語コンポーネントを最近インストールした場合は、そのコンポーネントをシステムから削除します。</span><span class="sxs-lookup"><span data-stu-id="5f48c-125">If a new linguistic component has been installed recently, remove it from the system.</span></span>  
  
2.  <span data-ttu-id="5f48c-126">クロール ログを調べて、フルテキスト インデックスの作成に失敗した新しいドキュメントがあるか確認します。該当するドキュメントがあれば、それを削除します。</span><span class="sxs-lookup"><span data-stu-id="5f48c-126">Look at the crawl log to identify any new document that failed to be full-text indexed, and remove it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f48c-127">参照</span><span class="sxs-lookup"><span data-stu-id="5f48c-127">See Also</span></span>  
 <span data-ttu-id="5f48c-128">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f48c-128">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="5f48c-129">[検索用のワードブレーカーとステミング機能の構成と管理](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="5f48c-129">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="5f48c-130">検索用フィルターの構成と管理</span><span class="sxs-lookup"><span data-stu-id="5f48c-130">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
