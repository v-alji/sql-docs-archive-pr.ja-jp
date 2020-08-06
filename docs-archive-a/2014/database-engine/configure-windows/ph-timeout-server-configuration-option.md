---
title: PH timeout サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713478"
---
# <a name="ph-timeout-server-configuration-option"></a><span data-ttu-id="ee2d0-102">PH timeout サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="ee2d0-102">PH timeout Server Configuration Option</span></span>
  <span data-ttu-id="ee2d0-103">PH timeout オプションは、フルテキスト プロトコル ハンドラーが、データベースへの接続をタイムアウトするまで待機する時間を秒単位で指定します。既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-103">Use the PH timeout option to specify the time, in seconds, that the full-text protocol handler should wait to connect to a database before timing out. The default value is 60 seconds.</span></span> <span data-ttu-id="ee2d0-104">一時的なネットワークの問題により接続試行がタイムアウトする場合は、ph timeout 値を大きくします。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-104">Increase the ph timeout value when connection attempts are timing out due to temporary network issues.</span></span>  
  
 <span data-ttu-id="ee2d0-105">フルテキスト プロトコル ハンドラーは、フィルター デーモン ホストでホストされ、フルテキスト インデックスの作成対象データを SQL Server からフェッチする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-105">The full-text protocol handler is hosted in the filter daemon host and is used to fetch from SQL Server the data to be full-text indexed.</span></span> <span data-ttu-id="ee2d0-106">フルテキスト検索コンポーネントの詳細については、「 [フルテキスト検索](../../relational-databases/search/full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-106">For more information about full-text search components, see [Full-Text Search](../../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="ee2d0-107">データ行をフェッチすると、指定した時間内にプロトコル ハンドラーが SQL Server に接続できない場合、その行に対するタイムアウト エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-107">When attempting to fetch a data row, if the protocol handler cannot connect to SQL Server within the specified time, it reports a time-out error for that row.</span></span> <span data-ttu-id="ee2d0-108">その行のフェッチは、後でフルテキストの Gatherer により再試行されます。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-108">The full-text gatherer will retry the row later.</span></span> <span data-ttu-id="ee2d0-109">フルテキストの Gatherer の詳細については、「 [フルテキスト インデックスの作成](../../relational-databases/indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee2d0-109">For more information about the full-text gatherer, see [Populate Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2d0-110">参照</span><span class="sxs-lookup"><span data-stu-id="ee2d0-110">See Also</span></span>  
 <span data-ttu-id="ee2d0-111">[フルテキスト検索](../../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="ee2d0-111">[Full-Text Search](../../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="ee2d0-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ee2d0-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="ee2d0-113">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee2d0-113">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="ee2d0-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ee2d0-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
