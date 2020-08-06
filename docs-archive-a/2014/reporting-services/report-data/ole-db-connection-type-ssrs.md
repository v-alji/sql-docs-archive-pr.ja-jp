---
title: OLE DB の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66d4074d6bf90a23814b13da8836fd0594e8cf1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742866"
---
# <a name="ole-db-connection-type-ssrs"></a><span data-ttu-id="5d0ee-102">OLE DB の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d0ee-102">OLE DB Connection Type (SSRS)</span></span>
  <span data-ttu-id="5d0ee-103">OLE DB データ プロバイダーのデータを含めるには、種類が OLE DB のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-103">To include data from an OLE DB data provider, you must have a dataset that is based on a report data source of type OLE DB.</span></span> <span data-ttu-id="5d0ee-104">このビルトイン データ ソースの種類は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB データ処理拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB data processing extension.</span></span>  
  
 <span data-ttu-id="5d0ee-105">OLE DB は、クライアントがさまざまなデータ プロバイダーに接続できるようにするデータ アクセス テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-105">OLE DB is a data access technology that enables clients to connect to a variety of data providers.</span></span> <span data-ttu-id="5d0ee-106">データ ソースの種類に OLE DB を選択したら、特定のデータ プロバイダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-106">After you select the data source type OLE DB, you must select a specific data provider.</span></span> <span data-ttu-id="5d0ee-107">パラメーターや資格情報などの機能のサポートは、選択したデータ プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-107">Support for features such as parameters and credentials are dependent on the data provider that you select.</span></span>  
  
 <span data-ttu-id="5d0ee-108">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-108">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="5d0ee-109">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-109">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="5d0ee-110">接続文字列</span><span class="sxs-lookup"><span data-stu-id="5d0ee-110">Connection String</span></span>  
 <span data-ttu-id="5d0ee-111">OLE DB データ処理拡張機能の接続文字列は、使用するデータ プロバイダーに依存します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-111">The connection string for the OLE DB data processing extension depends on the data provider that you want.</span></span> <span data-ttu-id="5d0ee-112">一般的な接続文字列は、データ プロバイダーでサポートされる名前と値のペアで構成されます。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-112">A typical connection string contains name/value pairs that are supported by the data provider.</span></span> <span data-ttu-id="5d0ee-113">たとえば、次の接続文字列は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の OLE DB プロバイダーおよび AdventureWorks データベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-113">For example, the following connection string specifies the OLE DB provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="5d0ee-114">使用する接続文字列は、接続先の外部データ ソースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-114">The connection string that you use depends on the external data source that you are connecting to.</span></span> <span data-ttu-id="5d0ee-115">データ プロバイダーに固有の接続文字列プロパティを設定するには、 **[データ ソースのプロパティ]** ダイアログ ボックスの **[全般]** ページで **[構築]** ボタンをクリックし、 **[接続プロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-115">To set connection string properties specific to a data provider, from the **General** page of the **Data Source Properties** dialog box, click the **Build** button to open the **Connection Properties** dialog box.</span></span> <span data-ttu-id="5d0ee-116">**[データ リンク プロパティ]** ダイアログ ボックスで、拡張データ ソース プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-116">Set extended data source properties through the **Data Link Properties** dialog box.</span></span>  
  
 <span data-ttu-id="5d0ee-117">接続文字列の例については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-117">For examples of connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="5d0ee-118">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="5d0ee-118">Credentials</span></span>  
 <span data-ttu-id="5d0ee-119">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-119">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="5d0ee-120">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-120">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="5d0ee-121">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-121">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
###### <a name="special-characters-in-a-password"></a><span data-ttu-id="5d0ee-122">パスワードの特殊文字</span><span class="sxs-lookup"><span data-stu-id="5d0ee-122">Special Characters in a Password</span></span>  
 <span data-ttu-id="5d0ee-123">OLE DB データ ソースの構成時に、パスワードが要求されるように設定したり、接続文字列にパスワードを含めた場合、ユーザーによって入力されたパスワードに句読点などの特殊文字が含まれていると、基になるデータ ソースのドライバーによってはその特殊文字を検証することができません。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-123">If you configure the OLE DB data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="5d0ee-124">レポートを処理する際に、この問題によって、"パスワードが無効です" というメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-124">When you process the report, the message "Not a valid password" may indicate this problem.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d0ee-125">パスワードなどのログイン情報を接続文字列に追加しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-125">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="5d0ee-126">レポート ビルダーでは、 **[データ ソース]** ダイアログ ボックスに、資格情報の入力に使用できるタブが別に用意されています。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-126">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="5d0ee-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d0ee-127">Parameters</span></span>  
 <span data-ttu-id="5d0ee-128">OLE DB プロバイダーによっては、無名パラメーターはサポートされても名前付きパラメーターはサポートされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-128">Some OLE DB providers support unnamed parameters and not named parameters.</span></span> <span data-ttu-id="5d0ee-129">パラメーターは、クエリ内でプレースホルダーを使用して位置を指定することで渡されます。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-129">Parameters are passed by position by using a placeholder in the query.</span></span> <span data-ttu-id="5d0ee-130">プレースホルダー文字は、データ プロバイダーによってサポートされている構文で決まります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-130">The placeholder character is determined by the syntax that is supported by the data provider.</span></span>  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="5d0ee-131">解説</span><span class="sxs-lookup"><span data-stu-id="5d0ee-131">Remarks</span></span>  
 <span data-ttu-id="5d0ee-132">OLEDB は、特定のデータ ソースのデータ プロバイダーを作成するためのネイティブ テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-132">OLEDB is a native technology for building data providers for specific data sources.</span></span> <span data-ttu-id="5d0ee-133">COM (コンポーネント オブジェクト モデル) インターフェイスを基盤とした、</span><span class="sxs-lookup"><span data-stu-id="5d0ee-133">OLEDB is based on COM (Component Object Model) interfaces.</span></span> <span data-ttu-id="5d0ee-134">ODBC よりも新しく ADO.NET データ プロバイダーよりも古いテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-134">OLEDB is a later technology than ODBC and earlier than ADO.NET data providers.</span></span> <span data-ttu-id="5d0ee-135">OLEDB データ プロバイダーは、他の COM コンポーネントと同様にオペレーティング システムに登録されます。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-135">OLEDB data providers are registered with the operating system like any other COM component.</span></span> <span data-ttu-id="5d0ee-136">OLEDB データ プロバイダーはマイクロソフトとサード パーティ ベンダーから入手できます。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-136">OLEDB data providers are available from Microsoft and third party vendors.</span></span> <span data-ttu-id="5d0ee-137">マイクロソフトは、ODBC ドライバーとの通信を仲介する OLEDB データ プロバイダーである MSDASQL も提供しています。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-137">Microsoft also provides MSDASQL, an OLEDB data provider that bridges communication to ODBC drivers.</span></span> <span data-ttu-id="5d0ee-138">詳細については、「[ODBC 接続の種類 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-138">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
 <span data-ttu-id="5d0ee-139">目的のデータを正常に取得するには、データ プロバイダーでサポートされるクエリ構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-139">To successfully retrieve the data that you want, you must provide query syntax that is supported by the data provider.</span></span> <span data-ttu-id="5d0ee-140">サポートされるパラメーターはデータ プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-140">Parameter support varies by data provider.</span></span> <span data-ttu-id="5d0ee-141">詳細については、使用するデータ プロバイダー向けのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-141">For more information, see topics that are specific to the data provider that you select.</span></span> <span data-ttu-id="5d0ee-142">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-142">For example:</span></span>  
  
-   [<span data-ttu-id="5d0ee-143">Analysis Services OLE DB Provider &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="5d0ee-143">Analysis Services OLE DB Provider &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [<span data-ttu-id="5d0ee-144">.NET Framework Data Provider for Oracle の使用</span><span class="sxs-lookup"><span data-stu-id="5d0ee-144">Using the .NET Framework Data Provider for Oracle</span></span>](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [<span data-ttu-id="5d0ee-145">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="5d0ee-145">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 <span data-ttu-id="5d0ee-146">特定の OLE DB データ プロバイダーの詳細については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のドキュメント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)) の「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-146">For more information about specific OLE DB data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="5d0ee-147">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="5d0ee-147">How-To Topics</span></span>  
 <span data-ttu-id="5d0ee-148">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-148">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="5d0ee-149">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="5d0ee-149">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5d0ee-150">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d0ee-150">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5d0ee-151">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="5d0ee-151">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="5d0ee-152">関連セクション</span><span class="sxs-lookup"><span data-stu-id="5d0ee-152">Related Sections</span></span>  
 <span data-ttu-id="5d0ee-153">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-153">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="5d0ee-154">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="5d0ee-154">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="5d0ee-155">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-155">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="5d0ee-156">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="5d0ee-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="5d0ee-157">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-157">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="5d0ee-158">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5d0ee-158">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="5d0ee-159">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-159">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="5d0ee-160">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5d0ee-160">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="5d0ee-161">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-161">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="5d0ee-162">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-162">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="5d0ee-163">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="5d0ee-163">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="5d0ee-164">参照</span><span class="sxs-lookup"><span data-stu-id="5d0ee-164">See Also</span></span>  
 <span data-ttu-id="5d0ee-165">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="5d0ee-165">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="5d0ee-166">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5d0ee-166">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5d0ee-167">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5d0ee-167">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
