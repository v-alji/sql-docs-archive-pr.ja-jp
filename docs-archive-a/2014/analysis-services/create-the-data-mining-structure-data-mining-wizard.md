---
title: データマイニング構造の作成 (データマイニングウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectminingtechnique.f1
ms.assetid: d1ff17b2-fff3-4ed7-a5d6-42d131e59f93
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9f738cff974bc0064fc9e93c86221f0b10c6e80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639826"
---
# <a name="create-the-data-mining-structure-data-mining-wizard"></a><span data-ttu-id="328fd-102">データ マイニング構造の作成 (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="328fd-102">Create the Data Mining Structure (Data Mining Wizard)</span></span>
  <span data-ttu-id="328fd-103">**[データ マイニング構造の作成]** ページを使用すると、データ マイニング構造および必要に応じて関連するマイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="328fd-103">Use the **Create the Data Mining Structure** page to create a data mining structure and optionally create an associated mining model.</span></span>  
  
 <span data-ttu-id="328fd-104">マイニング モデルの作成を選択した場合は、使用するデータ マイニング アルゴリズムも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="328fd-104">If you choose to create a mining model, you must also specify the data mining algorithm that you want to use.</span></span> <span data-ttu-id="328fd-105">この時点で構造だけを作成する場合は、後からマイニング モデルを構造に追加できます。</span><span class="sxs-lookup"><span data-stu-id="328fd-105">If you create only the structure now, you can add a mining model to the structure later.</span></span>  
  
 <span data-ttu-id="328fd-106">**詳細情報:** [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)、[データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="328fd-106">**For More Information:** [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="328fd-107">Options</span><span class="sxs-lookup"><span data-stu-id="328fd-107">Options</span></span>  
 <span data-ttu-id="328fd-108">**[マイニング モデルを含むマイニング構造を作成する]**</span><span class="sxs-lookup"><span data-stu-id="328fd-108">**Create mining structure with a mining model**</span></span>  
 <span data-ttu-id="328fd-109">マイニング構造を作成してから関連するモデルを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="328fd-109">Select to create a mining structure and then create an associated model.</span></span>  
  
 <span data-ttu-id="328fd-110">**[使用するデータ マイニング技法を指定してください。]**</span><span class="sxs-lookup"><span data-stu-id="328fd-110">**Which data mining technique do you want to use?**</span></span>  
 <span data-ttu-id="328fd-111">このモデルで使用するデータ マイニング アルゴリズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="328fd-111">Select the data mining algorithm to use with this model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="328fd-112">アルゴリズムの一覧は、マイニング構造の作成に使用された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスから取得されます。</span><span class="sxs-lookup"><span data-stu-id="328fd-112">The list of algorithms is populated from the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] on which you are creating the mining structure.</span></span> <span data-ttu-id="328fd-113">このサーバーが使用できない場合、既定のアルゴリズムのみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="328fd-113">If the server is not available, only the default algorithms will be available.</span></span>  
  
 <span data-ttu-id="328fd-114">**[モデルを含まないマイニング構造を作成する]**</span><span class="sxs-lookup"><span data-stu-id="328fd-114">**Create mining structure with no models**</span></span>  
 <span data-ttu-id="328fd-115">マイニング構造だけを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="328fd-115">Select to create only a mining structure.</span></span>  
  
 <span data-ttu-id="328fd-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="328fd-116">**Description**</span></span>  
 <span data-ttu-id="328fd-117">選択したアルゴリズムの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="328fd-117">Displays a description of the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328fd-118">参照</span><span class="sxs-lookup"><span data-stu-id="328fd-118">See Also</span></span>  
 <span data-ttu-id="328fd-119">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="328fd-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="328fd-120">[データマイニングウィザードの &#40;データソースビューの選択&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="328fd-120">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="328fd-121">[[定義方法 &#40;データマイニングウィザード] を選択し&#41;](select-the-definition-method-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="328fd-121">[Select the Definition Method &#40;Data Mining Wizard&#41;](select-the-definition-method-data-mining-wizard.md)</span></span>  
  
  
