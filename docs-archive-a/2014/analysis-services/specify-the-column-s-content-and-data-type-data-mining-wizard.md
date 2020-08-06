---
title: 列&#39;s コンテンツおよびデータ型の指定 (データマイニングウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifycontentdatatype.f1
ms.assetid: 7061f674-e806-46f2-8c15-e260a3c69a17
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66af7280e444036468b9cc33a131993524d3586d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643507"
---
# <a name="specify-the-column39s-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="8c0b1-102">[列&#39;s コンテンツおよびデータ型の指定] (データマイニングウィザード)</span><span class="sxs-lookup"><span data-stu-id="8c0b1-102">Specify the Column&#39;s Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="8c0b1-103">**[列のコンテンツおよびデータ型の指定]** ページを使用すると、ウィザードで既に設定されている列型およびコンテンツの種類を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-103">Use the **Specify the Column's Content and Data Type** page to modify the column and content types that have already been set by the wizard.</span></span> <span data-ttu-id="8c0b1-104">ウィザードは、ソース列のデータ型および選択されているアルゴリズムの機能を使用して、各列の既定のデータ型およびコンテンツの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-104">The wizard uses the data types of the source columns and the capabilities of the selected algorithm to determine the default data and content types for each column.</span></span>  
  
 <span data-ttu-id="8c0b1-105">**詳細情報:** [データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="8c0b1-105">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c0b1-106">Options</span><span class="sxs-lookup"><span data-stu-id="8c0b1-106">Options</span></span>  
 <span data-ttu-id="8c0b1-107">**[列]**</span><span class="sxs-lookup"><span data-stu-id="8c0b1-107">**Columns**</span></span>  
 <span data-ttu-id="8c0b1-108">ウィザードの **[トレーニング データの指定]** で定義された列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-108">A list of the columns that are defined in the **Specify the Training Data** page of the wizard.</span></span>  
  
 <span data-ttu-id="8c0b1-109">**コンテンツの種類**</span><span class="sxs-lookup"><span data-stu-id="8c0b1-109">**Content Type**</span></span>  
 <span data-ttu-id="8c0b1-110">各列に割り当てられたコンテンツの種類です。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-110">The content type that is assigned to each column.</span></span> <span data-ttu-id="8c0b1-111">セルの内側をクリックしてコンテンツの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-111">Click inside a cell to change the content type.</span></span> <span data-ttu-id="8c0b1-112">コンテンツの種類の詳細については、「[コンテンツの種類 (データ マイニング)](data-mining/content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-112">For more information about content types, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="8c0b1-113">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="8c0b1-113">**Data Type**</span></span>  
 <span data-ttu-id="8c0b1-114">各列に割り当てられたデータ型です。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-114">The data types that are assigned to each column.</span></span> <span data-ttu-id="8c0b1-115">セルの内側をクリックしてデータ型を変更します。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-115">Click inside a cell to change the data type.</span></span> <span data-ttu-id="8c0b1-116">データ型の詳細については、「[データ型 (データ マイニング)](data-mining/data-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-116">For more information about data types, see [Data Types &#40;Data Mining&#41;](data-mining/data-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="8c0b1-117">**Detect**</span><span class="sxs-lookup"><span data-stu-id="8c0b1-117">**Detect**</span></span>  
 <span data-ttu-id="8c0b1-118">クリックすると、数値列の連続または不連続のコンテンツの種類が自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-118">Click to automatically detect the continuous and discrete content types for numeric column.</span></span> <span data-ttu-id="8c0b1-119">これは、OLAP データ ソースに基づいたマイニング構造には適用されません。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-119">This does not apply to mining structures that are based on OLAP data sources.</span></span> <span data-ttu-id="8c0b1-120">OLAP マイニング構造の場合、ウィザードはコンテンツの種類を自動的に検出し、選択されているアルゴリズムと互換性のある種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-120">For OLAP mining structures, the wizard automatically detects content types and chooses a type that is compatible with the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0b1-121">参照</span><span class="sxs-lookup"><span data-stu-id="8c0b1-121">See Also</span></span>  
 <span data-ttu-id="8c0b1-122">[[ウィザードの完了] &#40;データマイニングウィザード&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="8c0b1-122">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="8c0b1-123">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8c0b1-123">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="8c0b1-124">データマイニング &#40;トレーニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="8c0b1-124">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
