---
title: Analysis Services | でサーバーのプロパティを構成するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
ms.openlocfilehash: 087154756960c6d53fbd66ca4c111ac157503a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640264"
---
# <a name="configure-server-properties-in-analysis-services"></a><span data-ttu-id="374cf-102">Analysis Services のサーバーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="374cf-102">Configure Server Properties in Analysis Services</span></span>
  <span data-ttu-id="374cf-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の管理者は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス用に既定のサーバー構成プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="374cf-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator can modify default server configuration properties for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="374cf-104">各インスタンスには、同じサーバーの他のインスタンスとは別に設定できる固有の構成プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="374cf-104">Each instance has its own configuration properties that can be set independently of other instances on the same server.</span></span>  
  
 <span data-ttu-id="374cf-105">サーバー プロパティを設定するには、SQL Server Management Studio を使用するか、特定のインスタンスの msmdsrv.ini ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="374cf-105">To set server properties, use SQL Server Management Studio or edit the msmdsrv.ini file of a specific instance.</span></span>  
  
 <span data-ttu-id="374cf-106">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="374cf-106">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="374cf-107">サーバー (インスタンス) のプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="374cf-107">Configure Server (Instance) Properties</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="374cf-108">サーバー プロパティ リファレンス</span><span class="sxs-lookup"><span data-stu-id="374cf-108">Server Property Reference</span></span>](#bkmk_ref)  
  
##  <a name="configure-server-instance-properties"></a><a name="bkmk_config"></a><span data-ttu-id="374cf-109">サーバー (インスタンス) のプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="374cf-109">Configure Server (Instance) Properties</span></span>  
 <span data-ttu-id="374cf-110">SQL Server Management Studio のプロパティ ページには、利用可能なプロパティのサブセットが含まれ、変更する可能性の高いプロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="374cf-110">The property pages in SQL Server Management Studio contain a subset of the available properties, showing only those properties that are more likely to be modified.</span></span> <span data-ttu-id="374cf-111">プロパティの完全なセットは msmdsrv.ini ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="374cf-111">The full set of properties can be found in the msmdsrv.ini file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="374cf-112">このトピックには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の配置構成プロパティに関する情報は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="374cf-112">This topic does not document the deployment configuration properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="374cf-113">配置構成の詳細については、「[ソリューション配置の構成設定の指定](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="374cf-113">For more information about deployment configuration, see [Specifying Configuration Settings for Solution Deployment](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).</span></span>  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a><span data-ttu-id="374cf-114">Management Studio での構成プロパティの表示または設定</span><span class="sxs-lookup"><span data-stu-id="374cf-114">View or set configuration properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="374cf-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="374cf-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="374cf-116">オブジェクト エクスプローラーで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="374cf-116">In Object Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and then click **Properties**.</span></span> <span data-ttu-id="374cf-117">[全般] ページが表示され、より使用頻度の高いプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="374cf-117">The General page appears, displaying the more commonly used properties.</span></span>  
  
2.  <span data-ttu-id="374cf-118">その他のプロパティを表示するには、ページ下部にある **[すべての詳細プロパティを表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="374cf-118">To view additional properties, click the **Show Advanced (All) Properties** checkbox at the bottom of the page.</span></span>  
  
     <span data-ttu-id="374cf-119">サーバー プロパティの変更は、テーブル モードおよび多次元モードのサーバーについてのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="374cf-119">Modifying server properties is supported only for tabular mode and multidimensional mode servers.</span></span> <span data-ttu-id="374cf-120">マイクロソフトの製品サポート エンジニアから別途指示された場合を除き、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールした場合は、必ず既定値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="374cf-120">If you installed [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], always use the default values unless you are directed otherwise by a Microsoft product support engineer.</span></span>  
  
     <span data-ttu-id="374cf-121">運用上またはパフォーマンス上の問題をサーバーのプロパティを通じて解消する方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="374cf-121">For guidance on how to address operational or performance issues through server properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
     <span data-ttu-id="374cf-122">サーバーのプロパティについては、Microsoft ホワイト ペーパー「 [SQL Server 2005 Analysis Services (SSAS) サーバー プロパティ](https://go.microsoft.com/fwlink/?LinkID=199102)」も参照してください。サーバーのプロパティの多くは、過去数回のリリースにわたり変更されていません。</span><span class="sxs-lookup"><span data-stu-id="374cf-122">You can also read about server properties (many of which are unchanged over the last several releases) in this Microsoft white paper, [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="374cf-123">一部のプロパティの設定は、msmdrsrv.ini ファイルでのみ行うことができます。</span><span class="sxs-lookup"><span data-stu-id="374cf-123">Some properties can only be set in the msmdrsrv.ini file.</span></span> <span data-ttu-id="374cf-124">詳細プロパティを表示しても設定する対象のプロパティが含まれていない場合は、msmdsrv.ini ファイルを直接編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="374cf-124">If the property you want to set is not visible even after you show advanced properties, you might need to edit the msmdsrv.ini file directly.</span></span>  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a><span data-ttu-id="374cf-125">msmdsrv.ini ファイルの構成プロパティの表示または編集</span><span class="sxs-lookup"><span data-stu-id="374cf-125">View or edit configuration properties in the msmdsrv.ini file</span></span>  
  
1.  <span data-ttu-id="374cf-126">開始する前に、Management Studio の [全般] プロパティページの**DataDir**プロパティをチェックして、msmdsrv.ini ファイルを含む Analysis Services プログラムファイルの場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="374cf-126">Before you begin, check the **DataDir** property in the General property page in Management Studio to verify the location of the Analysis Services program files, including the msmdsrv.ini file.</span></span> <span data-ttu-id="374cf-127">プログラム ファイルの場所を確認することで、確実に、目的のファイルに変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="374cf-127">Verifying the location of the program files will ensure that you are modifying the correct file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="374cf-128">既定のインストールでは、ファイルは \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="374cf-128">In a default installation, the file can be found in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder</span></span>  
  
2.  <span data-ttu-id="374cf-129">元のファイルに戻す必要がある場合は、ファイルのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="374cf-129">Create a backup of the file in case you need to revert to the original file.</span></span>  
  
3.  <span data-ttu-id="374cf-130">テキスト エディターを使用して、msmdsrv.ini ファイルを表示または編集します。</span><span class="sxs-lookup"><span data-stu-id="374cf-130">Use a text editor to view or edit the msmdsrv.ini file.</span></span>  
  
4.  <span data-ttu-id="374cf-131">ファイルを保存した後で、サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="374cf-131">After you save the file, you must restart the service.</span></span>  
  
##  <a name="server-property-reference"></a><a name="bkmk_ref"></a><span data-ttu-id="374cf-132">サーバープロパティのリファレンス</span><span class="sxs-lookup"><span data-stu-id="374cf-132">Server Property Reference</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="374cf-133">の構成プロパティは、システムを微調整するために重要です。</span><span class="sxs-lookup"><span data-stu-id="374cf-133">configuration properties are important for fine tuning your system.</span></span> <span data-ttu-id="374cf-134">たとえば、クエリ ログ動作を必要条件に合わせるために、関連するプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="374cf-134">For example, to make query log behavior consistent with your requirements, you can set the relevant properties.</span></span>  
  
 <span data-ttu-id="374cf-135">次のトピックでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のさまざまな構成プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="374cf-135">The following topics explain the various [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] configuration properties:</span></span>  
  
|<span data-ttu-id="374cf-136">トピック</span><span class="sxs-lookup"><span data-stu-id="374cf-136">Topic</span></span>|<span data-ttu-id="374cf-137">説明</span><span class="sxs-lookup"><span data-stu-id="374cf-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="374cf-138">全般プロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-138">General Properties</span></span>](general-properties.md)|<span data-ttu-id="374cf-139">全般プロパティには、基本プロパティと詳細プロパティの両方があり、データ ディレクトリ、バックアップ ディレクトリ、およびサーバーの他の動作を定義するプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-139">The general properties are both basic and advanced properties, and include properties that define the data directory, backup directory, and other server behaviors.</span></span>|  
|[<span data-ttu-id="374cf-140">データマイニングプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-140">Data Mining Properties</span></span>](data-mining-properties.md)|<span data-ttu-id="374cf-141">データ マイニング プロパティでは、どのデータ マイニング アルゴリズムを有効または無効にするかを制御します。</span><span class="sxs-lookup"><span data-stu-id="374cf-141">The data mining properties control which data mining algorithms are enabled and which are disabled.</span></span> <span data-ttu-id="374cf-142">既定では、すべてのアルゴリズムが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="374cf-142">By default, all of the algorithms are enabled.</span></span>|  
|<span data-ttu-id="374cf-143">DSO</span><span class="sxs-lookup"><span data-stu-id="374cf-143">DSO</span></span>|<span data-ttu-id="374cf-144">DSO は現在サポートされません。</span><span class="sxs-lookup"><span data-stu-id="374cf-144">DSO is no longer supported.</span></span> <span data-ttu-id="374cf-145">DSO のプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="374cf-145">DSO properties are ignored.</span></span>|  
|[<span data-ttu-id="374cf-146">Feature プロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-146">Feature Properties</span></span>](feature-properties.md)|<span data-ttu-id="374cf-147">機能プロパティは、製品の機能に関連しており、そのほとんどが詳細プロパティです。サーバー インスタンス間のリンクを制御するプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-147">The feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>|  
|[<span data-ttu-id="374cf-148">Filestore のプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-148">Filestore Properties</span></span>](filestore-properties.md)|<span data-ttu-id="374cf-149">ファイル ストア プロパティは、高度な用途のみを対象としています。</span><span class="sxs-lookup"><span data-stu-id="374cf-149">The file store properties are for advanced use only.</span></span> <span data-ttu-id="374cf-150">高度なメモリ管理設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-150">They include advanced memory management settings.</span></span>|  
|[<span data-ttu-id="374cf-151">ロックマネージャーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-151">Lock Manager Properties</span></span>](lock-manager-properties.md)|<span data-ttu-id="374cf-152">ロック マネージャー プロパティでは、ロックおよびタイムアウトに関連するサーバーの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="374cf-152">The lock manager properties define server behaviors pertaining to locking and timeouts.</span></span> <span data-ttu-id="374cf-153">これらのほとんどのプロパティは、高度な用途のみを対象としています。</span><span class="sxs-lookup"><span data-stu-id="374cf-153">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="374cf-154">ログのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-154">Log Properties</span></span>](log-properties.md)|<span data-ttu-id="374cf-155">ログ プロパティでは、サーバー上でイベントがログ記録される条件、場所、および方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="374cf-155">The log properties controls if, where, and how events are logged on the server.</span></span> <span data-ttu-id="374cf-156">これには、エラー ログ、例外ログ、フライト レコーダー、クエリ ログ、およびトレースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-156">This includes error logging, exception logging, flight recorder, query logging, and traces.</span></span>|  
|[<span data-ttu-id="374cf-157">メモリのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-157">Memory Properties</span></span>](memory-properties.md)|<span data-ttu-id="374cf-158">メモリ プロパティでは、サーバーでメモリが使用される方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="374cf-158">The memory properties control how the server uses memory.</span></span> <span data-ttu-id="374cf-159">主に高度な用途を対象としています。</span><span class="sxs-lookup"><span data-stu-id="374cf-159">They are primarily for advanced use.</span></span>|  
|[<span data-ttu-id="374cf-160">ネットワークのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-160">Network Properties</span></span>](network-properties.md)|<span data-ttu-id="374cf-161">ネットワーク プロパティでは、ネットワークに関連するサーバーの動作を制御します。圧縮およびバイナリ XML を制御するプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-161">The network properties control server behavior pertaining to networking, including properties that control compression and binary XML.</span></span> <span data-ttu-id="374cf-162">これらのほとんどのプロパティは、高度な用途のみを対象としています。</span><span class="sxs-lookup"><span data-stu-id="374cf-162">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="374cf-163">OLAP のプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-163">OLAP Properties</span></span>](olap-properties.md)|<span data-ttu-id="374cf-164">OLAP プロパティでは、キューブおよびディメンションの処理、レイジー処理、データのキャッシュ、およびクエリの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="374cf-164">The OLAP properties control cube and dimension processing, lazy processing, data caching, and query behavior.</span></span> <span data-ttu-id="374cf-165">基本プロパティと詳細プロパティの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-165">These include both basic and advanced properties.</span></span>|  
|[<span data-ttu-id="374cf-166">セキュリティのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-166">Security Properties</span></span>](security-properties.md)|<span data-ttu-id="374cf-167">セキュリティ セクションには、アクセス権を定義する基本プロパティと詳細プロパティの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="374cf-167">The security section contains both basic and advanced properties that define access permissions.</span></span> <span data-ttu-id="374cf-168">管理者およびユーザーに関連する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="374cf-168">This includes settings pertaining to administrators and users.</span></span>|  
|[<span data-ttu-id="374cf-169">スレッドプールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="374cf-169">Thread Pool Properties</span></span>](thread-pool-properties.md)|<span data-ttu-id="374cf-170">スレッド プール プロパティでは、サーバーによって作成されるスレッドの数を制御します。</span><span class="sxs-lookup"><span data-stu-id="374cf-170">The thread pool properties control how many threads the server creates.</span></span> <span data-ttu-id="374cf-171">これらは主に詳細プロパティです。</span><span class="sxs-lookup"><span data-stu-id="374cf-171">These are primarily advanced properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="374cf-172">参照</span><span class="sxs-lookup"><span data-stu-id="374cf-172">See Also</span></span>  
 <span data-ttu-id="374cf-173">[Analysis Services インスタンス管理](../instances/analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="374cf-173">[Analysis Services Instance Management](../instances/analysis-services-instance-management.md) </span></span>  
 [<span data-ttu-id="374cf-174">ソリューションの配置に関する構成設定の指定</span><span class="sxs-lookup"><span data-stu-id="374cf-174">Specifying Configuration Settings for Solution Deployment</span></span>](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
