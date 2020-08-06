---
title: DQS の参照データ サービス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4ed286b5834d81f775ee097672bfbc861c0b369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641251"
---
# <a name="reference-data-services-in-dqs"></a><span data-ttu-id="3eee3-102">DQS の参照データ サービス</span><span class="sxs-lookup"><span data-stu-id="3eee3-102">Reference Data Services in DQS</span></span>
  <span data-ttu-id="3eee3-103">参照データとは、信頼されたパブリック ドメインで使用できる、またはプレミアム商用コンテンツ プロバイダーから提供される、関連または項目別のグローバル データ (エンタープライズの境界を超えるデータ) の正確で完全なセットを表します。</span><span class="sxs-lookup"><span data-stu-id="3eee3-103">Reference data refers to an accurate and complete set of related or categorized global data (beyond the boundaries of an enterprise) that is available at trusted public domains or from premium commercial content providers.</span></span>  
  
 <span data-ttu-id="3eee3-104">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) の Reference Data Service 機能を使用すると、サード パーティ参照データ プロバイダーをサブスクライブしたり、ビジネス データを高品質データに対して検証してビジネス データを簡単にクレンジングおよび強化することができます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-104">The Reference Data Service feature in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) enables you to subscribe to third-party reference data providers, and to easily cleanse and enrich your business data by validating it against their high-quality data.</span></span> <span data-ttu-id="3eee3-105">DQS 内から業界をリードするデータ品質サービス プロバイダーのサービスを使用して、クレンジング プロセス中にデータを標準化、修正、または強化できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-105">You can use services from leading data quality service providers from within DQS to standardize, correct, or enrich your data during the cleansing process.</span></span> <span data-ttu-id="3eee3-106">たとえば、市外局番コードや郵便番号の一覧を参照データに対して使用して、顧客の住所を検証できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-106">For example, you can use a list of area codes or zip codes against the reference data to validate addresses of your customers.</span></span>  
  
 <span data-ttu-id="3eee3-107">Reference Data Service 機能には、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="3eee3-107">The Reference Data Service feature has the following benefits:</span></span>  
  
-   <span data-ttu-id="3eee3-108">参照データを使用すると、参照データをサード パーティ企業で保証されているデータと比較してデータの品質を確保できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-108">Reference data enables you to ensure the quality of your data by comparing it to data guaranteed by a third-party company.</span></span>  
  
-   <span data-ttu-id="3eee3-109">参照データ処理は、DQS ナレッジ ベースの構築およびデータ品質プロジェクトに組み込まれているので、包括的なデータ品質プロセスを確立できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-109">The reference data process is incorporated into DQS knowledge base building and a data quality project, enabling you to institute a comprehensive data quality process.</span></span>  
  
