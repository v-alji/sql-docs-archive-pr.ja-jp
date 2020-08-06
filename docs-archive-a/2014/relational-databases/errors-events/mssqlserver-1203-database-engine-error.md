---
title: MSSQLSERVER_1203 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cea816a60ccd1b90d849194766edebd2d64d0b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643401"
---
# <a name="mssqlserver_1203"></a><span data-ttu-id="18915-102">MSSQLSERVER_1203</span><span class="sxs-lookup"><span data-stu-id="18915-102">MSSQLSERVER_1203</span></span>
    
## <a name="details"></a><span data-ttu-id="18915-103">詳細</span><span class="sxs-lookup"><span data-stu-id="18915-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18915-104">製品名</span><span class="sxs-lookup"><span data-stu-id="18915-104">Product Name</span></span>|<span data-ttu-id="18915-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="18915-105">SQL Server</span></span>|  
|<span data-ttu-id="18915-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="18915-106">Event ID</span></span>|<span data-ttu-id="18915-107">1203</span><span class="sxs-lookup"><span data-stu-id="18915-107">1203</span></span>|  
|<span data-ttu-id="18915-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="18915-108">Event Source</span></span>|<span data-ttu-id="18915-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="18915-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="18915-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="18915-110">Component</span></span>|<span data-ttu-id="18915-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="18915-111">SQLEngine</span></span>|  
|<span data-ttu-id="18915-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="18915-112">Symbolic Name</span></span>|<span data-ttu-id="18915-113">LK_NOT</span><span class="sxs-lookup"><span data-stu-id="18915-113">LK_NOT</span></span>|  
|<span data-ttu-id="18915-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="18915-114">Message Text</span></span>|<span data-ttu-id="18915-115">プロセス ID %d は、所有していないリソース %.\*ls のロックを解除しようとしました。</span><span class="sxs-lookup"><span data-stu-id="18915-115">Process ID %d attempted to unlock a resource it does not own: %.\*ls.</span></span> <span data-ttu-id="18915-116">このエラーはタイミングによって発生する可能性があるので、トランザクションを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="18915-116">Retry the transaction, because this error may be caused by a timing condition.</span></span> <span data-ttu-id="18915-117">問題が解決しない場合は、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="18915-117">If the problem persists, contact the database administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="18915-118">説明</span><span class="sxs-lookup"><span data-stu-id="18915-118">Explanation</span></span>  
 <span data-ttu-id="18915-119">このエラーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が通常の後処理以外の何らかの処理を実行中に、ロックの解除を試みた特定のページのロックが既に解除されていることを検出した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="18915-119">This error occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is engaged in some activity other than ordinary post-processing cleanup and it finds that a particular page that it is trying to unlock is already unlocked.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="18915-120">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="18915-120">Possible Causes</span></span>  
 <span data-ttu-id="18915-121">このエラーの根本原因は、影響を受けたデータベース内の構造上の問題に関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18915-121">The underlying cause of this error may be related to structural problems within the affected database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="18915-122">では、マルチユーザー環境でのコンカレンシー制御を管理するために、ページの取得と解放を管理します。</span><span class="sxs-lookup"><span data-stu-id="18915-122">manages the acquisition and release of pages to maintain concurrency control in the multiuser environment.</span></span> <span data-ttu-id="18915-123">このメカニズムは、存在するロックのページと種類を識別するさまざまな内部ロック構造を使用することにより管理されます。</span><span class="sxs-lookup"><span data-stu-id="18915-123">This mechanism is maintained by using various internal lock structures that identify the page and the type of lock present.</span></span> <span data-ttu-id="18915-124">影響するページを処理するためにロックを取得し、処理が終了すると解放します。</span><span class="sxs-lookup"><span data-stu-id="18915-124">Locks are acquired for processing of affected pages and released when the processing is finished.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="18915-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="18915-125">User Action</span></span>  
 <span data-ttu-id="18915-126">オブジェクトが所属するデータベースに対して DBCC CHECKDB を実行します。</span><span class="sxs-lookup"><span data-stu-id="18915-126">Execute DBCC CHECKDB against the database in which the object belongs.</span></span> <span data-ttu-id="18915-127">DBCC CHECKDB でエラーが報告されない場合、接続を再度確立してコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18915-127">If DBCC CHECKDB reports no errors, try to reestablish the connection and execute the command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18915-128">いずれかの REPAIR 句を指定して DBCC CHECKDB を実行してもこの問題が解決しない場合、または REPAIR 句を指定して DBCC CHECKDB を実行した場合のデータへの影響がわからない場合は、購入元にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="18915-128">If you are executing DBCC CHECKDB with one of the REPAIR clauses does not correct the index problem, or if you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider.</span></span>  
  
  
