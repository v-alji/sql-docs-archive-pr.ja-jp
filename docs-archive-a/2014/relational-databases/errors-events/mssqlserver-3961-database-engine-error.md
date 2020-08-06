---
title: MSSQLSERVER_3961 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f55be9288b3c2e559633d0f67709829466fc8815
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644478"
---
# <a name="mssqlserver_3961"></a><span data-ttu-id="06aca-102">MSSQLSERVER_3961</span><span class="sxs-lookup"><span data-stu-id="06aca-102">MSSQLSERVER_3961</span></span>
    
## <a name="details"></a><span data-ttu-id="06aca-103">詳細</span><span class="sxs-lookup"><span data-stu-id="06aca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06aca-104">製品名</span><span class="sxs-lookup"><span data-stu-id="06aca-104">Product Name</span></span>|<span data-ttu-id="06aca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06aca-105">SQL Server</span></span>|  
|<span data-ttu-id="06aca-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="06aca-106">Event ID</span></span>|<span data-ttu-id="06aca-107">3961</span><span class="sxs-lookup"><span data-stu-id="06aca-107">3961</span></span>|  
|<span data-ttu-id="06aca-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="06aca-108">Event Source</span></span>|<span data-ttu-id="06aca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06aca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06aca-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="06aca-110">Component</span></span>|<span data-ttu-id="06aca-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06aca-111">SQLEngine</span></span>|  
|<span data-ttu-id="06aca-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="06aca-112">Symbolic Name</span></span>|<span data-ttu-id="06aca-113">XACT_METADATA_INVALID</span><span class="sxs-lookup"><span data-stu-id="06aca-113">XACT_METADATA_INVALID</span></span>|  
|<span data-ttu-id="06aca-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="06aca-114">Message Text</span></span>|<span data-ttu-id="06aca-115">データベース '%.\*ls' でスナップショット分離トランザクションが失敗しました。ステートメントからアクセスされるオブジェクトが、このトランザクションの開始後に別の同時トランザクションの DDL ステートメントで変更されました。</span><span class="sxs-lookup"><span data-stu-id="06aca-115">Snapshot isolation transaction failed in database '%.\*ls' because the object accessed by the statement has been modified by a DDL statement in another concurrent transaction since the start of this transaction.</span></span>  <span data-ttu-id="06aca-116">メタデータはバージョン管理されないため、この操作は許可されません。</span><span class="sxs-lookup"><span data-stu-id="06aca-116">It is disallowed because the metadata is not versioned.</span></span> <span data-ttu-id="06aca-117">メタデータに対する同時更新は、スナップショット分離と組み合わせると一貫性を損なう結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06aca-117">A concurrent update to metadata can lead to inconsistency if mixed with snapshot isolation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06aca-118">説明</span><span class="sxs-lookup"><span data-stu-id="06aca-118">Explanation</span></span>  
 <span data-ttu-id="06aca-119">このエラーは、スナップショット分離でメタデータのクエリを実行していて、かつスナップショット分離でアクセスされているメタデータを更新する同時 DDL ステートメントがある場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="06aca-119">This error can occur if you are querying metadata under snapshot isolation and there is a concurrent DDL statement that updates the metadata that is being accessed under snapshot isolation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="06aca-120">では、メタデータのバージョン管理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="06aca-120">does not support versioning of metadata.</span></span> <span data-ttu-id="06aca-121">このため、スナップショット分離で実行されている明示的なトランザクション内で実行できる DDL 操作には制限があります。</span><span class="sxs-lookup"><span data-stu-id="06aca-121">For this reason, there are restrictions on what DDL operations can be performed within an explicit transaction running under snapshot isolation.</span></span> <span data-ttu-id="06aca-122">定義によると、暗黙のトランザクションとは、DDL ステートメントについてもスナップショット分離のセマンティクスの実行を可能にする単一ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="06aca-122">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span> <span data-ttu-id="06aca-123">スナップショット分離下では、BEGIN TRANSACTION ステートメントの後に、ALTER TABLE、CREATE INDEX、CREATE XML INDEX、ALTER INDEX、DROP INDEX、DBCC REINDEX、ALTER PARTITION FUNCTION、ALTER PARTITION SCHEME などの DDL ステートメントを実行することはできません。共通言語ランタイム (CLR) の DDL ステートメントも同様です。</span><span class="sxs-lookup"><span data-stu-id="06aca-123">The following DDL statements are not permitted under snapshot isolation after a BEGIN TRANSACTION statement: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME, or any common language runtime (CLR) DDL statement.</span></span> <span data-ttu-id="06aca-124">暗黙のトランザクション内でスナップショット分離を使用しているときには、これらのステートメントは許可されます。</span><span class="sxs-lookup"><span data-stu-id="06aca-124">These statements are permitted when you are using snapshot isolation within implicit transactions.</span></span> <span data-ttu-id="06aca-125">定義によると、暗黙のトランザクションとは、DDL ステートメントについてもスナップショット分離のセマンティクスの実行を可能にする単一ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="06aca-125">An implicit transaction, by definition, is a single statement which makes it possible to enforce the semantics of snapshot isolation even with DDL statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06aca-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="06aca-126">User Action</span></span>  
 <span data-ttu-id="06aca-127">スナップショット分離レベルをスナップショット以外の分離レベル (メタデータに対してクエリを実行する前の READ COMMITTED など) に変更します。</span><span class="sxs-lookup"><span data-stu-id="06aca-127">Change the snapshot isolation level to a non-snapshot isolation level such as read committed before querying metadata.</span></span>  
  
  
