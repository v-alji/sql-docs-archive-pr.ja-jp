---
title: データマイニングアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 105f52e1-ad3b-4cd0-b67b-06dbb451c304
author: minewiskan
ms.author: owend
ms.openlocfilehash: a372972fd7fa39f7bcfd2e10abbc4fbf8f8c10aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644233"
---
# <a name="data-mining-architecture"></a><span data-ttu-id="ae925-102">データ マイニングのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ae925-102">Data Mining Architecture</span></span>
  <span data-ttu-id="ae925-103">ここでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスでホストされているデータ マイニング ソリューションのアーキテクチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ae925-103">This section describes the architecture of data mining solutions that are hosted in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ae925-104">このセクションのトピックでは、データ マイニングをサポートする [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの論理および物理アーキテクチャについて説明します。さらに、データ マイニング サーバーとの通信およびデータ マイニング オブジェクトのローカルまたはリモート操作に使用できるクライアント、プロバイダー、およびプロトコルに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ae925-104">The topics in this section describe the logical and physical architecture of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that supports data mining, and also provide information about the clients, providers, and protocols that can be used to communicate with data mining servers, and to work with data mining objects either locally or remotely.</span></span>  
  
 <span data-ttu-id="ae925-105">一般に、SQL Server データ マイニングは、多次元モードで実行される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの一部として提供されるサービスとして動作します。したがって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多次元ソリューションの操作、メンテナンス、および構成について説明しているオンライン ブックの次のセクションも参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae925-105">In general, SQL Server Data Mining operates as a service that is provided as part of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance running in multidimensional mode; therefore, we recommend that you also review the following sections of Books Online that describe the operation, maintenance, and configuration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional solutions.</span></span>  
  
 [<span data-ttu-id="ae925-106">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="ae925-106">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="ae925-107">Analysis Services への接続</span><span class="sxs-lookup"><span data-stu-id="ae925-107">Connect to Analysis Services</span></span>](../instances/connect-to-analysis-services.md)  
  
 [<span data-ttu-id="ae925-108">データベースの格納場所</span><span class="sxs-lookup"><span data-stu-id="ae925-108">Database Storage Location</span></span>](../multidimensional-models/database-storage-location.md)  
  
 [<span data-ttu-id="ae925-109">Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え</span><span class="sxs-lookup"><span data-stu-id="ae925-109">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
 <span data-ttu-id="ae925-110">ビジネス インテリジェンス ソリューションにデータ マイニングを実装する方法の詳細については、MSDN ライブラリの「ソリューション ガイド」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ae925-110">For more information about how you can implement data mining in your business intelligence solution, see the Solution Guides section of the MSDN Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae925-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ae925-111">In This Section</span></span>  
 [<span data-ttu-id="ae925-112">論理アーキテクチャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="ae925-112">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="ae925-113">物理アーキテクチャ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ae925-113">Physical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](physical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="ae925-114">データ マイニング サービスおよびデータ ソース</span><span class="sxs-lookup"><span data-stu-id="ae925-114">Data Mining Services and Data Sources</span></span>](data-mining-services-and-data-sources.md)  
  
 [<span data-ttu-id="ae925-115">データ マイニング ソリューションおよびオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="ae925-115">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
 [<span data-ttu-id="ae925-116">セキュリティの概要 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ae925-116">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae925-117">参照</span><span class="sxs-lookup"><span data-stu-id="ae925-117">See Also</span></span>  
 <span data-ttu-id="ae925-118">[多次元モデルのプログラミング](../multidimensional-models/multidimensional-model-programming.md) </span><span class="sxs-lookup"><span data-stu-id="ae925-118">[Multidimensional Model Programming](../multidimensional-models/multidimensional-model-programming.md) </span></span>  
 [<span data-ttu-id="ae925-119">データマイニングのプログラミング</span><span class="sxs-lookup"><span data-stu-id="ae925-119">Data Mining Programming</span></span>](../dev-guide/data-mining-programming.md)  
  
  
