---
title: サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriber data sources [Reporting Services]
- subscriptions [Reporting Services], external data sources
- query-based subscriptions [Reporting Services]
- external data sources [Reporting Services]
- data-driven subscriptions
- data sources [Reporting Services], subscriptions
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e23da709289ffb6ca345bb6211f40388877a1a87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739084"
---
# <a name="use-an-external-data-source-for-subscriber-data-data-driven-subscription"></a><span data-ttu-id="bea81-102">サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="bea81-102">Use an External Data Source for Subscriber Data (Data-Driven Subscription)</span></span>
  <span data-ttu-id="bea81-103">データ ドリブン サブスクリプションでは、外部データ ソースからデータを取得するクエリまたはコマンドによって、動的サブスクリプション データが提供されます。</span><span class="sxs-lookup"><span data-stu-id="bea81-103">In a data-driven subscription, dynamic subscription data is provided by a query or command that retrieves data from an external data source.</span></span> <span data-ttu-id="bea81-104">サブスクリプション データは、データ ドリブン サブスクリプション処理の要件を満たす、サポートされているデータ ソースから取得できます。</span><span class="sxs-lookup"><span data-stu-id="bea81-104">Subscription data can be retrieved from any supported data source that meets the requirements for data-driven subscription processing.</span></span> <span data-ttu-id="bea81-105">クエリまたはコマンドの構文は、レポート サーバーと一緒にインストールされたデータ処理拡張機能に対して有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-105">The query or command syntax must be valid for a data processing extension installed with your report server.</span></span>  
  
## <a name="data-processing-requirements"></a><span data-ttu-id="bea81-106">データ処理の要件</span><span class="sxs-lookup"><span data-stu-id="bea81-106">Data Processing Requirements</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="bea81-107">は、データ処理拡張機能を使用して、サブスクリプション データを取得します。</span><span class="sxs-lookup"><span data-stu-id="bea81-107">uses data processing extensions to retrieve subscription data.</span></span> <span data-ttu-id="bea81-108">推奨されているデータ ソースには、次の種類があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-108">Recommended data source types include the following:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bea81-109">リレーショナル データベース</span><span class="sxs-lookup"><span data-stu-id="bea81-109">relational databases</span></span>  
  
-   <span data-ttu-id="bea81-110">Oracle データベース</span><span class="sxs-lookup"><span data-stu-id="bea81-110">Oracle databases</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="bea81-111">の多次元データ ソースおよびデータ マイニング データ ソース</span><span class="sxs-lookup"><span data-stu-id="bea81-111">multidimensional and data mining data sources</span></span>  
  
-   <span data-ttu-id="bea81-112">XML データ ソース</span><span class="sxs-lookup"><span data-stu-id="bea81-112">XML data sources</span></span>  
  
     <span data-ttu-id="bea81-113">サブスクライバー データ用に XML データ処理拡張機能を使用する場合、サブスクリプションのクエリ タイムアウト設定を大きくしてください。</span><span class="sxs-lookup"><span data-stu-id="bea81-113">When using the XML data processing extension for subscriber data, be sure to increase the query timeout settings in the subscription.</span></span> <span data-ttu-id="bea81-114">XML データ処理拡張機能では、秒ではなくミリ秒がクエリ タイムアウト値に使用されています。</span><span class="sxs-lookup"><span data-stu-id="bea81-114">The XML data processing extension uses milliseconds rather than seconds for query timeout values.</span></span> <span data-ttu-id="bea81-115">タイムアウトの値を大きくしないと、処理時間の不足でサブスクリプションが失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="bea81-115">If you do not increase the timeout value, the subscription might fail due to insufficient processing time.</span></span>  
  
     <span data-ttu-id="bea81-116">サブスクライバー データ ソースへの接続を構成するときに **[資格情報を必要としない]** オプションを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="bea81-116">Avoid using the **Credentials are not required** option when configuring the connection to the subscriber data source.</span></span> <span data-ttu-id="bea81-117">XML データ処理拡張機能を使用して実行時にサブスクリプション データを取得する場合、保存されている資格情報を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bea81-117">Stored credentials are recommended when using the XML data processing extension to retrieve subscription data at run time.</span></span>  
  
 <span data-ttu-id="bea81-118">サポートされている他の種類のデータ ソースを使用できる場合もありますが、サポートされているすべてのデータ ソースに関して動作が保証されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bea81-118">You might be able to use other supported data source types, but not all of them are guaranteed to work.</span></span> <span data-ttu-id="bea81-119">たとえば、次のデータ ソースの種類は、サブスクライバー データに使用できません。</span><span class="sxs-lookup"><span data-stu-id="bea81-119">For example, the following data source types cannot be used for subscriber data:</span></span>  
  
