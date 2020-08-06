---
title: XMLA の概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
ms.openlocfilehash: b2e18917b56d40f8b813ba10083cc1b408e51a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642984"
---
# <a name="xmla-concepts"></a><span data-ttu-id="70495-102">XMLA の概念</span><span class="sxs-lookup"><span data-stu-id="70495-102">XMLA Concepts</span></span>
  <span data-ttu-id="70495-103">XML for Analysis (XMLA) オープン スタンダードでは、World Wide Web 上に存在するデータ ソースへのアクセスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="70495-103">The XML for Analysis (XMLA) open standard supports data access to data sources that reside on the World Wide Web.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="70495-104">xmla [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 1.1 仕様に従って xmla を実装します。</span><span class="sxs-lookup"><span data-stu-id="70495-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implements XMLA per the XMLA 1.1 specification.</span></span>  
  
 <span data-ttu-id="70495-105">XML for Analysis (XMLA) は Simple Object Access Protocol (SOAP) ベースの XML プロトコルで、Web 上に存在するあらゆる標準的な多次元データ ソースへの汎用データ アクセスを提供することを目的に特別に設計されています。</span><span class="sxs-lookup"><span data-stu-id="70495-105">XML for Analysis (XMLA) is a Simple Object Access Protocol (SOAP)-based XML protocol, designed specifically for universal data access to any standard multidimensional data source residing on the Web.</span></span> <span data-ttu-id="70495-106">XMLA では、コンポーネントオブジェクトモデル (COM) または .NET Framework インターフェイスを公開するクライアントコンポーネントを配置する必要もなくなり [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="70495-106">XMLA also eliminates the need to deploy a client component that exposes Component Object Model (COM) or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework interfaces.</span></span> <span data-ttu-id="70495-107">インターネット環境では、サーバーとのやり取りに多くの時間とリソースが費やされ、データへの状態を保持する接続によってサーバーへのユーザー接続が制限されることがありますが、XMLA はそのようなインターネット環境のために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="70495-107">XMLA is optimized for the Internet, when round trips to the server are expensive in terms of time and resources, and when stateful connections to a data source can limit user connections on the server.</span></span>  
  
 <span data-ttu-id="70495-108">XMLA は、のネイティブプロトコルで、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] クライアントアプリケーションとのインスタンスの間のすべてのやり取りに使用され [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="70495-108">XMLA is the native protocol for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], used for all interaction between a client application and an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="70495-109">は XML for Analysis 1.1 を完全にサポートし、さらには、メタデータ管理、セッション管理、およびロック機能をサポートする拡張機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="70495-109">fully supports XML for Analysis 1.1, and also provides extensions to support metadata management, session management, and locking capabilities.</span></span> <span data-ttu-id="70495-110">分析管理オブジェクト (AMO) と ADOMD.NET はいずれも、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとの通信に XMLA プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="70495-110">Both Analysis Management Objects (AMO) and ADOMD.NET use the XMLA protocol when communicating with an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="handling-xmla-communications"></a><span data-ttu-id="70495-111">XMLA 通信の処理</span><span class="sxs-lookup"><span data-stu-id="70495-111">Handling XMLA Communications</span></span>  
 <span data-ttu-id="70495-112">XMLA オープン スタンダードでは、2 つの汎用メソッド `Discover` および `Execute` を記述しています。</span><span class="sxs-lookup"><span data-stu-id="70495-112">The XMLA open standard describes two generally accessible methods: `Discover` and `Execute`.</span></span> <span data-ttu-id="70495-113">これらのメソッドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上で送受信される情報を処理するために、XML がサポートする疎結合のクライアント/サーバー アーキテクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="70495-113">These methods use the loosely-coupled client and server architecture supported by XML to handle incoming and outgoing information on an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="70495-114">`Discover` メソッドは Web サービスから情報とメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="70495-114">The `Discover` method obtains information and metadata from a Web service.</span></span> <span data-ttu-id="70495-115">この情報には、使用可能なデータ ソースの一覧、任意のデータ ソース プロバイダーに関する情報などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="70495-115">This information can include a list of available data sources, as well as information about any of the data source providers.</span></span> <span data-ttu-id="70495-116">データ ソースから取得されるデータは、プロパティによって定義および成形されます。</span><span class="sxs-lookup"><span data-stu-id="70495-116">Properties define and shape the data that is obtained from a data source.</span></span> <span data-ttu-id="70495-117">`Discover` メソッドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上のデータ ソースに対してクライアント アプリケーションが要求するさまざまな種類の情報を定義するための共通メソッドです。</span><span class="sxs-lookup"><span data-stu-id="70495-117">The `Discover` method is a common method for defining the many types of information a client application may require from data sources on [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instances.</span></span> <span data-ttu-id="70495-118">プロパティと汎用インターフェイスを使用すれば、クライアント アプリケーション内の既存の機能を書き直さなくても拡張機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="70495-118">The properties and the generic interface provide extensibility without requiring you to rewrite existing functions in a client application.</span></span>  
  
 <span data-ttu-id="70495-119">`Execute` メソッドを使用すると、アプリケーションはプロバイダー固有のコマンドを XMLA データ ソースに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="70495-119">The `Execute` method allows applications to run provider-specific commands against XMLA data sources.</span></span>  
  
 <span data-ttu-id="70495-120">XMLA プロトコルは Web アプリケーション用に最適化されていますが、LAN 指向のアプリケーションでもこれを利用できます。</span><span class="sxs-lookup"><span data-stu-id="70495-120">Although the XMLA protocol is optimized for Web applications, it can also be leveraged for LAN-oriented applications.</span></span> <span data-ttu-id="70495-121">次のようなアプリケーションは、この XML ベースの API の利点を活用できます。</span><span class="sxs-lookup"><span data-stu-id="70495-121">The following applications can benefit from this XML-based API:</span></span>  
  
-   <span data-ttu-id="70495-122">クライアント/サーバー間の柔軟な通信テクノロジを必要とするクライアント/サーバー アプリケーション</span><span class="sxs-lookup"><span data-stu-id="70495-122">Client/server applications that require flexible technology between clients and the server</span></span>  
  
-   <span data-ttu-id="70495-123">複数のオペレーティング システムを扱うことを想定したクライアント/サーバー アプリケーション</span><span class="sxs-lookup"><span data-stu-id="70495-123">Client/server applications that target multiple operating systems</span></span>  
  
-   <span data-ttu-id="70495-124">サーバー容量を増やすために大きなステートを要求しないクライアント</span><span class="sxs-lookup"><span data-stu-id="70495-124">Clients that do not require significant state in order to increase server capacity</span></span>  
  
## <a name="xmla-and-the-unified-dimensional-model"></a><span data-ttu-id="70495-125">XMLA と統合ディメンショナル モデル</span><span class="sxs-lookup"><span data-stu-id="70495-125">XMLA and the Unified Dimensional Model</span></span>  
 <span data-ttu-id="70495-126">XMLA は、統合ディメンショナル モデル (UDM) の手法を採用しているビジネス インテリジェンス アプリケーションによって使用されるプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="70495-126">XMLA is the protocol used by business intelligence applications that employ the Unified Dimensional Model (UDM) methodology</span></span>  
  
  
