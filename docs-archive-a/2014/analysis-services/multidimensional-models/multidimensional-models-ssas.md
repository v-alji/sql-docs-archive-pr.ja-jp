---
title: 多次元モデリング (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 509df042-fdb3-4e2c-a6b8-86943ce1b0fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7348a932eccb62f2e00c0b154ca9efc8086fcd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743570"
---
# <a name="multidimensional-modeling-ssas"></a><span data-ttu-id="426c4-102">多次元モデリング (SSAS)</span><span class="sxs-lookup"><span data-stu-id="426c4-102">Multidimensional Modeling (SSAS)</span></span>
  <span data-ttu-id="426c4-103">Analysis Services 多次元ソリューションは、複数のディメンションにわたるビジネス データの分析にキューブ構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="426c4-103">An Analysis Services multidimensional solution uses cube structures for analyzing business data across multiple dimensions.</span></span> <span data-ttu-id="426c4-104">多次元モードは Analysis Services の既定のサーバー モードです。</span><span class="sxs-lookup"><span data-stu-id="426c4-104">Multidimensional mode is the default server mode of Analysis Services.</span></span> <span data-ttu-id="426c4-105">OLAP データ用のクエリおよび計算エンジンが含まれており、パフォーマンスとスケーラブルなデータ要件のバランスをとるために MOLAP、ROLAP、および HOLAP ストレージ モードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="426c4-105">It includes a query and calculation engine for OLAP data, with MOLAP, ROLAP, and HOLAP storage modes to balance performance with scalable data requirements.</span></span> <span data-ttu-id="426c4-106">Analysis Services OLAP エンジンは、業界最高レベルの OLAP サーバーであり、さまざまな BI ツールに対応しています。</span><span class="sxs-lookup"><span data-stu-id="426c4-106">The Analysis Services OLAP engine is an industry leading OLAP server that works well with a broad range of BI tools.</span></span> <span data-ttu-id="426c4-107">ほとんどの Analysis Services 配置は、従来の OLAP サーバーとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="426c4-107">Most Analysis Services deployments are installed as classic OLAP servers.</span></span>  
  
## <a name="benefits-of-using-multidimensional-solutions"></a><span data-ttu-id="426c4-108">多次元ソリューションを使用する利点</span><span class="sxs-lookup"><span data-stu-id="426c4-108">Benefits of Using Multidimensional Solutions</span></span>  
 <span data-ttu-id="426c4-109">Analysis Services 多次元モデルを構築する主な理由は、ビジネス データに対するアドホック クエリのパフォーマンスを高めるためです。</span><span class="sxs-lookup"><span data-stu-id="426c4-109">The primary reason for building an Analysis Services multidimensional model is to achieve fast performance of ad hoc queries against business data.</span></span> <span data-ttu-id="426c4-110">多次元モデルは、注釈を設定して複雑なクエリ構築をサポートするように拡張できるキューブおよびディメンションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="426c4-110">A multidimensional model is composed of cubes and dimensions that can be annotated and extended to support complex query constructions.</span></span> <span data-ttu-id="426c4-111">BI 開発者は、高速な応答時間をサポートし、ビジネス レポートを作成するための 1 つのデータ ソースを提供するキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="426c4-111">BI developers create cubes to support fast response times, and to provide a single data source for business reporting.</span></span> <span data-ttu-id="426c4-112">組織のあらゆるレベルでビジネス インテリジェンスの重要性が増す中、分析データの単一のソースを持つことにより、相違点は完全には除去されないものの最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="426c4-112">Given the growing importance of business intelligence across all levels of an organization, having a single source of analytical data ensures that discrepancies are kept to a minimum, if not eliminated entirely.</span></span>  
  
 <span data-ttu-id="426c4-113">Analysis Services 多次元データベースを使用するもう 1 つの重要な利点は、Excel、Reporting Services、PerformancePoint などの一般的に使用される BI レポート ツール、およびカスタム アプリケーションやサード パーティ ソリューションとの統合です。</span><span class="sxs-lookup"><span data-stu-id="426c4-113">Another important benefit to using Analysis Services multidimensional databases is integration with commonly used BI reporting tools such as Excel, Reporting Services, and PerformancePoint, as well as custom applications and third-party solutions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="426c4-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="426c4-114">In This Section</span></span>  
 [<span data-ttu-id="426c4-115">多次元モデル ソリューション (SSAS)</span><span class="sxs-lookup"><span data-stu-id="426c4-115">Multidimensional Model Solutions &#40;SSAS&#41;</span></span>](multidimensional-model-solutions-ssas.md)  
  
 [<span data-ttu-id="426c4-116">多次元モデル データベース &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="426c4-116">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-model-databases-ssas.md)  
  
 [<span data-ttu-id="426c4-117">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="426c4-117">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="426c4-118">ロールと権限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="426c4-118">Roles and Permissions &#40;Analysis Services&#41;</span></span>](roles-and-permissions-analysis-services.md)  
  
 [<span data-ttu-id="426c4-119">多次元モデルの Power View</span><span class="sxs-lookup"><span data-stu-id="426c4-119">Power View for Multidimensional Models</span></span>](power-view-for-multidimensional-models.md)  
  
 [<span data-ttu-id="426c4-120">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="426c4-120">Multidimensional Model Assemblies Management</span></span>](multidimensional-model-assemblies-management.md)  
  
  
