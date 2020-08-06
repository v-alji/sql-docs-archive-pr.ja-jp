---
title: テーブルモデリング (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44f358f0f36e84ad903a0a4fcb0203291019e7aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634067"
---
# <a name="tabular-modeling-ssas-tabular"></a><span data-ttu-id="108be-102">テーブル モデリング (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="108be-102">Tabular Modeling (SSAS Tabular)</span></span>
  <span data-ttu-id="108be-103">表形式のモデルは、Analysis Services のメモリ内データベースです。</span><span class="sxs-lookup"><span data-stu-id="108be-103">Tabular models are in-memory databases in Analysis Services.</span></span> <span data-ttu-id="108be-104">xVelocity メモリ内分析エンジン (VertiPaq) は、最新の圧縮アルゴリズムとマルチスレッド クエリ プロセッサを使用して、Microsoft Excel や Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのレポート クライアント アプリケーションによる、表形式のモデルのオブジェクトとデータへの高速アクセスを実現します。</span><span class="sxs-lookup"><span data-stu-id="108be-104">Using state-of-the-art compression algorithms and multi-threaded query processor, the xVelocity in-memory analytics engine (VertiPaq) delivers fast access to tabular model objects and data by reporting client applications such as Microsoft Excel and Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
 <span data-ttu-id="108be-105">表形式のモデルは、キャッシュ モードおよび DirectQuery モードの 2 つのモードによるデータ アクセスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="108be-105">Tabular models support data access through two modes: Cached mode and DirectQuery mode.</span></span> <span data-ttu-id="108be-106">キャッシュ モードでは、リレーショナル データベース、データ フィード、フラット テキスト ファイルなどの複数のソースからのデータを統合できます。</span><span class="sxs-lookup"><span data-stu-id="108be-106">In cached mode, you can integrate data from multiple sources including relational databases, data feeds, and flat text files.</span></span> <span data-ttu-id="108be-107">DirectQuery モードでは、メモリ内モデルをバイパスでき、クライアント アプリケーションはデータを (SQL Server リレーショナル) ソースで直接クエリできます。</span><span class="sxs-lookup"><span data-stu-id="108be-107">In DirectQuery mode, you can bypass the in-memory model, allowing client applications to query data directly at the (SQL Server relational) source.</span></span>  
  
 <span data-ttu-id="108be-108">表形式のモデルは、新しい表形式モデル プロジェクトのテンプレートを使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成されます。</span><span class="sxs-lookup"><span data-stu-id="108be-108">Tabular models are authored in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] using new tabular model project templates.</span></span> <span data-ttu-id="108be-109">複数のソースからデータをインポートしてから、リレーションシップ、計算列、メジャー、KPI、および階層を追加すると、階層モデルを拡充できます。</span><span class="sxs-lookup"><span data-stu-id="108be-109">You can import data from multiple sources, and then enrich the model by adding relationships, calculated columns, measures, KPIs, and hierarchies.</span></span> <span data-ttu-id="108be-110">モデルは、クライアント レポート アプリケーションの接続先の Analysis Services のインスタンスに配置できます。</span><span class="sxs-lookup"><span data-stu-id="108be-110">Models can then be deployed to an instance of Analysis Services where client reporting applications can connect to them.</span></span> <span data-ttu-id="108be-111">配置済みのモデルは、SQL Server Management Studio で多次元モデルのように管理できます。</span><span class="sxs-lookup"><span data-stu-id="108be-111">Deployed models can be managed in SQL Server Management Studio just like multidimensional models.</span></span> <span data-ttu-id="108be-112">また、最適処理のためにパーティション分割したり、ロール ベースのセキュリティを使用して行レベルに保護したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="108be-112">They can also be partitioned for optimized processing and secured to the row-level by using role based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="108be-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="108be-113">In This Section</span></span>  
 [<span data-ttu-id="108be-114">テーブル モデル ソリューション &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="108be-114">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
 [<span data-ttu-id="108be-115">表形式モデルのデータベース (SSAS 表形式)</span><span class="sxs-lookup"><span data-stu-id="108be-115">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-model-databases-ssas-tabular.md)  
  
 [<span data-ttu-id="108be-116">テーブル モデル データ アクセス</span><span class="sxs-lookup"><span data-stu-id="108be-116">Tabular Model Data Access</span></span>](tabular-model-data-access.md)  
  
  
