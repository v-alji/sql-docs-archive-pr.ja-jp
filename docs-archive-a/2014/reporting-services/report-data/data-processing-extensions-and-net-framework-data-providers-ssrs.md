---
title: データ処理拡張機能と .NET Framework データ プロバイダー (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd84af68af54b165c75317280bc19bb23da53366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712797"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a><span data-ttu-id="ab0d9-102">データ処理拡張機能と .NET Framework データ プロバイダー (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ab0d9-102">Data Processing Extensions and .NET Framework Data Providers (SSRS)</span></span>
  <span data-ttu-id="ab0d9-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能は、特定の種類のデータ ソースからのデータ取得や、レポート デザインやレポート処理をサポートする追加機能を提供することを目的として、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と共にインストールされるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension is a component installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], designed to retrieve data from a specific type of data source and to provide extra functionality to support report design and report processing.</span></span> <span data-ttu-id="ab0d9-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーは、特定の種類のデータ ソースからのデータの取得や変更を可能にする <xref:System.Data> インターフェイスをサポートするコンポーネントで、[!INCLUDE[msCoName](../../includes/msconame-md.md)] またはサード パーティ ソースから入手できます。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-104">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider is a component available from [!INCLUDE[msCoName](../../includes/msconame-md.md)] or third-party sources that supports <xref:System.Data> interfaces that allow you to retrieve and to modify data from a specific type of data source.</span></span>  
  
## <a name="understanding-a-data-processing-extension"></a><span data-ttu-id="ab0d9-105">データ処理拡張機能について</span><span class="sxs-lookup"><span data-stu-id="ab0d9-105">Understanding a Data Processing Extension</span></span>  
 <span data-ttu-id="ab0d9-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能では、<xref:System.Data> インターフェイスのサブセットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-106">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension supports a subset of the <xref:System.Data> interfaces.</span></span> <span data-ttu-id="ab0d9-107">データ処理拡張機能には、データ ソースへの読み取り専用アクセスのみが必要です。書き込みおよび更新用のインターフェイスは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-107">Data processing extensions require only read-only access to a data source, so the interfaces for write and update are not implemented.</span></span> <span data-ttu-id="ab0d9-108">それぞれのデータ処理拡張機能では、レポート処理をサポートするカスタム機能を設定できます。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-108">Each data processing extension can provide custom features to support report processing.</span></span> <span data-ttu-id="ab0d9-109">たとえば、データ処理拡張機能がサポートしている機能の種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-109">For example, a data processing extension might support the following types of features:</span></span>  
  
-   <span data-ttu-id="ab0d9-110">資格情報を接続文字列とは別に管理</span><span class="sxs-lookup"><span data-stu-id="ab0d9-110">Managing credentials separately from the connection string</span></span>  
  
-   <span data-ttu-id="ab0d9-111">複数値パラメーターのサポート</span><span class="sxs-lookup"><span data-stu-id="ab0d9-111">Supporting multivalue parameters</span></span>  
  
-   <span data-ttu-id="ab0d9-112">データ ソースで計算されたサーバー集計の取得</span><span class="sxs-lookup"><span data-stu-id="ab0d9-112">Retrieving server aggregates, which are calculated on the data source</span></span>  
  
-   <span data-ttu-id="ab0d9-113">データ ソースからのデータ プロパティおよびデータ値の取得</span><span class="sxs-lookup"><span data-stu-id="ab0d9-113">Retrieving data properties as well as data values from the data source</span></span>  
  
## <a name="understanding-a-data-provider"></a><span data-ttu-id="ab0d9-114">データ プロバイダーについて</span><span class="sxs-lookup"><span data-stu-id="ab0d9-114">Understanding a Data Provider</span></span>  
 <span data-ttu-id="ab0d9-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー (ドライバーと呼ばれることもある) では、データ ソースのデータを読み込み、書き込み、更新するための <xref:System.Data> インターフェイスの標準セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-115">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider (sometimes known as a driver) supports a standard set of <xref:System.Data> interfaces for reading, writing, and updating data on a data source.</span></span> <span data-ttu-id="ab0d9-116">データ プロバイダーは、特定の種類のデータ ソースに対して使用できるデータ処理拡張機能がない場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-116">A data provider can be used when there is no data processing extension available for a specific type of data source.</span></span> <span data-ttu-id="ab0d9-117">サード パーティの標準 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーは多数あります。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-117">Many third-party standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers are available.</span></span>  
  
 <span data-ttu-id="ab0d9-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には拡張可能なデータ プロバイダー アーキテクチャがあるので、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能によって提供される追加機能を含めたカスタムのデータ処理拡張機能を構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-118">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has an extensible data provider architecture, you can build a custom data processing extension to include the extra functionality supplied by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="ab0d9-119">詳細については、「 [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-119">For more information, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span> <span data-ttu-id="ab0d9-120">サード パーティのデータ処理拡張機能の詳細については、サード パーティのデータ処理拡張機能に付属するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-120">For third-party data processing extensions, see the documentation that comes with the third-party data processing extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab0d9-121">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーまたはカスタム データ処理拡張機能を使用してデータ ソースのデータにアクセスするには、インストールと登録が事前に完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-121">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or custom data processing extension must be installed and registered before it can be used to access data from a data source.</span></span> <span data-ttu-id="ab0d9-122">レポートを作成するためのレポート クライアントと、パブリッシュされたレポートを表示するためのレポート サーバーの両方で、データ処理拡張機能をインストールおよび登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-122">The data processing extension must be installed and registered both on the reporting client to author the report and on the report server to view the published report.</span></span> <span data-ttu-id="ab0d9-123">すべてのデータ プロバイダーがサーバー環境で機能するように設計されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-123">Not all data providers are designed to work in a server environment.</span></span> <span data-ttu-id="ab0d9-124">詳細については、「[標準 .NET Framework データ プロバイダーを登録する &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md)」と「[データ処理拡張機能の配置](../extensions/data-processing/deploying-a-data-processing-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab0d9-124">For more information, see [Register a Standard .NET Framework Data Provider &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md).and [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0d9-125">参照</span><span class="sxs-lookup"><span data-stu-id="ab0d9-125">See Also</span></span>  
 <span data-ttu-id="ab0d9-126">[データ処理拡張機能の概要](../extensions/data-processing/data-processing-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="ab0d9-126">[Data Processing Extensions Overview](../extensions/data-processing/data-processing-extensions-overview.md) </span></span>  
 [<span data-ttu-id="ab0d9-127">レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ab0d9-127">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
