---
title: 外部データ ソースのデータを追加する (SSRS)
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 04/27/2017
ms.openlocfilehash: 1f1df02d99ebbf21ba7e769f3704aebdbb29cc40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631598"
---
# <a name="add-data-from-external-data-sources-ssrs"></a><span data-ttu-id="55f39-102">外部データ ソースのデータを追加する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="55f39-102">Add Data from External Data Sources (SSRS)</span></span>

<span data-ttu-id="55f39-103">外部データ ソースからデータを取得するには、データ接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="55f39-103">To retrieve data from an external data source, you use a data connection.</span></span> <span data-ttu-id="55f39-104">データ接続情報は、通常は権限の付与と使用する資格情報の指定を担う外部データ ソースの所有者によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-104">Data connection information is usually provided by the owner of the external data source, who is responsible for granting permissions and specifying which types of credentials to use.</span></span> <span data-ttu-id="55f39-105">データ接続情報は、レポート データ ソースとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-105">Data connection information is saved as a report data source.</span></span> <span data-ttu-id="55f39-106">データ ソースの種類により、データの取得に使用するデータ拡張機能が決まります。</span><span class="sxs-lookup"><span data-stu-id="55f39-106">The data source type specifies which data extension to use to retrieve the data.</span></span>  

##  <a name="understanding-data-access-technology"></a><a name="DataAccess"></a><span data-ttu-id="55f39-107">データアクセステクノロジについて</span><span class="sxs-lookup"><span data-stu-id="55f39-107">Understanding Data Access Technology</span></span>  

<span data-ttu-id="55f39-108">レポート データセットのデータを取得するには、複数のレイヤーにわたるデータ アクセス ソフトウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="55f39-108">To retrieve data for a report dataset requires multiple layers of data access software.</span></span> <span data-ttu-id="55f39-109">以下に、データ アクセス テクノロジによるレポートのしくみを簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-109">The following list provides a simple description of how reports work with data access technologies:</span></span>  

-   <span data-ttu-id="55f39-110">**アプリケーションとユーザー インターフェイス** データ ソースの作成、共有データ ソースへの参照の追加、共有データセットの追加、依存先のデータ ソースおよびデータセットを含むレポート パーツの追加などに使用する、レポート ビルダー アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="55f39-110">**Application and user interface** The Report Builder application that you use to create a data source, add a reference to a shared data source, add a shared dataset, or add a report part that includes the data sources and datasets that it depends on..</span></span>  

-   <span data-ttu-id="55f39-111">**レポート定義要素** データ ソースとデータセットは、レポート定義の一部です。</span><span class="sxs-lookup"><span data-stu-id="55f39-111">**Report definition elements** Data sources and datasets are part of the report definition.</span></span> <span data-ttu-id="55f39-112">レポートをレポート サーバーにパブリッシュすると、共有データ ソースと共有データセットはレポート定義から独立して管理されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-112">After a report is published to a report server, shared data sources and shared datasets are managed independently from the report definition.</span></span>  

  -   <span data-ttu-id="55f39-113">**データ ソースと共有データ ソース** データ処理拡張機能の種類、接続情報、および認証に関する情報を含む、レポート定義の一部です。</span><span class="sxs-lookup"><span data-stu-id="55f39-113">**Data source and Shared data source** Part of a report definition that includes the information about the type of data processing extension, the connection information, and the authentication.</span></span>  

  -   <span data-ttu-id="55f39-114">**データセットとフィールド コレクション** クエリ、フィールド コレクション、およびフィールドのデータ型を含む、レポート定義の一部です。</span><span class="sxs-lookup"><span data-stu-id="55f39-114">**Dataset and field collection** Part of a report definition that includes the query, the field collection, and the field data types.</span></span>  

