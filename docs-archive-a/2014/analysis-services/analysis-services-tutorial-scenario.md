---
title: Analysis Services チュートリアルのシナリオ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2f5b1a42-b814-4d7d-b603-5383d9ac66b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: add9065990881ea4629b34e37ca84831de4b87c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633650"
---
# <a name="analysis-services-tutorial-scenario"></a><span data-ttu-id="eff5d-102">Analysis Services のチュートリアル シナリオ</span><span class="sxs-lookup"><span data-stu-id="eff5d-102">Analysis Services Tutorial Scenario</span></span>
  <span data-ttu-id="eff5d-103">このチュートリアルには、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]という架空の会社が登場します。</span><span class="sxs-lookup"><span data-stu-id="eff5d-103">This tutorial is based on [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], a fictitious company.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="eff5d-104">は、特殊合金自転車を北米、ヨーロッパ、およびアジアの市場に供給する大規模な多国籍製造会社です。</span><span class="sxs-lookup"><span data-stu-id="eff5d-104">is a large, multinational manufacturing company that produces and distributes metal and composite bicycles to commercial markets in North America, Europe, and Asia.</span></span> <span data-ttu-id="eff5d-105">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] はワシントン州のボセルに本社を置き、500 名の従業員を抱えています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-105">The headquarters for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is Bothell, Washington, where the company employs 500 workers.</span></span> <span data-ttu-id="eff5d-106">さらに、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の各市場には、その地域を担当する販売チームがいます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-106">Additionally, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] employs several regional sales teams throughout its market base.</span></span>  
  
 <span data-ttu-id="eff5d-107">近年、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、メキシコの小さな製造工場 Importadores Neptuno を買収しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-107">In recent years, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] bought a small manufacturing plant, Importadores Neptuno, which is located in Mexico.</span></span> <span data-ttu-id="eff5d-108">Importadores Neptuno は、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の生産ラインにおけるいくつかの重要な部品を製造しています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-108">Importadores Neptuno manufactures several critical subcomponents for the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] product line.</span></span> <span data-ttu-id="eff5d-109">これらの部品はボセルに出荷され、そこで完成品が組み立てられます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-109">These subcomponents are shipped to the Bothell location for final product assembly.</span></span> <span data-ttu-id="eff5d-110">2005 年、同社は、ツーリング自転車製品群を独占的に製造、流通する企業に成長しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-110">In 2005, Importadores Neptuno became the sole manufacturer and distributor of the touring bicycle product group.</span></span>  
  
 <span data-ttu-id="eff5d-111">好調なこの年に続き、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、対象顧客を絞って広告を打ち、Web サイトを通じた製品販売も開始することで、市場シェアをさらに拡大しようとしています。同時に、製造コストを抑え、最終的には販売コストを削減することも同社の目標の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="eff5d-111">Following a successful fiscal year, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] now wants to broaden its market share by targeting advertising to its best customers, extending product availability through an external Web site, and reducing the cost of sales by reducing production costs.</span></span>  
  
## <a name="current-analysis-environment"></a><span data-ttu-id="eff5d-112">現在の分析環境</span><span class="sxs-lookup"><span data-stu-id="eff5d-112">Current Analysis Environment</span></span>  
 <span data-ttu-id="eff5d-113">Adventure Works Cycles では、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズに対応するため、トランザクション データ (取引データ) は [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] データベースから取り出し、販売量などの非トランザクション データはスプレッドシートから取り出して、これらの情報を **AdventureWorksDW2012** と呼ばれるリレーショナル データ ウェアハウスに統合しています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-113">To support the data analysis needs of the sales and marketing teams and of senior management, the company currently takes transactional data from the [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] database, and non-transactional information such as sales quotas from spreadsheets, and consolidates this information into the **AdventureWorksDW2012** relational data warehouse.</span></span> <span data-ttu-id="eff5d-114">しかし、リレーショナル データ ウェアハウスには次の問題があります。</span><span class="sxs-lookup"><span data-stu-id="eff5d-114">However, the relational data warehouse presents the following challenges:</span></span>  
  
