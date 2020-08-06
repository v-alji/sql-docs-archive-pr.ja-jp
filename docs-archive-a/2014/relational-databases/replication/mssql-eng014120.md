---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7f3484d9344a203ca8c44fee6b79605163ea069
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630930"
---
# <a name="mssql_eng014120"></a><span data-ttu-id="a2d98-102">MSSQL_ENG014120</span><span class="sxs-lookup"><span data-stu-id="a2d98-102">MSSQL_ENG014120</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a2d98-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="a2d98-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2d98-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a2d98-104">Product Name</span></span>|<span data-ttu-id="a2d98-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a2d98-105">SQL Server</span></span>|  
|<span data-ttu-id="a2d98-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a2d98-106">Event ID</span></span>|<span data-ttu-id="a2d98-107">14120</span><span class="sxs-lookup"><span data-stu-id="a2d98-107">14120</span></span>|  
|<span data-ttu-id="a2d98-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a2d98-108">Event Source</span></span>|<span data-ttu-id="a2d98-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a2d98-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a2d98-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a2d98-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a2d98-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a2d98-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a2d98-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a2d98-112">Message Text</span></span>|<span data-ttu-id="a2d98-113">ディストリビューション データベース '%s' を削除できませんでした。</span><span class="sxs-lookup"><span data-stu-id="a2d98-113">Could not drop the distribution database '%s'.</span></span> <span data-ttu-id="a2d98-114">このディストリビューション データベースはパブリッシャーに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a2d98-114">This distributor database is associated with a Publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a2d98-115">説明</span><span class="sxs-lookup"><span data-stu-id="a2d98-115">Explanation</span></span>  
 <span data-ttu-id="a2d98-116">ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。</span><span class="sxs-lookup"><span data-stu-id="a2d98-116">The distribution database stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="a2d98-117">このエラーは、1 つ以上のパブリッシャーに関連付けられているディストリビューション データベースを削除しようとした場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a2d98-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a2d98-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a2d98-118">User Action</span></span>  
 <span data-ttu-id="a2d98-119">ディストリビューション データベースを削除するには、まずディストリビューターとパブリッシャーの関連付けを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2d98-119">To drop a distribution database you must first drop the association between the Distributor and the Publisher.</span></span> <span data-ttu-id="a2d98-120">詳細については、「[sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2d98-120">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d98-121">参照</span><span class="sxs-lookup"><span data-stu-id="a2d98-121">See Also</span></span>  
 <span data-ttu-id="a2d98-122">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="a2d98-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="a2d98-123">[[ディストリビューションの構成]](configure-distribution.md)</span><span class="sxs-lookup"><span data-stu-id="a2d98-123">[Configure Distribution](configure-distribution.md)</span></span>  
  
  
