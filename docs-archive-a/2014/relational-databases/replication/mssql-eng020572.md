---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5762f160e119012f4fdc0ca1a205ba0ecf690378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645549"
---
# <a name="mssql_eng020572"></a><span data-ttu-id="7ca69-102">MSSQL_ENG020572</span><span class="sxs-lookup"><span data-stu-id="7ca69-102">MSSQL_ENG020572</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7ca69-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="7ca69-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ca69-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7ca69-104">Product Name</span></span>|<span data-ttu-id="7ca69-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ca69-105">SQL Server</span></span>|  
|<span data-ttu-id="7ca69-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7ca69-106">Event ID</span></span>|<span data-ttu-id="7ca69-107">20572</span><span class="sxs-lookup"><span data-stu-id="7ca69-107">20572</span></span>|  
|<span data-ttu-id="7ca69-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7ca69-108">Event Source</span></span>|<span data-ttu-id="7ca69-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7ca69-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7ca69-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7ca69-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7ca69-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7ca69-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7ca69-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7ca69-112">Message Text</span></span>|<span data-ttu-id="7ca69-113">パブリケーション '%s' のアーティクル '%s' に対するサブスクライバー '%s' のサブスクリプションが、検証エラーの発生後、再初期化されました。</span><span class="sxs-lookup"><span data-stu-id="7ca69-113">Subscriber '%s' subscription to article '%s' in publication '%s' has been reinitialized after a validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ca69-114">説明</span><span class="sxs-lookup"><span data-stu-id="7ca69-114">Explanation</span></span>  
 <span data-ttu-id="7ca69-115">サブスクライバーのデータがパブリッシャーのデータに対して検証され、データが一致しなかったため検証に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="7ca69-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="7ca69-116">検証を実行するように指定したときに、検証が失敗した場合にサブスクリプションを再初期化するオプションを選択しました。</span><span class="sxs-lookup"><span data-stu-id="7ca69-116">When you specified that validation should be performed, you selected the option that a subscription should be reinitialized if validation failed.</span></span> <span data-ttu-id="7ca69-117">サブスクリプションを再初期化するには、サブスクライバーで新しいスナップショットを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ca69-117">Reinitializing a subscription involves applying a new snapshot at the Subscriber.</span></span> <span data-ttu-id="7ca69-118">検証の詳細については、「 [Validate Replicated Data](validate-data-at-the-subscriber.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ca69-118">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ca69-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7ca69-119">User Action</span></span>  
 <span data-ttu-id="7ca69-120">サブスクライバーで新しいスナップショットを適用すると、パブリッシャーのデータとサブスクライバーのデータが一致します。</span><span class="sxs-lookup"><span data-stu-id="7ca69-120">Data at the Publisher and Subscriber will match after the new snapshot is applied at the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca69-121">参照</span><span class="sxs-lookup"><span data-stu-id="7ca69-121">See Also</span></span>  
 [<span data-ttu-id="7ca69-122">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="7ca69-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
