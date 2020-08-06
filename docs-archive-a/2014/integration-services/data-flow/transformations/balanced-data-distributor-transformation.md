---
title: Balanced Data Distributor (BDD) 変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.balanceddatadistributor.f1
ms.assetid: ae0b33dd-f44b-42df-b6f6-69861770ce10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09591013bc1f21659720fa9fec2e94167be93a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640181"
---
# <a name="balanced-data-distributor-transformation"></a><span data-ttu-id="16b76-102">Balanced Data Distributor (BDD) 変換</span><span class="sxs-lookup"><span data-stu-id="16b76-102">Balanced Data Distributor Transformation</span></span>
  <span data-ttu-id="16b76-103">Balanced Data Distributor (BDD) 変換では最新 CPU の同時処理機能を利用します。</span><span class="sxs-lookup"><span data-stu-id="16b76-103">The Balanced Data Distributor (BDD) transformation takes advantage of concurrent processing capability of modern CPUs.</span></span> <span data-ttu-id="16b76-104">この手法では、複数の着信バッファーを、個別のスレッド上に存在する出力に対して一様に分配します。</span><span class="sxs-lookup"><span data-stu-id="16b76-104">It distributes buffers of incoming rows uniformly across outputs on separate threads.</span></span> <span data-ttu-id="16b76-105">BDD コンポーネントは各出力パスに対応する個別のスレッドを使用することで、マルチコアまたはマルチプロセッサのコンピューターで SSIS パッケージのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="16b76-105">By using separate threads for each output path, the BDD component improves the performance of an SSIS package on multi-core or multi-processor machines.</span></span> <span data-ttu-id="16b76-106">BDD コンポーネントは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Feature Pack の一部です。</span><span class="sxs-lookup"><span data-stu-id="16b76-106">The BDD component is part of the Feature Pack for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="16b76-107">[こちら](https://go.microsoft.com/fwlink/p/?LinkId=391999)からダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="16b76-107">Download and install it from [here](https://go.microsoft.com/fwlink/p/?LinkId=391999).</span></span>  
  
 <span data-ttu-id="16b76-108">次の図に、BDD 変換を使用する簡単な例を示します。</span><span class="sxs-lookup"><span data-stu-id="16b76-108">The following diagram shows a simple example of using the BDD transformation.</span></span> <span data-ttu-id="16b76-109">この例では、BDD 変換はフラット ファイル変換元から得られる入力データから、一度に 1 つのパイプライン バッファーを選択し、3 つの出力パスのいずれかに対してラウンド ロビン形式で送信します。</span><span class="sxs-lookup"><span data-stu-id="16b76-109">In this example, the BDD transformation picks one pipeline buffer at a time from the input data from a flat file source and sends it down one of the three output paths in a round robin fashion.</span></span> <span data-ttu-id="16b76-110">SQL Server データ ツールで、データ フロー タスクのプロパティを表示する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>ペインを使用して、 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(パイプラインのバッファーの既定のサイズ) と **DefaultBufferMaxRows** (パイプライン バッファー内にある最大行数の既定値) の値を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="16b76-110">In SQL Server Data Tools, you can check the values of a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>(default size of the pipeline buffer) and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(default maximum number of rows in a pipeline buffer) in the **Properties** window displaying properties of a data flow task.</span></span>  
  
 <span data-ttu-id="16b76-111">![Balanced Data Distributor](../../media/balanceddatadistributor.JPG "Balanced Data Distributor")</span><span class="sxs-lookup"><span data-stu-id="16b76-111">![Balanced Data Distributor](../../media/balanceddatadistributor.JPG "Balanced Data Distributor")</span></span>  
  
 <span data-ttu-id="16b76-112">次の条件を満たすシナリオで、Balanced Data Distributor (BDD) 変換を使用して、パッケージのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="16b76-112">The Balanced Data Distributor transformation helps improve performance of a package in a scenario that satisfies the following conditions:</span></span>  
  
1.  <span data-ttu-id="16b76-113">BDD 変換に対して到着する大量のデータがあります。</span><span class="sxs-lookup"><span data-stu-id="16b76-113">There is large amount of data coming into the BDD transformation.</span></span> <span data-ttu-id="16b76-114">データ サイズが小さく、わずか 1 個のバッファーでデータを保持できる場合は、BDD 変換を使用する利点はありません。</span><span class="sxs-lookup"><span data-stu-id="16b76-114">If the data size is small and only one buffer can hold the data, there is no point in using the BDD transformation.</span></span> <span data-ttu-id="16b76-115">データ サイズが大きく、データを保持するために複数のバッファーが必要な場合は、BDD は個別のスレッドを使用してデータ バッファーを効率的に並行処理することができます。</span><span class="sxs-lookup"><span data-stu-id="16b76-115">If the data size is large and several buffers are required to hold the data, BDD can efficiently process buffers of data in parallel by using separate threads.</span></span>  
  
2.  <span data-ttu-id="16b76-116">データ フローの残りの部分による処理速度より高速に、データを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="16b76-116">The data can be read faster than the rest of the data flow can process it.</span></span> <span data-ttu-id="16b76-117">このシナリオでは、データの到着速度に比べると、データに対して実行される変換の方が遅くなっています。</span><span class="sxs-lookup"><span data-stu-id="16b76-117">In this scenario, the transformations that are performed on the data run slowly compared to the rate at which data is coming.</span></span> <span data-ttu-id="16b76-118">ボトルネックが転送先に存在する場合は、変換先を並列化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16b76-118">If the bottleneck is at the destination, the destination must be parallelizable though.</span></span>  
  
3.  <span data-ttu-id="16b76-119">データを並べ替える必要がありません。</span><span class="sxs-lookup"><span data-stu-id="16b76-119">The data does not need to be ordered.</span></span> <span data-ttu-id="16b76-120">たとえば、データを並べ替えた状態で維持する必要がある場合は、BDD 変換を使用してデータを分割することを避けてください。</span><span class="sxs-lookup"><span data-stu-id="16b76-120">For example, if the data needs to stay sorted, you should not split the data using the BDD transformation.</span></span>  
  
 <span data-ttu-id="16b76-121">変換元からデータを読み取るレートが原因で、ボトルネックが SSIS パッケージ内に存在する場合は、BDD コンポーネントはパフォーマンス向上に役立たないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="16b76-121">Note that if the bottleneck in an SSIS package is due to the rate at which data can be read from the source, the BDD component does not help improve the performance.</span></span> <span data-ttu-id="16b76-122">変換先が並列処理をサポートしていないことが原因でボトルネックが SSIS パッケージ内に存在する場合も、BDD は役に立ちません。ただし、すべての変換を並列実行し、データを変換先に送信する前に、全体結合という変換を使用して、BDD 変換の複数の出力パスから到着した出力データを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="16b76-122">If the bottleneck in an SSIS package is because the destination does not support parallelism, the BDD does not help; however, you can perform all the transformations in parallel and use the Union All transformation to combine the output data coming out of different output paths of the BDD transformation before sending the data to the destination.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="16b76-123"> 変換の使用方法を示すプレゼンテーションとして、TechNet ライブラリの [Balanced Data Distributor ビデオに関するページ](https://go.microsoft.com/fwlink/?LinkID=226278) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16b76-123">See the [Balanced Data Distributor video](https://go.microsoft.com/fwlink/?LinkID=226278) on the TechNet Library for a presentation with a demo on using the transformation.</span></span>  
  
  
