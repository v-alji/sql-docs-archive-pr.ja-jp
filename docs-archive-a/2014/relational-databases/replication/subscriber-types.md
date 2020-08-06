---
title: サブスクライバーの種類 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d356377dec1f5307fa136c94ea682c0824479a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644998"
---
# <a name="subscriber-types"></a><span data-ttu-id="ffa68-102">サブスクライバーの種類</span><span class="sxs-lookup"><span data-stu-id="ffa68-102">Subscriber Types</span></span>
  <span data-ttu-id="ffa68-103">マージ レプリケーションを使用すると、パブリケーションがサポートする必要があるサブスクライバーの種類を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ffa68-103">Merge replication allows you to specify the types of Subscribers that a publication must support.</span></span> <span data-ttu-id="ffa68-104">サブスクライバーの種類を選択することで、パブリケーションが使用できる機能を決定する *パブリケーションの互換性レベル*が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ffa68-104">Selecting Subscriber types sets the *publication compatibility level*, which determines which features can be used by a publication.</span></span>  
  
 <span data-ttu-id="ffa68-105">パブリケーション スナップショットが作成された後は、パブリケーションの互換性レベルは、 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[全般]** ページ上で高く (より制限) することができますが、互換性レベルを低くすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ffa68-105">After a publication snapshot is created, the publication compatibility level can be increased (made more restrictive) on the **General** page of the **Publication Properties** dialog box; the compatibility level cannot be decreased.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ffa68-106">オプション</span><span class="sxs-lookup"><span data-stu-id="ffa68-106">Options</span></span>  
 <span data-ttu-id="ffa68-107">このパブリケーションでサポートする必要がある各サブスクライバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa68-107">Select each Subscriber type that this publication must support.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 <span data-ttu-id="ffa68-108">パブリケーションはすべての機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ffa68-108">The publication can use all features.</span></span>  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 <span data-ttu-id="ffa68-109">パブリケーションは、スナップショット ファイルが文字形式 (これは、スナップショット エージェントによって自動的に処理されます) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffa68-109">The publication requires snapshot files to be in character format (this is handled automatically by the Snapshot Agent).</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="ffa68-110">には、互換性レベルとは別の制限事項もあります。</span><span class="sxs-lookup"><span data-stu-id="ffa68-110">also has a number of restrictions not related to compatibility level.</span></span>  
  
 <span data-ttu-id="ffa68-111">このオプションが選択されている場合、Web 同期オプションはこのパブリケーションで有効です。</span><span class="sxs-lookup"><span data-stu-id="ffa68-111">If this option is selected, the Web synchronization option is enabled for the publication.</span></span> <span data-ttu-id="ffa68-112">Web 同期の詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffa68-112">For more information about Web synchronization, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa68-113">参照</span><span class="sxs-lookup"><span data-stu-id="ffa68-113">See Also</span></span>  
 <span data-ttu-id="ffa68-114">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="ffa68-114">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="ffa68-115">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="ffa68-115">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="ffa68-116">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="ffa68-116">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
