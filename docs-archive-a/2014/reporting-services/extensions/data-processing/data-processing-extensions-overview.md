---
title: データ処理拡張機能の概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e589d3a4e090aee52d2590c0b2ccff435c2321a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639905"
---
# <a name="data-processing-extensions-overview"></a><span data-ttu-id="55473-102">データ処理拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="55473-102">Data Processing Extensions Overview</span></span>
  <span data-ttu-id="55473-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を使用することによって、データ ソースに接続し、データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="55473-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="55473-104">データ処理拡張機能は、データ ソースとデータセット間のブリッジとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="55473-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="55473-105">のデータ処理拡張機能は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] データ プロバイダー インターフェイスのサブセットに倣っています。</span><span class="sxs-lookup"><span data-stu-id="55473-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>

 <span data-ttu-id="55473-106">次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えているデータ処理拡張機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="55473-106">The following table lists the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

|<span data-ttu-id="55473-107">データ処理拡張機能</span><span class="sxs-lookup"><span data-stu-id="55473-107">Data processing extension</span></span>|<span data-ttu-id="55473-108">説明</span><span class="sxs-lookup"><span data-stu-id="55473-108">Description</span></span>|
|-------------------------------|-----------------|
|<span data-ttu-id="55473-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 向けデータ処理拡張機能</span><span class="sxs-lookup"><span data-stu-id="55473-109">Data processing extension for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="55473-110">.NET Framework Data Provider for SQL Server を使用して [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]と接続し、データを取得します。</span><span class="sxs-lookup"><span data-stu-id="55473-110">Uses the .NET Framework Data Provider for SQL Server to connect to and retrieve data from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>|
|<span data-ttu-id="55473-111">OLE DB 向けデータ処理拡張機能</span><span class="sxs-lookup"><span data-stu-id="55473-111">Data processing extension for OLE DB</span></span>|<span data-ttu-id="55473-112">.NET Framework Data Provider for OLE DB を使用します。</span><span class="sxs-lookup"><span data-stu-id="55473-112">Uses the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="55473-113">この拡張機能を使用して、レポート サーバーは、OLE DB プロバイダーを持つすべてのデータ ソースをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="55473-113">With this extension, the report server can query any data source that has an OLE DB provider.</span></span>|
|<span data-ttu-id="55473-114">Oracle 向けデータ処理拡張機能</span><span class="sxs-lookup"><span data-stu-id="55473-114">Data processing extension for Oracle</span></span>|<span data-ttu-id="55473-115">.NET Framework Data Provider for Oracle を使用します。</span><span class="sxs-lookup"><span data-stu-id="55473-115">Uses the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="55473-116">この拡張機能を使用して、レポート サーバーは、Oracle クライアント接続ソフトウェアをとおして Oracle データ ソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="55473-116">With this extension, the report server can access Oracle data sources through Oracle client connectivity software.</span></span>|
|<span data-ttu-id="55473-117">ODBC 向けデータ処理拡張機能</span><span class="sxs-lookup"><span data-stu-id="55473-117">Data processing extension for ODBC</span></span>|<span data-ttu-id="55473-118">.NET Framework Data Provider for ODBC を使用します。</span><span class="sxs-lookup"><span data-stu-id="55473-118">Uses the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="55473-119">この拡張機能を使用して、レポート サーバーは、ODBC ドライバーが存在するすべてのデータベースのデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="55473-119">With this extension, the report server can access data in any database for which there is an ODBC driver.</span></span>|

 <span data-ttu-id="55473-120">[!INCLUDE[ssRS](../../../includes/ssrs.md)] データ処理 API を使用して、カスタム データ処理をレポート サーバーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="55473-120">You can use the [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing API to add custom data processing to your report server.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="55473-121">には、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のデータ プロバイダーに対するサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="55473-121">has built-in support for data providers in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="55473-122">既に完全なデータ プロバイダーを実装している場合は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="55473-122">If you have already implemented a full data provider, you do not need to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="55473-123">ただし、セキュリティで保護された接続の資格情報やサーバー側の集計など、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 に固有の機能を含むようにデータ プロバイダーの拡張を検討してください。</span><span class="sxs-lookup"><span data-stu-id="55473-123">However, you should consider extending your data provider to include functionality specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005, which includes secure connection credentials and server-side aggregates.</span></span>

 <span data-ttu-id="55473-124">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えている各データ処理拡張機能は、共通するインターフェイスのセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="55473-124">Each of the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a common set of interfaces.</span></span> <span data-ttu-id="55473-125">これにより、各拡張機能に比較機能が確実に実装されます。</span><span class="sxs-lookup"><span data-stu-id="55473-125">This ensures that each extension implements comparable functionality.</span></span>

 <span data-ttu-id="55473-126">独自のデータ ソース用のデータ処理拡張機能を開発できます。インターフェイスを使用して、データ処理の層を共通するデータベース インフラストラクチャに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="55473-126">You can develop data processing extensions for your own data sources, or you can use the interfaces to add an additional layer of data processing to common database infrastructures.</span></span> <span data-ttu-id="55473-127">カスタム データ処理拡張機能を配置して、組織の既存レポート サーバーにデータをシームレスに統合できます。</span><span class="sxs-lookup"><span data-stu-id="55473-127">You can deploy your custom data processing extensions to enable seamless integration of data into the existing report servers in your organization.</span></span> <span data-ttu-id="55473-128">ユーザーに提供するカスタム レポート スイートの一部として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="55473-128">You can also use them as part of a custom reporting suite that you provide to your consumers.</span></span>

 <span data-ttu-id="55473-129">![データ処理拡張機能のアーキテクチャ](../../media/bk-dataprocess-extensions.gif "データ処理拡張機能のアーキテクチャ")Reporting Services データ処理拡張機能のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="55473-129">![Data processing extension architecture](../../media/bk-dataprocess-extensions.gif "Data processing extension architecture") Reporting Services data processing extension architecture</span></span>

 <span data-ttu-id="55473-130">カスタム [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装する利点は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55473-130">The advantages to implementing a custom [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension include:</span></span>

-   <span data-ttu-id="55473-131">データ アクセス アーキテクチャを簡便化します。多くの場合、メンテナンスがしやすくなり、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="55473-131">A simplified data access architecture, often with better maintainability and improved performance.</span></span>

-   <span data-ttu-id="55473-132">拡張機能固有の機能をユーザーに直接提示できます。</span><span class="sxs-lookup"><span data-stu-id="55473-132">The ability to directly expose extension-specific functionality to consumers.</span></span>

-   <span data-ttu-id="55473-133">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 内のデータ ソースにユーザーが直接アクセスするための固有のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="55473-133">A specific interface for your consumers to access your data source within [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="data-extension-process-flow"></a><span data-ttu-id="55473-134">データ拡張機能の処理フロー</span><span class="sxs-lookup"><span data-stu-id="55473-134">Data Extension Process Flow</span></span>
 <span data-ttu-id="55473-135">カスタム データ拡張機能を開発する前に、レポート サーバーがデータ拡張機能を使用してどのようにデータを処理するか理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="55473-135">Before developing your custom data extension, you should understand how the report server uses data extensions to process data.</span></span> <span data-ttu-id="55473-136">レポート サーバーによって呼び出されるコンストラクターとメソッドも理解してください。</span><span class="sxs-lookup"><span data-stu-id="55473-136">You should also understand the constructors and methods that are called by the report server.</span></span>

 <span data-ttu-id="55473-137">![データ処理拡張機能のプロセスフロー](../../media/bk-ext-01.gif "データ処理拡張機能の処理の流れ")レポートサーバーによって呼び出されるデータ拡張機能のステップバイステップ処理フロー</span><span class="sxs-lookup"><span data-stu-id="55473-137">![Process flow for data processing extension](../../media/bk-ext-01.gif "Process flow for data processing extension") The step-by-step process flow of a data extension that is called by the report server</span></span>

 <span data-ttu-id="55473-138">この図は、次の順序によるイベントを示しています。</span><span class="sxs-lookup"><span data-stu-id="55473-138">The illustration shows the following sequence of events:</span></span>

1.  <span data-ttu-id="55473-139">レポート サーバーは、接続オブジェクトを作成し、レポートに関連付けられた接続文字列と資格情報を渡します。</span><span class="sxs-lookup"><span data-stu-id="55473-139">The report server creates a connection object and passes in the connection string and credentials associated with the report.</span></span>

2.  <span data-ttu-id="55473-140">レポートのコマンド テキストを使用して、コマンド オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="55473-140">The command text of the report is used to create a command object.</span></span> <span data-ttu-id="55473-141">このプロセスでは、コマンド テキストを解析し、コマンドのパラメーターを作成するコードがデータ処理拡張機能に含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="55473-141">In the process, the data processing extension may include code that parses the command text and creates any parameters for the command.</span></span>

3.  <span data-ttu-id="55473-142">コマンド オブジェクトとパラメーターを処理した後、データ リーダーを生成します。データ リーダーによって、結果セットが返され、レポート サーバーがレポート データをレポート レイアウトに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="55473-142">Once the command object and any parameters are processed, a data reader is generated that returns a result set and enables the report server to associate the report data with the report layout.</span></span>

## <a name="developer-requirements"></a><span data-ttu-id="55473-143">開発者要件</span><span class="sxs-lookup"><span data-stu-id="55473-143">Developer Requirements</span></span>
 <span data-ttu-id="55473-144">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を開発するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55473-144">Developing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension requires you to have:</span></span>

-   <span data-ttu-id="55473-145">レポート デザイナーまたはレポート サーバーがインストールされた配置用コンピューター</span><span class="sxs-lookup"><span data-stu-id="55473-145">A deployment computer with Report Designer or a report server installed.</span></span>

-   <span data-ttu-id="55473-146">[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]以上、または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ソフトウェア開発キット (SDK) がインストールされている開発用コンピューター。</span><span class="sxs-lookup"><span data-stu-id="55473-146">A development computer with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] or above, or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installed.</span></span>

-   <span data-ttu-id="55473-147">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の機能についてよく理解していること</span><span class="sxs-lookup"><span data-stu-id="55473-147">An in-depth understanding of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>

-   <span data-ttu-id="55473-148">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] アーキテクチャ、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] データプロバイダー、ADO.NET DataSet オブジェクト、および共通インターフェイスについての理解を深め [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="55473-148">An in-depth understanding of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] architecture, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data providers, ADO.NET DataSet objects, and the common [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] interfaces.</span></span>

-   <span data-ttu-id="55473-149">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# や .net などの言語での開発エクスペリエンス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="55473-149">Development experience in a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] language such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="55473-150">参照</span><span class="sxs-lookup"><span data-stu-id="55473-150">See Also</span></span>
 <span data-ttu-id="55473-151">拡張機能[ライブラリ Reporting Services](../reporting-services-extension-library.md)の[Reporting Services 拡張機能](../reporting-services-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="55473-151">[Reporting Services Extensions](../reporting-services-extensions.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