-   <span data-ttu-id="bea81-120">SAP Netweaver BI データベース</span><span class="sxs-lookup"><span data-stu-id="bea81-120">SAP Netweaver BI databases</span></span>  
  
-   <span data-ttu-id="bea81-121">レポート モデル</span><span class="sxs-lookup"><span data-stu-id="bea81-121">report models</span></span>  
  
 <span data-ttu-id="bea81-122">データ ドリブン サブスクリプションでカスタム データ処理拡張機能を使用する場合は、 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> および <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-122">If you have a custom data processing extension that you want to use in data-driven subscriptions, it must implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> and the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interfaces.</span></span> <span data-ttu-id="bea81-123">データ処理拡張機能では、スキーマのみのクエリ実行をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-123">The data processing extension must support a schema-only query execution.</span></span> <span data-ttu-id="bea81-124">このクエリは、デザイン時に列のメタデータを取得するために使用します。これにより、サブスクリプション定義の配信オプションおよびレポート パラメーターにユーザーが列をマップできるようになります。</span><span class="sxs-lookup"><span data-stu-id="bea81-124">This query is used to retrieve column metadata at design-time so that users can map columns to delivery options and report parameters in the subscription definition.</span></span> <span data-ttu-id="bea81-125">スキーマのみのクエリ実行は、ユーザーによるサブスクリプション定義の初期段階に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bea81-125">Schema-only query execution occurs at an early stage when the user is defining the subscription.</span></span>  
  
## <a name="query-requirements"></a><span data-ttu-id="bea81-126">クエリの要件</span><span class="sxs-lookup"><span data-stu-id="bea81-126">Query Requirements</span></span>  
 <span data-ttu-id="bea81-127">サブスクリプション データを取得するクエリを作成する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="bea81-127">When creating query that retrieves subscription data, keep the following points in mind:</span></span>  
  
-   <span data-ttu-id="bea81-128">サブスクリプションに対して作成できるクエリは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="bea81-128">You can only create one query for the subscription.</span></span>  
  
-   <span data-ttu-id="bea81-129">クエリでは、配信オプションおよびレポート パラメーターの指定に使用するすべての値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-129">The query must return all of the values that you want to use for delivery options and for specifying report parameters.</span></span>  
  
-   <span data-ttu-id="bea81-130">レポート サーバーでは、結果セットの行ごとにレポート配信が作成されます。</span><span class="sxs-lookup"><span data-stu-id="bea81-130">The report server will create a report delivery for every row in the result set.</span></span> <span data-ttu-id="bea81-131">結果セットが 300 行の場合、レポート サーバーでは、300 個のレポートについて配信が試行されます。</span><span class="sxs-lookup"><span data-stu-id="bea81-131">If the result set consists of three hundred rows, the report server will attempt to deliver three hundred reports.</span></span>  
  
