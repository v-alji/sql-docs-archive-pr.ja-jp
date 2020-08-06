---
title: トランザクション レプリケーションのアーティクル オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641600"
---
# <a name="article-options-for-transactional-replication"></a><span data-ttu-id="ebcee-102">トランザクション レプリケーションのアーティクル オプション</span><span class="sxs-lookup"><span data-stu-id="ebcee-102">Article Options for Transactional Replication</span></span>
  <span data-ttu-id="ebcee-103">トランザクション パブリケーションには、アーティクルのためのオプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="ebcee-103">There are a number of options for articles in transactional publications.</span></span> <span data-ttu-id="ebcee-104">たとえば、トランザクション レプリケーションでは次のようなことが可能です。</span><span class="sxs-lookup"><span data-stu-id="ebcee-104">With transactional replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="ebcee-105">パブリッシャーからサブスクライバーに変更を反映する方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-105">Specify how changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="ebcee-106">詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebcee-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
-   <span data-ttu-id="ebcee-107">ストアド プロシージャの実行をレプリケートするように指定できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-107">Specify that the execution of a stored procedure be replicated.</span></span> <span data-ttu-id="ebcee-108">これは、大量のデータに影響を与えるメンテナンス用ストアド プロシージャの結果をレプリケートする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="ebcee-108">This is useful in replicating the results of maintenance-oriented stored procedures that affect large amounts of data.</span></span> <span data-ttu-id="ebcee-109">詳細については、「[トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行](publishing-stored-procedure-execution-in-transactional-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ebcee-109">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="ebcee-110">制約やトリガーをサブスクライバーにコピーするかどうかなど、スキーマ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebcee-110">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="ebcee-111">詳細については、「[スキーマ オプションの指定](../publish/specify-schema-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebcee-111">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="ebcee-112">行フィルターや列フィルターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-112">Use row filters and column filters.</span></span> <span data-ttu-id="ebcee-113">テーブル アーティクルをフィルター選択すると、パブリッシュされるデータのパーティションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ebcee-113">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="ebcee-114">詳細については、「[パブリッシュされたデータのフィルター選択](../publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebcee-114">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcee-115">参照</span><span class="sxs-lookup"><span data-stu-id="ebcee-115">See Also</span></span>  
 [<span data-ttu-id="ebcee-116">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="ebcee-116">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