-   <span data-ttu-id="55f39-115">**Reporting Services データ拡張機能** レポート ビルダーと共にインストールされる、組み込みのデータ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="55f39-115">**Reporting Services data extensions** Built-in data extensions that are installed with Report Builder.</span></span> <span data-ttu-id="55f39-116">データ拡張機能は、認証、サーバー集計値、および複数値パラメーターを処理する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="55f39-116">A data extension provides functionality that handles authentication, server aggregates, and multi-value parameters.</span></span>  

-   <span data-ttu-id="55f39-117">**データ プロバイダー** 外部データ ソースとの接続およびデータの取得を管理するソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="55f39-117">**Data provider** The software that manages the connection and retrieval of data from the external data source.</span></span> <span data-ttu-id="55f39-118">データ プロバイダーは、接続文字列の構文を定義します。</span><span class="sxs-lookup"><span data-stu-id="55f39-118">The data provider defines the connection string syntax.</span></span> <span data-ttu-id="55f39-119">ほとんどのデータ拡張機能は、データ プロバイダー レイヤーの上位に構築されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-119">Most data extensions are built on top of a data provider layer.</span></span>  

-   <span data-ttu-id="55f39-120">**外部データ ソース** データベース、ファイル、キューブ、Web サービスなど、レポート データの取得先です。</span><span class="sxs-lookup"><span data-stu-id="55f39-120">**External data source** Where to retrieve report data from, for example, a database, a file, a cube, or a Web service.</span></span>  

