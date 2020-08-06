---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 30b57aae907d6f0acc4d1c0e6021bf936621c69e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631986"
---
# <a name="mssqlserver_2530"></a><span data-ttu-id="00b2f-102">MSSQLSERVER_2530</span><span class="sxs-lookup"><span data-stu-id="00b2f-102">MSSQLSERVER_2530</span></span>
    
## <a name="details"></a><span data-ttu-id="00b2f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="00b2f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00b2f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="00b2f-104">Product Name</span></span>|<span data-ttu-id="00b2f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="00b2f-105">SQL Server</span></span>|  
|<span data-ttu-id="00b2f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="00b2f-106">Event ID</span></span>|<span data-ttu-id="00b2f-107">2530</span><span class="sxs-lookup"><span data-stu-id="00b2f-107">2530</span></span>|  
|<span data-ttu-id="00b2f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="00b2f-108">Event Source</span></span>|<span data-ttu-id="00b2f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="00b2f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="00b2f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="00b2f-110">Component</span></span>|<span data-ttu-id="00b2f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="00b2f-111">SQLEngine</span></span>|  
|<span data-ttu-id="00b2f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="00b2f-112">Symbolic Name</span></span>|<span data-ttu-id="00b2f-113">DBCC_INDEX_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="00b2f-113">DBCC_INDEX_IS_OFFLINE</span></span>|  
|<span data-ttu-id="00b2f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="00b2f-114">Message Text</span></span>|<span data-ttu-id="00b2f-115">テーブル "%.\*ls" のインデックス "%.\*ls" は無効です。</span><span class="sxs-lookup"><span data-stu-id="00b2f-115">The index "%.\*ls" on table "%.\*ls" is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="00b2f-116">説明</span><span class="sxs-lookup"><span data-stu-id="00b2f-116">Explanation</span></span>  
 <span data-ttu-id="00b2f-117">指定されたインデックスが無効になっているため、DBCC ステートメントを実行できません。</span><span class="sxs-lookup"><span data-stu-id="00b2f-117">The DBCC statement cannot proceed because the specified index is disabled.</span></span> <span data-ttu-id="00b2f-118">インデックスを無効にすると、そのインデックスは再構築、または削除されて再作成されるまで無効になります。</span><span class="sxs-lookup"><span data-stu-id="00b2f-118">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped and re-created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00b2f-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="00b2f-119">User Action</span></span>  
  
1.  <span data-ttu-id="00b2f-120">次のいずれかの方法を使用して、無効になっているインデックスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="00b2f-120">Enable the disabled index by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="00b2f-121">REBUILD 句を指定した ALTER INDEX ステートメント</span><span class="sxs-lookup"><span data-stu-id="00b2f-121">ALTER INDEX statement with the REBUILD clause</span></span>  
  
    -   <span data-ttu-id="00b2f-122">DROP_EXISTING 句を指定した CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="00b2f-122">CREATE INDEX with the DROP_EXISTING clause</span></span>  
  
    -   <span data-ttu-id="00b2f-123">DBCC DBREINDEX</span><span class="sxs-lookup"><span data-stu-id="00b2f-123">DBCC DBREINDEX</span></span>  
  
2.  <span data-ttu-id="00b2f-124">DBCC ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="00b2f-124">Rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b2f-125">参照</span><span class="sxs-lookup"><span data-stu-id="00b2f-125">See Also</span></span>  
 <span data-ttu-id="00b2f-126">[インデックスと制約の有効化](../indexes/enable-indexes-and-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="00b2f-126">[Enable Indexes and Constraints](../indexes/enable-indexes-and-constraints.md) </span></span>  
 <span data-ttu-id="00b2f-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00b2f-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="00b2f-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="00b2f-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="00b2f-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="00b2f-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
