---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643909"
---
# <a name="mssqlserver_15517"></a><span data-ttu-id="f6520-102">MSSQLSERVER_15517</span><span class="sxs-lookup"><span data-stu-id="f6520-102">MSSQLSERVER_15517</span></span>
    
## <a name="details"></a><span data-ttu-id="f6520-103">詳細</span><span class="sxs-lookup"><span data-stu-id="f6520-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6520-104">製品名</span><span class="sxs-lookup"><span data-stu-id="f6520-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="f6520-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f6520-105">Event ID</span></span>|<span data-ttu-id="f6520-106">15517</span><span class="sxs-lookup"><span data-stu-id="f6520-106">15517</span></span>|  
|<span data-ttu-id="f6520-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="f6520-107">Event Source</span></span>|<span data-ttu-id="f6520-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f6520-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f6520-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f6520-109">Component</span></span>|<span data-ttu-id="f6520-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f6520-110">SQLEngine</span></span>|  
|<span data-ttu-id="f6520-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="f6520-111">Symbolic Name</span></span>|<span data-ttu-id="f6520-112">SEC_CANNOTEXECUTEASUSER</span><span class="sxs-lookup"><span data-stu-id="f6520-112">SEC_CANNOTEXECUTEASUSER</span></span>|  
|<span data-ttu-id="f6520-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f6520-113">Message Text</span></span>|<span data-ttu-id="f6520-114">データベース プリンシパルとして実行できません。プリンシパル "*principal*" が存在しないか、この種類のプリンシパルで権限を借用できないか、ユーザーに権限がありません。</span><span class="sxs-lookup"><span data-stu-id="f6520-114">Cannot execute as the database principal because the principal "*principal*" does not exist, this type of principal cannot be impersonated, or you do not have permission.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="f6520-115">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f6520-115">User Action</span></span>  
 <span data-ttu-id="f6520-116">既存のプリンシパルの名前を使用するか、そのプリンシパルに対する IMPERSONATE 権限を取得します。</span><span class="sxs-lookup"><span data-stu-id="f6520-116">Use the name of an existing principal or get the IMPERSONATE permission on that principal.</span></span>  
  
 <span data-ttu-id="f6520-117">15517 は、元のデータベースの所有者以外のユーザーによってデータベースのアタッチおよび復元が実行された後に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6520-117">15517 can also occur after performing an attach and restore of a database by someone other than the original database owner.</span></span> <span data-ttu-id="f6520-118">このエラーを解決するには、次のコマンドを実行して、サーバーにログインするための db_owner を変更します。</span><span class="sxs-lookup"><span data-stu-id="f6520-118">To resolve this error, change the db_owner to a login on your server, by running the following command:</span></span>  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6520-119">参照</span><span class="sxs-lookup"><span data-stu-id="f6520-119">See Also</span></span>  
 [<span data-ttu-id="f6520-120">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="f6520-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
