---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f77e39c71901166085d011d6d00f9a4a379bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713225"
---
# <a name="mssqlserver_17300"></a><span data-ttu-id="32d21-102">MSSQLSERVER_17300</span><span class="sxs-lookup"><span data-stu-id="32d21-102">MSSQLSERVER_17300</span></span>
    
## <a name="details"></a><span data-ttu-id="32d21-103">詳細</span><span class="sxs-lookup"><span data-stu-id="32d21-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32d21-104">製品名</span><span class="sxs-lookup"><span data-stu-id="32d21-104">Product Name</span></span>|<span data-ttu-id="32d21-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="32d21-105">SQL Server</span></span>|  
|<span data-ttu-id="32d21-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32d21-106">Event ID</span></span>|<span data-ttu-id="32d21-107">17300</span><span class="sxs-lookup"><span data-stu-id="32d21-107">17300</span></span>|  
|<span data-ttu-id="32d21-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="32d21-108">Event Source</span></span>|<span data-ttu-id="32d21-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="32d21-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="32d21-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="32d21-110">Component</span></span>|<span data-ttu-id="32d21-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="32d21-111">SQLEngine</span></span>|  
|<span data-ttu-id="32d21-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="32d21-112">Symbolic Name</span></span>|<span data-ttu-id="32d21-113">PROC_OUT_OF_SYSTASK_SESSIONS</span><span class="sxs-lookup"><span data-stu-id="32d21-113">PROC_OUT_OF_SYSTASK_SESSIONS</span></span>|  
|<span data-ttu-id="32d21-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="32d21-114">Message Text</span></span>|<span data-ttu-id="32d21-115">メモリが不足しているか、構成されているセッション数がこのサーバーで許可されている最大数を超えているので、SQL Server で新しいシステム タスクを実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="32d21-115">SQL Server was unable to run a new system task, either because there is insufficient memory or the number of configured sessions exceeds the maximum allowed in the server.</span></span> <span data-ttu-id="32d21-116">サーバーに十分なメモリがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="32d21-116">Verify that the server has adequate memory.</span></span> <span data-ttu-id="32d21-117">ユーザー接続の許容最大数を確認するにはオプション 'user connections' を指定して sp_configure を使用してください。</span><span class="sxs-lookup"><span data-stu-id="32d21-117">Use sp_configure with option 'user connections' to check the maximum number of user connections allowed.</span></span> <span data-ttu-id="32d21-118">ユーザー プロセスを含めた現在のセッション数を確認するには sys.dm_exec_sessions を使用してください。</span><span class="sxs-lookup"><span data-stu-id="32d21-118">Use sys.dm_exec_sessions to check the current number of sessions, including user processes.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="32d21-119">説明</span><span class="sxs-lookup"><span data-stu-id="32d21-119">Explanation</span></span>  
 <span data-ttu-id="32d21-120">メモリが不足しているか、サーバーに構成されているセッション数を超えたため、新しいシステム タスクを実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="32d21-120">An attempt to run a new system task failed because of insufficient memory or because the number of configured sessions in the server was exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="32d21-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="32d21-121">User Action</span></span>  
 <span data-ttu-id="32d21-122">サーバーに十分なメモリがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="32d21-122">Verify that the server has enough memory.</span></span> <span data-ttu-id="32d21-123">sys.dm_exec_sessions を使用して現在のシステム タスク数を確認し、sp_configure を使用してユーザー接続の最大数の構成値を確認します。</span><span class="sxs-lookup"><span data-stu-id="32d21-123">Verify the current number of system tasks by using sys.dm_exec_sessions, and verify the configured value of maximum user connections by using sp_configure.</span></span>  
  
 <span data-ttu-id="32d21-124">必要に応じて、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="32d21-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="32d21-125">サーバーにメモリを追加します。</span><span class="sxs-lookup"><span data-stu-id="32d21-125">Add more memory to the server.</span></span>  
  
-   <span data-ttu-id="32d21-126">1 つ以上のセッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="32d21-126">Terminate one or more sessions.</span></span>  
  
-   <span data-ttu-id="32d21-127">サーバー上で許可されるユーザー接続の最大数を増やします。</span><span class="sxs-lookup"><span data-stu-id="32d21-127">Increase the maximum number of user connections allowed on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d21-128">参照</span><span class="sxs-lookup"><span data-stu-id="32d21-128">See Also</span></span>  
 <span data-ttu-id="32d21-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32d21-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="32d21-130">[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32d21-130">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="32d21-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32d21-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span></span>  
 <span data-ttu-id="32d21-132">[User connections サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="32d21-132">[Configure the user connections Server Configuration Option](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="32d21-133">KILL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32d21-133">KILL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
