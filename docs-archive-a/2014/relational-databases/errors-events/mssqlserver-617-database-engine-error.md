---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88e9feb7c3ac5d8cf646d2243319b2b160b7757e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718153"
---
# <a name="mssqlserver_617"></a><span data-ttu-id="f7faa-102">MSSQLSERVER_617</span><span class="sxs-lookup"><span data-stu-id="f7faa-102">MSSQLSERVER_617</span></span>
    
## <a name="details"></a><span data-ttu-id="f7faa-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f7faa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7faa-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f7faa-104">Product Name</span></span>|<span data-ttu-id="f7faa-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f7faa-105">SQL Server</span></span>|  
|<span data-ttu-id="f7faa-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f7faa-106">Event ID</span></span>|<span data-ttu-id="f7faa-107">617</span><span class="sxs-lookup"><span data-stu-id="f7faa-107">617</span></span>|  
|<span data-ttu-id="f7faa-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f7faa-108">Event Source</span></span>|<span data-ttu-id="f7faa-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f7faa-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f7faa-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f7faa-110">Component</span></span>|<span data-ttu-id="f7faa-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f7faa-111">SQLEngine</span></span>|  
|<span data-ttu-id="f7faa-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f7faa-112">Symbolic Name</span></span>|<span data-ttu-id="f7faa-113">NODESHASH</span><span class="sxs-lookup"><span data-stu-id="f7faa-113">NODESHASH</span></span>|  
|<span data-ttu-id="f7faa-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f7faa-114">Message Text</span></span>|<span data-ttu-id="f7faa-115">データベース ID %d のオブジェクト ID %ld の記述子の非ハッシュ化を試みたときに、記述子がハッシュ テーブルに見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f7faa-115">Descriptor for object ID %ld in database ID %d not found in the hash table during attempt to unhash it.</span></span> <span data-ttu-id="f7faa-116">作業テーブルがエントリに見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f7faa-116">A work table is missing an entry.</span></span> <span data-ttu-id="f7faa-117">クエリを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="f7faa-117">Rerun the query.</span></span> <span data-ttu-id="f7faa-118">カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。</span><span class="sxs-lookup"><span data-stu-id="f7faa-118">If a cursor is involved, close and reopen the cursor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f7faa-119">説明</span><span class="sxs-lookup"><span data-stu-id="f7faa-119">Explanation</span></span>  
 <span data-ttu-id="f7faa-120">SQL Server で、作業テーブルの特定のエントリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f7faa-120">SQL Server cannot locate the work table for a specific entry.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f7faa-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f7faa-121">User Action</span></span>  
  
1.  <span data-ttu-id="f7faa-122">カーソルが含まれている場合は、カーソルを閉じてから再度開いてください。</span><span class="sxs-lookup"><span data-stu-id="f7faa-122">If a cursor is involved, close the cursor and re-open the cursor.</span></span>  
  
2.  <span data-ttu-id="f7faa-123">クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="f7faa-123">Run the query again.</span></span>  
  
  
