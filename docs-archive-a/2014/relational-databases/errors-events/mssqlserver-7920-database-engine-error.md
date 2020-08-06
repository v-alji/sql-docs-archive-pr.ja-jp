---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8084a0542e9163ad72623336a909e65ca7617f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641673"
---
# <a name="mssqlserver_7920"></a><span data-ttu-id="f0831-102">MSSQLSERVER_7920</span><span class="sxs-lookup"><span data-stu-id="f0831-102">MSSQLSERVER_7920</span></span>
    
## <a name="details"></a><span data-ttu-id="f0831-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f0831-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0831-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f0831-104">Product Name</span></span>|<span data-ttu-id="f0831-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f0831-105">SQL Server</span></span>|  
|<span data-ttu-id="f0831-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f0831-106">Event ID</span></span>|<span data-ttu-id="f0831-107">7920</span><span class="sxs-lookup"><span data-stu-id="f0831-107">7920</span></span>|  
|<span data-ttu-id="f0831-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f0831-108">Event Source</span></span>|<span data-ttu-id="f0831-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f0831-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f0831-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f0831-110">Component</span></span>|<span data-ttu-id="f0831-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f0831-111">SQLEngine</span></span>|  
|<span data-ttu-id="f0831-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f0831-112">Symbolic Name</span></span>|<span data-ttu-id="f0831-113">DBCC2_SUMMARY_ENTRIES</span><span class="sxs-lookup"><span data-stu-id="f0831-113">DBCC2_SUMMARY_ENTRIES</span></span>|  
|<span data-ttu-id="f0831-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f0831-114">Message Text</span></span>|<span data-ttu-id="f0831-115">データベース ID D_ID のシステム カタログ内にある ENTRY_COUNT エントリを処理しました。</span><span class="sxs-lookup"><span data-stu-id="f0831-115">Processed ENTRY_COUNT entries in system catalog for database ID D_ID.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f0831-116">説明</span><span class="sxs-lookup"><span data-stu-id="f0831-116">Explanation</span></span>  
 <span data-ttu-id="f0831-117">これは、DBCC CHECKALLOC 以外のすべての DBCC CHECK コマンドによって返される情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="f0831-117">This is an informational message returned by all DBCC CHECK commands except DBCC CHECKALLOC.</span></span> <span data-ttu-id="f0831-118">返される値は、チェックされた行セットの合計数です。</span><span class="sxs-lookup"><span data-stu-id="f0831-118">The value returned is the total number of rowsets checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0831-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f0831-119">User Action</span></span>  
 <span data-ttu-id="f0831-120">なし</span><span class="sxs-lookup"><span data-stu-id="f0831-120">None</span></span>  
  
  
