---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac3fe9314386836633a11f17d6775c75019de93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631068"
---
# <a name="mssqlserver_1222"></a><span data-ttu-id="bff23-102">MSSQLSERVER_1222</span><span class="sxs-lookup"><span data-stu-id="bff23-102">MSSQLSERVER_1222</span></span>
    
## <a name="details"></a><span data-ttu-id="bff23-103">詳細</span><span class="sxs-lookup"><span data-stu-id="bff23-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bff23-104">製品名</span><span class="sxs-lookup"><span data-stu-id="bff23-104">Product Name</span></span>|<span data-ttu-id="bff23-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bff23-105">SQL Server</span></span>|  
|<span data-ttu-id="bff23-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="bff23-106">Event ID</span></span>|<span data-ttu-id="bff23-107">1222</span><span class="sxs-lookup"><span data-stu-id="bff23-107">1222</span></span>|  
|<span data-ttu-id="bff23-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="bff23-108">Event Source</span></span>|<span data-ttu-id="bff23-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bff23-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bff23-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bff23-110">Component</span></span>|<span data-ttu-id="bff23-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bff23-111">SQLEngine</span></span>|  
|<span data-ttu-id="bff23-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="bff23-112">Symbolic Name</span></span>|<span data-ttu-id="bff23-113">LK_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bff23-113">LK_TIMEOUT</span></span>|  
|<span data-ttu-id="bff23-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="bff23-114">Message Text</span></span>|<span data-ttu-id="bff23-115">ロック要求がタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bff23-115">Lock request time out period exceeded.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bff23-116">説明</span><span class="sxs-lookup"><span data-stu-id="bff23-116">Explanation</span></span>  
 <span data-ttu-id="bff23-117">必要なリソースが、このクエリが待機できる時間より長く別のトランザクションによって拘束されています。</span><span class="sxs-lookup"><span data-stu-id="bff23-117">Another transaction held a lock on a required resource longer than this query could wait for it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bff23-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="bff23-118">User Action</span></span>  
 <span data-ttu-id="bff23-119">問題を軽減するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="bff23-119">Perform the following tasks to alleviate the problem:</span></span>  
  
1.  <span data-ttu-id="bff23-120">可能であれば、必要なリソースのロックを保持しているトランザクションを探します。</span><span class="sxs-lookup"><span data-stu-id="bff23-120">Locate the transaction that is holding the lock on the required resource, if possible.</span></span> <span data-ttu-id="bff23-121">**sys.dm_os_waiting_tasks** および **sys.dm_tran_locks** 動的管理ビューを使用してください。</span><span class="sxs-lookup"><span data-stu-id="bff23-121">Use **sys.dm_os_waiting_tasks** and **sys.dm_tran_locks** dynamic management views.</span></span>  
  
2.  <span data-ttu-id="bff23-122">トランザクションがロックをまだ保持している場合は、必要に応じてこのトランザクションを中止します。</span><span class="sxs-lookup"><span data-stu-id="bff23-122">If the transaction is still holding the lock, terminate that transaction if appropriate.</span></span>  
  
3.  <span data-ttu-id="bff23-123">クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="bff23-123">Execute the query again.</span></span>  
  
 <span data-ttu-id="bff23-124">このエラーが頻繁に発生する場合は、ロック要求のタイムアウト時間を変更するか、原因となっているトランザクションを修正してロックの拘束時間を短くします。</span><span class="sxs-lookup"><span data-stu-id="bff23-124">If this error occurs frequently change the lock time-out period or modify the offending transactions so that they hold the lock for less time.</span></span>  
  
  
