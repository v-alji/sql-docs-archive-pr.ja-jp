---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e224e9a87d40fa826a05c669216649c45185037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645548"
---
# <a name="mssql_eng020574"></a><span data-ttu-id="02016-102">MSSQL_ENG020574</span><span class="sxs-lookup"><span data-stu-id="02016-102">MSSQL_ENG020574</span></span>
    
## <a name="message-details"></a><span data-ttu-id="02016-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="02016-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02016-104">製品名</span><span class="sxs-lookup"><span data-stu-id="02016-104">Product Name</span></span>|<span data-ttu-id="02016-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="02016-105">SQL Server</span></span>|  
|<span data-ttu-id="02016-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="02016-106">Event ID</span></span>|<span data-ttu-id="02016-107">20574</span><span class="sxs-lookup"><span data-stu-id="02016-107">20574</span></span>|  
|<span data-ttu-id="02016-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="02016-108">Event Source</span></span>|<span data-ttu-id="02016-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="02016-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="02016-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="02016-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="02016-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="02016-111">Symbolic Name</span></span>||  
|<span data-ttu-id="02016-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="02016-112">Message Text</span></span>|<span data-ttu-id="02016-113">パブリケーション '%s' のアーティクル '%s' に対するサブスクライバー '%s' のサブスクリプションで、データ検証に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="02016-113">Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02016-114">説明</span><span class="sxs-lookup"><span data-stu-id="02016-114">Explanation</span></span>  
 <span data-ttu-id="02016-115">サブスクライバーのデータがパブリッシャーのデータに対して検証され、データが一致しなかったため検証に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="02016-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="02016-116">検証の詳細については、「 [Validate Replicated Data](validate-data-at-the-subscriber.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02016-116">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02016-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="02016-117">User Action</span></span>  
 <span data-ttu-id="02016-118">次を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="02016-118">We recommend that you do the following:</span></span>  
  
-   <span data-ttu-id="02016-119">検証に失敗した原因を確認します。</span><span class="sxs-lookup"><span data-stu-id="02016-119">Determine why validation failed.</span></span>  
  
-   <span data-ttu-id="02016-120">失敗の原因である根本的な問題を修正します。</span><span class="sxs-lookup"><span data-stu-id="02016-120">Correct the underlying issue that caused the failure.</span></span>  
  
-   <span data-ttu-id="02016-121">サブスクリプションの再初期化やその他の方法によってデータを集約させます。</span><span class="sxs-lookup"><span data-stu-id="02016-121">Bring the data into convergence by reinitializing the subscription or through another method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02016-122">参照</span><span class="sxs-lookup"><span data-stu-id="02016-122">See Also</span></span>  
 [<span data-ttu-id="02016-123">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="02016-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
