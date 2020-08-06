---
title: '[既存のオブジェクトのデータソース] (データソースウィザード) (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 621c938f4902c95dee1e2fcccb0f292597a565f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716962"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a><span data-ttu-id="2d827-102">[既存のオブジェクトのデータ ソース] (データ ソース ウィザード) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2d827-102">Data sources from existing objects (Data Source Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="2d827-103">**[既存のオブジェクトのデータ ソース]** ページを使用すると、新しいデータ ソースの基となる既存のデータ ソースまたはプロジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d827-103">Use the **Data sources from existing objects** page to specify an existing data source or project on which to base the new data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d827-104">Options</span><span class="sxs-lookup"><span data-stu-id="2d827-104">Options</span></span>  
 <span data-ttu-id="2d827-105">**[ソリューションの既存のデータ ソースに基づいてデータ ソースを作成する]**</span><span class="sxs-lookup"><span data-stu-id="2d827-105">**Create a data source based on an existing data source in your solution**</span></span>  
 <span data-ttu-id="2d827-106">新しいデータ ソースは、ソリューションの既存のデータ ソースに基づきます。</span><span class="sxs-lookup"><span data-stu-id="2d827-106">Select to base the new data source on an existing data source in the solution.</span></span> <span data-ttu-id="2d827-107">新しいデータ ソースを使用するプロジェクトが構築、更新、または配置される場合、この新しいデータ ソースの設定は、このオプションを選択したときに指定したデータ ソースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="2d827-107">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires the settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="2d827-108">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="2d827-108">**Data source**</span></span>  
 <span data-ttu-id="2d827-109">プロジェクトによってグループ化されたデータ ソースの一覧から新しいデータ ソースの基になるデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d827-109">Select a data source on which you want to base the new data source from the list of data sources, which is grouped by project.</span></span>  
  
 <span data-ttu-id="2d827-110">**[Analysis Services プロジェクトに基づいてデータ ソースを作成する]**</span><span class="sxs-lookup"><span data-stu-id="2d827-110">**Create a data source based on an Analysis Services project**</span></span>  
 <span data-ttu-id="2d827-111">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 現在のソリューション内の別のプロジェクトを参照する新しいデータソースを作成する場合に選択し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2d827-111">Select to create a new data source that references another [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in the current solution.</span></span> <span data-ttu-id="2d827-112">新しいデータ ソースは、選択されたプロジェクトの `TargetServer` プロパティと `TargetDatabase` プロパティから設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d827-112">The new data source acquires settings from the `TargetServer` and `TargetDatabase` properties of the selected project.</span></span> <span data-ttu-id="2d827-113">新しいデータ ソースを使用するプロジェクトが構築、更新、または配置される場合、この新しいデータ ソースの設定は、このオプションを選択したときに指定したデータ ソースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="2d827-113">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="2d827-114">**プロジェクト**</span><span class="sxs-lookup"><span data-stu-id="2d827-114">**Project**</span></span>  
 <span data-ttu-id="2d827-115">新しいデータ ソースで参照するプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d827-115">Select the project that you want to reference in the new data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d827-116">参照</span><span class="sxs-lookup"><span data-stu-id="2d827-116">See Also</span></span>  
 <span data-ttu-id="2d827-117">[データソースウィザードの F1 ヘルプ &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2d827-117">[Data Source Wizard F1 Help &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span></span>  
 <span data-ttu-id="2d827-118">[多次元モデルのデータソース](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="2d827-118">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="2d827-119">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="2d827-119">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
