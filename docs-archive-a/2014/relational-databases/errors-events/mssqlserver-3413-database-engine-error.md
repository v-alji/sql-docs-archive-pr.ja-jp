---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a5d59ea61cff7051c3e1163a463c29443c553923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643865"
---
# <a name="mssqlserver_3413"></a><span data-ttu-id="dcbe8-102">MSSQLSERVER_3413</span><span class="sxs-lookup"><span data-stu-id="dcbe8-102">MSSQLSERVER_3413</span></span>
    
## <a name="details"></a><span data-ttu-id="dcbe8-103">詳細</span><span class="sxs-lookup"><span data-stu-id="dcbe8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcbe8-104">製品名</span><span class="sxs-lookup"><span data-stu-id="dcbe8-104">Product Name</span></span>|<span data-ttu-id="dcbe8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dcbe8-105">SQL Server</span></span>|  
|<span data-ttu-id="dcbe8-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="dcbe8-106">Event ID</span></span>|<span data-ttu-id="dcbe8-107">3413</span><span class="sxs-lookup"><span data-stu-id="dcbe8-107">3413</span></span>|  
|<span data-ttu-id="dcbe8-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="dcbe8-108">Event Source</span></span>|<span data-ttu-id="dcbe8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dcbe8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dcbe8-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dcbe8-110">Component</span></span>|<span data-ttu-id="dcbe8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dcbe8-111">SQLEngine</span></span>|  
|<span data-ttu-id="dcbe8-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="dcbe8-112">Symbolic Name</span></span>|<span data-ttu-id="dcbe8-113">MARKDB</span><span class="sxs-lookup"><span data-stu-id="dcbe8-113">MARKDB</span></span>|  
|<span data-ttu-id="dcbe8-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="dcbe8-114">Message Text</span></span>|<span data-ttu-id="dcbe8-115">データベース ID %d。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-115">Database ID %d.</span></span> <span data-ttu-id="dcbe8-116">データベースを問題ありに設定できませんでした。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-116">Could not mark database as suspect.</span></span> <span data-ttu-id="dcbe8-117">sys.databases.database_id での Getnext NC スキャンが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-117">Getnext NC scan on sys.databases.database_id failed.</span></span> <span data-ttu-id="dcbe8-118">エラー ログで以前のエラーを参照して原因を特定し、関連している問題をすべて修正してください。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-118">Refer to previous errors in the error log to identify the cause and correct any associated problems.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dcbe8-119">説明</span><span class="sxs-lookup"><span data-stu-id="dcbe8-119">Explanation</span></span>  
 <span data-ttu-id="dcbe8-120">カタログ内で、ユーザー データベースを SUSPECT に設定しようとして、予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-120">There was an unexpected failure while trying to mark a user database as SUSPECT in the catalog.</span></span> <span data-ttu-id="dcbe8-121">SUSPECT 状態は保存されません。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-121">The SUSPECT state will not be persisted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dcbe8-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="dcbe8-122">User Action</span></span>  
 <span data-ttu-id="dcbe8-123">これより前に発生したエラーを調べて、問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="dcbe8-123">See previous errors and correct the problem.</span></span>  
  
  
