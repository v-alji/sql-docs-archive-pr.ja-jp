---
title: MSSQLSERVER_5235 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740026"
---
# <a name="mssqlserver_5235"></a><span data-ttu-id="90103-102">MSSQLSERVER_5235</span><span class="sxs-lookup"><span data-stu-id="90103-102">MSSQLSERVER_5235</span></span>
    
## <a name="details"></a><span data-ttu-id="90103-103">詳細</span><span class="sxs-lookup"><span data-stu-id="90103-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90103-104">製品名</span><span class="sxs-lookup"><span data-stu-id="90103-104">Product Name</span></span>|<span data-ttu-id="90103-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="90103-105">SQL Server</span></span>|  
|<span data-ttu-id="90103-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90103-106">Event ID</span></span>|<span data-ttu-id="90103-107">5235</span><span class="sxs-lookup"><span data-stu-id="90103-107">5235</span></span>|  
|<span data-ttu-id="90103-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="90103-108">Event Source</span></span>|<span data-ttu-id="90103-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="90103-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="90103-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="90103-110">Component</span></span>|<span data-ttu-id="90103-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="90103-111">SQLEngine</span></span>|  
|<span data-ttu-id="90103-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="90103-112">Symbolic Name</span></span>|<span data-ttu-id="90103-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span><span class="sxs-lookup"><span data-stu-id="90103-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span></span>|  
|<span data-ttu-id="90103-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="90103-114">Message Text</span></span>|<span data-ttu-id="90103-115">[EMERGENCY] エラー状態 ERROR_STATE により、USER_NAME から実行された DBCC DBCC_COMMAND_DETAILS が異常終了しました。</span><span class="sxs-lookup"><span data-stu-id="90103-115">[EMERGENCY] DBCC DBCC_COMMAND_DETAILS executed by USER_NAME terminated abnormally due to error state ERROR_STATE.</span></span> <span data-ttu-id="90103-116">経過時間:HOURS 時間 MINUTES 分 SECONDS 秒。</span><span class="sxs-lookup"><span data-stu-id="90103-116">Elapsed time: HOURS hours MINUTES minutes SECONDS seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="90103-117">説明</span><span class="sxs-lookup"><span data-stu-id="90103-117">Explanation</span></span>  
 <span data-ttu-id="90103-118">これは、コマンドの実行中に予期しない異常終了が発生した場合に DBCC によって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに出力される概要メッセージです。</span><span class="sxs-lookup"><span data-stu-id="90103-118">This is the summary message that DBCC prints to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log when an unexpected termination occurs while the command is running.</span></span> <span data-ttu-id="90103-119">予期しない異常終了の種類は、メッセージで報告されるエラー状態で示されます。</span><span class="sxs-lookup"><span data-stu-id="90103-119">The error state reported in the message defines the type of unexpected termination.</span></span>  
  
 <span data-ttu-id="90103-120">次の表に、エラー状態の一覧と定義を示します。</span><span class="sxs-lookup"><span data-stu-id="90103-120">The following table lists and defines the error states.</span></span>  
  
