---
title: 物理アーキテクチャ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- server architecture [Analysis Services]
- architecture [Analysis Services]
ms.assetid: 25eeecf0-6e85-4527-b94d-5503d27edaed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 787ca28c08dc41a6b9561251077716a406358c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718986"
---
# <a name="physical-architecture-analysis-services---data-mining"></a><span data-ttu-id="bf986-102">物理アーキテクチャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="bf986-102">Physical Architecture (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="bf986-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、サーバーとクライアントの両方のコンポーネントを使用して、ビジネスインテリジェンスアプリケーションにデータマイニング機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="bf986-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses both server and client components to supply data mining functionality for business intelligence applications:</span></span>

-   <span data-ttu-id="bf986-104">サーバー コンポーネントは、Microsoft Windows サービスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="bf986-104">The server component is implemented as a Microsoft Windows service.</span></span> <span data-ttu-id="bf986-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは Windows サービスの別個のインスタンスとして実装されるため、同一のコンピューター上で複数のインスタンスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bf986-105">You can have multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>

-   <span data-ttu-id="bf986-106">クライアントは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf986-106">Clients communicate with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="bf986-107">クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージド プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bf986-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>

-   <span data-ttu-id="bf986-108">クエリ コマンドは、データ マイニング指向の業界標準クエリ言語であるデータ マイニング拡張機能 (DMX) を使用して発行できます。</span><span class="sxs-lookup"><span data-stu-id="bf986-108">Query commands can be issued using Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="bf986-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bf986-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database objects.</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="bf986-110">アーキテクチャの図</span><span class="sxs-lookup"><span data-stu-id="bf986-110">Architectural Diagram</span></span>
 <span data-ttu-id="bf986-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスはスタンドアロン サービスとして実行され、サービスとの通信は、HTTP または TCP を使用して XML for Analysis (XMLA) 経由で行われます。</span><span class="sxs-lookup"><span data-stu-id="bf986-111">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span>

 <span data-ttu-id="bf986-112">AMO は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理オブジェクトへのアクセスを提供する、ユーザー アプリケーションと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの間のレイヤーです。</span><span class="sxs-lookup"><span data-stu-id="bf986-112">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that provides access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="bf986-113">AMO は、クライアント アプリケーションからコマンドを受け取り、それを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス用の XMLA メッセージに変換するクラス ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="bf986-113">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="bf986-114">AMO は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス オブジェクトをクラスとして、エンド ユーザー アプリケーションに提示します。このクラスには、コマンドを実行するメソッド メンバーと、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのデータを持つプロパティ メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf986-114">AMO presents [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="bf986-115">次の図は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントのアーキテクチャを示しており、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス内のサービスと、インスタンスと連携するユーザー コンポーネントを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="bf986-115">The following illustration shows the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components architecture, including services within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and user components that interact with the instance.</span></span>

 <span data-ttu-id="bf986-116">この図は、XML for Analysis (XMLA) リスナーと、HTTP または TCP のいずれかを使用する以外に、インスタンスにアクセスする方法がないことも示しています。</span><span class="sxs-lookup"><span data-stu-id="bf986-116">The illustration shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

> [!WARNING]
>  <span data-ttu-id="bf986-117">DSO は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="bf986-117">DSO has been deprecated.</span></span> <span data-ttu-id="bf986-118">ソリューションの開発に DSO を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="bf986-118">You should not use DSO to develop solutions.</span></span>

 <span data-ttu-id="bf986-119">![Analysis Services のシステム アーキテクチャ図](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services のシステム アーキテクチャ図")</span><span class="sxs-lookup"><span data-stu-id="bf986-119">![Analysis Services System Architecture Diagram](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="server-configuration"></a><span data-ttu-id="bf986-120">[サーバーの構成]</span><span class="sxs-lookup"><span data-stu-id="bf986-120">Server Configuration</span></span>
 <span data-ttu-id="bf986-121">1 つのサーバー インスタンスで複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをサポートできます。各データベースに、クライアント要求に応答してオブジェクトを処理する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスの固有のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="bf986-121">One server instance can support multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, each with its own instance of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that responds to client requests and processes objects.</span></span>

 <span data-ttu-id="bf986-122">テーブル モデルとデータ マイニング モデル/多次元モデルの両方を操作する場合は、別個のインスタンスをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf986-122">Separate instances must be installed if you want to work with both tabular models and data mining and/or multidimensional models.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="bf986-123">では、表形式モードで実行される (xVelocity メモリ内分析エンジン (VertiPaq) ストレージ エンジンを使用する) インスタンスと従来の OLAP、MOLAP、ROLAP 構成のいずれかで実行されるインスタンスのサイド バイ サイド インストールがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bf986-123">supports side-by-side installation of instances running in tabular mode (which uses the xVelocity in-memory analytics engine (VertiPaq) storage engine) and instances running in one of the conventional OLAP, MOLAP, or ROLAP configurations.</span></span> <span data-ttu-id="bf986-124">詳細については、「 [Analysis Services インスタンスのサーバー モードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf986-124">For more information, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>

 <span data-ttu-id="bf986-125">クライアントと Analysis Services サーバーの間のすべての通信には、プラットフォームや言語に依存しないプロトコルである XMLA が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf986-125">All communications between a client and the Analysis Services server use XMLA, which is a platform-independent and language-independent protocol.</span></span> <span data-ttu-id="bf986-126">Analysis Services は、クライアントからの要求を受け取ると、その要求が OLAP に関連しているかデータ マイニングに関連しているかを判断して、適切にルーティングします。</span><span class="sxs-lookup"><span data-stu-id="bf986-126">When a request is received from a client, Analysis Services determines whether the request relates to OLAP or data mining, and routes the request appropriately.</span></span> <span data-ttu-id="bf986-127">サーバー コンポーネントの詳細については、「 [OLAP エンジンのサーバー コンポーネント](../multidimensional-models/olap-physical/olap-engine-server-components.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf986-127">For more information, see [OLAP Engine Server Components](../multidimensional-models/olap-physical/olap-engine-server-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf986-128">参照</span><span class="sxs-lookup"><span data-stu-id="bf986-128">See Also</span></span>
 [<span data-ttu-id="bf986-129">論理アーキテクチャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="bf986-129">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)


