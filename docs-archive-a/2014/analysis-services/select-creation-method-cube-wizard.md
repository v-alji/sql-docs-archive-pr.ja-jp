---
title: '[作成方法の選択] (キューブウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: c8c4d611e00a2b3f5d115ea5749b1e494a44bf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644155"
---
# <a name="select-creation-method-cube-wizard"></a><span data-ttu-id="551bc-102">[作成方法の選択] (キューブ ウィザード)</span><span class="sxs-lookup"><span data-stu-id="551bc-102">Select Creation Method (Cube Wizard)</span></span>
  <span data-ttu-id="551bc-103">**[作成方法の選択]** ページを使用すると、キューブの作成方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="551bc-103">Use the **Select Creation Method** page to specify how to create the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="551bc-104">Options</span><span class="sxs-lookup"><span data-stu-id="551bc-104">Options</span></span>  
 <span data-ttu-id="551bc-105">**[既存のテーブルの使用]**</span><span class="sxs-lookup"><span data-stu-id="551bc-105">**Use existing tables**</span></span>  
 <span data-ttu-id="551bc-106">データ ソース内の既存のテーブルを使用してキューブを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="551bc-106">Select to create a cube by using existing tables in a data source.</span></span> <span data-ttu-id="551bc-107">ウィザードの指示に従って、既存のテーブルに基づいてメジャー グループとディメンションを選択および定義し、新しいキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="551bc-107">The wizard will guide you through the process of selecting and defining measure groups and dimensions based on existing tables to build your new cube.</span></span>  
  
 <span data-ttu-id="551bc-108">**[空のキューブの作成]**</span><span class="sxs-lookup"><span data-stu-id="551bc-108">**Create an empty cube**</span></span>  
 <span data-ttu-id="551bc-109">空のキューブを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="551bc-109">Select to create an empty cube.</span></span> <span data-ttu-id="551bc-110">このオプションは、すべてを手動で作成する場合やキューブ内のすべてのメジャー グループがリンク メジャー グループである場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="551bc-110">This option is useful when you want to create everything manually, or when all measure groups in the cube are linked measure groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="551bc-111">このオプションは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを使用している場合にのみ使用でき、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに直接接続している場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="551bc-111">This option is only available when you are working with an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and not when you are connected directly to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="551bc-112">**[データ ソースにテーブルを生成]**</span><span class="sxs-lookup"><span data-stu-id="551bc-112">**Generate tables in the data source**</span></span>  
 <span data-ttu-id="551bc-113">キューブを作成してからそのキューブの定義に基づいてデータ ソースに新しいテーブルを生成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="551bc-113">Select to create a cube first and then generate new tables in the data source based on the cube definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="551bc-114">このオプションを使用するには、基になるデータ ソースにオブジェクトを作成する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="551bc-114">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="551bc-115">このオプションを選択すると、 **[テンプレート]** オプションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="551bc-115">Selecting this option will make the **Template** option available.</span></span>  
  
 <span data-ttu-id="551bc-116">**テンプレート**</span><span class="sxs-lookup"><span data-stu-id="551bc-116">**Template**</span></span>  
 <span data-ttu-id="551bc-117">キューブの作成に使用するテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="551bc-117">Select the template that you want to use to create the cube.</span></span> <span data-ttu-id="551bc-118">テンプレートは、特定のビジネス用途向けの定義のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="551bc-118">Templates provide a set of definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="551bc-119">このオプションは、 **[データ ソースにテーブルを生成]** オプションが選択された場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="551bc-119">This option is only available when the **Generate tables in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551bc-120">参照</span><span class="sxs-lookup"><span data-stu-id="551bc-120">See Also</span></span>  
 <span data-ttu-id="551bc-121">[キューブオブジェクト &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="551bc-121">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="551bc-122">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="551bc-122">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="551bc-123">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="551bc-123">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
