---
title: Analysis Services OLE DB Provider (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services OLE DB Provider
ms.assetid: cdeecd50-1d91-4162-a4a2-01c7799b02a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c0348a23a6def4c3cdbd083354083947ce1390b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645908"
---
# <a name="analysis-services-ole-db-provider-analysis-services---multidimensional-data"></a><span data-ttu-id="4d6b7-102">Analysis Services OLE DB Provider (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-102">Analysis Services OLE DB Provider (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4d6b7-103">Analysis Services OLE DB Provider は、と対話するアプリケーションのインターフェイスです [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-103">The Analysis Services OLE DB Provider is an interface for applications interacting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4d6b7-104">これを使用して、多次元データを扱うクライアント アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-104">It is used to build client applications that interact with multidimensional data.</span></span> <span data-ttu-id="4d6b7-105">このプロバイダーは、多次元データとリレーショナル データのオンラインやオフラインでのデータ マイニング分析用のメソッドを提供しており、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に含まれています。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-105">This provider also provides methods for online and offline data mining analysis of multidimensional data and relational data, and is included as part of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4d6b7-106">サードパーティのクライアント アプリケーションにより、再配布できます。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-106">It can be redistributed by third-party client applications.</span></span>  
  
 <span data-ttu-id="4d6b7-107">キューブやデータ マイニング モデルへの接続、キューブやデータ マイニング モデルへのクエリ、スキーマ情報の取得などのタスクを実行するために [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] と相互作用する場合、基本的には Analysis Services OLE DB Provider が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-107">The Analysis Services OLE DB Provider is the primary method for interacting with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in order to accomplish such tasks as connecting to a cube or data mining model, querying a cube or data mining model, and retrieving schema information.</span></span>  
  
 <span data-ttu-id="4d6b7-108">Analysis Services OLE DB Provider はスタンドアロンのプロバイダーとして機能し、クライアント アプリケーションがリレーショナル ソースや多次元ソースからローカルのキューブ ファイルやマイニング モデルを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-108">As a stand-alone provider, the Analysis Services OLE DB Provider provides client applications with the ability to create local cube files and mining models from relational and multidimensional sources.</span></span> <span data-ttu-id="4d6b7-109">クライアント アプリケーションは、ローカル キューブに接続して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを実行するフルスケールのサーバーと対話することなく、MDX (多次元式) を使用したクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4d6b7-109">Client applications can connect to a local cube and execute queries using Multidimensional Expressions (MDX) without interacting with the full-scale server running the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6b7-110">参照</span><span class="sxs-lookup"><span data-stu-id="4d6b7-110">See Also</span></span>  
 [<span data-ttu-id="4d6b7-111">多次元モデルのデータアクセス &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="4d6b7-111">Multidimensional Model Data Access &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
