---
title: ODBC の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2bf5ee6f3eeaa38796e4fa41f3cc0634fd128cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632912"
---
# <a name="odbc-connection-type-ssrs"></a><span data-ttu-id="e6d87-102">ODBC の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e6d87-102">ODBC Connection Type (SSRS)</span></span>
  <span data-ttu-id="e6d87-103">ODBC データ プロバイダーのデータを含めるには、種類が ODBC のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="e6d87-103">To include data from an ODBC data provider, you must have a dataset that is based on a report data source of type ODBC.</span></span> <span data-ttu-id="e6d87-104">このビルトイン データ ソースの種類は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC データ処理拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e6d87-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC data processing extension.</span></span>  
  
 <span data-ttu-id="e6d87-105">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="e6d87-106">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="e6d87-107">接続文字列</span><span class="sxs-lookup"><span data-stu-id="e6d87-107">Connection String</span></span>  
 <span data-ttu-id="e6d87-108">ODBC データ処理拡張機能の接続文字列は、使用する ODBC ドライバーに依存します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-108">The connection string for the ODBC data processing extension depends on the ODBC driver that you want.</span></span> <span data-ttu-id="e6d87-109">一般的な接続文字列は、ドライバーでサポートされる名前と値のペアで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e6d87-109">A typical connection string contains name/value pairs that are supported by the driver.</span></span> <span data-ttu-id="e6d87-110">たとえば、次の接続文字列は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーおよび AdventureWorks データベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="e6d87-110">For example, the following connection string specifies the ODBC driver for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="e6d87-111">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="e6d87-111">Credentials</span></span>  
 <span data-ttu-id="e6d87-112">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6d87-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="e6d87-113">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6d87-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="e6d87-114">パスワードを要求したり、接続文字列にパスワードを含めるように ODBC データ ソースを構成し、ユーザーが句読点などの特殊文字を使用してパスワードを入力した場合、基になるデータ ソースのドライバーによってはその特殊文字を検証することができません。</span><span class="sxs-lookup"><span data-stu-id="e6d87-114">If you configure your ODBC data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="e6d87-115">レポートを処理する際に、この問題によって、"パスワードが無効です" というメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6d87-115">When you process the report, the message "Not a valid password" might indicate this problem.</span></span> <span data-ttu-id="e6d87-116">パスワードを変更できない場合は、データベース管理者と協力して、適切な資格情報をシステム ODBC データ ソース名 (DSN) の一部としてレポート サーバーに格納することができます。</span><span class="sxs-lookup"><span data-stu-id="e6d87-116">If changing the password is impractical, you can work with your database administrator to store the appropriate credentials on the report server as part of a system ODBC data source name (DSN).</span></span> <span data-ttu-id="e6d87-117">詳細については、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントの「OdbcConnection.ConnectionString」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-117">For more information, see "OdbcConnection.ConnectionString" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6d87-118">パスワードなどのログイン情報を接続文字列に追加しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e6d87-118">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="e6d87-119">レポート ビルダーでは、 **[データ ソース]** ダイアログ ボックスに、資格情報の入力に使用できるタブが別に用意されています。</span><span class="sxs-lookup"><span data-stu-id="e6d87-119">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
 <span data-ttu-id="e6d87-120">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-120">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="e6d87-121">解説</span><span class="sxs-lookup"><span data-stu-id="e6d87-121">Remarks</span></span>  
 <span data-ttu-id="e6d87-122">ODBC は初期のデータ アクセス テクノロジで、その発展形が OLEDB です。</span><span class="sxs-lookup"><span data-stu-id="e6d87-122">ODBC is an early data access technology that preceded OLEDB.</span></span> <span data-ttu-id="e6d87-123">ODBC でサポートされるのはリレーショナル データ ソースだけです。</span><span class="sxs-lookup"><span data-stu-id="e6d87-123">ODBC supports only relational data sources.</span></span> <span data-ttu-id="e6d87-124">ODBC データ プロバイダーは *ドライバー*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e6d87-124">ODBC data providers are called *drivers*.</span></span> <span data-ttu-id="e6d87-125">ODBC ドライバーはマイクロソフトとサード パーティ ベンダーによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="e6d87-125">ODBC drivers are provided by Microsoft and third party vendors.</span></span> <span data-ttu-id="e6d87-126">たとえば、Microsoft Office では、Office ファイル形式に接続する ODBC ドライバーがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e6d87-126">For example, Microsoft Office installs ODBC drivers that connect to Office file formats.</span></span>  
  
 <span data-ttu-id="e6d87-127">ODBC 接続文字列を作成するには、ODBC ドライバーがインストールされている必要があり、マシン DSN またはシステム DSN を作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6d87-127">Before you can build an ODBC connection string, you must have ODBC drivers installed and build a machine or system DSN.</span></span> <span data-ttu-id="e6d87-128">目的のデータを正常に取得するには、ドライバーでサポートされるクエリ構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6d87-128">To successfully retrieve the data that you want, you must provide query syntax that is supported by the driver.</span></span> <span data-ttu-id="e6d87-129">パラメーターのサポートはドライバーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e6d87-129">Parameter support varies by driver.</span></span> <span data-ttu-id="e6d87-130">詳細については、選択するドライバーに応じたトピック (「[SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)」など) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-130">For more information, see topics that are specific to the driver that you select, for example, [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="e6d87-131">プラットフォームおよびバージョン情報</span><span class="sxs-lookup"><span data-stu-id="e6d87-131">Platform and Version Information</span></span>  
 <span data-ttu-id="e6d87-132">特定の ODBC データ プロバイダーの詳細については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のドキュメント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)) の「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6d87-132">For more information about specific ODBC data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="e6d87-133">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="e6d87-133">How-To Topics</span></span>  
 <span data-ttu-id="e6d87-134">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-134">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="e6d87-135">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="e6d87-135">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="e6d87-136">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e6d87-136">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="e6d87-137">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e6d87-137">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="e6d87-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6d87-138">Related Sections</span></span>  
 <span data-ttu-id="e6d87-139">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="e6d87-139">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="e6d87-140">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="e6d87-140">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="e6d87-141">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-141">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="e6d87-142">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="e6d87-142">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="e6d87-143">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-143">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="e6d87-144">レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e6d87-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="e6d87-145">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-145">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="e6d87-146">データセット フィールド コレクション (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e6d87-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="e6d87-147">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e6d87-147">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="e6d87-148">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="e6d87-148">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="e6d87-149">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="e6d87-149">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="e6d87-150">参照</span><span class="sxs-lookup"><span data-stu-id="e6d87-150">See Also</span></span>  
 <span data-ttu-id="e6d87-151">[レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e6d87-151">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e6d87-152">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e6d87-152">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e6d87-153">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e6d87-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
