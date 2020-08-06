---
title: SQL Server 2014 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
ms.openlocfilehash: c111bdadefeb508897538089ecb9d9a7b583d410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633645"
---
# <a name="sql-server-2014-analysis-services"></a><span data-ttu-id="e847e-102">SQL Server 2014 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="e847e-102">SQL Server 2014 Analysis Services</span></span>

  <span data-ttu-id="e847e-103">SQL Server 2014 Analysis Services は、意思決定支援およびビジネスインテリジェンス (BI) ソリューションで使用される分析データエンジンであり、Excel、Reporting Services レポート、その他のサードパーティ製 BI ツールなどのビジネスレポートとクライアントアプリケーションの分析データを提供します。</span><span class="sxs-lookup"><span data-stu-id="e847e-103">SQL Server 2014 Analysis Services is an analytical data engine used in decision support and business intelligence (BI) solutions, providing the analytical data for business reports and client applications such as Excel, Reporting Services reports, and other third-party BI tools.</span></span> 

## <a name="about-sql-server-analysis-services-documentation"></a><span data-ttu-id="e847e-104">SQL Server Analysis Services のドキュメントについて</span><span class="sxs-lookup"><span data-stu-id="e847e-104">About SQL Server Analysis Services documentation</span></span>

<span data-ttu-id="e847e-105">ドキュメントはバージョン別に分けられます。</span><span class="sxs-lookup"><span data-stu-id="e847e-105">Documentation is separated by version.</span></span> <span data-ttu-id="e847e-106">現在は SQL Server 2014 Analysis Services ドキュメントにあります。</span><span class="sxs-lookup"><span data-stu-id="e847e-106">You are currently in SQL Server 2014 Analysis Services documentation.</span></span>

