---
title: Reporting Services クエリデザイナー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719461"
---
# <a name="reporting-services-query-designers"></a><span data-ttu-id="b8fe7-102">Reporting Services クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="b8fe7-102">Reporting Services Query Designers</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="b8fe7-103">にはグラフィカルおよびテキスト ベースのクエリ デザイナーが用意されており、レポートのデータ ソースの種類ごとにクエリを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-103">provides graphical and text-based query designers to help you build queries for each data source type in your report.</span></span>  
  
 <span data-ttu-id="b8fe7-104">一部のデータ ソースでは、クエリを対話形式で作成できるグラフィカル デザイナーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-104">Some data sources support graphical designers that help you build a query interactively.</span></span> <span data-ttu-id="b8fe7-105">その他のデータ ソースでは、テキスト ベースのクエリ デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-105">Other data sources use a text-based query designer.</span></span> <span data-ttu-id="b8fe7-106">グラフィカル クエリ デザイナーでは、データ ソースの基になるデータを表すメタデータ アイテムをクエリ デザイン画面にドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-106">By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface.</span></span> <span data-ttu-id="b8fe7-107">テキスト ベースのクエリ デザイナーでは、コマンド テキストをクエリ ペインに入力できます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-107">By using a text-based query designer, you can type command text into a query pane.</span></span> <span data-ttu-id="b8fe7-108">グラフィカル クエリ デザイナーからテキスト ベースのクエリ デザイナーに変更するには、ツール バーのテキスト ベースのクエリ デザイナー アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-108">You can change from a graphical query designer to a text-based query designer by clicking the text-based query designer icon on the toolbar.</span></span>  
  
 <span data-ttu-id="b8fe7-109">レポートで使用できるデータ ソースの種類は、クライアントまたはレポート サーバーにインストールされている [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] データ拡張機能によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-109">The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data extensions installed on your client or report server.</span></span> <span data-ttu-id="b8fe7-110">詳細については、「 [Rsreportdesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md)」と「 [rsreportserver 構成ファイル](report-server/rsreportserver-config-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-110">For more information, see [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) and [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="b8fe7-111">データ処理拡張機能および関連するクエリ デザイナーは、次のようにデータ ソースのサポートにおいて異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-111">A data processing extension and its associated query designer can differ in support for data sources in the following ways:</span></span>  
  
-   <span data-ttu-id="b8fe7-112">**クエリ デザイナーの種類。**</span><span class="sxs-lookup"><span data-stu-id="b8fe7-112">**By query designer type.**</span></span> <span data-ttu-id="b8fe7-113">たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースでは、グラフィカルとテキスト ベースの両方のクエリ デザイナーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-113">For example, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source supports both the graphical and text-based query designers.</span></span>  
  
-   <span data-ttu-id="b8fe7-114">**クエリ言語のバリエーション。**</span><span class="sxs-lookup"><span data-stu-id="b8fe7-114">**By query language variation.**</span></span> <span data-ttu-id="b8fe7-115">たとえば、 [!INCLUDE[tsql](../includes/tsql-md.md)] などのクエリ言語は、データ ソースの種類によって構文が異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-115">For example, a query language such as [!INCLUDE[tsql](../includes/tsql-md.md)] can differ in syntax depending on the data source type.</span></span> <span data-ttu-id="b8fe7-116">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 言語および Oracle SQL 言語には、クエリコマンドの構文のバリエーションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-116">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] language and the Oracle SQL language have some variation in syntax for a query command.</span></span>  
  
-   <span data-ttu-id="b8fe7-117">**データベース オブジェクト名のスキーマの部分に対するサポート。**</span><span class="sxs-lookup"><span data-stu-id="b8fe7-117">**By support for the schema part of a database object name.**</span></span> <span data-ttu-id="b8fe7-118">データ ソースでデータベース オブジェクト識別子の一部としてスキーマが使用されている場合、既定のスキーマを使用しない名前については、クエリにスキーマ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-118">When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema.</span></span> <span data-ttu-id="b8fe7-119">たとえば、`SELECT FirstName, LastName FROM [Person].[Person]` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-119">For example, `SELECT FirstName, LastName FROM [Person].[Person]`.</span></span>  
  
