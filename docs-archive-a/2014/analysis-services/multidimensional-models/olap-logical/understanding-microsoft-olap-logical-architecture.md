---
title: 論理アーキテクチャ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
ms.openlocfilehash: d93361fb14bc6544ffa7376439c2da0c8e06c3fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643562"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a><span data-ttu-id="624fa-102">論理アーキテクチャ (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="624fa-102">Logical Architecture (Analysis Services - Multidimensional Data)</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="624fa-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、サーバーコンポーネントとクライアントコンポーネントの両方を使用して、ビジネスインテリジェンスアプリケーションのオンライン分析処理 (OLAP) およびデータマイニング機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="624fa-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses both server and client components to supply online analytical processing (OLAP) and data mining functionality for business intelligence applications:</span></span>  
  
-   <span data-ttu-id="624fa-104">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のサーバー コンポーネントは、Microsoft Windows サービスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="624fa-104">The server component of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is implemented as a Microsoft Windows service.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="624fa-105">は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 同じコンピューター上の複数のインスタンスをサポートし、の各インスタンス [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は Windows サービスの個別のインスタンスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="624fa-105">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>  
  
-   <span data-ttu-id="624fa-106">クライアントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。</span><span class="sxs-lookup"><span data-stu-id="624fa-106">Clients communicate with [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="624fa-107">クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージド プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="624fa-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>  
  
-   <span data-ttu-id="624fa-108">クエリ コマンドは、SQL、分析用の業界標準クエリ言語である多次元式 (MDX)、またはデータ マイニング指向の業界標準クエリ言語であるデータ マイニング拡張機能 (DMX) を使用して発行できます。</span><span class="sxs-lookup"><span data-stu-id="624fa-108">Query commands can be issued using the following languages: SQL; Multidimensional Expressions (MDX), an industry standard query language for analysis; or Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="624fa-109">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="624fa-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database objects.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="624fa-110">では、接続されていないクライアント上のアプリケーションがローカルに格納された多次元データを参照することを可能にするローカル キューブ エンジンもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="624fa-110">also supports a local cube engine that enables applications on disconnected clients to browse locally stored multidimensional data.</span></span> <span data-ttu-id="624fa-111">詳細については、「 [Analysis Services の開発に関するクライアントアーキテクチャの要件](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="624fa-111">For more information, see [Client Architecture Requirements for Analysis Services Development](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="624fa-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="624fa-112">In This Section</span></span>  
 <span data-ttu-id="624fa-113">**論理アーキテクチャの概要**</span><span class="sxs-lookup"><span data-stu-id="624fa-113">**Logical Architecture Overview**</span></span>  
 [<span data-ttu-id="624fa-114">論理アーキテクチャの概要 &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-114">Logical Architecture Overview &#40;Analysis Services - Multidimensional Data&#41;</span></span>](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="624fa-115">**サーバーオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="624fa-115">**Server Objects**</span></span>  
 [<span data-ttu-id="624fa-116">サーバーオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-116">Server Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](server-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="624fa-117">**データベースオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="624fa-117">**Database Objects**</span></span>  
 [<span data-ttu-id="624fa-118">データベース オブジェクト &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-118">Database Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](database-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="624fa-119">**Dimension オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="624fa-119">**Dimension Objects**</span></span>  
 [<span data-ttu-id="624fa-120">ディメンションオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-120">Dimension Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="624fa-121">**[キューブ オブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="624fa-121">**Cube Objects**</span></span>  
 [<span data-ttu-id="624fa-122">キューブオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-122">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="624fa-123">**ユーザー アクセス セキュリティ**</span><span class="sxs-lookup"><span data-stu-id="624fa-123">**User Access Security**</span></span>  
 [<span data-ttu-id="624fa-124">ユーザー アクセス セキュリティ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="624fa-124">User Access Security Architecture</span></span>](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a><span data-ttu-id="624fa-125">参照</span><span class="sxs-lookup"><span data-stu-id="624fa-125">See Also</span></span>  
 <span data-ttu-id="624fa-126">[Microsoft OLAP アーキテクチャについて](../olap-physical/understanding-microsoft-olap-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="624fa-126">[Understanding Microsoft OLAP Architecture](../olap-physical/understanding-microsoft-olap-architecture.md) </span></span>  
 [<span data-ttu-id="624fa-127">物理アーキテクチャ &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="624fa-127">Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
