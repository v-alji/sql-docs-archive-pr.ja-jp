---
title: プラグインアルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
ms.openlocfilehash: ebc5e007dcc6de7fb25d59547e21f1e892100570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718974"
---
# <a name="plugin-algorithms"></a><span data-ttu-id="9b45b-102">プラグイン アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="9b45b-102">Plugin Algorithms</span></span>
  <span data-ttu-id="9b45b-103">に用意されているアルゴリズムに加えて [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、データマイニングに使用できるアルゴリズムは他にも多数あります。</span><span class="sxs-lookup"><span data-stu-id="9b45b-103">In addition to the algorithms that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, there are many other algorithms that you can use for data mining.</span></span> <span data-ttu-id="9b45b-104">したがって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、サード パーティ製アルゴリズムを "プラグイン" するためのメカニズムが提供されています。</span><span class="sxs-lookup"><span data-stu-id="9b45b-104">Accordingly, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a mechanism for "plugging in" algorithms that are created by third parties.</span></span> <span data-ttu-id="9b45b-105">サード パーティのアルゴリズムが特定の規格に従っている限り、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] アルゴリズムを使用する場合と同様に、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 内でそれらのアルゴリズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b45b-105">As long as the algorithms follow certain standards, you can use them within [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] just as you use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms.</span></span> <span data-ttu-id="9b45b-106">プラグインアルゴリズムには、に用意されているアルゴリズムのすべての機能が備わってい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9b45b-106">Plugin algorithms have all the capabilities of algorithms that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span>  
  
 <span data-ttu-id="9b45b-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がプラグイン アルゴリズムとの通信に使用するインターフェイスの詳細については、 [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web サイトで公開されている、カスタム アルゴリズムとカスタム モデル ビューアーを作成するためのサンプルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b45b-107">For a full description of the interfaces that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to communicate with plugin algorithms, see the samples for creating a custom algorithm and custom model viewer that are published on [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) Web site.</span></span>  
  
## <a name="algorithm-requirements"></a><span data-ttu-id="9b45b-108">アルゴリズムの必要条件</span><span class="sxs-lookup"><span data-stu-id="9b45b-108">Algorithm Requirements</span></span>  
 <span data-ttu-id="9b45b-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にアルゴリズムをプラグインするには、次の COM インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b45b-109">To plug an algorithm into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must implement the following COM interfaces:</span></span>  
  
 `IDMAlgorithm`  
 <span data-ttu-id="9b45b-110">モデルを生成するアルゴリズムを実装し、結果のモデルの予測操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="9b45b-110">Implements an algorithm that produces models, and implements the prediction operations of the resulting models.</span></span>  
  
 `IDMAlgorithmNavigation`  
 <span data-ttu-id="9b45b-111">ブラウザーがモデルのコンテンツにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b45b-111">Enables browsers to access the content of the models.</span></span>  
  
 `IDMPersist`  
 <span data-ttu-id="9b45b-112">アルゴリズムによってトレーニングされるモデルを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で保存して読み込むことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b45b-112">Enables the models that the algorithm trains to be saved and loaded by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 `IDMAlgorithmMetadata`  
 <span data-ttu-id="9b45b-113">アルゴリズムの機能および入力パラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="9b45b-113">Describes the capabilities and input parameters of the algorithm.</span></span>  
  
 `IDMAlgorithmFactory`  
 <span data-ttu-id="9b45b-114">アルゴリズム インターフェイスを実装するオブジェクトのインスタンスを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] にアルゴリズム メタデータ インターフェイスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b45b-114">Creates instances of the objects that implement the algorithm interface, and provides [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] with access to the algorithm-metadata interface.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="9b45b-115">では、これらの COM インターフェイスを使用してプラグイン アルゴリズムと通信します。</span><span class="sxs-lookup"><span data-stu-id="9b45b-115">uses these COM interfaces to communicate with plugin algorithms.</span></span> <span data-ttu-id="9b45b-116">使用するプラグイン アルゴリズムでは [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining 仕様をサポートしている必要はありますが、仕様内のデータ マイニング オプションをすべてサポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9b45b-116">Although plugin algorithms that you use must support the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB for Data Mining specification, they do not have to support all the data mining options in the specification.</span></span> <span data-ttu-id="9b45b-117">アルゴリズムの機能を決定するには、 [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) スキーマ行セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b45b-117">You can use the [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) schema rowset to determine the capabilities of an algorithm.</span></span> <span data-ttu-id="9b45b-118">このスキーマ行セットでは、プラグイン アルゴリズム プロバイダーごとにデータ マイニング サポート オプションが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b45b-118">This schema rowset lists the data mining support options for each plugin algorithm provider.</span></span>  
  
 <span data-ttu-id="9b45b-119">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で新しいアルゴリズムを使用する前に、そのアルゴリズムを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b45b-119">You must register new algorithms before you use them with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9b45b-120">アルゴリズムを登録するには、アルゴリズムを含める [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの .ini ファイルに次の情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b45b-120">To register an algorithm, include the following information in the .ini file of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on which you want to include the algorithms:</span></span>  
  
-   <span data-ttu-id="9b45b-121">アルゴリズム名</span><span class="sxs-lookup"><span data-stu-id="9b45b-121">The algorithm name</span></span>  
  
-   <span data-ttu-id="9b45b-122">ProgID (プラグイン アルゴリズムにのみ含まれるオプションです)</span><span class="sxs-lookup"><span data-stu-id="9b45b-122">ProgID (this is optional and will only be included for plugin algorithms)</span></span>  
  
-   <span data-ttu-id="9b45b-123">アルゴリズムが有効か無効かを示すフラグ</span><span class="sxs-lookup"><span data-stu-id="9b45b-123">A flag that indicates whether the algorithm is enabled or not</span></span>  
  
 <span data-ttu-id="9b45b-124">次のコード サンプルは、新しいアルゴリズムの登録方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b45b-124">The following code sample illustrates how to register a new algorithm:</span></span>  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a><span data-ttu-id="9b45b-125">参照</span><span class="sxs-lookup"><span data-stu-id="9b45b-125">See Also</span></span>  
 <span data-ttu-id="9b45b-126">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9b45b-126">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="9b45b-127">DMSCHEMA_MINING_SERVICES 行セット</span><span class="sxs-lookup"><span data-stu-id="9b45b-127">DMSCHEMA_MINING_SERVICES Rowset</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
