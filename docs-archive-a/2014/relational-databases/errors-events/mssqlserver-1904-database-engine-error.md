---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640039"
---
# <a name="mssqlserver_1904"></a><span data-ttu-id="8a1dc-102">MSSQLSERVER_1904</span><span class="sxs-lookup"><span data-stu-id="8a1dc-102">MSSQLSERVER_1904</span></span>
    
## <a name="details"></a><span data-ttu-id="8a1dc-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8a1dc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a1dc-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8a1dc-104">Product Name</span></span>|<span data-ttu-id="8a1dc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a1dc-105">SQL Server</span></span>|  
|<span data-ttu-id="8a1dc-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8a1dc-106">Event ID</span></span>|<span data-ttu-id="8a1dc-107">1904</span><span class="sxs-lookup"><span data-stu-id="8a1dc-107">1904</span></span>|  
|<span data-ttu-id="8a1dc-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8a1dc-108">Event Source</span></span>|<span data-ttu-id="8a1dc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a1dc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a1dc-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a1dc-110">Component</span></span>|<span data-ttu-id="8a1dc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8a1dc-111">SQLEngine</span></span>|  
|<span data-ttu-id="8a1dc-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8a1dc-112">Symbolic Name</span></span>|<span data-ttu-id="8a1dc-113">KEYCOUNT</span><span class="sxs-lookup"><span data-stu-id="8a1dc-113">KEYCOUNT</span></span>|  
|<span data-ttu-id="8a1dc-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8a1dc-114">Message Text</span></span>|<span data-ttu-id="8a1dc-115">テーブル'%.\*ls' の %S_MSG '%.\*ls' の %S_MSG キー リストに %d 個の列名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-115">The %S_MSG '%.\*ls' on table '%.\*ls' has %d column names in %S_MSG key list.</span></span> <span data-ttu-id="8a1dc-116">インデックスまたは統計のキー列リストの上限は %d です。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-116">The maximum limit for index or statistics key column list is %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a1dc-117">説明</span><span class="sxs-lookup"><span data-stu-id="8a1dc-117">Explanation</span></span>  
 <span data-ttu-id="8a1dc-118">指定したインデックスまたは統計のキー列リストが許容される最大列数を超えています。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-118">The key column list for the specified index or statistics exceeds the maximum number of columns allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a1dc-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8a1dc-119">User Action</span></span>  
 <span data-ttu-id="8a1dc-120">キー列リストの列数が指定された最大列数以下になるように変更します。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-120">Modify the key column list to include no more than the specified maximum number of columns.</span></span>  
  
 <span data-ttu-id="8a1dc-121">非クラスター化インデックスの場合は、CREATE INDEX ステートメントの INCLUDE 句を使用して、列を非キー列としてインデックスに追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-121">For nonclustered indexes, consider using the INCLUDE clause in the CREATE INDEX statement to add columns to the index as nonkey columns.</span></span> <span data-ttu-id="8a1dc-122">この方法を使用すると、キー列の数が現在のインデックス サイズの上限である 16 を超えないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-122">This method avoids exceeding the current index size limitation of a maximum of 16 key columns.</span></span> <span data-ttu-id="8a1dc-123">詳細については、「 [付加列インデックスの作成](../indexes/create-indexes-with-included-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a1dc-123">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1dc-124">参照</span><span class="sxs-lookup"><span data-stu-id="8a1dc-124">See Also</span></span>  
 <span data-ttu-id="8a1dc-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a1dc-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="8a1dc-126">CREATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8a1dc-126">CREATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
