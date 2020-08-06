---
title: Oracle の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9bf19953c5d2dc2f818eddcacf445e641972d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640736"
---
# <a name="oracle-connection-type-ssrs"></a><span data-ttu-id="52091-102">Oracle の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="52091-102">Oracle Connection Type (SSRS)</span></span>
  <span data-ttu-id="52091-103">Oracle データベースのデータをレポートで使用するには、種類が Oracle のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="52091-103">To use data from an Oracle database in your report, you must you must have a dataset that is based on a report data source of type Oracle.</span></span> <span data-ttu-id="52091-104">このビルトイン データ ソースの種類は、.NET Framework Managed Provider for Oracle に基づいており、Oracle クライアント ソフトウェア コンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="52091-104">This built-in data source type is based on the .NET Framework Managed Provider for Oracle and requires an Oracle client software component.</span></span>  
  
 <span data-ttu-id="52091-105">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="52091-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="52091-106">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="52091-107">接続文字列</span><span class="sxs-lookup"><span data-stu-id="52091-107">Connection String</span></span>  
 <span data-ttu-id="52091-108">データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="52091-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="52091-109">次に示す接続文字列の例では、Unicode を使用して "Oracle9" というサーバー上の Oracle データベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="52091-109">The following connection string example specifies an Oracle database on the server named "Oracle9" using Unicode.</span></span> <span data-ttu-id="52091-110">サーバー名は、Tnsnames.ora 構成ファイルで Oracle サーバー インスタンス名として定義されたものと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52091-110">The server name must match what is defined in the Tnsnames.ora configuration file as the Oracle server instance name.</span></span>  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 <span data-ttu-id="52091-111">接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-111">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="52091-112">認証</span><span class="sxs-lookup"><span data-stu-id="52091-112">Credentials</span></span>  
 <span data-ttu-id="52091-113">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="52091-113">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="52091-114">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="52091-114">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="52091-115">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  

  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="52091-116">問い合わせ</span><span class="sxs-lookup"><span data-stu-id="52091-116">Queries</span></span>  
 <span data-ttu-id="52091-117">データセットを作成するには、ボックスの一覧からストアド プロシージャを選択するか、SQL クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="52091-117">To create a dataset, you can either select a stored procedure from a drop-down list or create an SQL query.</span></span> <span data-ttu-id="52091-118">クエリを作成するには、テキストベースのクエリ デザイナーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52091-118">To build a query, you must use the text-based query designer.</span></span> <span data-ttu-id="52091-119">詳細については、「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](text-based-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-119">For more information, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="52091-120">結果セットを 1 つだけ返すストアド プロシージャを指定できます。</span><span class="sxs-lookup"><span data-stu-id="52091-120">You can specify stored procedures that return only one result set.</span></span> <span data-ttu-id="52091-121">カーソル ベースのクエリは使用できません。</span><span class="sxs-lookup"><span data-stu-id="52091-121">Using cursor-based queries are not supported.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="52091-122">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52091-122">Parameters</span></span>  
 <span data-ttu-id="52091-123">クエリにクエリ変数が含まれている場合は、対応するレポート パラメーターが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="52091-123">If the query includes query variables, corresponding report parameters are automatically generated.</span></span> <span data-ttu-id="52091-124">この拡張機能では、名前付きパラメーターがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="52091-124">Named parameters are supported by this extension.</span></span> <span data-ttu-id="52091-125">Oracle Version 9 以降の場合、複数値パラメーターがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="52091-125">For Oracle version 9 or later, multivalue parameters are supported.</span></span>  
  
 <span data-ttu-id="52091-126">レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="52091-126">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="52091-127">たとえば、各レポート パラメーターのデータ型は **Text**です。</span><span class="sxs-lookup"><span data-stu-id="52091-127">For example, each report parameter is data type **Text**.</span></span> <span data-ttu-id="52091-128">レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="52091-128">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="52091-129">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="52091-129">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="52091-130">解説</span><span class="sxs-lookup"><span data-stu-id="52091-130">Remarks</span></span>  
 <span data-ttu-id="52091-131">Oracle データ ソースに接続するには、システム管理者が、Oracle データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Oracle をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="52091-131">Before you can connect an Oracle data source, the system administrator must have installed the version of the .NET Data Provider for Oracle that supports retrieving data from the Oracle database.</span></span> <span data-ttu-id="52091-132">このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52091-132">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="52091-133">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="52091-133">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="52091-134">msdn.microsoft.com の「[.NET Framework Data Provider for Oracle の使用](https://go.microsoft.com/fwlink/?LinkId=112314) 」</span><span class="sxs-lookup"><span data-stu-id="52091-134">[Using the .NET Framework Data Provider for Oracle](https://go.microsoft.com/fwlink/?LinkId=112314) on msdn.microsoft.com</span></span>  
  
-   [<span data-ttu-id="52091-135">Reporting Services を使用して Oracle データ ソースの構成およびアクセスを行う方法</span><span class="sxs-lookup"><span data-stu-id="52091-135">How to use Reporting Services to configure and to access an Oracle data source</span></span>](https://support.microsoft.com/kb/834305)  
  
-   [<span data-ttu-id="52091-136">NETWORK SERVICE セキュリティ プリンシパルに権限を追加する方法</span><span class="sxs-lookup"><span data-stu-id="52091-136">How to add permissions for the NETWORK SERVICE security principal</span></span>](https://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a><span data-ttu-id="52091-137">代替データ拡張機能</span><span class="sxs-lookup"><span data-stu-id="52091-137">Alternate Data Extensions</span></span>  
 <span data-ttu-id="52091-138">Oracle データベースからのデータの取得は、OLE DB のデータ ソースの種類を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="52091-138">You can also retrieve data from an Oracle database by using an OLE DB data source type.</span></span> <span data-ttu-id="52091-139">詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-139">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md).</span></span>  
  
###### <a name="report-models"></a><span data-ttu-id="52091-140">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="52091-140">Report Models</span></span>  
 <span data-ttu-id="52091-141">Oracle データベースに基づくモデルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="52091-141">You can also create models based on an Oracle database.</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="52091-142">プラットフォームおよびバージョン情報</span><span class="sxs-lookup"><span data-stu-id="52091-142">Platform and Version Information</span></span>  
 <span data-ttu-id="52091-143">プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52091-143">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="52091-144">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="52091-144">How-To Topics</span></span>  
 <span data-ttu-id="52091-145">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="52091-145">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="52091-146">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="52091-146">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="52091-147">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="52091-147">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="52091-148">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="52091-148">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="52091-149">関連セクション</span><span class="sxs-lookup"><span data-stu-id="52091-149">Related Sections</span></span>  
 <span data-ttu-id="52091-150">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="52091-150">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="52091-151">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="52091-151">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="52091-152">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="52091-152">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="52091-153">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="52091-153">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="52091-154">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="52091-154">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="52091-155">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52091-155">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="52091-156">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="52091-156">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="52091-157">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52091-157">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="52091-158">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="52091-158">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="52091-159">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="52091-159">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="52091-160">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="52091-160">Provides in-depth information about platform and version support for each data extension.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="52091-161">参照</span><span class="sxs-lookup"><span data-stu-id="52091-161">See Also</span></span>  
 <span data-ttu-id="52091-162">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="52091-162">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="52091-163">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52091-163">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="52091-164">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52091-164">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
