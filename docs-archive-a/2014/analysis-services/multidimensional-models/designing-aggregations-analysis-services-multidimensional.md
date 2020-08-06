---
title: 集計のデザイン (Analysis Services-多次元) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18d8ea1adb645868a11b70966ba3be2ed1764fbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645212"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a><span data-ttu-id="83af0-102">集計のデザイン (Analysis Services - 多次元)</span><span class="sxs-lookup"><span data-stu-id="83af0-102">Designing Aggregations (Analysis Services - Multidimensional)</span></span>
  <span data-ttu-id="83af0-103">集計とは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で高速なクエリ応答を実現するために、キューブ データを事前に計算してまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="83af0-103">Aggregations are precalculated summaries of cube data that help enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide rapid query responses.</span></span>  
  
 <span data-ttu-id="83af0-104">パーティションのストレージ オプションを設定し、集計をデザインするには、集計のデザイン ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="83af0-104">To set storage options and design aggregations for a partition, use the Aggregation Design Wizard.</span></span> <span data-ttu-id="83af0-105">このウィザードでは、メジャー グループのパーティションが一度に 1 つずつ処理されるため、パーティションごとに異なるオプションとデザインを選択できます。</span><span class="sxs-lookup"><span data-stu-id="83af0-105">The wizard operates on a single partition of a measure group at a time so that you can select different options and designs for each partition.</span></span> <span data-ttu-id="83af0-106">画面に表示される手順に従って操作するだけで、パーティションのストレージを構成し、集計をデザインできます。</span><span class="sxs-lookup"><span data-stu-id="83af0-106">The wizard takes you through steps to configure storage and design aggregation for a partition.</span></span> <span data-ttu-id="83af0-107">ストレージの構成の詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83af0-107">For more information about configuring storage, see.</span></span>  
  
 <span data-ttu-id="83af0-108">ウィザードでデザインする集計数の制御方法を選択すると、集計がデザインされます。</span><span class="sxs-lookup"><span data-stu-id="83af0-108">Select a method for controlling the number of aggregations the wizard will design, and then let the wizard design the aggregations.</span></span>  
  
 <span data-ttu-id="83af0-109">その目的は、最適な数の集計をデザインすることにあります。</span><span class="sxs-lookup"><span data-stu-id="83af0-109">The goal is to design the optimal number of aggregations.</span></span> <span data-ttu-id="83af0-110">集計数が最適であれば、満足のゆく応答時間が得られるだけでなく、パーティションのサイズが過度に大きくなるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="83af0-110">This number should not only provide satisfactory response time, but also prevent excessive partition size.</span></span> <span data-ttu-id="83af0-111">集計の数を多くすると、応答時間は短くなりますが、必要な記憶領域が増加し、計算にかかる時間が長くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="83af0-111">A greater number of aggregations produces faster response times but it also requires more storage space and may take longer to compute.</span></span> <span data-ttu-id="83af0-112">さらに、ウィザードでは、初めのころに行う集計の方が、後から行う集計よりもパフォーマンスがより向上するように、さらに多くの集計をデザインしていきます。</span><span class="sxs-lookup"><span data-stu-id="83af0-112">Moreover, as the wizard designs more and more aggregations, earlier aggregations produce considerably larger performance gains than later aggregations.</span></span> <span data-ttu-id="83af0-113">不要な集計を減らしても、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="83af0-113">Reduction in less useful aggregations increases performance as well.</span></span> <span data-ttu-id="83af0-114">ウィザードがデザインする集計の数は、ウィザードに用意されている以下のいずれかの方法で調整できます。</span><span class="sxs-lookup"><span data-stu-id="83af0-114">You can control the number of aggregations the wizard designs by one of the following methods available in the wizard:</span></span>  
  
-   <span data-ttu-id="83af0-115">集計に使用する記憶領域を制限する。</span><span class="sxs-lookup"><span data-stu-id="83af0-115">Specify a storage space limit for the aggregations.</span></span>  
  
-   <span data-ttu-id="83af0-116">パフォーマンスを制限する。</span><span class="sxs-lookup"><span data-stu-id="83af0-116">Specify a performance gain limit.</span></span>  
  
-   <span data-ttu-id="83af0-117">パフォーマンスとサイズの比較を示すグラフが許容可能なパフォーマンスの値で横ばいになったら、ウィザードを手動で停止する。</span><span class="sxs-lookup"><span data-stu-id="83af0-117">Stop the wizard manually when the displayed performance versus size curve starts to level off at an acceptable performance gain.</span></span>  
  
-   <span data-ttu-id="83af0-118">集計をデザインしない。</span><span class="sxs-lookup"><span data-stu-id="83af0-118">Choose not to design aggregations.</span></span>  
  
 <span data-ttu-id="83af0-119">ストレージをデザインするには、ウィザードがターゲット サーバー上の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に接続できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="83af0-119">To design storage, the wizard must be able to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on the target server.</span></span> <span data-ttu-id="83af0-120">ターゲット サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が実行されていない場合や、それ以外の理由でストレージ デザイン プロセスがターゲット サーバーに接続できない場合は、ウィザードにエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83af0-120">The wizard will display an error message if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not running on the target server or if the storage design process is otherwise unable to connect to the target server.</span></span>  
  
 <span data-ttu-id="83af0-121">ストレージ デザイン ウィザードの最後の手順では、処理を今すぐに行うか、後で行うかを指定するオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83af0-121">The final step of the wizard allows you to process or defer processing.</span></span> <span data-ttu-id="83af0-122">すぐに処理すると、このウィザードでデザインした集計が作成されますが、保留にすると、デザインした集計は後で処理するために保存され、処理しないでデザイン行動を継続できます。</span><span class="sxs-lookup"><span data-stu-id="83af0-122">Processing creates the aggregations you design with the wizard, while deferring processing saves the designed aggregations for future processing, thus allowing design activities to continue without processing.</span></span> <span data-ttu-id="83af0-123">パーティションのサイズによっては、処理にかなりの時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="83af0-123">Depending on the size of the partition, processing may take considerable time.</span></span> <span data-ttu-id="83af0-124">必要に応じて、パーティションの処理を中断することもできます。</span><span class="sxs-lookup"><span data-stu-id="83af0-124">If you choose, you can interrupt processing a partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83af0-125">参照</span><span class="sxs-lookup"><span data-stu-id="83af0-125">See Also</span></span>  
 [<span data-ttu-id="83af0-126">集計と集計デザイン</span><span class="sxs-lookup"><span data-stu-id="83af0-126">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
