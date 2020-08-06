---
title: サブスクリプションの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f024d360fdeab477ace09970b4f140a97696c2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632338"
---
# <a name="initialize-a-subscription"></a><span data-ttu-id="e07f9-102">サブスクリプションの初期化</span><span class="sxs-lookup"><span data-stu-id="e07f9-102">Initialize a Subscription</span></span>
  <span data-ttu-id="e07f9-103">レプリケーション トポロジ内の各サブスクライバーでは、初期化を行って、サブスクライブしているパブリケーション内の各アーティクルのスキーマ、およびストアド プロシージャ、トリガー、メタデータ テーブルなどの必要なレプリケーション オブジェクトをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e07f9-103">Subscribers in a replication topology must be initialized, so that they have a copy of the schema from each article in the publication they have subscribed to and any replication objects that are required, such as stored procedures, triggers, and metadata tables.</span></span> <span data-ttu-id="e07f9-104">また、サブスクライバーは一般に初期データセットを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e07f9-104">In addition, the Subscriber typically receives an initial dataset.</span></span> <span data-ttu-id="e07f9-105">既定の初期化方法では、スキーマ、レプリケーション オブジェクト、データが含まれる完全なスナップショットを使用しますが、完全なスナップショットがなくてもパブリケーションを初期化することが可能です。</span><span class="sxs-lookup"><span data-stu-id="e07f9-105">The default initialization method uses a full snapshot that includes schema, replication objects, and data, but publications can also be initialized without a full snapshot.</span></span>  
  
 <span data-ttu-id="e07f9-106">詳細については、「 [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) 」および「 [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e07f9-106">For more information, see [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) and [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
  
