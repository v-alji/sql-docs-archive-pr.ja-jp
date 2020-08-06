---
title: Visio のデータマイニング図形 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a12d7d5f3ad021105f06043f47dcdfe5c3e5c2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643035"
---
# <a name="data-mining-shapes-for-visio"></a><span data-ttu-id="d1465-102">Visio 用のデータ マイニング図形</span><span class="sxs-lookup"><span data-stu-id="d1465-102">Data Mining Shapes for Visio</span></span>
  <span data-ttu-id="d1465-103">Visio 用データ マイニング図形は、データ マイニング モデルを表示するためにカスタマイズされたテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="d1465-103">The Data Mining Shapes for Visio provide templates customized for displaying data mining models.</span></span> <span data-ttu-id="d1465-104">これらのテンプレートを使用すると、作成したモデルに接続し、インタラクティブなプレゼンテーションを作成してデータ マイニングの結果を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="d1465-104">By using these templates, you can connect to a model that you have created, and create interactive presentations to illustrate the results of data mining.</span></span>  
  
 <span data-ttu-id="d1465-105">テンプレートには、静的グラフや画面キャプチャよりも多くの利点があります。これらは、Analysis Services のインスタンスに格納されている基になるデータマイニングモデルと対話し、マイニングモデルのパターンの表示方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d1465-105">The templates offer many advantages over static graphs and screen captures - they interact with the underlying data mining models, which are stored on an instance of Analysis Services, and let you customize the way that the patterns in the mining model are displayed.</span></span> <span data-ttu-id="d1465-106">ツリー モデルはレベルの折りたたみと展開ができ、データ ノードに対して、または属性別にフィルター処理を実行できるほか、確率や係数などのモデル統計を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1465-106">You can collapse and expand a tree model, filter on data nodes or by attributes, and display model statistics such as probabilities and coefficients.</span></span>  
  
 <span data-ttu-id="d1465-107">![DM](media/dm-stencil.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="d1465-107">![DM](media/dm-stencil.gif "DM")</span></span>  
  
 <span data-ttu-id="d1465-108">Visio テンプレートには、以下のウィザードが含まれています:</span><span class="sxs-lookup"><span data-stu-id="d1465-108">The Visio templates include these wizards:</span></span>  
  
-   <span data-ttu-id="d1465-109">**依存関係ネットワークダイアグラム:** このウィザードを使用して、デシジョンツリーとニューラルネットワークのグラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1465-109">**Dependency Network diagram:** Use this wizard to create graphs for decision trees and neural networks.</span></span>  
  
-   <span data-ttu-id="d1465-110">**デシジョンツリーダイアグラム:** このウィザードを使用すると、デシジョンツリーモデルに関連付けられている決定ポイントと数式を示すダイアグラムを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1465-110">**Decision Tree diagram:** Use this wizard to create diagrams that show the decision points and formulas associated with decision tree models.</span></span> <span data-ttu-id="d1465-111">このダイアグラムは、回帰モデルでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1465-111">This diagram can also be used with regression models.</span></span>  
  
-   <span data-ttu-id="d1465-112">**クラスターダイアグラム:** このウィザードを使用して、セグメンテーションモデルのカラフルなグラフを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1465-112">**Cluster diagram:** Use this wizard to create colorful graphs for your segmentation models.</span></span> <span data-ttu-id="d1465-113">属性の識別、プロファイル、依存関係などのビューを切り替え、クラスターの外観をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1465-113">You can toggle between views such as attribute discrimination, cluster profiles, and dependencies, and cusotmize the appearance of clusters.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="d1465-114">インストール</span><span class="sxs-lookup"><span data-stu-id="d1465-114">Installation</span></span>  
 <span data-ttu-id="d1465-115">Visio 用のデータマイニングテンプレートをインストールすると、既定では、次のファイルが \<drive> SQL Server 2012 DM アドイン (または、または \<drive> Program files (x86) \Microsoft SQL SERVER 2012 dm アドイン) にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d1465-115">When you install the Data Mining Templates for Visio, by default the following files are installed to \<drive>\Program Files\Microsoft SQL Server 2012 DM Add-Ins (or \<drive>\ or Program Files (x86)\Microsoft SQL Server 2012 DM Add-Ins):</span></span>  
  
-   <span data-ttu-id="d1465-116">**Microsoft データマイニング. vst**このテンプレートには、データマイニング図形の操作に役立つ、デザイン済みの書式設定、レイアウト、およびウィザードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1465-116">**Microsoft Data Mining.vst** This template contains pre-designed formatting, layout, and wizards to help you work with the data mining shapes.</span></span>  
  
-   <span data-ttu-id="d1465-117">**Microsoft データマイニング図形 Studio .vss**このステンシルファイルには、テンプレートに関連付けられた図形が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1465-117">**Microsoft Data Mining Shape Studio.vss** This stencil file contains shapes associated with the template.</span></span>  
  
## <a name="how-to-use-the-templates"></a><span data-ttu-id="d1465-118">テンプレートの使用方法</span><span class="sxs-lookup"><span data-stu-id="d1465-118">How to Use the Templates</span></span>  
 <span data-ttu-id="d1465-119">テンプレートを開くには、図形ファイルをダブルクリックするか、Visio を開いてから図形テンプレートを開きます。</span><span class="sxs-lookup"><span data-stu-id="d1465-119">To open the templates, you can double-click the shape file, or you can open Visio and then open the shape template.</span></span>  
  
1.  <span data-ttu-id="d1465-120">Visio データ マイニング図形をステンシルから新しいページにドロップします。</span><span class="sxs-lookup"><span data-stu-id="d1465-120">Drop one of the Visio data mining shapes from the stencil onto a new page.</span></span>  
  
2.  <span data-ttu-id="d1465-121">ウィザードが起動したら、表示するデータ マイニング モデルがあるサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="d1465-121">When the wizard starts, connect to the server that has the data mining model that you want to display.</span></span>  
  
3.  <span data-ttu-id="d1465-122">データ マイニング モデルを選択して、モデルの種類を視覚化の種類と一致させます。</span><span class="sxs-lookup"><span data-stu-id="d1465-122">Select the data mining model, matching the type of model to the type of visualization.</span></span>  
  
4.  <span data-ttu-id="d1465-123">データの表示オプションと書式設定オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d1465-123">Set options for how the data should be displayed and formatted.</span></span>  
  
5.  <span data-ttu-id="d1465-124">**データマイニング図形ウィザード**を完了すると、Visio の機能を使用して変更および強化できるダイアグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1465-124">After you have completed the **Data Mining Shape Wizard**, you have a diagram that you can modify and enhance using the features of Visio.</span></span>  
  
 <span data-ttu-id="d1465-125">Visio モデル図を使用および強化する方法の詳細については、「 [visio でのデータマイニングモデルの表示 &#40;データマイニングアドイン](viewing-data-mining-models-in-visio-data-mining-add-ins.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="d1465-125">For more information about how to work with and enhance Visio model diagrams, see [Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1465-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="d1465-126">Requirements</span></span>  
  
-   <span data-ttu-id="d1465-127">テンプレートを使用するには、最初に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1465-127">To use the templates, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="d1465-128">ウィザードに従って、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーを選択し、マイニング モデルが格納されているデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1465-128">The wizard will prompt you to select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and specify the database that contains the mining model.</span></span>  
  
     <span data-ttu-id="d1465-129">接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1465-129">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
-   <span data-ttu-id="d1465-130">テーブル分析ツールを使用している場合は、モデルをサーバーに保存し、一時的なモデルを使用しないようにしてください [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d1465-130">If you are using the Table Analysis Tools, make sure that you save your models to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, and do not use temporary models.</span></span>  
  
-   <span data-ttu-id="d1465-131">モデルは、サポートされているアルゴリズム (クラスタリング、デシジョン ツリー、ニューラル ネットワーク、Naïve Bayes、またはロジスティック回帰) を使用して作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1465-131">The model must have been created using one of the supported algorithms: clustering, decision trees, neural networks, Naïve Bayes, or logistic regression.</span></span>  
  
  
