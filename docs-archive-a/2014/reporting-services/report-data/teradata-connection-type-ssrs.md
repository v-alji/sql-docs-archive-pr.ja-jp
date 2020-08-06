---
title: Teradata の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73e51c82a824bb607d75c2e78cfc9b0f37476e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643181"
---
# <a name="teradata-connection-type-ssrs"></a><span data-ttu-id="20866-102">Teradata の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="20866-102">Teradata Connection Type (SSRS)</span></span>
  <span data-ttu-id="20866-103">Teradata リレーショナル データベースのデータをレポートに含めるには、種類が Teradata のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="20866-103">To include data from a Teradata relational database in your report, you must have a dataset that is based on a report data source of type Teradata.</span></span> <span data-ttu-id="20866-104">このビルトイン データ ソースの種類は、.NET Managed Provider for Teradata データ処理拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="20866-104">This built-in data source type is based on the .NET Managed Provider for Teradata data processing extension.</span></span>  
  
 <span data-ttu-id="20866-105">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="20866-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="20866-106">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20866-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="20866-107">接続文字列</span><span class="sxs-lookup"><span data-stu-id="20866-107">Connection String</span></span>  
 <span data-ttu-id="20866-108">データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="20866-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="20866-109">次の接続文字列の例では、IP アドレスで指定したサーバー上の Teradata データベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="20866-109">The following connection string example specifies a Teradata database on the server specified with an IP address:</span></span>  
  
```  
data source=<IP Address>  
```  
  
 <span data-ttu-id="20866-110">接続文字列の例について詳しくは、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="20866-110">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="20866-111">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="20866-111">Credentials</span></span>  
 <span data-ttu-id="20866-112">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="20866-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="20866-113">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="20866-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="20866-114">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20866-114">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  

##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="20866-115">解説</span><span class="sxs-lookup"><span data-stu-id="20866-115">Remarks</span></span>  
 <span data-ttu-id="20866-116">Teradata データ ソースに接続するには、システム管理者が、Teradata データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Teradata をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="20866-116">Before you can connect a Teradata data source, the system administrator must have installed the version of the .NET Data Provider for Teradata that supports retrieving data from the Teradata database.</span></span> <span data-ttu-id="20866-117">このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20866-117">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="20866-118">このデータ プロバイダーでは使用できないレポート配信モードもあります。</span><span class="sxs-lookup"><span data-stu-id="20866-118">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="20866-119">このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="20866-119">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="20866-120">詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312) の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のドキュメントの「[サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20866-120">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  

##  <a name="report-models"></a><a name="Models"></a> <span data-ttu-id="20866-121">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="20866-121">Report Models</span></span>  
 <span data-ttu-id="20866-122">Teradata データ ソースに基づくレポート モデルからデータセットを作成するには、モデルを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のモデル デザイナーでデザインし、レポート サーバーでパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="20866-122">To create a dataset from a report model that is based on a Teradata data source, the model must be designed in Model Designer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and published on a report server.</span></span>  

##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="20866-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="20866-123">Related Sections</span></span>  
 <span data-ttu-id="20866-124">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="20866-124">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="20866-125">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="20866-125">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="20866-126">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="20866-126">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="20866-127">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="20866-127">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="20866-128">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="20866-128">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="20866-129">レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="20866-129">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="20866-130">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="20866-130">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="20866-131">データセット フィールド コレクション (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="20866-131">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="20866-132">データセット クエリによって生成されるフィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="20866-132">Provides information about the field collection that is generated by the dataset query.</span></span>  
  
 <span data-ttu-id="20866-133">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="20866-133">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="20866-134">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="20866-134">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 [<span data-ttu-id="20866-135">Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata (英語)</span><span class="sxs-lookup"><span data-stu-id="20866-135">Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata</span></span>](https://go.microsoft.com/fwlink/?LinkID=130848)  
 <span data-ttu-id="20866-136">このデータ拡張機能の使用に関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="20866-136">Provides detailed information about working with this data extension.</span></span>  

## <a name="see-also"></a><span data-ttu-id="20866-137">参照</span><span class="sxs-lookup"><span data-stu-id="20866-137">See Also</span></span>  
 <span data-ttu-id="20866-138">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="20866-138">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="20866-139">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="20866-139">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="20866-140">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="20866-140">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