> [!NOTE]  
>  <span data-ttu-id="55f39-121">レポート サーバーに接続していないときは、レポート ビルダーと共にインストールされたデータ拡張機能を選択できます。</span><span class="sxs-lookup"><span data-stu-id="55f39-121">When you are not connected to a report server, you can choose from data extensions that are installed with Report Builder.</span></span> <span data-ttu-id="55f39-122">データには、使用しているコンピューターの資格情報を使用して、シングル ユーザーとしてアクセスします。</span><span class="sxs-lookup"><span data-stu-id="55f39-122">You access the data as a single user using credentials from your computer.</span></span> <span data-ttu-id="55f39-123">レポート サーバーに接続しているときは、レポート サーバーにインストールされているデータ拡張機能を選択できます。</span><span class="sxs-lookup"><span data-stu-id="55f39-123">When you are connected to a report server, you can choose from data extensions that are installed on the report server.</span></span> <span data-ttu-id="55f39-124">データには、レポートを実行する複数のユーザーの 1 人としてアクセスし、レポート サーバー上の資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="55f39-124">You access the data as one of multiple users who run the report and you are using credentials on the report server.</span></span> <span data-ttu-id="55f39-125">詳細については、「 [レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55f39-125">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  

##  <a name="understanding-report-data"></a><a name="ReportData"></a> <span data-ttu-id="55f39-126">レポート データについて</span><span class="sxs-lookup"><span data-stu-id="55f39-126">Understanding Report Data</span></span>  
<span data-ttu-id="55f39-127">簡単に言うと、レポートでは、レポート データセットのデータがレポート ページのデータ領域に表示されます。このデータ領域は、単一のテーブル、グラフ、マトリックス、またはその他の種類のレポート データ領域です。</span><span class="sxs-lookup"><span data-stu-id="55f39-127">In its simplest form, a report displays data from a report dataset in a data region on the report page, that is, in a single table, chart, matrix, or other type of report data region.</span></span> <span data-ttu-id="55f39-128">レポート データセットのデータは、外部データ ソースに読み取り専用アクセスを実行する単一のクエリ コマンドから返された最初の結果セットから取得されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-128">The data in a report dataset comes from the first result set that is returned from a single query command that runs from read-only access to an external data source.</span></span> <span data-ttu-id="55f39-129">各データ領域は、データセットのすべてのデータを表示するために、必要に応じて拡張されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-129">Each data region expands as needed to display all the data from the dataset.</span></span>  

<span data-ttu-id="55f39-130">データセットのデータは、必然的に表形式になります。</span><span class="sxs-lookup"><span data-stu-id="55f39-130">Data in a dataset are essentially tabular.</span></span> <span data-ttu-id="55f39-131">列は、データセット クエリのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="55f39-131">Columns are the fields from the dataset query.</span></span> <span data-ttu-id="55f39-132">行は、結果セットの行です。</span><span class="sxs-lookup"><span data-stu-id="55f39-132">Rows are from the rows in the result set.</span></span> <span data-ttu-id="55f39-133">次の一般化されたデータの種類をレポートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="55f39-133">You can use the following generalized types of data in a report:</span></span>  

-   <span data-ttu-id="55f39-134">四角形データ。</span><span class="sxs-lookup"><span data-stu-id="55f39-134">Rectangular data.</span></span> <span data-ttu-id="55f39-135">すべての行に同じ数の列が含まれる結果セットのデータです。</span><span class="sxs-lookup"><span data-stu-id="55f39-135">Data from a result set that has the same number of columns in every row.</span></span>  

-   <span data-ttu-id="55f39-136">階層データは、フラット化された行セットとしてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55f39-136">Hierarchical data is supported as a flattened rowset.</span></span>  

  -   <span data-ttu-id="55f39-137">データの各行の列数が異なる不規則階層はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="55f39-137">Ragged hierarchies, where there is a different number of columns for each row of data, is not supported.</span></span> <span data-ttu-id="55f39-138">データ拡張機能によっては、このことが問題になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55f39-138">For some data extensions, this has some implications.</span></span>  

  -   <span data-ttu-id="55f39-139">多次元データ ソースを利用するデータ拡張機能は、XML for Analysis プロトコルを使用し、データをセル セットとしてではなく、フラット化された行セットとして取得します。</span><span class="sxs-lookup"><span data-stu-id="55f39-139">Data extensions that work with multidimensional data sources use XML for Analysis protocol and retrieve data as a flattened row set and not as a cell set.</span></span>  

  -   <span data-ttu-id="55f39-140">XML データ拡張機能は、XML データをレポートで使用できるように自動的にフラット化します。</span><span class="sxs-lookup"><span data-stu-id="55f39-140">The XML data extension automatically flattens XML data to use it in a report.</span></span> <span data-ttu-id="55f39-141">XML 要素の最初のインスタンスにすべての属性またはサブ要素が含まれない場合、データはレポート データとして利用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55f39-141">If the first instance of an XML element does not include all attributes or subelements, the data might not be available as report data.</span></span>  

-   <span data-ttu-id="55f39-142">再帰型データはサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55f39-142">Recursive data is supported.</span></span> <span data-ttu-id="55f39-143">再帰型データ階層を含む結果セットは、階層構造に関するすべての情報を四角形の結果セット内に含みます。</span><span class="sxs-lookup"><span data-stu-id="55f39-143">A result set that contains a recursive data hierarchy includes all the information about the hierarchy structure in a rectangular result set.</span></span> <span data-ttu-id="55f39-144">たとえば、会社内の上司/部下構造は、2 つの列 (従業員とマネージャー) を含むテーブルで表すことができます。</span><span class="sxs-lookup"><span data-stu-id="55f39-144">For example, the report-to structure in a company can be represented by a table that includes two columns: an employee and a manager.</span></span> <span data-ttu-id="55f39-145">各マネージャーは、マネージャーがいる従業員でもあります。</span><span class="sxs-lookup"><span data-stu-id="55f39-145">Each manager also is an employee with a manager.</span></span> <span data-ttu-id="55f39-146">最上位のマネージャーは、通常、その従業員にマネージャーがいないことを示す NULL または他の識別子を含みます。</span><span class="sxs-lookup"><span data-stu-id="55f39-146">The top manager usually contains a null or some other identifier that indicates that this employee has no manager.</span></span>  



##  <a name="working-with-data-types"></a><a name="DataTypes"></a><span data-ttu-id="55f39-147">データ型の操作</span><span class="sxs-lookup"><span data-stu-id="55f39-147">Working with Data Types</span></span>  
<span data-ttu-id="55f39-148">データセットを作成すると、フィールドのデータ型は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]の共通言語ランタイム (CLR) データ型のサブセットにマップされます。</span><span class="sxs-lookup"><span data-stu-id="55f39-148">When you create a dataset, the data types of the fields are mapped to a subset of common language runtime (CLR) data types from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="55f39-149">明示的にマップできないデータ型は、文字列として返されます。</span><span class="sxs-lookup"><span data-stu-id="55f39-149">Data types that cannot be clearly mapped are returned as strings.</span></span> <span data-ttu-id="55f39-150">フィールドのデータ型の操作の詳細については、「 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55f39-150">For more information about working with field data types, see [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="55f39-151">パラメーターを作成する場合、データ型は、サポートされているレポート定義のデータ型であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="55f39-151">When you create a parameter, the data type must be a supported report definition data type.</span></span> <span data-ttu-id="55f39-152">データ プロバイダーからレポート パラメーターへデータ型をマップする方法の詳細については、「[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55f39-152">For more information about mapping data types from the data provider to a report parameter, see [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md).</span></span>  



