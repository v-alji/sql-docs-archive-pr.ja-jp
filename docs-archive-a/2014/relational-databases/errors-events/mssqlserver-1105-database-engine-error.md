---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dea326fab7edd6a5c155c8f0182bffc044505eb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631999"
---
# <a name="mssqlserver_1105"></a><span data-ttu-id="4d127-102">MSSQLSERVER_1105</span><span class="sxs-lookup"><span data-stu-id="4d127-102">MSSQLSERVER_1105</span></span>
    
## <a name="details"></a><span data-ttu-id="4d127-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4d127-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d127-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4d127-104">Product Name</span></span>|<span data-ttu-id="4d127-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4d127-105">SQL Server</span></span>|  
|<span data-ttu-id="4d127-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4d127-106">Event ID</span></span>|<span data-ttu-id="4d127-107">1105</span><span class="sxs-lookup"><span data-stu-id="4d127-107">1105</span></span>|  
|<span data-ttu-id="4d127-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4d127-108">Event Source</span></span>|<span data-ttu-id="4d127-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4d127-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4d127-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4d127-110">Component</span></span>|<span data-ttu-id="4d127-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4d127-111">SQLEngine</span></span>|  
|<span data-ttu-id="4d127-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4d127-112">Symbolic Name</span></span>|<span data-ttu-id="4d127-113">NO_MORE_SPACE_IN_FG</span><span class="sxs-lookup"><span data-stu-id="4d127-113">NO_MORE_SPACE_IN_FG</span></span>|  
|<span data-ttu-id="4d127-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4d127-114">Message Text</span></span>|<span data-ttu-id="4d127-115">データベース '%.\*ls' にオブジェクト '%.\*ls'%.\*ls の領域を割り当てられませんでした。'%.\*ls' ファイル グループがいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="4d127-115">Could not allocate space for object '%.\*ls'%.\*ls in database '%.\*ls' because the '%.\*ls' filegroup is full.</span></span> <span data-ttu-id="4d127-116">不要なファイルの削除、ファイル グループ内のオブジェクトの削除、ファイル グループへの新しいファイルの追加、またはファイル グループの既存のファイルの自動拡張の設定のいずれかを行ってディスク領域を作成してください。</span><span class="sxs-lookup"><span data-stu-id="4d127-116">Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4d127-117">説明</span><span class="sxs-lookup"><span data-stu-id="4d127-117">Explanation</span></span>  
 <span data-ttu-id="4d127-118">ファイル グループでディスク領域が不足しています。</span><span class="sxs-lookup"><span data-stu-id="4d127-118">No disk space is available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4d127-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4d127-119">User Action</span></span>  
 <span data-ttu-id="4d127-120">次の操作により、ファイル グループで領域を使用できるようになることがあります。</span><span class="sxs-lookup"><span data-stu-id="4d127-120">The following actions may make space available in the filegroup:</span></span>  
  
-   <span data-ttu-id="4d127-121">AUTOGROW をオンにする。</span><span class="sxs-lookup"><span data-stu-id="4d127-121">Turn on autogrow.</span></span>  
  
-   <span data-ttu-id="4d127-122">ファイル グループにファイルをさらに追加する。</span><span class="sxs-lookup"><span data-stu-id="4d127-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="4d127-123">不要になったインデックスやテーブルを削除することにより、ディスク領域を解放する。</span><span class="sxs-lookup"><span data-stu-id="4d127-123">Free disk space by dropping index or tables that are no longer needed.</span></span>  
  
-   <span data-ttu-id="4d127-124">詳細については、SQL Server オンライン ブックの「データ ディスク領域の不足に関するトラブルシューティング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d127-124">For more information, see "Troubleshooting Insufficient Data Disk Space" in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d127-125">1 つのインデックスが複数のファイルに存在している場合に、いずれかのファイルがいっぱいになると、`ALTER INDEX REORGANIZE` からエラー 1105 が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d127-125">When an index is located on several files, `ALTER INDEX REORGANIZE` can return error 1105 when one of the files is full.</span></span> <span data-ttu-id="4d127-126">いっぱいになったファイルに行を移動しようとしたときに、再構成プロセスはブロックされます。</span><span class="sxs-lookup"><span data-stu-id="4d127-126">The reorganization process is blocked when the process tries to move rows to the full file.</span></span> <span data-ttu-id="4d127-127">この制限を回避するには、`ALTER INDEX REBUILD` ではなく `ALTER INDEX REORGANIZE` を実行するか、いっぱいになったファイルの拡張制限を大きくしてください。</span><span class="sxs-lookup"><span data-stu-id="4d127-127">To work around this limitation perform an `ALTER INDEX REBUILD` instead of `ALTER INDEX REORGANIZE` or increase the file growth limit of any files that are full.</span></span>  
  
  
