---
title: MSSQLSERVER_2539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f061d2a827dca641bfc0c348af1328fd71856fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643873"
---
# <a name="mssqlserver_2539"></a><span data-ttu-id="8cecf-102">MSSQLSERVER_2539</span><span class="sxs-lookup"><span data-stu-id="8cecf-102">MSSQLSERVER_2539</span></span>
    
## <a name="details"></a><span data-ttu-id="8cecf-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8cecf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8cecf-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8cecf-104">Product Name</span></span>|<span data-ttu-id="8cecf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8cecf-105">SQL Server</span></span>|  
|<span data-ttu-id="8cecf-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8cecf-106">Event ID</span></span>|<span data-ttu-id="8cecf-107">2539</span><span class="sxs-lookup"><span data-stu-id="8cecf-107">2539</span></span>|  
|<span data-ttu-id="8cecf-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8cecf-108">Event Source</span></span>|<span data-ttu-id="8cecf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8cecf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8cecf-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8cecf-110">Component</span></span>|<span data-ttu-id="8cecf-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8cecf-111">SQLEngine</span></span>|  
|<span data-ttu-id="8cecf-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8cecf-112">Symbolic Name</span></span>|<span data-ttu-id="8cecf-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span><span class="sxs-lookup"><span data-stu-id="8cecf-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span></span>|  
|<span data-ttu-id="8cecf-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8cecf-114">Message Text</span></span>|<span data-ttu-id="8cecf-115">このデータベース内のエクステントの合計数 = EXTENTS、使用ページ数 = USED_PAGES、および予約ページ数 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="8cecf-115">Total number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES in this database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8cecf-116">説明</span><span class="sxs-lookup"><span data-stu-id="8cecf-116">Explanation</span></span>  
 <span data-ttu-id="8cecf-117">この情報は、DBCC CHECKALLOC コマンドからの出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="8cecf-117">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="8cecf-118">この情報は、指定されたデータベースについて、割り当てられたエクステント数、使用ページ数、および予約ページ数を示す要約です。</span><span class="sxs-lookup"><span data-stu-id="8cecf-118">This information is the summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8cecf-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8cecf-119">User Action</span></span>  
 <span data-ttu-id="8cecf-120">なし</span><span class="sxs-lookup"><span data-stu-id="8cecf-120">None</span></span>  
  
  