##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="55f39-153">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="55f39-153">How-To Topics</span></span>  
<span data-ttu-id="55f39-154">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-154">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  

[<span data-ttu-id="55f39-155">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="55f39-155">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  

[<span data-ttu-id="55f39-156">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="55f39-156">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  

[<span data-ttu-id="55f39-157">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="55f39-157">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  

## <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="55f39-158">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="55f39-158">In This Section</span></span>  

<span data-ttu-id="55f39-159">次のトピックでは、各組み込みデータ拡張機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-159">The following topics provide information about each built-in data extension.</span></span>  

|<span data-ttu-id="55f39-160">トピック</span><span class="sxs-lookup"><span data-stu-id="55f39-160">Topic</span></span>|<span data-ttu-id="55f39-161">データ ソースの種類</span><span class="sxs-lookup"><span data-stu-id="55f39-161">Data Source Type</span></span>|  
|-----------|----------------------|  
|[<span data-ttu-id="55f39-162">SQL Server の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-162">SQL Server Connection Type &#40;SSRS&#41;</span></span>](sql-server-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-163">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f39-163">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>|  
|[<span data-ttu-id="55f39-164">MDX のための Analysis Services の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="55f39-164">Analysis Services Connection Type for MDX &#40;SSRS&#41;</span></span>](analysis-services-connection-type-for-mdx-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f39-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>|  
|[<span data-ttu-id="55f39-166">PowerPivot の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-166">PowerPivot Connection Type &#40;SSRS&#41;</span></span>](power-pivot-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f39-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>|  
|[<span data-ttu-id="55f39-168">SharePoint リストの接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-168">SharePoint List Connection Type &#40;SSRS&#41;</span></span>](sharepoint-list-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-169">SharePoint リスト</span><span class="sxs-lookup"><span data-stu-id="55f39-169">SharePoint List</span></span>|  
|[<span data-ttu-id="55f39-170">SQL Azure の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-170">SQL Azure Connection Type &#40;SSRS&#41;</span></span>](sql-azure-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-171">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f39-171">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]</span></span>|  
|[<span data-ttu-id="55f39-172">SQL Server 並列データ ウェアハウスの接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-172">SQL Server Parallel Data Warehouse Connection Type &#40;SSRS&#41;</span></span>](sql-server-parallel-data-warehouse-connection-type-ssrs.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="55f39-173">[!INCLUDE[ssDWfull](../../includes/ssdwfull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f39-173">[!INCLUDE[ssDWfull](../../includes/ssdwfull-md.md)]</span></span>|  
|[<span data-ttu-id="55f39-174">SAP NetWeaver BI の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-174">SAP NetWeaver BI Connection Type &#40;SSRS&#41;</span></span>](sap-netweaver-bi-connection-type-ssrs.md)|<span data-ttu-id="55f39-175">SAP NetWeaver BI</span><span class="sxs-lookup"><span data-stu-id="55f39-175">SAP NetWeaver BI</span></span>|  
|[<span data-ttu-id="55f39-176">Hyperion Essbase の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-176">Hyperion Essbase Connection Type &#40;SSRS&#41;</span></span>](hyperion-essbase-connection-type-ssrs.md)|<span data-ttu-id="55f39-177">Hyperion Essbase</span><span class="sxs-lookup"><span data-stu-id="55f39-177">Hyperion Essbase</span></span>|  
|[<span data-ttu-id="55f39-178">OLE DB の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-178">OLE DB Connection Type &#40;SSRS&#41;</span></span>](ole-db-connection-type-ssrs.md)|<span data-ttu-id="55f39-179">OLE DB (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="55f39-179">OLE DB</span></span>|  
|[<span data-ttu-id="55f39-180">ODBC の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-180">ODBC Connection Type &#40;SSRS&#41;</span></span>](odbc-connection-type-ssrs.md)|<span data-ttu-id="55f39-181">ODBC</span><span class="sxs-lookup"><span data-stu-id="55f39-181">ODBC</span></span>|  
|[<span data-ttu-id="55f39-182">XML の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-182">XML Connection Type &#40;SSRS&#41;</span></span>](xml-connection-type-ssrs.md)|<span data-ttu-id="55f39-183">XML</span><span class="sxs-lookup"><span data-stu-id="55f39-183">XML</span></span>|  

## <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="55f39-184">関連セクション</span><span class="sxs-lookup"><span data-stu-id="55f39-184">Related Sections</span></span>  

<span data-ttu-id="55f39-185">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="55f39-185">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  

|<span data-ttu-id="55f39-186">トピック</span><span class="sxs-lookup"><span data-stu-id="55f39-186">Topic</span></span>|<span data-ttu-id="55f39-187">説明</span><span class="sxs-lookup"><span data-stu-id="55f39-187">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="55f39-188">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="55f39-188">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)|<span data-ttu-id="55f39-189">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-189">Provides an overview of accessing data for your report.</span></span>|  
|[<span data-ttu-id="55f39-190">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="55f39-190">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)|<span data-ttu-id="55f39-191">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-191">Provides information about data connections and data sources.</span></span>|  
|[<span data-ttu-id="55f39-192">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-192">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)|<span data-ttu-id="55f39-193">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-193">Provides information about embedded and shared datasets.</span></span>|  
|[<span data-ttu-id="55f39-194">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-194">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)|<span data-ttu-id="55f39-195">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55f39-195">Provides information about the dataset field collection generated by the query.</span></span>|  
|<span data-ttu-id="55f39-196">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="55f39-196">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>|<span data-ttu-id="55f39-197">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="55f39-197">Provides in-depth information about platform and version support for each data extension.</span></span>|  
|<span data-ttu-id="55f39-198">[データ処理拡張機能の概要](../extensions/data-processing/data-processing-extensions-overview.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント)</span><span class="sxs-lookup"><span data-stu-id="55f39-198">[Data Processing Extensions Overview](../extensions/data-processing/data-processing-extensions-overview.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>|<span data-ttu-id="55f39-199">データ拡張機能に関する上級ユーザー向けの詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="55f39-199">Provides in-depth information for advanced users about data extensions.</span></span>|  

## <a name="see-also"></a><span data-ttu-id="55f39-200">参照</span><span class="sxs-lookup"><span data-stu-id="55f39-200">See Also</span></span>  

- [<span data-ttu-id="55f39-201">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="55f39-201">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)
- [<span data-ttu-id="55f39-202">クエリ デザイナー &#40;レポート ビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="55f39-202">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)