---
title: OLAP エンジンサーバーコンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740543"
---
# <a name="olap-engine-server-components"></a><span data-ttu-id="02c44-102">OLAP エンジンのサーバー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="02c44-102">OLAP Engine Server Components</span></span>
  <span data-ttu-id="02c44-103">のサーバーコンポーネント [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、Windows サービスとして実行される**msmdsrv.exe**アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="02c44-103">The server component of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is the **msmdsrv.exe** application, which runs as a Windows service.</span></span> <span data-ttu-id="02c44-104">このアプリケーションは、セキュリティ コンポーネント、XML for Analysis (XMLA) リスナー コンポーネント、クエリ プロセッサ コンポーネント、および次の機能を実行するその他多くの内部コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="02c44-104">This application consists of security components, an XML for Analysis (XMLA) listener component, a query processor component and numerous other internal components that perform the following functions:</span></span>

-   <span data-ttu-id="02c44-105">クライアントから受信したステートメントの解析</span><span class="sxs-lookup"><span data-stu-id="02c44-105">Parsing statements received from clients</span></span>

-   <span data-ttu-id="02c44-106">メタデータの管理</span><span class="sxs-lookup"><span data-stu-id="02c44-106">Managing metadata</span></span>

-   <span data-ttu-id="02c44-107">トランザクションの処理</span><span class="sxs-lookup"><span data-stu-id="02c44-107">Handling transactions</span></span>

-   <span data-ttu-id="02c44-108">計算の処理</span><span class="sxs-lookup"><span data-stu-id="02c44-108">Processing calculations</span></span>

-   <span data-ttu-id="02c44-109">ディメンションおよびセル データの格納</span><span class="sxs-lookup"><span data-stu-id="02c44-109">Storing dimension and cell data</span></span>

-   <span data-ttu-id="02c44-110">集計の作成</span><span class="sxs-lookup"><span data-stu-id="02c44-110">Creating aggregations</span></span>

-   <span data-ttu-id="02c44-111">クエリのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="02c44-111">Scheduling queries</span></span>

-   <span data-ttu-id="02c44-112">オブジェクトのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="02c44-112">Caching objects</span></span>

-   <span data-ttu-id="02c44-113">サーバー リソースの管理</span><span class="sxs-lookup"><span data-stu-id="02c44-113">Managing server resources</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="02c44-114">アーキテクチャの図</span><span class="sxs-lookup"><span data-stu-id="02c44-114">Architectural Diagram</span></span>
 <span data-ttu-id="02c44-115">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスはスタンドアロン サービスとして実行され、サービスとの通信は、HTTP または TCP を使用して XML for Analysis (XMLA) 経由で行われます。</span><span class="sxs-lookup"><span data-stu-id="02c44-115">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span> <span data-ttu-id="02c44-116">AMO は、ユーザー アプリケーションと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの間のレイヤーです。</span><span class="sxs-lookup"><span data-stu-id="02c44-116">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="02c44-117">このレイヤーは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理オブジェクトへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="02c44-117">This layer provides access to [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="02c44-118">AMO は、クライアント アプリケーションからコマンドを受け取り、それを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス用の XMLA メッセージに変換するクラス ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="02c44-118">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="02c44-119">AMO は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス オブジェクトをクラスとして、エンド ユーザー アプリケーションに提示します。このクラスには、コマンドを実行するメソッド メンバーと、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトのデータを持つプロパティ メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="02c44-119">AMO presents [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="02c44-120">次の図は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] コンポーネントのアーキテクチャを示しており、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス内で実行されるすべての主要な要素と、インスタンスと連携するすべてのユーザー コンポーネントを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="02c44-120">The following illustration shows the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] components architecture, including all major elements running within the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance and all user components that interact with the instance.</span></span> <span data-ttu-id="02c44-121">また、この図は、XML for Analysis (XMLA) リスナーと、HTTP または TCP のいずれかを使用する以外に、インスタンスにアクセスする方法がないことも示しています。</span><span class="sxs-lookup"><span data-stu-id="02c44-121">The illustration also shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

 <span data-ttu-id="02c44-122">![Analysis Services のシステム アーキテクチャ図](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services のシステム アーキテクチャ図")</span><span class="sxs-lookup"><span data-stu-id="02c44-122">![Analysis Services System Architecture Diagram](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="xmla-listener"></a><span data-ttu-id="02c44-123">XMLA リスナー</span><span class="sxs-lookup"><span data-stu-id="02c44-123">XMLA Listener</span></span>
 <span data-ttu-id="02c44-124">XMLA リスナー コンポーネントでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] とそのクライアントの間のすべての XMLA 通信が処理されます。</span><span class="sxs-lookup"><span data-stu-id="02c44-124">The XMLA listener component handles all XMLA communications between [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] and its clients.</span></span> <span data-ttu-id="02c44-125">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini ファイルの構成設定を使用して、インスタンスがリッスンするポートを指定でき [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="02c44-125">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` configuration setting in the msmdsrv.ini file can be used to specify a port on which an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance listens.</span></span> <span data-ttu-id="02c44-126">このファイルの 0 の値は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が既定のポートをリッスンすることを示します。</span><span class="sxs-lookup"><span data-stu-id="02c44-126">A value of 0 in this file indicates that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] listen on the default port.</span></span> <span data-ttu-id="02c44-127">特に指定がなければ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では次の既定の TCP ポートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="02c44-127">Unless otherwise specified, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the following default TCP ports:</span></span>

|<span data-ttu-id="02c44-128">Port</span><span class="sxs-lookup"><span data-stu-id="02c44-128">Port</span></span>|<span data-ttu-id="02c44-129">説明</span><span class="sxs-lookup"><span data-stu-id="02c44-129">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="02c44-130">2383</span><span class="sxs-lookup"><span data-stu-id="02c44-130">2383</span></span>|<span data-ttu-id="02c44-131">の既定のインスタンス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02c44-131">Default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="02c44-132">2382</span><span class="sxs-lookup"><span data-stu-id="02c44-132">2382</span></span>|<span data-ttu-id="02c44-133">の他のインスタンスのリダイレクター [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02c44-133">Redirector for other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="02c44-134">サーバーの起動時に動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="02c44-134">Dynamically assigned at server startup</span></span>|<span data-ttu-id="02c44-135">の名前付きインスタンス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02c44-135">Named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|

 <span data-ttu-id="02c44-136">詳細については[、「Analysis Services アクセスを許可するための Windows ファイアウォールの構成」を](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="02c44-136">See [Configure the Windows Firewall to Allow Analysis Services Access](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for more details.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c44-137">参照</span><span class="sxs-lookup"><span data-stu-id="02c44-137">See Also</span></span>
 <span data-ttu-id="02c44-138">[オブジェクトの名前付け規則 &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [物理アーキテクチャ &#40;Analysis Services-多次元データ&#41;](understanding-microsoft-olap-physical-architecture.md) [論理アーキテクチャ &#40;Analysis Services-多次元データ&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="02c44-138">[Object Naming Rules &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;](understanding-microsoft-olap-physical-architecture.md) [Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span></span>