|<span data-ttu-id="90103-121">エラー状態</span><span class="sxs-lookup"><span data-stu-id="90103-121">Error state</span></span>|<span data-ttu-id="90103-122">定義</span><span class="sxs-lookup"><span data-stu-id="90103-122">Definition</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="90103-123">状態 0</span><span class="sxs-lookup"><span data-stu-id="90103-123">State 0</span></span>|<span data-ttu-id="90103-124">致命的なメタデータの破損により、ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="90103-124">The statement was terminated because of a fatal metadata corruption.</span></span> <span data-ttu-id="90103-125">このメッセージは、1 件以上のエラー 8930 を伴います。</span><span class="sxs-lookup"><span data-stu-id="90103-125">This message will be accompanied by one or more instances of error 8930.</span></span>|  
|<span data-ttu-id="90103-126">状態 1</span><span class="sxs-lookup"><span data-stu-id="90103-126">State 1</span></span>|<span data-ttu-id="90103-127">内部チェック エラーにより、ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="90103-127">The statement was terminated because of an internal check failure.</span></span> <span data-ttu-id="90103-128">このメッセージは、1 件以上のエラー 8967 を伴います。</span><span class="sxs-lookup"><span data-stu-id="90103-128">This message will be accompanied by one or more instances of error 8967.</span></span>|  
|<span data-ttu-id="90103-129">状態 2</span><span class="sxs-lookup"><span data-stu-id="90103-129">State 2</span></span>|<span data-ttu-id="90103-130">ストレージ エンジンのコア システム テーブルの基本システム テーブル チェックが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="90103-130">Basic system table checks of the core storage engine system tables failed.</span></span> <span data-ttu-id="90103-131">このメッセージは、1 件以上のエラー [7984](mssqlserver-7984-database-engine-error.md)、7985、[7986](mssqlserver-7986-database-engine-error.md)、[7987](mssqlserver-7987-database-engine-error.md)、または [7988](mssqlserver-7988-database-engine-error.md) を伴います。</span><span class="sxs-lookup"><span data-stu-id="90103-131">This message will be accompanied by one or more instances of error [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md), or [7988](mssqlserver-7988-database-engine-error.md).</span></span>|  
|<span data-ttu-id="90103-132">状態 3</span><span class="sxs-lookup"><span data-stu-id="90103-132">State 3</span></span>|<span data-ttu-id="90103-133">トランザクション ログの再構築後にデータベースを起動できなかったため、DBCC 緊急モードでの修復が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="90103-133">DBCC emergency-mode repair failed because the database could not be started after rebuilding the transaction log.</span></span> <span data-ttu-id="90103-134">このメッセージは、エラー 7909 を伴います。</span><span class="sxs-lookup"><span data-stu-id="90103-134">This message will be accompanied by error 7909.</span></span>|  
|<span data-ttu-id="90103-135">状態 4</span><span class="sxs-lookup"><span data-stu-id="90103-135">State 4</span></span>|<span data-ttu-id="90103-136">コマンドの実行中に、アサーションの失敗またはアクセス違反が発生しました。</span><span class="sxs-lookup"><span data-stu-id="90103-136">A failed assertion or access violation occurred during the execution of the command.</span></span>|  
|<span data-ttu-id="90103-137">状態 5</span><span class="sxs-lookup"><span data-stu-id="90103-137">State 5</span></span>|<span data-ttu-id="90103-138">不明なエラーが発生し、DBCC コマンドが予期せず終了しました。</span><span class="sxs-lookup"><span data-stu-id="90103-138">An unknown failure occurred that unexpectedly terminated the DBCC command.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="90103-139">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="90103-139">User Action</span></span>  
 <span data-ttu-id="90103-140">次の表に、指定されたエラー状態に対応するユーザーのアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="90103-140">The following table provides the user action that is appropriate for the specified error state.</span></span>  
  
|<span data-ttu-id="90103-141">エラー状態</span><span class="sxs-lookup"><span data-stu-id="90103-141">Error state</span></span>|<span data-ttu-id="90103-142">ユーザー アクション</span><span class="sxs-lookup"><span data-stu-id="90103-142">User action</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="90103-143">状態 0</span><span class="sxs-lookup"><span data-stu-id="90103-143">State 0</span></span>|<span data-ttu-id="90103-144">バックアップからの復元を行います。</span><span class="sxs-lookup"><span data-stu-id="90103-144">Restore from backup.</span></span>|  
|<span data-ttu-id="90103-145">状態 1</span><span class="sxs-lookup"><span data-stu-id="90103-145">State 1</span></span>|<span data-ttu-id="90103-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) に問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="90103-146">Contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>|  
|<span data-ttu-id="90103-147">状態 2</span><span class="sxs-lookup"><span data-stu-id="90103-147">State 2</span></span>|<span data-ttu-id="90103-148">バックアップからの復元を行います。</span><span class="sxs-lookup"><span data-stu-id="90103-148">Restore from backup.</span></span>|  
|<span data-ttu-id="90103-149">状態 3</span><span class="sxs-lookup"><span data-stu-id="90103-149">State 3</span></span>|<span data-ttu-id="90103-150">バックアップからの復元を行います。</span><span class="sxs-lookup"><span data-stu-id="90103-150">Restore from backup.</span></span>|  
|<span data-ttu-id="90103-151">状態 4</span><span class="sxs-lookup"><span data-stu-id="90103-151">State 4</span></span>|<span data-ttu-id="90103-152">CSS に問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="90103-152">Contact CSS.</span></span>|  
|<span data-ttu-id="90103-153">状態 5</span><span class="sxs-lookup"><span data-stu-id="90103-153">State 5</span></span>|<span data-ttu-id="90103-154">コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="90103-154">Run the command again.</span></span> <span data-ttu-id="90103-155">問題が解決しない場合は、CSS に問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="90103-155">If the problem persists, contact CSS.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90103-156">参照</span><span class="sxs-lookup"><span data-stu-id="90103-156">See Also</span></span>  
 [<span data-ttu-id="90103-157">DBCC &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90103-157">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
