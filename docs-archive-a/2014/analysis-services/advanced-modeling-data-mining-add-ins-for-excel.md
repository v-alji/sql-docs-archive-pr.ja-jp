---
title: 高度なモデリング (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 771eb6111765b558995ee3b0eb98196c63951567
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633695"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a><span data-ttu-id="0cbdc-102">高度なモデリング (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="0cbdc-102">Advanced Modeling (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="0cbdc-103">**高度な**データモデリングオプションを使用すると、ウィザードによって作成されたものとは異なるパラメーターを使用して、カスタムデータマイニング構造およびモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-103">You can use the **Advanced** data modeling options to create custom data mining structures and models with parameters different from those created by the wizards.</span></span> <span data-ttu-id="0cbdc-104">このセクションで説明する 2 つのウィザードでは、まったく新しいデータ マイニング構造を作成したり、既存のデータ マイニング構造に適用する新しいマイニング モデルを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-104">The two wizards described in this section help you create a completely new data mining structure, and a new mining model to apply to an existing data mining structure.</span></span>  
  
## <a name="create-mining-structure"></a><span data-ttu-id="0cbdc-105">マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="0cbdc-105">Create Mining Structure</span></span>  
 <span data-ttu-id="0cbdc-106">![[データ マイニング] リボンの [マイニング構造の作成] ボタン](media/dmc-createstruct.gif "[データ マイニング] リボンの [マイニング構造の作成] ボタン")</span><span class="sxs-lookup"><span data-stu-id="0cbdc-106">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="0cbdc-107">**マイニング構造の作成ウィザード**を使用すると、新しいデータマイニング構造を構築できます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-107">The **Create Mining Structure Wizard** helps you build a new data mining structure.</span></span> <span data-ttu-id="0cbdc-108">構造とは、指定したデータ ソースから抽出したデータのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-108">A structure is a collection of data extracted from a specified data source.</span></span>  <span data-ttu-id="0cbdc-109">マイニング構造は、基になる新しいデータで更新できますが、マイニング構造を作成するときは、分析時のデータの使用方法を定義するデータ型と名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-109">A mining structure can be updated with new data at the source, but when you create the mining structure, you define data types and names that define how the data is used for analysis.</span></span>  
  
 <span data-ttu-id="0cbdc-110">Excel テーブル、Excel 範囲、または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソース ビューとして定義済みである外部データ ソースの任意のデータをデータ ソースとして、構造を構築することができます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-110">You can use the following data sources to build your structure: an Excel table, an Excel range, or any data in an external data source that has already been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="0cbdc-111">テスト用および検証用のデータを構造ごとに確保することができます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-111">For each structure, you have the option of setting aside some of the data to use for testing and validation.</span></span> <span data-ttu-id="0cbdc-112">データソースを設定するときに、この*予約データセット*を作成することによって、構造に基づくすべてのモデルで、テストに一貫性のあるデータセットを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-112">By creating this *holdout data set* when you set up your data sources, you can ensure that all models that are based on the structure are able to use a consistent data set for testing.</span></span>  
  
 <span data-ttu-id="0cbdc-113">マイニング構造を作成した後、複数のモデルを追加して、異なる分析方法を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-113">After you have created a mining structure, you can add multiple models to apply different methods of analysis.</span></span>  
  
 <span data-ttu-id="0cbdc-114">**マイニング構造の作成ウィザード**を使用する方法の詳細については、「 [create マイニング Structure &#40;SQL Server データマイニングアドイン&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-114">For more information about how to use the **Create Mining Structure Wizard**, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="add-model-to-structure"></a><span data-ttu-id="0cbdc-115">構造へのモデルの追加</span><span class="sxs-lookup"><span data-stu-id="0cbdc-115">Add Model to Structure</span></span>  
 <span data-ttu-id="0cbdc-116">![[構造へのモデルの追加] ボタン](media/dmc-addmodel.gif "[構造へのモデルの追加] ボタン")</span><span class="sxs-lookup"><span data-stu-id="0cbdc-116">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="0cbdc-117">新しいモデルを構造に追加する場合は、別のアルゴリズムまたは別のパラメーターを使用してデータを分析します。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-117">When you add a new model to a structure, you analyze the data by using a different algorithm, or with different parameters.</span></span> <span data-ttu-id="0cbdc-118">このオプションは、データ マイニング クライアント ツールで公開されていないアルゴリズムの 1 つを使用してモデルを作成する場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-118">This option is particularly useful if you want to create a model using one of the algorithms not exposed in the Data Mining Client tools.</span></span>  
  
 <span data-ttu-id="0cbdc-119">たとえば、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でサポートされている次のようなアルゴリズムを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-119">For example, you can use any of the algorithms supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], such as:</span></span>  
  
-   <span data-ttu-id="0cbdc-120">Linear regression (線形回帰)</span><span class="sxs-lookup"><span data-stu-id="0cbdc-120">Linear regression</span></span>  
  
-   <span data-ttu-id="0cbdc-121">シーケンス クラスター</span><span class="sxs-lookup"><span data-stu-id="0cbdc-121">Sequence clustering</span></span>  
  
-   <span data-ttu-id="0cbdc-122">入れ子になったデータ セットのアソシエーション分析</span><span class="sxs-lookup"><span data-stu-id="0cbdc-122">Association analysis on nested data sets</span></span>  
  
 <span data-ttu-id="0cbdc-123">使用できるマイニング構造の種類を確認するには、[ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **モデルの管理**] または [**参照**] をクリックして、に格納されているモデルと構造を参照できます。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-123">To see what kind of mining structures are available, you can browse the models and structures stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] by clicking either **Manage Models** or **Browse**.</span></span>  
  
 <span data-ttu-id="0cbdc-124">使用できるのは、現在のセッション中に作成されたデータ マイニング構造、または、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに保存されたマイニング構造に限定されています。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-124">You are limited to data mining structures that were created during the current session, or mining structures that were saved to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0cbdc-125">詳細については、「 [Add Model To Structure &#40;&#41;Excel 用データマイニングアドイン](add-model-to-structure-data-mining-add-ins-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cbdc-125">For more information, see [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbdc-126">参照</span><span class="sxs-lookup"><span data-stu-id="0cbdc-126">See Also</span></span>  
 <span data-ttu-id="0cbdc-127">[データマイニングアドイン SQL Server &#40;モデルの管理&#41;](manage-models-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="0cbdc-127">[Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="0cbdc-128">Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;</span><span class="sxs-lookup"><span data-stu-id="0cbdc-128">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