-   <span data-ttu-id="eff5d-115">レポートが静的である。</span><span class="sxs-lookup"><span data-stu-id="eff5d-115">Reports are static.</span></span> <span data-ttu-id="eff5d-116">[!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel のピボット テーブルなどと違い、データをインタラクティブに操作してレポートを生成できないので、詳細情報を取得できません。</span><span class="sxs-lookup"><span data-stu-id="eff5d-116">Users have no way to interactively explore the data in the reports to obtain more detailed information, such as they could do with a [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel pivot table.</span></span> <span data-ttu-id="eff5d-117">既存の定義済みレポートで十分な情報を得られるユーザーも多いのですが、インタラクティブなクエリと専門的なレポートを使用する上級ユーザーは、データベースに直接クエリを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eff5d-117">Although the existing set of predefined reports is sufficient for many users, more advanced users need direct query access to the database for interactive queries and specialized reports.</span></span> <span data-ttu-id="eff5d-118">ただし、 **AdventureWorksDW2012**データベースが複雑になるため、効果的なクエリの作成方法を習得するのに時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="eff5d-118">However, because of the complexity of the **AdventureWorksDW2012** database, too much time is needed for such users to learn how to create effective queries.</span></span>  
  
-   <span data-ttu-id="eff5d-119">クエリ パフォーマンスの落差が大きい。</span><span class="sxs-lookup"><span data-stu-id="eff5d-119">Query performance is widely variable.</span></span> <span data-ttu-id="eff5d-120">たとえば、クエリによって、結果が数秒で返される場合と、数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eff5d-120">For example, some queries return results very quickly, in only a few seconds, while other queries take several minutes to return.</span></span>  
  
-   <span data-ttu-id="eff5d-121">集計テーブルの管理が難しい。</span><span class="sxs-lookup"><span data-stu-id="eff5d-121">Aggregate tables are difficult to manage.</span></span> <span data-ttu-id="eff5d-122">クエリの応答時間を短縮するため、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] のデータ ウェアハウス チームは、 **AdventureWorksDW2012** データベースにいくつかの集計テーブルを作成しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-122">In an attempt to improve query response times, the data warehouse team at [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] built several aggregate tables in the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="eff5d-123">たとえば、月ごとの売上を要約するテーブルなどです。</span><span class="sxs-lookup"><span data-stu-id="eff5d-123">For example, they built a table that summarizes sales by month.</span></span> <span data-ttu-id="eff5d-124">これらの集計テーブルはクエリ パフォーマンスを非常に向上させますが、テーブルを保守するために構築したインフラストラクチャは時間の経過と共に劣化し、エラーを招きます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-124">However, while these aggregate tables greatly improve query performance, the infrastructure that they built to maintain the tables over time is fragile and prone to errors.</span></span>  
  
-   <span data-ttu-id="eff5d-125">複雑な計算ロジックがレポート定義に組み込まれているため、レポート間での計算ロジックの共有が困難。</span><span class="sxs-lookup"><span data-stu-id="eff5d-125">Complex calculation logic is buried in report definitions and is difficult to share between reports.</span></span> <span data-ttu-id="eff5d-126">このビジネス ロジックはレポートごとに個別に生成されるため、概要情報がレポートごとに異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eff5d-126">Because this business logic is generated separately for each report, summary information sometimes is different between reports.</span></span> <span data-ttu-id="eff5d-127">したがって、データ ウェアハウスのレポートでは管理の信頼性が限られます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-127">Therefore, management has limited confidence in the data warehouse reports.</span></span>  
  
-   <span data-ttu-id="eff5d-128">必要となるデータ ビューが事業部によって異なる。</span><span class="sxs-lookup"><span data-stu-id="eff5d-128">Users in different business units are interested in different views of the data.</span></span> <span data-ttu-id="eff5d-129">各グループとは無関係なデータ要素によって情報が散漫になり、混乱を招きます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-129">Each group is distracted and confused by data elements that are irrelevant to them.</span></span>  
  
-   <span data-ttu-id="eff5d-130">専門的なレポートを必要とするユーザーにとって、計算ロジックが高いハードルとなる。</span><span class="sxs-lookup"><span data-stu-id="eff5d-130">Calculation logic is particularly challenging for users who need specialized reports.</span></span> <span data-ttu-id="eff5d-131">専門的なレポートを生成する場合は、レポートごとに計算ロジックを定義する必要があります。計算ロジックの定義方法を一本化することはできません。</span><span class="sxs-lookup"><span data-stu-id="eff5d-131">Because such users must define the calculation logic separately for each report, there is no centralized control over how the calculation logic is defined.</span></span> <span data-ttu-id="eff5d-132">たとえば、移動平均など、基本的な統計手法を使用すればよいことがわかっていても、その計算式の作成方法を理解していなければ、必要なレポートを生成できません。</span><span class="sxs-lookup"><span data-stu-id="eff5d-132">For example, some users know that they should use basic statistical techniques such as moving averages, but they do not know how to construct such calculations and so do not use these techniques.</span></span>  
  
-   <span data-ttu-id="eff5d-133">関連する情報のセットを組み合わせることが困難。</span><span class="sxs-lookup"><span data-stu-id="eff5d-133">It is difficult to combine related sets of information.</span></span> <span data-ttu-id="eff5d-134">売上と販売量など、関連する 2 つの情報を組み合わせる特殊なクエリを作成することは、ビジネス ユーザーにとっては困難です。</span><span class="sxs-lookup"><span data-stu-id="eff5d-134">Specialized queries that combine two sets of related information, such as sales and sales quotas, are difficult for business users to construct.</span></span> <span data-ttu-id="eff5d-135">このようなクエリはデータベースに大きい負荷をかけるため、Adventure Works Cycles のユーザーは、複数分野のデータのセットをデータ ウェアハウス チームに要求しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="eff5d-135">Such queries overwhelmed the database, so the company requires that users request cross-subject-area sets of data from the data warehouse team.</span></span> <span data-ttu-id="eff5d-136">結果として、複数の分野のデータを組み合わせた、少数の定義済みレポートを定義するのみになっています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-136">As a result, only a handful of predefined reports have been defined that combine data from multiple subject areas.</span></span> <span data-ttu-id="eff5d-137">また、これらのレポートは複雑であるため、ユーザーはレポートに手を加えることを敬遠しています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-137">Additionally, users are reluctant to try to modify these reports because of their complexity.</span></span>  
  
-   <span data-ttu-id="eff5d-138">レポートの仕様が、主に米国のビジネス情報に合わせられている。</span><span class="sxs-lookup"><span data-stu-id="eff5d-138">Reports are focused primarily on business information in the United States.</span></span> <span data-ttu-id="eff5d-139">米国外の子会社のユーザーはこの仕様に大きな不満を持っており、自国の通貨単位および言語でレポートを表示したいという要望を持っています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-139">Users in the non-U.S. subsidiaries are very dissatisfied with this focus, and want to be able to view reports in different currencies and different languages.</span></span>  
  
-   <span data-ttu-id="eff5d-140">情報の監査が難しい。</span><span class="sxs-lookup"><span data-stu-id="eff5d-140">Information is difficult to audit.</span></span> <span data-ttu-id="eff5d-141">現在、経理部門は、一括クエリを行うためのデータ ソースとしてのみ **AdventureWorksDW2012** データベースを使用しています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-141">The Finance department currently uses the **AdventureWorksDW2012** database only as a source of data from which to query in bulk.</span></span> <span data-ttu-id="eff5d-142">その後、各スプレッドシートにデータがダウンロードされ、スプレッドシートの準備と操作に膨大な時間が費やされます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-142">They then download the data into individual spreadsheets, and spend significant time preparing the data and manipulating the spreadsheets.</span></span> <span data-ttu-id="eff5d-143">したがって、経理レポートの準備、監査、および全社的な管理が困難です。</span><span class="sxs-lookup"><span data-stu-id="eff5d-143">The corporate financial reports are therefore difficult to prepare, audit, and manage across the company.</span></span>  
  
## <a name="the-solution"></a><span data-ttu-id="eff5d-144">解決策</span><span class="sxs-lookup"><span data-stu-id="eff5d-144">The Solution</span></span>  
 <span data-ttu-id="eff5d-145">先ごろ、データ ウェアハウス チームは、現在の分析システムの設計を再評価しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-145">The data warehouse team recently performed a design review of the current analysis system.</span></span> <span data-ttu-id="eff5d-146">この評価には、現在の問題点と今後の要望のずれを調査するギャップ分析も含まれています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-146">The review included a gap analysis of current issues and future demands.</span></span> <span data-ttu-id="eff5d-147">データ ウェアハウス チームは、 **AdventureWorksDW2012** データベースが適切なディメンションと代理キーを持つ優れた設計のディメンショナル データベースであると判断しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-147">The data warehouse team determined that the **AdventureWorksDW2012** database is a well-designed dimensional database with conformed dimensions and surrogate keys.</span></span> <span data-ttu-id="eff5d-148">適切なディメンションにより、時間ディメンションや製品ディメンションなど複数のデータ マートでディメンションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-148">Conformed dimensions enable a dimension to be used in multiple data marts, such as a time dimension or a product dimension.</span></span> <span data-ttu-id="eff5d-149">代理キーは、ディメンションとファクト テーブルをリンクする擬似的なキーです。一意性を確保し、パフォーマンスを向上させるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-149">Surrogate keys are artificial keys that link dimension and fact tables and that are used to ensure uniqueness and to improve performance.</span></span> <span data-ttu-id="eff5d-150">また、 **AdventureWorksDW2012** データベースでベース テーブルの読み込みと管理を行う分には、現在のところ大きな問題はないと判断しました。</span><span class="sxs-lookup"><span data-stu-id="eff5d-150">Moreover, the data warehouse team determined that there currently are no significant problems with the loading and management of the base tables in the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="eff5d-151">このため、を使用して次のことを行うことが決定されました [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eff5d-151">The team has therefore decided to use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to accomplish the following:</span></span>  
  
-   <span data-ttu-id="eff5d-152">分析的な調査やレポート生成では、共通のメタデータ層を経由するようデータへのアクセス経路を統合する。</span><span class="sxs-lookup"><span data-stu-id="eff5d-152">Provide unified data access through a common metadata layer for analytical analysis and reporting.</span></span>  
  
-   <span data-ttu-id="eff5d-153">ユーザーのデータ表示を簡略化し、対話型のクエリ、定義済みクエリ、および定義済みレポートの開発効率を向上させる。</span><span class="sxs-lookup"><span data-stu-id="eff5d-153">Simplify users' view of data, speeding the development of both interactive and predefined queries and predefined reports.</span></span>  
  
-   <span data-ttu-id="eff5d-154">複数の分野のデータを組み合わせたクエリを適切に作成する。</span><span class="sxs-lookup"><span data-stu-id="eff5d-154">Correctly construct queries that combine data from multiple subject areas.</span></span>  
  
-   <span data-ttu-id="eff5d-155">集計を管理する。</span><span class="sxs-lookup"><span data-stu-id="eff5d-155">Manage aggregates.</span></span>  
  
-   <span data-ttu-id="eff5d-156">複雑な計算を保存し、再利用できるようにする。</span><span class="sxs-lookup"><span data-stu-id="eff5d-156">Store and reuse complex calculations.</span></span>  
  
-   <span data-ttu-id="eff5d-157">米国外のビジネス ユーザーにローカライズされたサービスを提供する。</span><span class="sxs-lookup"><span data-stu-id="eff5d-157">Present a localized experience to business users outside the United States.</span></span>  
  
 <span data-ttu-id="eff5d-158">Analysis Services チュートリアルのレッスンには、これらのすべての目標に適したキューブ データベースを構築するためのガイダンスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eff5d-158">The lessons in the Analysis Services tutorial provide guidance in building a cube database that meets all of these goals.</span></span> <span data-ttu-id="eff5d-159">まず、「 [レッスン 1: 新しいテーブル モデル プロジェクトの作成](lesson-1-create-a-new-tabular-model-project.md)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="eff5d-159">To get started, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff5d-160">参照</span><span class="sxs-lookup"><span data-stu-id="eff5d-160">See Also</span></span>  
 [<span data-ttu-id="eff5d-161">多次元モデリング (Adventure Works チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="eff5d-161">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  