---
title: データマイニングプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712610"
---
# <a name="data-mining-programming"></a><span data-ttu-id="72fd5-102">データ マイニングのプログラミング</span><span class="sxs-lookup"><span data-stu-id="72fd5-102">Data Mining Programming</span></span>
  <span data-ttu-id="72fd5-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の組み込みのツールやビューアーが要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="72fd5-103">If you find that the built-in tools and viewers in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="72fd5-104">この方法では、次の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="72fd5-104">In this approach, you have two options:</span></span>  
  
-   <span data-ttu-id="72fd5-105">**XMLA**</span><span class="sxs-lookup"><span data-stu-id="72fd5-105">**XMLA**</span></span>  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="72fd5-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]は、クライアントアプリケーションと通信するためのプロトコルとして XML for Analysis (XMLA) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="72fd5-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] supports XML for Analysis (XMLA) as a protocol for communication with client applications.</span></span> <span data-ttu-id="72fd5-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、XML for Analysis 仕様を拡張する追加のコマンドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="72fd5-107">Additional commands are supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that extend the XML for Analysis specification.</span></span>  
  
     <span data-ttu-id="72fd5-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではデータ定義、データ操作、およびデータ制御サポートに XMLA を使用するため、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] に用意されているビジュアル ツールを使用してマイニング構造とマイニング モデルを作成し、データ マイニング拡張機能 (DMX) と Analysis Services スクリプト言語 (ASSL) のスクリプトを使用して作成したデータ マイニング オブジェクトを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="72fd5-108">Because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses XMLA for data definition, data manipulation, and data control support, you can create mining structures and mining models by using the visual tools provided by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then extend the data mining objects that you have created by using Data Mining Extensions (DMX) and Analysis Services Scripting Language (ASSL) scripts.</span></span>  
  
     <span data-ttu-id="72fd5-109">データ マイニング オブジェクトを XMLA スクリプトだけで作成および変更できます。また、プログラムを使用して、独自のアプリケーションからモデルに対して予測クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="72fd5-109">You can create and modify data mining objects entirely in XMLA scripts, and run prediction queries against the models programmatically from your own applications.</span></span>  
  
-   <span data-ttu-id="72fd5-110">**分析管理オブジェクト (AMO)**</span><span class="sxs-lookup"><span data-stu-id="72fd5-110">**Analysis Management Objects (AMO)**</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="72fd5-111">には、サード パーティのデータ マイニング プロバイダーがデータ マイニング オブジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に統合できるようにする完全なフレームワークも用意されています。</span><span class="sxs-lookup"><span data-stu-id="72fd5-111">also provides a complete framework that enables third-party data mining providers to integrate the data mining objects into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="72fd5-112">AMO を使用して、マイニング構造とマイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="72fd5-112">You can create mining structures and mining models by using AMO.</span></span> <span data-ttu-id="72fd5-113">CodePlex の次のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72fd5-113">See the following samples in CodePlex:</span></span>  
  
    -   <span data-ttu-id="72fd5-114">[AMO ブラウザー]</span><span class="sxs-lookup"><span data-stu-id="72fd5-114">AMO Browser</span></span>  
  
         <span data-ttu-id="72fd5-115">指定した SSAS インスタンスに接続し、マイニング構造とマイニング モデルを含め、すべてのサーバー オブジェクトとそれらのプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-115">Connects to the SSAS instance you specify and lists all server objects and their properties, including mining structure and mining models.</span></span>  
  
    -   <span data-ttu-id="72fd5-116">AMO の簡単な例</span><span class="sxs-lookup"><span data-stu-id="72fd5-116">AMO Simple Sample</span></span>  
  
         <span data-ttu-id="72fd5-117">AS Simple サンプルは、ほとんどの主要なオブジェクトに対するプログラムによるアクセスを取り扱い、メタデータの参照方法やオブジェクト内の値へのアクセス方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-117">The AS Simple Sample covers programmatic access to most major objects, and demonstrates metadata browsing, and access to the values in objects.</span></span>  
  
         <span data-ttu-id="72fd5-118">このサンプルでは、データ マイニング構造とモデルを作成して操作する方法や、既存のデータ マイニング モデルを参照する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-118">The sample also demonstrates how to create and process a data mining structure and model, as well as browse an existing data mining model.</span></span>  
  
-   <span data-ttu-id="72fd5-119">**DMX**</span><span class="sxs-lookup"><span data-stu-id="72fd5-119">**DMX**</span></span>  
  
     <span data-ttu-id="72fd5-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーへの接続を作成したことを前提とすると、DMX を使用して、コマンド ステートメント、予測クエリ、およびメタデータ クエリをカプセル化し、表形式で結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="72fd5-120">You can use DMX to encapsulate command statements, prediction queries, and metadata queries and return results in a tabular format, assuming you have created a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72fd5-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72fd5-121">In This Section</span></span>  
 [<span data-ttu-id="72fd5-122">OLE DB for Data Mining</span><span class="sxs-lookup"><span data-stu-id="72fd5-122">OLE DB for Data Mining</span></span>](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 <span data-ttu-id="72fd5-123">データ マイニングと多次元データをサポートするための仕様への追加項目として、新しいスキーマ行セットと列、およびマイニング構造の作成と管理のためのデータ マイニング拡張機能 (DMX) 言語について説明します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-123">Describes additions to the specification to support data mining and multidimensional data: new schema rowsets and columns, Data Mining Extensions (DMX) language for creating and managing mining structures.</span></span>  
  
## <a name="related-reference"></a><span data-ttu-id="72fd5-124">関連リファレンス</span><span class="sxs-lookup"><span data-stu-id="72fd5-124">Related Reference</span></span>  
 [<span data-ttu-id="72fd5-125">ADOMD.NET での開発</span><span class="sxs-lookup"><span data-stu-id="72fd5-125">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 <span data-ttu-id="72fd5-126">ADOMD.NET のクライアントおよびサーバープログラミングオブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-126">Introduces ADOMD.NET client and server programming objects.</span></span>  
  
 [<span data-ttu-id="72fd5-127">分析管理オブジェクト &#40;AMO&#41; による開発</span><span class="sxs-lookup"><span data-stu-id="72fd5-127">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 <span data-ttu-id="72fd5-128">AMO プログラミング ライブラリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-128">Introduces the AMO programming library.</span></span>  
  
 [<span data-ttu-id="72fd5-129">Analysis Services スクリプト言語 (ASSL) での開発</span><span class="sxs-lookup"><span data-stu-id="72fd5-129">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 <span data-ttu-id="72fd5-130">XML for Analysis (XMLA) とその拡張機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="72fd5-130">Introduces XML for Analysis (XMLA) and its extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fd5-131">参照</span><span class="sxs-lookup"><span data-stu-id="72fd5-131">See Also</span></span>  
 <span data-ttu-id="72fd5-132">[開発者ガイド &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="72fd5-132">[Developer's Guide &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span></span>  
 [<span data-ttu-id="72fd5-133">データ マイニング拡張機能 &#40;DMX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="72fd5-133">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
