---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c2bc421fb969e4f24e49871ff97047be9040ae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643904"
---
# <a name="mssqlserver_17066"></a><span data-ttu-id="c34f6-102">MSSQLSERVER_17066</span><span class="sxs-lookup"><span data-stu-id="c34f6-102">MSSQLSERVER_17066</span></span>
    
## <a name="details"></a><span data-ttu-id="c34f6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c34f6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c34f6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c34f6-104">Product Name</span></span>|<span data-ttu-id="c34f6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c34f6-105">SQL Server</span></span>|  
|<span data-ttu-id="c34f6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c34f6-106">Event ID</span></span>|<span data-ttu-id="c34f6-107">17066</span><span class="sxs-lookup"><span data-stu-id="c34f6-107">17066</span></span>|  
|<span data-ttu-id="c34f6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c34f6-108">Event Source</span></span>|<span data-ttu-id="c34f6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c34f6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c34f6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c34f6-110">Component</span></span>|<span data-ttu-id="c34f6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c34f6-111">SQLEngine</span></span>|  
|<span data-ttu-id="c34f6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c34f6-112">Symbolic Name</span></span>|<span data-ttu-id="c34f6-113">SQLASSERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="c34f6-113">SQLASSERT_ONLY</span></span>|  
|<span data-ttu-id="c34f6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c34f6-114">Message Text</span></span>|<span data-ttu-id="c34f6-115">SQL Server アサーション:ファイル: \<%s>、行 = %d 失敗したアサーション = '%s'。</span><span class="sxs-lookup"><span data-stu-id="c34f6-115">SQL Server Assertion: File: \<%s>, line=%d Failed Assertion = '%s'.</span></span> <span data-ttu-id="c34f6-116">このエラーはタイミングに関係している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c34f6-116">This error may be timing-related.</span></span> <span data-ttu-id="c34f6-117">ステートメントの再実行後もエラーが解決しない場合は、DBCC CHECKDB を使用してデータベースの構造上の整合性を確認するか、またはサーバーを再起動してインメモリ データ構造体が壊れていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c34f6-117">If the error persists after rerunning the statement, use DBCC CHECKDB to check the database for structural integrity, or restart the server to ensure in-memory data structures are not corrupted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c34f6-118">説明</span><span class="sxs-lookup"><span data-stu-id="c34f6-118">Explanation</span></span>  
 <span data-ttu-id="c34f6-119">このエラーは、一時的なタイミングに関係する問題や、メモリ内またはディスク上のデータの破損によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c34f6-119">This error can be caused by transient, timing-related errors, or by in-memory or on-disk data corruption.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c34f6-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c34f6-120">User Action</span></span>  
 <span data-ttu-id="c34f6-121">例外を発生させたステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="c34f6-121">Rerun the statement that caused the exception to fire.</span></span> <span data-ttu-id="c34f6-122">タイミングに関係しているイベントによって発生したエラーの場合、エラーは再び発生しません。</span><span class="sxs-lookup"><span data-stu-id="c34f6-122">If the error was caused by a timing-related event, the error may not recur.</span></span> <span data-ttu-id="c34f6-123">問題が引き続き発生する場合は、DBCC CHECKDB を実行してディスク上の破損を確認します。</span><span class="sxs-lookup"><span data-stu-id="c34f6-123">If the problem persists, run DBCC CHECKDB to  check for on-disk corruption.</span></span> <span data-ttu-id="c34f6-124">サーバーを再起動し、インメモリ データ構造体が壊れていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c34f6-124">Restart the server to ensure that the in-memory data structures are not corrupted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34f6-125">参照</span><span class="sxs-lookup"><span data-stu-id="c34f6-125">See Also</span></span>  
 [<span data-ttu-id="c34f6-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c34f6-126">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
