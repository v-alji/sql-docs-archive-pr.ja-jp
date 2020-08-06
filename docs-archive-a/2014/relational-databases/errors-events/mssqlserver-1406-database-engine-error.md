---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adaa0084b875f720c477189e0e8e085af124f4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718207"
---
# <a name="mssqlserver_1406"></a><span data-ttu-id="c5f01-102">MSSQLSERVER_1406</span><span class="sxs-lookup"><span data-stu-id="c5f01-102">MSSQLSERVER_1406</span></span>
    
## <a name="details"></a><span data-ttu-id="c5f01-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c5f01-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5f01-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c5f01-104">Product Name</span></span>|<span data-ttu-id="c5f01-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c5f01-105">SQL Server</span></span>|  
|<span data-ttu-id="c5f01-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c5f01-106">Event ID</span></span>|<span data-ttu-id="c5f01-107">1406</span><span class="sxs-lookup"><span data-stu-id="c5f01-107">1406</span></span>|  
|<span data-ttu-id="c5f01-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c5f01-108">Event Source</span></span>|<span data-ttu-id="c5f01-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c5f01-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c5f01-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c5f01-110">Component</span></span>|<span data-ttu-id="c5f01-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c5f01-111">SQLEngine</span></span>|  
|<span data-ttu-id="c5f01-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c5f01-112">Symbolic Name</span></span>|<span data-ttu-id="c5f01-113">DBM_BADSTATEFORFORCESERVICE</span><span class="sxs-lookup"><span data-stu-id="c5f01-113">DBM_BADSTATEFORFORCESERVICE</span></span>|  
|<span data-ttu-id="c5f01-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c5f01-114">Message Text</span></span>|<span data-ttu-id="c5f01-115">サービスを安全に実行できません。</span><span class="sxs-lookup"><span data-stu-id="c5f01-115">Unable to force service safely.</span></span> <span data-ttu-id="c5f01-116">アクセスできるようにするには、データベース ミラーリングを削除して、データベース "%.\*ls" を復旧してください。</span><span class="sxs-lookup"><span data-stu-id="c5f01-116">Remove database mirroring and recover database "%.\*ls" to gain access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c5f01-117">説明</span><span class="sxs-lookup"><span data-stu-id="c5f01-117">Explanation</span></span>  
 <span data-ttu-id="c5f01-118">ミラーリング状態ではサービスを強制するプロセスが正しく動作することを保証できないため、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]でサービスを強制できません。</span><span class="sxs-lookup"><span data-stu-id="c5f01-118">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot force service because the mirroring state cannot guarantee that the force service process would work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5f01-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c5f01-119">User Action</span></span>  
 <span data-ttu-id="c5f01-120">データベース ミラーリングを削除します。</span><span class="sxs-lookup"><span data-stu-id="c5f01-120">Remove database mirroring.</span></span> <span data-ttu-id="c5f01-121">その後、ミラー データベースを復旧して、このデータベースにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5f01-121">You can then recover the mirror database to gain access to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f01-122">参照</span><span class="sxs-lookup"><span data-stu-id="c5f01-122">See Also</span></span>  
 <span data-ttu-id="c5f01-123">[データベース ミラーリング セッションでのサービスの強制 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="c5f01-123">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 [<span data-ttu-id="c5f01-124">データベース ミラーリングの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c5f01-124">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
