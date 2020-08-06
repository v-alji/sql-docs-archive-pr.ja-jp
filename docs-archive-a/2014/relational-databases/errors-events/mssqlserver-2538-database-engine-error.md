---
title: MSSQLSERVER_2538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f4ae886a6fd0abee2f7aa22c6a234c0a6c2d040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643874"
---
# <a name="mssqlserver_2538"></a><span data-ttu-id="ffe59-102">MSSQLSERVER_2538</span><span class="sxs-lookup"><span data-stu-id="ffe59-102">MSSQLSERVER_2538</span></span>
    
## <a name="details"></a><span data-ttu-id="ffe59-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ffe59-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffe59-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ffe59-104">Product Name</span></span>|<span data-ttu-id="ffe59-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ffe59-105">SQL Server</span></span>|  
|<span data-ttu-id="ffe59-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ffe59-106">Event ID</span></span>|<span data-ttu-id="ffe59-107">2538</span><span class="sxs-lookup"><span data-stu-id="ffe59-107">2538</span></span>|  
|<span data-ttu-id="ffe59-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ffe59-108">Event Source</span></span>|<span data-ttu-id="ffe59-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ffe59-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ffe59-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ffe59-110">Component</span></span>|<span data-ttu-id="ffe59-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ffe59-111">SQLEngine</span></span>|  
|<span data-ttu-id="ffe59-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ffe59-112">Symbolic Name</span></span>|<span data-ttu-id="ffe59-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span><span class="sxs-lookup"><span data-stu-id="ffe59-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span></span>|  
|<span data-ttu-id="ffe59-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ffe59-114">Message Text</span></span>|<span data-ttu-id="ffe59-115">ファイル FILE。</span><span class="sxs-lookup"><span data-stu-id="ffe59-115">File FILE.</span></span> <span data-ttu-id="ffe59-116">エクステント数 = EXTENTS、使用ページ数 = USED_PAGES、予約ページ数 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="ffe59-116">Number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ffe59-117">説明</span><span class="sxs-lookup"><span data-stu-id="ffe59-117">Explanation</span></span>  
 <span data-ttu-id="ffe59-118">この情報は、DBCC CHECKALLOC コマンドからの出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="ffe59-118">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="ffe59-119">この情報はファイルごとの要約であり、指定されたデータベースについて、割り当てられたエクステント数、使用ページ数、および予約ページ数を示します。</span><span class="sxs-lookup"><span data-stu-id="ffe59-119">This information is the per-file summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ffe59-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ffe59-120">User Action</span></span>  
 <span data-ttu-id="ffe59-121">なし</span><span class="sxs-lookup"><span data-stu-id="ffe59-121">None</span></span>  
  
  
