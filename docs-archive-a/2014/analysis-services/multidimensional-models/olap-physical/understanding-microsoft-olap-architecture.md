---
title: Microsoft OLAP アーキテクチャについて |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multidimensional data [Analysis Services], about multidimensional data
ms.assetid: a2eaaee8-7b06-48af-ba44-e21a3678c4c4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1abbbbd7c2f7caa99407bbcd17ace07deac5dfeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642372"
---
# <a name="understanding-microsoft-olap-architecture"></a><span data-ttu-id="0de24-102">Microsoft OLAP アーキテクチャについて</span><span class="sxs-lookup"><span data-stu-id="0de24-102">Understanding Microsoft OLAP Architecture</span></span>
  <span data-ttu-id="0de24-103">以下のトピックを参照して、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 多次元データベースを十分に理解し、ビジネス インテリジェンス ソリューションに多次元データベースを実装する計画を立てます。</span><span class="sxs-lookup"><span data-stu-id="0de24-103">Use these topics to better understand [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] multidimensional databases and plan how to implement multidimensional databases in your business intelligence solution.</span></span>  
  
 <span data-ttu-id="0de24-104">![小さいファイルフォルダーアイコン](../../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")**論理アーキテクチャ**</span><span class="sxs-lookup"><span data-stu-id="0de24-104">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Logical Architecture**</span></span>  
 [<span data-ttu-id="0de24-105">サーバーオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="0de24-105">Server Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="0de24-106">ディメンションオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="0de24-106">Dimension Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="0de24-107">キューブオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="0de24-107">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="0de24-108">もっとその。。。</span><span class="sxs-lookup"><span data-stu-id="0de24-108">More...</span></span>](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
 <span data-ttu-id="0de24-109">![小さいファイルフォルダーアイコン](../../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")の**物理アーキテクチャ**</span><span class="sxs-lookup"><span data-stu-id="0de24-109">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Physical Architecture**</span></span>  
 [<span data-ttu-id="0de24-110">OLAP エンジンのサーバー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0de24-110">OLAP Engine Server Components</span></span>](olap-engine-server-components.md)  
  
 [<span data-ttu-id="0de24-111">ローカルキューブ &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="0de24-111">Local Cubes &#40;Analysis Services - Multidimensional Data&#41;</span></span>](local-cubes-analysis-services-multidimensional-data.md)  
  
 [<span data-ttu-id="0de24-112">もっとその。。。</span><span class="sxs-lookup"><span data-stu-id="0de24-112">More...</span></span>](understanding-microsoft-olap-physical-architecture.md)  
  
 <span data-ttu-id="0de24-113">![小さいファイルフォルダーアイコン](../../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")の**プログラミングアーキテクチャ**</span><span class="sxs-lookup"><span data-stu-id="0de24-113">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Programming Architecture**</span></span>  
 [<span data-ttu-id="0de24-114">分析管理オブジェクト &#40;AMO&#41; による開発</span><span class="sxs-lookup"><span data-stu-id="0de24-114">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
  
 [<span data-ttu-id="0de24-115">Analysis Services スクリプト言語 (ASSL) での開発</span><span class="sxs-lookup"><span data-stu-id="0de24-115">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [<span data-ttu-id="0de24-116">ADOMD.NET での開発</span><span class="sxs-lookup"><span data-stu-id="0de24-116">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
 <span data-ttu-id="0de24-117">![小さいファイルフォルダーアイコン](../../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")**国際化に関する注意点**</span><span class="sxs-lookup"><span data-stu-id="0de24-117">![Small File Folder Icon](../../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **International Considerations**</span></span>  
 [<span data-ttu-id="0de24-118">Analysis Services 多次元のグローバル化のシナリオ</span><span class="sxs-lookup"><span data-stu-id="0de24-118">Globalization scenarios for Analysis Services Multiidimensional</span></span>](../../globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
## <a name="see-also"></a><span data-ttu-id="0de24-119">参照</span><span class="sxs-lookup"><span data-stu-id="0de24-119">See Also</span></span>  
 [<span data-ttu-id="0de24-120">SSAS&#41;&#40;テクニカルリファレンス</span><span class="sxs-lookup"><span data-stu-id="0de24-120">Technical Reference &#40;SSAS&#41;</span></span>](../../powershell/technical-reference-ssas.md)  
  
  