-   <span data-ttu-id="b8fe7-120">**クエリ パラメーターのサポート。**</span><span class="sxs-lookup"><span data-stu-id="b8fe7-120">**By support for query parameters.**</span></span> <span data-ttu-id="b8fe7-121">パラメーターのサポートは、データ プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-121">Data providers differ in support for parameters.</span></span> <span data-ttu-id="b8fe7-122">一部のデータ プロバイダーでは、 `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`のような名前付きパラメーターがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-122">Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span></span> <span data-ttu-id="b8fe7-123">また別のデータ プロバイダーでは、 `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`のような無名パラメーターがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-123">Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span></span> <span data-ttu-id="b8fe7-124">パラメーター識別子はデータ プロバイダーごとに異なります。たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では "アット" (@) 記号を使用し、Oracle ではコロン (:) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-124">The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses the "at" (@) symbol, Oracle uses the colon (:).</span></span> <span data-ttu-id="b8fe7-125">パラメーターがサポートされないデータ プロバイダーもあります。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-125">Some data providers do not support parameters.</span></span>  
  
-   <span data-ttu-id="b8fe7-126">**クエリをインポートする機能。**</span><span class="sxs-lookup"><span data-stu-id="b8fe7-126">**By ability to import queries.**</span></span> <span data-ttu-id="b8fe7-127">たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースの場合は、レポート定義ファイル (.rdl) または .sql ファイルからクエリをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-127">For example, for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source, you can import a query from a report definition file (.rdl) or from a .sql file.</span></span>  
  
## <a name="query-designers"></a><span data-ttu-id="b8fe7-128">クエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="b8fe7-128">Query Designers</span></span>  
 <span data-ttu-id="b8fe7-129">次のトピックでは、各クエリ デザイナーのユーザー インターフェイスについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="b8fe7-129">The following topics describe the user interface for each query designer.</span></span>  
  
-   [<span data-ttu-id="b8fe7-130">Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-130">Analysis Services MDX Query Designer User Interface</span></span>](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-131">Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-131">Analysis Services DMX Query Designer User Interface</span></span>](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-132">グラフィカル クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-132">Graphical Query Designer User Interface</span></span>](report-data/graphical-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-133">リレーショナル クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-133">Relational Query Designer User Interface</span></span>](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-134">Hyperion Essbase クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-134">Hyperion Essbase Query Designer User Interface</span></span>](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-135">レポート モデル クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-135">Report Model Query Designer User Interface</span></span>](report-data/report-model-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-136">SAP NetWeaver BI Query Designer のユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-136">SAP NetWeaver BI Query Designer User Interface</span></span>](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="b8fe7-137">SharePoint リストのクエリ デザイナー</span><span class="sxs-lookup"><span data-stu-id="b8fe7-137">SharePoint List Query Designer</span></span>](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [<span data-ttu-id="b8fe7-138">テキストベースのクエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8fe7-138">Text-based Query Designer User Interface</span></span>](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8fe7-139">参照</span><span class="sxs-lookup"><span data-stu-id="b8fe7-139">See Also</span></span>  
 <span data-ttu-id="b8fe7-140">[Reporting Services &#40;SSRS&#41;でサポートされるデータソース](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="b8fe7-140">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="b8fe7-141">[SSRS&#41;&#40;外部データソースからデータを追加する](report-data/add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b8fe7-141">[Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="b8fe7-142">[データ処理拡張機能と .NET Framework データプロバイダー &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b8fe7-142">[Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span></span>  
 [<span data-ttu-id="b8fe7-143">拡張機能 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b8fe7-143">Extensions &#40;SSRS&#41;</span></span>](extensions-ssrs.md)  
  
  