## <a name="setting-delivery-options-using-variable-data-from-a-subscriber-database"></a><span data-ttu-id="bea81-132">サブスクライバー データベースの変数データを使用した配信オプションの設定</span><span class="sxs-lookup"><span data-stu-id="bea81-132">Setting Delivery Options Using Variable Data from a Subscriber Database</span></span>  
 <span data-ttu-id="bea81-133">サブスクライバー データベースのデータを使用して、各受信者に関する配信オプションをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="bea81-133">You can use data in the subscriber database to customize delivery options for each recipient.</span></span> <span data-ttu-id="bea81-134">利用可能なオプションは、使用している配信拡張機能の種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bea81-134">The kind of delivery extension you are using determines which options are available.</span></span> <span data-ttu-id="bea81-135">レポート サーバーの電子メール配信拡張機能を使用している場合、クエリは、各サブスクライバーの電子メール エイリアスを含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-135">If you are using the report server e-mail delivery extension, the query should contain an e-mail alias for each subscriber.</span></span> <span data-ttu-id="bea81-136">ファイル共有配信を使用している場合、サブスクライバー固有のレポート ファイルの作成や配信先の指定に使用できる値をサブスクライバー データに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-136">If you are using file share delivery, the subscriber data should include values that can be used to create subscriber-specific report files or to provide a destination for the delivery.</span></span> <span data-ttu-id="bea81-137">詳細については、「 [Reporting Services でのファイル共有の配信](file-share-delivery-in-reporting-services.md)」と「 [Reporting Services での電子メール配信](e-mail-delivery-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bea81-137">For more information, see [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) and [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
## <a name="passing-parameter-values-from-the-subscriber-database-to-the-report"></a><span data-ttu-id="bea81-138">サブスクライバー データベースからレポートへのパラメーター値の受け渡し</span><span class="sxs-lookup"><span data-stu-id="bea81-138">Passing Parameter Values from the Subscriber Database to the Report</span></span>  
 <span data-ttu-id="bea81-139">パラメーター化されたレポート用のデータ ドリブン サブスクリプションを作成する場合、変数パラメーター値を使用して、各レポートの出力をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="bea81-139">If you are creating a data-driven subscription for a parameterized report, you can use variable parameter values to customize the output of each report.</span></span> <span data-ttu-id="bea81-140">たとえば、サブスクライバー データベースには、レポート データのフィルター処理に使用できる従業員 ID 番号、雇用日、職種、および勤務地情報が含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="bea81-140">For example, the subscriber database might contain employee identification numbers, hire dates, job titles, and office location information that can be used to filter report data.</span></span> <span data-ttu-id="bea81-141">これらの列データまたは他の使用可能な列データに基づいたパラメーターをレポートが受け取ると、そのパラメーターを適切な列にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="bea81-141">If the report accepts parameters that are based on these or other available column data, you can map the parameter to the appropriate column.</span></span>  
  
 <span data-ttu-id="bea81-142">サブスクライバー フィールドをレポート パラメーターにマップするときは、データ型および列の長さに互換性があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bea81-142">When mapping subscriber fields to report parameters, make sure that the data types and column lengths are compatible.</span></span> <span data-ttu-id="bea81-143">データ型に不一致がある場合、サブスクリプションの処理中にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bea81-143">If there is a data type mismatch, an error will occur during subscription processing.</span></span> <span data-ttu-id="bea81-144">パラメーター化したレポートでのサブスクライバー データの使用については、「[データドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bea81-144">To learn more about using subscriber data in a parameterized report, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
## <a name="modifying-the-subscriber-data-source"></a><span data-ttu-id="bea81-145">サブスクライバー データ ソースの変更</span><span class="sxs-lookup"><span data-stu-id="bea81-145">Modifying the Subscriber Data Source</span></span>  
 <span data-ttu-id="bea81-146">サブスクライバー データ ソースに以下の変更を加えると、サブスクリプションの実行を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="bea81-146">The following modifications to the subscriber data source can prevent the subscription from running:</span></span>  
  
-   <span data-ttu-id="bea81-147">サブスクリプションで参照されている列の削除</span><span class="sxs-lookup"><span data-stu-id="bea81-147">Removing columns that are referenced in the subscription.</span></span>  
  
-   <span data-ttu-id="bea81-148">データ ソースのテーブル構造の変更</span><span class="sxs-lookup"><span data-stu-id="bea81-148">Modifying the table structure of the data source.</span></span>  
  
-   <span data-ttu-id="bea81-149">データ型およびその他の列プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="bea81-149">Changing data type and other column properties.</span></span>  
  
 <span data-ttu-id="bea81-150">これらの変更のいずれかを行う場合は、サブスクリプションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bea81-150">If you make any of these changes, you must update the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea81-151">参照</span><span class="sxs-lookup"><span data-stu-id="bea81-151">See Also</span></span>  
 <span data-ttu-id="bea81-152">[データドリブンサブスクリプションの作成、変更、および削除](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="bea81-152">[Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="bea81-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="bea81-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="bea81-154">サブスクリプションと配信 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bea81-154">Subscriptions and Delivery &#40;Reporting Services&#41;</span></span>](subscriptions-and-delivery-reporting-services.md)  
  
  
