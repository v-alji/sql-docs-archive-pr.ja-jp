---
title: MSSQLSERVER_3417 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 680e5a4266c7d0d9aaacb7b3deb9525a002077e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643861"
---
# <a name="mssqlserver_3417"></a><span data-ttu-id="fd6a3-102">MSSQLSERVER_3417</span><span class="sxs-lookup"><span data-stu-id="fd6a3-102">MSSQLSERVER_3417</span></span>
    
## <a name="details"></a><span data-ttu-id="fd6a3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="fd6a3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd6a3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="fd6a3-104">Product Name</span></span>|<span data-ttu-id="fd6a3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd6a3-105">SQL Server</span></span>|  
|<span data-ttu-id="fd6a3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="fd6a3-106">Event ID</span></span>|<span data-ttu-id="fd6a3-107">3417</span><span class="sxs-lookup"><span data-stu-id="fd6a3-107">3417</span></span>|  
|<span data-ttu-id="fd6a3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="fd6a3-108">Event Source</span></span>|<span data-ttu-id="fd6a3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fd6a3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fd6a3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fd6a3-110">Component</span></span>|<span data-ttu-id="fd6a3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fd6a3-111">SQLEngine</span></span>|  
|<span data-ttu-id="fd6a3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="fd6a3-112">Symbolic Name</span></span>|<span data-ttu-id="fd6a3-113">REC_BADMASTER</span><span class="sxs-lookup"><span data-stu-id="fd6a3-113">REC_BADMASTER</span></span>|  
|<span data-ttu-id="fd6a3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="fd6a3-114">Message Text</span></span>|<span data-ttu-id="fd6a3-115">master データベースを復旧できません。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-115">Cannot recover the master database.</span></span> <span data-ttu-id="fd6a3-116">SQL Server を実行できません。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-116">SQL Server is unable to run.</span></span> <span data-ttu-id="fd6a3-117">master データベースを、完全バックアップを使用して復元するか、修復または再構築してください。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-117">Restore master from a full backup, repair it, or rebuild it.</span></span> <span data-ttu-id="fd6a3-118">master データベースを再構築する方法の詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fd6a3-119">説明</span><span class="sxs-lookup"><span data-stu-id="fd6a3-119">Explanation</span></span>  
 <span data-ttu-id="fd6a3-120">SQL Server は **master** データベースを起動できません。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-120">SQL Server cannot start the **master** database.</span></span> <span data-ttu-id="fd6a3-121">**master** または **tempdb** がオンライン状態にならないと、SQL Server は稼働しません。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-121">If the **master** or **tempdb** cannot be brought online, SQL Server cannot run.</span></span> <span data-ttu-id="fd6a3-122">このエラーは通常、別のエラーの後に発生します。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-122">This error is usually preceded by other errors.</span></span> <span data-ttu-id="fd6a3-123">エラー ログで、根本的な原因を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-123">Review error logs to find the root cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fd6a3-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="fd6a3-124">User Action</span></span>  
 <span data-ttu-id="fd6a3-125">データベースのバックアップを復元するか、データベースを修復します。</span><span class="sxs-lookup"><span data-stu-id="fd6a3-125">Restore backup of the database or repair the database.</span></span>  
  
  