-   <span data-ttu-id="3eee3-110">は、サードパーティ参照データプロバイダーから直接、または Azure Marketplace からの参照データの使用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3eee3-110">Supports using reference data from Azure Marketplace as well as directly from third party reference data providers.</span></span>  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a><span data-ttu-id="3eee3-111">Azure Marketplace から参照データを使用する</span><span class="sxs-lookup"><span data-stu-id="3eee3-111">Using Reference Data from Azure Marketplace</span></span>  
 <span data-ttu-id="3eee3-112">DQS では、Azure Marketplace の参照データを使用して、コンテンツプロバイダーが Marketplace を通じて参照データサービスを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3eee3-112">DQS supports using reference data from Azure Marketplace to enable content providers to provide reference data services through Marketplace.</span></span> <span data-ttu-id="3eee3-113">Marketplace は、高品質データおよびアプリケーションの単一のマーケットプレイスと配信チャネルをクラウド サービスとして提供するマイクロソフトのサービスです。</span><span class="sxs-lookup"><span data-stu-id="3eee3-113">Marketplace is a service from Microsoft that provides a single marketplace and delivery channel for high-quality data and applications as cloud services.</span></span> <span data-ttu-id="3eee3-114">Marketplace の詳細については、「 [Azure Marketplace につい](https://azuremarketplace.microsoft.com/marketplace/)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3eee3-114">For more information about Marketplace, see [Learn About Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/).</span></span>  
  
 <span data-ttu-id="3eee3-115">Marketplace と DQS のシームレスな統合により、DQS 内からのデータ品質プロジェクトに関する情報の検出、検索、および取得に関連付けられている手順が簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-115">The seamless integration between Marketplace and DQS simplifies the steps associated with discovering, exploring, and acquiring information for data quality projects from within DQS.</span></span> <span data-ttu-id="3eee3-116">このデータは DQS から使用され、DQS ユーザーはこのデータを使用して DQS、Marketplace、および参照データ サービス プロバイダーを革新的な方法で 1 つにまとめて、データの品質を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-116">The data is consumed from DQS, and helps DQS users achieve high data quality by bringing together DQS, Marketplace, and reference data service providers in an innovative way.</span></span>  
  
 <span data-ttu-id="3eee3-117">DQS でクレンジング アクティビティに Marketplace の参照データを使用するには、Marketplace アカウント キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="3eee3-117">To use reference data from Marketplace in DQS for the cleansing activity, you must have a Marketplace account key.</span></span> <span data-ttu-id="3eee3-118">Marketplace アカウント キーの作成は無料です。有料のデータセットをサブスクライブする場合にのみ料金がかかります。</span><span class="sxs-lookup"><span data-stu-id="3eee3-118">Creating a Marketplace account key is free, and you pay only if you subscribe to paid datasets.</span></span> <span data-ttu-id="3eee3-119">無料のデータセットのサブスクライブと使用には料金はかかりません。</span><span class="sxs-lookup"><span data-stu-id="3eee3-119">There is no charge for subscribing to, and using free datasets.</span></span> <span data-ttu-id="3eee3-120">Marketplace アカウントキーの作成の詳細については、「[アカウントの作成](https://go.microsoft.com/fwlink/?LinkId=212936)」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="3eee3-120">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span>  
  
 <span data-ttu-id="3eee3-121">また、DQS 内から次の Marketplace アクティビティを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-121">Additionally, you can perform the following Marketplace activities from within DQS:</span></span>  
  
-   <span data-ttu-id="3eee3-122">Marketplace でデータセットを参照する。</span><span class="sxs-lookup"><span data-stu-id="3eee3-122">Browse data sets in Marketplace.</span></span>  
  
-   <span data-ttu-id="3eee3-123">Marketplace アカウント キーを作成する。</span><span class="sxs-lookup"><span data-stu-id="3eee3-123">Create a Marketplace account key.</span></span>  
  
-   <span data-ttu-id="3eee3-124">アカウント キーやデータ プロバイダーのサブスクリプションなど、Marketplace アカウントの詳細を管理する。</span><span class="sxs-lookup"><span data-stu-id="3eee3-124">Manage your Marketplace account details such as account keys and subscriptions to data providers.</span></span>  
  
 <span data-ttu-id="3eee3-125">これらのアクティビティは、 **の** [構成] **画面の** [参照データ] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]タブで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-125">You can perform these activities in the **Reference Data** tab of the **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> <span data-ttu-id="3eee3-126">サード パーティ参照データ プロバイダーから参照データを直接使用する</span><span class="sxs-lookup"><span data-stu-id="3eee3-126">Using Reference Data Directly from the Third Party Reference Data Providers</span></span>  
 <span data-ttu-id="3eee3-127">インターネットに接続していないため Marketplace を使用できない場合は、DQS で組織のネットワーク内で使用できるデータ プロバイダーに直接接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-127">If you are not connected to the Internet and therefore cannot use Marketplace, DQS also supports direct connection to data providers that are available within your organization's network.</span></span> <span data-ttu-id="3eee3-128">ダイレクト オンライン サード パーティ参照データ プロバイダーの参照データを使用するには、DQS でデータ プロバイダーのレコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eee3-128">To use reference data from direct online third-party reference data providers, you have to create a record for the data provider in DQS.</span></span>  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> <span data-ttu-id="3eee3-129">参照データを使用してデータをクレンジングする方法</span><span class="sxs-lookup"><span data-stu-id="3eee3-129">How to Cleanse Data by Using the Reference Data</span></span>  
 <span data-ttu-id="3eee3-130">参照データを使用した DQS でのデータのクレンジングには、次の 3 つの手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-130">Cleansing your data in DQS using reference data includes the following three steps:</span></span>  
  
