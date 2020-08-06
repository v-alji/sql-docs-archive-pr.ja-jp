---
title: Excel でのモデルの参照 (データマイニングアドインの SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- browse models
- mining models, viewing
ms.assetid: a8cca1d7-602a-449a-875c-99da564965bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: c992f1f61112478a85276b6596da0137ccd5c9be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633553"
---
# <a name="browsing-models-in-excel-sql-server-data-mining-add-ins"></a><span data-ttu-id="c6f4f-102">Excel におけるモデルの参照 (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="c6f4f-102">Browsing Models in Excel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="c6f4f-103">![[データ マイニング] リボンの [モデルの参照] ボタン](media/dmc-browse.gif "[データ マイニング] リボンの [モデルの参照] ボタン")</span><span class="sxs-lookup"><span data-stu-id="c6f4f-103">![Browse Model button in Data Mining ribbon](media/dmc-browse.gif "Browse Model button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="c6f4f-104">視覚的にモデルを調査すると、通常は、分析で発見されたルールおよびリレーションシップを最も速く最も容易に理解することができます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-104">Visually exploring the model is usually the fastest and easiest way to get an understanding of the rules and relationships discovered by analysis.</span></span> <span data-ttu-id="c6f4f-105">Excel 用のデータ マイニング クライアントを使用すると、Excel の現在のセッションで作成された一時モデル、および、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに格納されたモデルの両方を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-105">By using the Data Mining Client for Excel, you can browse both temporary models created during the current Excel session, and models stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c6f4f-106">モデルを参照するには、利用可能なモデルの一覧からモデルおよび関連付けられている構造を選択します。そのデータ マイニング アルゴリズムに適したビューアーが自動的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-106">To browse a model, you select a model and its associated structure from a list of available models, and the add-in automatically picks the viewer that is appropriate for that data mining algorithm.</span></span> <span data-ttu-id="c6f4f-107">最も興味深い動向を調べ、完成したデータ マイニング モデルをフィルター処理し、グラフやデータを Excel または Visio にコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-107">You can drill into the most interesting trends, filter the completed data mining model, and copy graphs and data to Excel or to Visio.</span></span>  
  
## <a name="using-the-browse-model-wizard"></a><span data-ttu-id="c6f4f-108">モデル参照ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="c6f4f-108">Using the Browse Model Wizard</span></span>  
  
1.  <span data-ttu-id="c6f4f-109">[**データマイニング**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-109">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="c6f4f-110">[**モデルの使用法**] グループで、[**参照**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-110">In the **Model Usage** group, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="c6f4f-111">[**モデルの選択**] ダイアログボックスで、一覧からマイニングモデルを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-111">In the **Select Model** dialog box, choose a mining model from the list, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="c6f4f-112">ウィザードにより、選択したモデルの種類に適した [**参照**] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-112">The wizard opens a **Browse** window that is appropriate for the type of model that you selected.</span></span>  
  
## <a name="list-of-data-mining-viewers"></a><span data-ttu-id="c6f4f-113">データ マイニング ビューアーの一覧</span><span class="sxs-lookup"><span data-stu-id="c6f4f-113">List of Data Mining Viewers</span></span>  
 <span data-ttu-id="c6f4f-114">モデルの作成時に使用したデータマイニングアルゴリズムによっては、[**参照**] ウィンドウの表示が少し異なります。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-114">Depending on the data mining algorithm that you used when you created the model, the **Browse** window will look a bit different.</span></span> <span data-ttu-id="c6f4f-115">結果の解釈に役立つグラフ、追加の詳細を含む凡例、データを操作するコントロールなどが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-115">It can include graphs to help interpret the results, legends that contain additional detail, and controls for interacting with the data.</span></span>  
  
 <span data-ttu-id="c6f4f-116">以下のトピックでは、複雑なグラフを解釈するためのヒントも含めて、ビューアーそれぞれの使用方法や、結果の変更、コピー、操作を行う方法に関するガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="c6f4f-116">The following topics provide guidance in how to use each of the viewers, including tips on interpreting the complex graphs, and how to change, copy, or work with the results.</span></span>  
  
 [<span data-ttu-id="c6f4f-117">アソシエーション ルール モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-117">Browsing an Association Rules Model</span></span>](browsing-an-association-rules-model.md)  
  
 [<span data-ttu-id="c6f4f-118">クラスター モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-118">Browsing a Clustering Model</span></span>](browsing-a-clustering-model.md)  
  
 [<span data-ttu-id="c6f4f-119">デシジョン ツリー モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-119">Browsing a Decision Trees Model</span></span>](browsing-a-decision-trees-model.md)  
  
 [<span data-ttu-id="c6f4f-120">予測モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-120">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
 [<span data-ttu-id="c6f4f-121">Naive Bayes モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-121">Browsing a Naive Bayes Model</span></span>](browsing-a-naive-bayes-model.md)  
  
 [<span data-ttu-id="c6f4f-122">ニューラル ネットワーク モデルの参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-122">Browsing a Neural Network Model</span></span>](browsing-a-neural-network-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6f4f-123">参照</span><span class="sxs-lookup"><span data-stu-id="c6f4f-123">See Also</span></span>  
 <span data-ttu-id="c6f4f-124">[Visio &#40;データマイニングアドインのデータマイニングモデルの表示&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="c6f4f-124">[Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="c6f4f-125">データマイニングアドイン SQL Server &#40;モデルの管理&#41;</span><span class="sxs-lookup"><span data-stu-id="c6f4f-125">Manage Models &#40;SQL Server Data Mining Add-ins&#41;</span></span>](manage-models-sql-server-data-mining-add-ins.md)  
  
  
