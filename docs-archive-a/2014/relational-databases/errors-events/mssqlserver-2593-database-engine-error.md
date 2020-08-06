---
title: MSSQLSERVER_2593 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecd231f38fbb36e2f98a1e9ce254165002bb56e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713186"
---
# <a name="mssqlserver_2593"></a><span data-ttu-id="6a6ea-102">MSSQLSERVER_2593</span><span class="sxs-lookup"><span data-stu-id="6a6ea-102">MSSQLSERVER_2593</span></span>
    
## <a name="details"></a><span data-ttu-id="6a6ea-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6a6ea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a6ea-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6a6ea-104">Product Name</span></span>|<span data-ttu-id="6a6ea-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a6ea-105">SQL Server</span></span>|  
|<span data-ttu-id="6a6ea-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6a6ea-106">Event ID</span></span>|<span data-ttu-id="6a6ea-107">2593</span><span class="sxs-lookup"><span data-stu-id="6a6ea-107">2593</span></span>|  
|<span data-ttu-id="6a6ea-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6a6ea-108">Event Source</span></span>|<span data-ttu-id="6a6ea-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a6ea-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a6ea-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6a6ea-110">Component</span></span>|<span data-ttu-id="6a6ea-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a6ea-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a6ea-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6a6ea-112">Symbolic Name</span></span>|<span data-ttu-id="6a6ea-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span><span class="sxs-lookup"><span data-stu-id="6a6ea-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span></span>|  
|<span data-ttu-id="6a6ea-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6a6ea-114">Message Text</span></span>|<span data-ttu-id="6a6ea-115">オブジェクト 'OBJECT' の PAGECOUNT ページには ROWCOUNT 行あります。</span><span class="sxs-lookup"><span data-stu-id="6a6ea-115">There are ROWCOUNT rows in PAGECOUNT pages for object 'OBJECT'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a6ea-116">説明</span><span class="sxs-lookup"><span data-stu-id="6a6ea-116">Explanation</span></span>  
 <span data-ttu-id="6a6ea-117">このメッセージは、DBCC CHECKALLOC を除くすべての DBCC チェックから返される情報出力の一部であり、指定されたオブジェクトの行カウントおよびページ カウントを示しています。</span><span class="sxs-lookup"><span data-stu-id="6a6ea-117">This message is part of the informational output that is returned by all DBCC checks, except DBCC CHECKALLOC, and indicates the row and page counts for a specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a6ea-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6a6ea-118">User Action</span></span>  
 <span data-ttu-id="6a6ea-119">なし</span><span class="sxs-lookup"><span data-stu-id="6a6ea-119">None</span></span>  
  
  