- <span data-ttu-id="e847e-107">SQL Server 2012 以前の詳細については、 [SQL Server 前のバージョンのドキュメント](https://docs.microsoft.com/previous-versions/sql/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-107">To learn more about SQL Server 2012 and earlier, see [SQL Server previous versions documentation](https://docs.microsoft.com/previous-versions/sql/).</span></span>
- <span data-ttu-id="e847e-108">SQL Server 2014 の詳細については、 [SQL Server 2014 のオンラインブック](../index.yml)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-108">To learn more about SQL Server 2014, see [Books Online for SQL Server 2014](../index.yml)</span></span>
- <span data-ttu-id="e847e-109">SQL Server 2016 以降の詳細については、 [Analysis Services のドキュメント](https://docs.microsoft.com/analysis-services/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-109">To learn more about SQL Server 2016 and later, see [Analysis Services documentation](https://docs.microsoft.com/analysis-services/).</span></span>
- <span data-ttu-id="e847e-110">Azure Analysis Services の詳細については、 [Azure Analysis Services のドキュメント](https://docs.microsoft.com/azure/analysis-services/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-110">To learn more about Azure Analysis Services, see [Azure Analysis Services Documentation](https://docs.microsoft.com/azure/analysis-services/).</span></span>

## <a name="analysis-services-workflow"></a><span data-ttu-id="e847e-111">Analysis Services ワークフロー</span><span class="sxs-lookup"><span data-stu-id="e847e-111">Analysis Services workflow</span></span>

<span data-ttu-id="e847e-112">一般的なワークフローには、OLAP または表形式のデータモデルを構築し、そのモデルをデータベースとしてサーバーインスタンスに配置し、データを読み込むようにデータベースを処理してから、データアクセスを許可する権限を割り当てることがあります。</span><span class="sxs-lookup"><span data-stu-id="e847e-112">A typical workflow includes building an OLAP or tabular data model, deploy the model as a database to a server instance, process the database to load it with data, and then assign permissions to allow data access.</span></span> <span data-ttu-id="e847e-113">準備が完了すると、複数の用途を持つこのデータ モデルに、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をデータ ソースとしてサポートしている任意のクライアント アプリケーションがアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e847e-113">When it's ready to go, this multi-purpose data model can be accessed by any client application supporting [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] as a data source.</span></span>  
  
 <span data-ttu-id="e847e-114">モデルを作成するには、SQL Server Data Tools を使用します (「 [Analysis Services で使用されるツールとアプリケーション](tools-and-applications-used-in-analysis-services.md)」を参照)。表形式または多次元およびデータマイニングプロジェクトテンプレートのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e847e-114">To create a model, use SQL Server Data Tools (see [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md)), choosing either a Tabular or Multidimensional and Data Mining project template.</span></span> <span data-ttu-id="e847e-115">プロジェクト テンプレートには、モデルで必要とされるすべてのオブジェクトのフォルダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e847e-115">The project template contains folders for all of the objects needed in a model.</span></span> <span data-ttu-id="e847e-116">ウィザードを使用して、データ ソース、データ ソース ビュー、ディメンション、キューブ、ロールなど、すべての基本的な要素を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e847e-116">You can use wizards to create all of the basic elements, such as data sources, data source views, dimensions, cubes, and roles.</span></span>  
  
 <span data-ttu-id="e847e-117">モデルは、外部データ システムから取得したデータによって作成されます。通常は外部データ システムとして、SQL Server または Oracle リレーショナル データベース エンジンでホストされているデータ ウェアハウスを使用します (テーブル モデルでは、追加のデータ ソースの種類もサポートされています)。</span><span class="sxs-lookup"><span data-stu-id="e847e-117">Models are populated with data from external data systems, usually data warehouses hosted on a SQL Server or Oracle relational database engine (Tabular models support additional data source types).</span></span> <span data-ttu-id="e847e-118">モデルは、キューブなどのクエリ オブジェクトを指定しますが、複数のキューブ、計算、KPI (ビジネス ロジック、ナビゲーションやドリルスルー動作などの相互作用をカプセル化する) で使用できるディメンションも指定します。</span><span class="sxs-lookup"><span data-stu-id="e847e-118">Models specify query objects, such as cubes, but also specify dimensions that can be used in multiple cubes, calculations and KPIs that encapsulate business logic, and interactions such as navigation and drill-through behaviors.</span></span>  
  
 <span data-ttu-id="e847e-119">モデルを使用するには、特定のサーバーモードでデータベースを実行するサーバーインスタンスに配置します。これにより、Excel または他のアプリケーションを介して接続する承認されたユーザーがデータを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e847e-119">To use a model, it's deployed to a server instance that runs databases in a particular server mode, making the data available to authorized users who connect through Excel or other applications.</span></span>  
  
 <span data-ttu-id="e847e-120">インスタンスは、次の3つのサーバーモードのいずれかでインストールできます。</span><span class="sxs-lookup"><span data-stu-id="e847e-120">You can install an instance in one of three server modes:</span></span>  
  
-   <span data-ttu-id="e847e-121">テーブル インスタンスとしてインストールし、テーブル モデルを実行します。</span><span class="sxs-lookup"><span data-stu-id="e847e-121">As a Tabular instance, running Tabular models.</span></span>  
  
-   <span data-ttu-id="e847e-122">多次元およびデータ マイニングのインスタンスとしてインストールし、OLAP キューブとデータ マイニング モデルを実行します (既定)。</span><span class="sxs-lookup"><span data-stu-id="e847e-122">As a Multidimensional and Data Mining instance, running OLAP cubes and data mining models (this is the default).</span></span>  
  
-   <span data-ttu-id="e847e-123">PowerPivot for SharePoint としてインストールし、SharePoint 上で PowerPivot と Excel データ モデルを実行します (PowerPivot for SharePoint は中間層のデータ エンジンであり、SharePoint でホストされているデータ モデルの読み込み、クエリ、更新を実行します)。</span><span class="sxs-lookup"><span data-stu-id="e847e-123">As PowerPivot for SharePoint, running PowerPivot and Excel data models in SharePoint (PowerPivot for SharePoint is a middle-tier data engine that loads, queries, and refreshes data models hosted in SharePoint).</span></span>  
  
 <span data-ttu-id="e847e-124">同じデータ エンジンを、3 つの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e847e-124">Same data engine; three different ways to use it.</span></span> <span data-ttu-id="e847e-125">サーバー モードはインストール中に設定され、後で変更できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-125">Note that server modes are set during installation and cannot be changed later.</span></span> <span data-ttu-id="e847e-126">別のモードが必要な場合は、新しいインスタンスをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e847e-126">You should install a new instance if you require a different mode.</span></span>  
  
 <span data-ttu-id="e847e-127">Analysis Services に関する基本ドキュメントは、作成するプロジェクトの種類に対応するセクション別に分類されます。</span><span class="sxs-lookup"><span data-stu-id="e847e-127">Foundational documentation for Analysis Services is organized into sections that correspond to the type of project you are building.</span></span> <span data-ttu-id="e847e-128">それぞれのモードまたは機能領域の詳細については、次のリンクから選択してください。</span><span class="sxs-lookup"><span data-stu-id="e847e-128">Choose from the following links to learn more about each mode or feature area.</span></span>  
  
 <span data-ttu-id="e847e-129">**領域ごとのコンテンツの参照**</span><span class="sxs-lookup"><span data-stu-id="e847e-129">**Browse Content by Area**</span></span>  
 <span data-ttu-id="e847e-130">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [SSAS&#41;&#40;テーブルソリューションと多次元ソリューションの比較](comparing-tabular-and-multidimensional-solutions-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-130">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)</span></span>  
  
 <span data-ttu-id="e847e-131">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [Analysis Services インスタンス管理](instances/analysis-services-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-131">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Analysis Services Instance Management](instances/analysis-services-instance-management.md)</span></span>  
  
 <span data-ttu-id="e847e-132">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テーブルモデリング &#40;SSAS 表形式&#41;](tabular-models/tabular-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-132">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Tabular Modeling &#40;SSAS Tabular&#41;](tabular-models/tabular-models-ssas.md)</span></span>  
  
 <span data-ttu-id="e847e-133">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[多次元モデリング &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-133">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Multidimensional Modeling &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span></span>  
  
 <span data-ttu-id="e847e-134">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[データマイニング &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-134">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span></span>  
  
 <span data-ttu-id="e847e-135">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="e847e-135">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="e847e-136">の機能は、エディションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e847e-136">features vary by edition.</span></span> <span data-ttu-id="e847e-137">多次元およびデータ マイニング モデルは Standard Edition で使用できますが、上位エディションに比べると機能が少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="e847e-137">Multidimensional and data mining models are available in standard edition, but with fewer features than higher editions.</span></span> <span data-ttu-id="e847e-138">テーブル モデルと PowerPivot for SharePoint はプレミアム機能であり、Standard Edition のライセンスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e847e-138">Tabular models and PowerPivot for SharePoint are premium features and are not available in a standard edition license.</span></span> <span data-ttu-id="e847e-139">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e847e-139">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e847e-140">参照</span><span class="sxs-lookup"><span data-stu-id="e847e-140">See Also</span></span>  
 <span data-ttu-id="e847e-141">[Analysis Services チュートリアル &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="e847e-141">[Analysis Services Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span></span>  
 <span data-ttu-id="e847e-142">[SQL Server 2014 のインストール](../database-engine/install-windows/installation-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e847e-142">[Installation for SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md) </span></span>  
 <span data-ttu-id="e847e-143">[開発者ガイド &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="e847e-143">[Developer's Guide &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="e847e-144">[SQL Server リソースセンター](https://go.microsoft.com/fwlink/?linkID=219676) </span><span class="sxs-lookup"><span data-stu-id="e847e-144">[SQL Server Resource Center](https://go.microsoft.com/fwlink/?linkID=219676) </span></span>  
 [<span data-ttu-id="e847e-145">SQLCat.com</span><span class="sxs-lookup"><span data-stu-id="e847e-145">SQLCat.com</span></span>](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
