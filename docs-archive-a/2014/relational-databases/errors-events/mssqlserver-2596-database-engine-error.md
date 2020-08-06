---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27b2ceed40274df4ba57c4d61a83fbc60b6a7f80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641006"
---
# <a name="mssqlserver_2596"></a><span data-ttu-id="02d39-102">MSSQLSERVER_2596</span><span class="sxs-lookup"><span data-stu-id="02d39-102">MSSQLSERVER_2596</span></span>
    
## <a name="details"></a><span data-ttu-id="02d39-103">詳細</span><span class="sxs-lookup"><span data-stu-id="02d39-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02d39-104">製品名</span><span class="sxs-lookup"><span data-stu-id="02d39-104">Product Name</span></span>|<span data-ttu-id="02d39-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="02d39-105">SQL Server</span></span>|  
|<span data-ttu-id="02d39-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="02d39-106">Event ID</span></span>|<span data-ttu-id="02d39-107">2596</span><span class="sxs-lookup"><span data-stu-id="02d39-107">2596</span></span>|  
|<span data-ttu-id="02d39-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="02d39-108">Event Source</span></span>|<span data-ttu-id="02d39-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="02d39-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="02d39-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="02d39-110">Component</span></span>|<span data-ttu-id="02d39-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="02d39-111">SQLEngine</span></span>|  
|<span data-ttu-id="02d39-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="02d39-112">Symbolic Name</span></span>|<span data-ttu-id="02d39-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span><span class="sxs-lookup"><span data-stu-id="02d39-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span></span>|  
|<span data-ttu-id="02d39-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="02d39-114">Message Text</span></span>|<span data-ttu-id="02d39-115">修復ステートメントは処理されませんでした。</span><span class="sxs-lookup"><span data-stu-id="02d39-115">The repair statement was not processed.</span></span> <span data-ttu-id="02d39-116">データベースを読み取り専用モードにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="02d39-116">The database cannot be in read-only mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02d39-117">説明</span><span class="sxs-lookup"><span data-stu-id="02d39-117">Explanation</span></span>  
 <span data-ttu-id="02d39-118">このメッセージは、データベースが読み取り専用モードであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="02d39-118">This message indicates that the database is in read-only mode.</span></span> <span data-ttu-id="02d39-119">データベースが読み取り専用モードである場合は、修復が不可能です。</span><span class="sxs-lookup"><span data-stu-id="02d39-119">Repairs are not possible when a database is in read-only mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02d39-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="02d39-120">User Action</span></span>  
 <span data-ttu-id="02d39-121">ALTER DATABASE を使用してデータベースを読み取り/書き込み可能に設定し、DBCC コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="02d39-121">Set the database to read-write by using ALTER DATABASE, and then re-run the DBCC command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d39-122">参照</span><span class="sxs-lookup"><span data-stu-id="02d39-122">See Also</span></span>  
 [<span data-ttu-id="02d39-123">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d39-123">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