1.  <span data-ttu-id="3eee3-131">**DQS で参照データ プロバイダーの詳細を構成する**: DQS で参照データを使用する前に、DQS で参照データ サービスの詳細を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eee3-131">**Configuring the reference data provider details in DQS**: Before you can use reference data in DQS, you must configure reference data service details in DQS.</span></span>  
  
    1.  <span data-ttu-id="3eee3-132">Marketplace を使用している場合は、有効な Marketplace アカウント キーを指定し、Marketplace で [Data Quality Services](../data-quality-services/data-quality-services.md) データ カテゴリを参照して、必要なプロバイダーをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="3eee3-132">If you are using Marketplace, provide a valid Marketplace account key, browse to the [Data Quality Services](../data-quality-services/data-quality-services.md) data category in Marketplace, and subscribe to the required providers.</span></span>  
  
    2.  <span data-ttu-id="3eee3-133">ダイレクト オンライン参照データ プロバイダーを使用する場合は、ダイレクト参照データ プロバイダーを DQS に追加してから使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3eee3-133">If you are using a direct online reference data provider, you must add direct reference data provider details in DQS before you can use it.</span></span>  
  
     <span data-ttu-id="3eee3-134">DQS での参照データ プロバイダーの詳細の構成は、1 つのデータ プロバイダーに対して 1 回だけ実行するアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="3eee3-134">Configuring the reference data provider details in DQS is one time activity for a particular data provider.</span></span> <span data-ttu-id="3eee3-135">DQS 管理者だけが、DQS で参照データ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3eee3-135">Only DQS administrators can configure reference data settings in DQS.</span></span>  
  
2.  <span data-ttu-id="3eee3-136">**ナレッジ ベースのドメインまたは複合ドメインを参照データ サービスにマップする**: 手順 1. でサブスクライブまたは追加された適切な参照データ サービスに、ドメインまたは複合ドメインをマップします。</span><span class="sxs-lookup"><span data-stu-id="3eee3-136">**Map a domain/composite domain in a knowledge base to the reference data service**: Map a domain/composite domain to the appropriate reference data service subscribed/added in step 1.</span></span>  
  
3.  <span data-ttu-id="3eee3-137">**データ品質プロジェクトでマップされたドメインをクレンジング アクティビティに使用する**: **クレンジング** アクティビティのデータ品質プロジェクトを作成しているときに、手順 2. で参照データ サービスにマップされたドメインまたは複合ドメインを含むナレッジ ベースを選択し、クレンジング アクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="3eee3-137">**Use the Mapped Domains for the Cleansing activity in a data quality project**: While creating a data quality project for the **Cleansing** activity, select the knowledge base that contains domains/composite domains mapped with reference data services in step 2, and perform the cleansing activity.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3eee3-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3eee3-138">Related Tasks</span></span>  
  
|<span data-ttu-id="3eee3-139">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="3eee3-139">Task Description</span></span>|<span data-ttu-id="3eee3-140">トピック</span><span class="sxs-lookup"><span data-stu-id="3eee3-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="3eee3-141">Marketplace またはダイレクト オンライン サード パーティ データ プロバイダーの参照データ サービスを使用するように DQS を構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3eee3-141">Describes how to configure DQS to use reference data services from Marketplace or direct third-party online data providers.</span></span>|[<span data-ttu-id="3eee3-142">参照データを使用する DQS の構成</span><span class="sxs-lookup"><span data-stu-id="3eee3-142">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="3eee3-143">ナレッジ ベースのドメインまたは複合ドメインを参照データ サービスにマップする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3eee3-143">Describes how to map a domain/composite domain in a knowledge base to a reference data service.</span></span>|[<span data-ttu-id="3eee3-144">参照データにドメインまたは複合ドメインをアタッチする</span><span class="sxs-lookup"><span data-stu-id="3eee3-144">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="3eee3-145">参照データ サービスを使用してデータをクレンジングする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3eee3-145">Describes how to cleanse data using reference data service.</span></span>|[<span data-ttu-id="3eee3-146">参照データ &#40;外部&#41; のナレッジを使用したデータのクレンジング</span><span class="sxs-lookup"><span data-stu-id="3eee3-146">Cleanse Data Using Reference Data &#40;External&#41; Knowledge</span></span>](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
