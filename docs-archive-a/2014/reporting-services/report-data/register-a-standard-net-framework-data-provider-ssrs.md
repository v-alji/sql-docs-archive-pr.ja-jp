---
title: 標準 .NET Framework データ プロバイダーを登録する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fd26f9c7fa163d9e6005d42e24c7b1483987f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712773"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a><span data-ttu-id="34918-102">標準 .NET Framework データ プロバイダーを登録する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="34918-102">Register a Standard .NET Framework Data Provider (SSRS)</span></span>
  <span data-ttu-id="34918-103">サード パーティの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート データセット用のデータを取得するには、レポート作成クライアントとレポート サーバーの 2 か所に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリを配置し、登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-103">To use a third-party [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to retrieve data for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report dataset, you need to deploy and register the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly in two locations: on the report authoring client and on the report server.</span></span> <span data-ttu-id="34918-104">レポート作成クライアントでは、データ プロバイダーをデータ ソースの種類として登録し、それをクエリ デザイナーに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-104">On the report authoring client, you must register the data provider as a data source type and associate it with a query designer.</span></span> <span data-ttu-id="34918-105">これにより、レポート データセットを作成する際に、データ ソースの種類としてこのデータ プロバイダーを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="34918-105">You can then select this data provider as a type of data source when you create a report dataset.</span></span> <span data-ttu-id="34918-106">関連付けられているクエリ デザイナーが開き、それを利用してこのデータ ソースの種類に対するクエリを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="34918-106">The associated query designer opens to help you create queries for this data source type.</span></span> <span data-ttu-id="34918-107">レポート サーバーでは、データ プロバイダーをデータ ソースの種類として登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-107">On the report server, you must register the data provider as a data source type.</span></span> <span data-ttu-id="34918-108">そうすることで、このデータ プロバイダーを使用してデータ ソースからデータを取得するパブリッシュ済みレポートを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="34918-108">You can then process published reports that retrieve data from a data source using this data provider.</span></span>  
  
 <span data-ttu-id="34918-109">サード パーティのデータ プロバイダーには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能で使用できるすべての機能が用意されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="34918-109">Third-party data providers do not necessarily provide all the functionality available with the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="34918-110">詳細については、「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34918-110">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span> <span data-ttu-id="34918-111">.[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34918-111">To learn about extending the functionality of a .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span></span> <span data-ttu-id="34918-112">データ プロバイダーの機能の拡張については、「 [データ処理拡張機能の実装](../extensions/data-processing/implementing-a-data-processing-extension.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34918-112">data provider, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="34918-113">データ プロバイダーのインストールと登録を行うには、管理者の資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="34918-113">You need administrator credentials to install and register data providers.</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a><span data-ttu-id="34918-114">レポート サーバーへの .NET Framework データ プロバイダーの登録</span><span class="sxs-lookup"><span data-stu-id="34918-114">Registering a .NET Framework Data Provider on the Report Server</span></span>  
 <span data-ttu-id="34918-115">この [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーをレポート サーバーで使用するパブリッシュ済みレポートを処理するには、レポート サーバーにアセンブリをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-115">In order to process published reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider on the report server, you need to install the assembly on the report server.</span></span> <span data-ttu-id="34918-116">それには 2 つの構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-116">You must modify two configuration files.</span></span> <span data-ttu-id="34918-117">データ プロバイダーを登録するには、rsreportserver.config を変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-117">Modify rsreportserver.config to register the data provider.</span></span> <span data-ttu-id="34918-118">アセンブリにコード アクセス セキュリティ権限を許可するには、rssrvpolicy.config を変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-118">Modify rssrvpolicy.config to grant code access security permissions for the assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a><span data-ttu-id="34918-119">レポート サーバーにデータ プロバイダー アセンブリをインストールするには</span><span class="sxs-lookup"><span data-stu-id="34918-119">To install a data provider assembly on the report server</span></span>  
  
1.  <span data-ttu-id="34918-120">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用するレポート サーバーの bin ディレクトリの既定の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="34918-120">Navigate to the default location of the bin directory on the report server on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="34918-121">レポートサーバーの bin ディレクトリの既定の場所 *\<drive>* MSRS10_50 SQL Server は、MSSQLSERVER\Reporting ます。です。</span><span class="sxs-lookup"><span data-stu-id="34918-121">The default location of the report server bin directory is *\<drive>*:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span>  
  
2.  <span data-ttu-id="34918-122">ステージング場所からレポート サーバーの bin ディレクトリに、アセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="34918-122">Copy your assembly from your staging location to the bin directory of the report server.</span></span> <span data-ttu-id="34918-123">または、グローバル アセンブリ キャッシュ (GAC) にアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="34918-123">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="34918-124">詳細については、MSDN の [SDK ドキュメントの「](https://go.microsoft.com/fwlink/?linkid=63912) アセンブリとグローバル アセンブリ キャッシュの使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34918-124">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a><span data-ttu-id="34918-125">レポート サーバーに .NET データ プロバイダーを登録するには</span><span class="sxs-lookup"><span data-stu-id="34918-125">To register a .NET data provider on the report server</span></span>  
  
1.  <span data-ttu-id="34918-126">bin の親ディレクトリ ReportServer に、RSReportServer.config ファイルのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="34918-126">Make a backup of the RSReportServer.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="34918-127">RSReportServer.config を開きます。[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などの簡単なテキスト エディターを使用して、構成ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="34918-127">Open RSReportServer.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="34918-128">RSReportServer.config ファイルで `Data` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="34918-128">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="34918-129">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリは、次の場所に作成されます。</span><span class="sxs-lookup"><span data-stu-id="34918-129">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="34918-130">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="34918-130">Add an entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
    |<span data-ttu-id="34918-131">属性</span><span class="sxs-lookup"><span data-stu-id="34918-131">Attribute</span></span>|<span data-ttu-id="34918-132">説明</span><span class="sxs-lookup"><span data-stu-id="34918-132">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="34918-133">データ プロバイダーの固有名を入力します (たとえば「 **MyNETDataProvider**」など)。</span><span class="sxs-lookup"><span data-stu-id="34918-133">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="34918-134">`Name` 属性の最大文字数は 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="34918-134">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="34918-135">名前は、構成ファイルの `Extension` 要素内のすべてのエントリの中で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-135">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="34918-136">ここで指定した値は、新しいデータ ソースを作成する際にデータ ソースの種類を示すドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="34918-136">The value you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="34918-137"><xref:System.Data.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間と、その後に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリの名前 (.dll ファイル名拡張子を含まない) を指定する、コンマ区切りのリストを入力します。</span><span class="sxs-lookup"><span data-stu-id="34918-137">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="34918-138">たとえば、DLL に関する次のようなエントリがレポート サーバーの bin ディレクトリに配置されているとします。</span><span class="sxs-lookup"><span data-stu-id="34918-138">For example, the entry might resemble the following for a DLL deployed to the report server bin directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="34918-139">アセンブリをグローバル アセンブリ キャッシュ (GAC) に読み込む場合、厳密な名前のプロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-139">If you load your assembly into the global assembly cache (GAC), you must provide the strong name properties.</span></span> <span data-ttu-id="34918-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34918-140">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a><span data-ttu-id="34918-141">.NET データ プロバイダーのコード グループ ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="34918-141">To set the code group policy for a .NET data provider</span></span>  
  
1.  <span data-ttu-id="34918-142">bin の親ディレクトリ ReportServer に、rssrvpolicy.config ファイルのバックアップ コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="34918-142">Make a backup copy of the rssrvpolicy.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="34918-143">rssrvpolicy.config を開きます。またはメモ帳などの簡単なテキストエディターを使用して、構成ファイルを開くことができ [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="34918-143">Open rssrvpolicy.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="34918-144">rssrvpolicy.config ファイル内で `CodeGroup` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="34918-144">Locate the `CodeGroup` element in the rssrvpolicy.config file.</span></span>  
  
4.  <span data-ttu-id="34918-145">`FullTrust` 権限を許可するデータ プロバイダー アセンブリ用のコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="34918-145">Add a code group for the data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="34918-146">コード グループは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="34918-146">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="34918-147">URL メンバーシップは、多くのメンバーシップ条件の中からデータ プロバイダー用に選択した 1 つのみになります。</span><span class="sxs-lookup"><span data-stu-id="34918-147">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration"></a><span data-ttu-id="34918-148">配置と登録の検証</span><span class="sxs-lookup"><span data-stu-id="34918-148">Verifying the Deployment and Registration</span></span>  
 <span data-ttu-id="34918-149">レポート マネージャーを開き、データ プロバイダーが使用可能なデータ ソースの一覧に含まれていることを確認することで、データ プロバイダーがレポート サーバーに正常に配置されたかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="34918-149">You can verify whether the data provider was deployed successfully to the report server by opening Report Manager and verifying that the data provider is included in the list of available data sources.</span></span> <span data-ttu-id="34918-150">レポート マネージャーとデータ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34918-150">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a><span data-ttu-id="34918-151">レポート デザイナー クライアントへの .NET Framework データ プロバイダーの登録</span><span class="sxs-lookup"><span data-stu-id="34918-151">Registering a .NET Framework Data Provider on the Report Designer Client</span></span>  
 <span data-ttu-id="34918-152">この [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーをデータ ソースとして使用するレポートを作成するには、レポート デザイナーが実行されているクライアント コンピューターにアセンブリをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-152">In order to author reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider for a data source, you must install the assembly on your client computer that runs Report Designer.</span></span> <span data-ttu-id="34918-153">それには 2 つの構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-153">You must modify two configuration files.</span></span> <span data-ttu-id="34918-154">データ ソースとしてデータ プロバイダーを登録し、汎用クエリ デザイナーを使用できるようにするには、RSReportDesigner.config を変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-154">Modify RSReportDesigner.config to register the data provider as a data source and to use the generic query designer.</span></span> <span data-ttu-id="34918-155">データ プロバイダー アセンブリにコード アクセス セキュリティ権限を許可するには、RSPreviewPolicy.config を変更します。</span><span class="sxs-lookup"><span data-stu-id="34918-155">Modify RSPreviewPolicy.config to grant code access security permissions for the data provider assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a><span data-ttu-id="34918-156">レポート デザイナー クライアントにデータ プロバイダー アセンブリをインストールするには</span><span class="sxs-lookup"><span data-stu-id="34918-156">To install a data provider assembly on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="34918-157">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを使用するレポート デザイナー クライアントの PrivateAssemblies ディレクトリの既定の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="34918-157">Navigate to the default location of the PrivateAssemblies directory on the Report Designer client on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="34918-158">PrivateAssemblies ディレクトリの既定の場所は、 *\<drive>* 次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="34918-158">The default location of the PrivateAssemblies directory is *\<drive>*:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="34918-159">ステージング場所からレポート デザイナー クライアントの PrivateAssemblies ディレクトリに、アセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="34918-159">Copy your assembly from your staging location to the PrivateAssemblies directory of the Report Designer client.</span></span> <span data-ttu-id="34918-160">または、グローバル アセンブリ キャッシュ (GAC) にアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="34918-160">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="34918-161">詳細については、MSDN の [SDK ドキュメントの「](https://go.microsoft.com/fwlink/?linkid=63912) アセンブリとグローバル アセンブリ キャッシュの使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34918-161">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="34918-162">レポート デザイナー クライアントに .NET データ プロバイダーを登録するには</span><span class="sxs-lookup"><span data-stu-id="34918-162">To register a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="34918-163">PrivateAssemblies ディレクトリに RSReportDesigner.config ファイルのバックアップ コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="34918-163">Make a backup copy of the RSReportDesigner.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="34918-164">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] またはメモ帳などの簡単なテキスト エディターを使用して、RSReportDesigner.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="34918-164">Open RSReportDesigner.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="34918-165">RSReportDesigner.config ファイル内で `Data` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="34918-165">Locate the `Data` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="34918-166">データ プロバイダー用のエントリは、次の場所に作成されます。</span><span class="sxs-lookup"><span data-stu-id="34918-166">An entry for the data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="34918-167">データ プロバイダーのエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="34918-167">Add an entry for the data provider.</span></span>  
  
    |<span data-ttu-id="34918-168">属性</span><span class="sxs-lookup"><span data-stu-id="34918-168">Attribute</span></span>|<span data-ttu-id="34918-169">説明</span><span class="sxs-lookup"><span data-stu-id="34918-169">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="34918-170">データ プロバイダーの固有名を入力します (たとえば「 **MyNETDataProvider**」など)。</span><span class="sxs-lookup"><span data-stu-id="34918-170">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="34918-171">`Name` 属性の最大文字数は 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="34918-171">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="34918-172">名前は、構成ファイルの `Extension` 要素内のすべてのエントリの中で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-172">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="34918-173">ここで指定した値は、新しいデータ ソースを作成する際にデータ ソースの種類を示すドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="34918-173">The value that you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="34918-174"><xref:System.Data.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間と、その後に [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリの名前 (.dll ファイル名拡張子を含まない) を指定する、コンマ区切りのリストを入力します。</span><span class="sxs-lookup"><span data-stu-id="34918-174">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="34918-175">たとえば、DLL に関する次のようなエントリが [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の PrivateAssemblies ディレクトリに配置されているとします。</span><span class="sxs-lookup"><span data-stu-id="34918-175">For example, the entry might resemble the following for a DLL deployed to the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="34918-176">アセンブリを GAC に読み込む場合、厳密な名前のプロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-176">If you load your assembly into the GAC, you must provide the strong name properties.</span></span> <span data-ttu-id="34918-177">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34918-177">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  <span data-ttu-id="34918-178">RSReportDesigner.config ファイル内で `Designer` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="34918-178">Locate the `Designer` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="34918-179">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー用のエントリは、次の場所に作成されます。</span><span class="sxs-lookup"><span data-stu-id="34918-179">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  <span data-ttu-id="34918-180">RSReportDesigner.config ファイルの `Designer` 要素の下に、次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="34918-180">Add the following entry to the RSReportDesigner.config file under the `Designer` element.</span></span> <span data-ttu-id="34918-181">`Name` 属性の名前を前のエントリで入力した名前に置き換えるだけです。</span><span class="sxs-lookup"><span data-stu-id="34918-181">You need to replace only the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="34918-182">レポート デザイナー クライアントにおける .NET データ プロバイダーのコード グループ ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="34918-182">To set the code group policy for a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="34918-183">PrivateAssemblies ディレクトリに RSPreviewPolicy.config ファイルのバックアップ コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="34918-183">Make a backup copy of the RSPreviewPolicy.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="34918-184">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] または単純なテキスト エディター (メモ帳など) を使用して、RSPreviewPolicy.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="34918-184">Open RSPreviewPolicy.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="34918-185">RSPreviewPolicy.config ファイル内で `CodeGroup` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="34918-185">Locate the `CodeGroup` element in the RSPreviewPolicy.config file.</span></span>  
  
4.  <span data-ttu-id="34918-186">`FullTrust` 権限を許可する [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー アセンブリ用のコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="34918-186">Add a code group for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="34918-187">コード グループは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="34918-187">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="34918-188">URL メンバーシップは、多くのメンバーシップ条件の中からデータ プロバイダー用に選択した 1 つのみになります。</span><span class="sxs-lookup"><span data-stu-id="34918-188">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a><span data-ttu-id="34918-189">レポート デザイナー クライアントでの配置と登録の検証</span><span class="sxs-lookup"><span data-stu-id="34918-189">Verifying the Deployment and Registration on the Report Designer Client</span></span>  
 <span data-ttu-id="34918-190">配置を検証するには、ローカル コンピューターの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインスタンスをすべて閉じておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-190">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="34918-191">現在のセッションをすべて終了した後、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]で新しいレポート プロジェクトを作成することで、データ プロバイダーがレポート デザイナーに正常に配置されたかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="34918-191">After you have ended all current sessions, you can verify whether your data provider was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="34918-192">レポートの新しいデータセットを作成するときに、使用可能なデータ ソースの種類にそのデータ プロバイダーが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-192">The data provider should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="platform-considerations"></a><span data-ttu-id="34918-193">プラットフォームに関する注意点</span><span class="sxs-lookup"><span data-stu-id="34918-193">Platform Considerations</span></span>  
 <span data-ttu-id="34918-194">64 ビット (x64) プラットフォームでは、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] は 32 ビット WOW モードで動作します。</span><span class="sxs-lookup"><span data-stu-id="34918-194">On a 64-bit (x64) platform, [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] runs in 32-bit WOW mode.</span></span> <span data-ttu-id="34918-195">x64 プラットフォームでレポートを作成する場合、レポートをプレビューするためには、レポート作成クライアントに 32 ビットのデータ プロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-195">When you author reports on an x64 platform, you need 32-bit data providers installed on the report authoring client in order to preview your reports.</span></span> <span data-ttu-id="34918-196">同じシステムでレポートをパブリッシュした場合、レポート マネージャーでレポートを表示するためには x64 データ プロバイダーが必要になります。</span><span class="sxs-lookup"><span data-stu-id="34918-196">If you publish the report on the same system, you need x64 data providers to view the report with Report Manager.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="34918-197">は、 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]ベースのプラットフォームではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="34918-197">is not supported for [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based platforms.</span></span>  
  
 <span data-ttu-id="34918-198">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共にインストールするデータ処理拡張機能は、各プラットフォーム用にネイティブでコンパイルし、正しい場所にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-198">The data processing extensions that are installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] must be compiled natively for each platform and installed in the correct locations.</span></span> <span data-ttu-id="34918-199">カスタム データ プロバイダーまたは標準の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーを登録する場合、適切なプラットフォーム用にネイティブでコンパイルし、適切な場所にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-199">If you register a custom data provider or a standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider, it needs to be compiled natively for the appropriate platform and installed the appropriate locations.</span></span> <span data-ttu-id="34918-200">32 ビット プラットフォームで実行する場合、データ プロバイダーを 32 ビット プラットフォーム用にコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-200">If you are running on a 32-bit platform, the data provider must be compiled for a 32-bit platform.</span></span> <span data-ttu-id="34918-201">64 ビット プラットフォームで実行する場合、データ プロバイダーを 64 ビット プラットフォーム用にコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34918-201">If you are running on a 64-bit platform, the data provider must be compiled for the 64-bit platform.</span></span> <span data-ttu-id="34918-202">64 ビット インターフェイスでラップした 32 ビット データ プロバイダーを 64 ビット プラットフォームで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="34918-202">You cannot use a 32-bit data provider wrapped with 64-bit interfaces on a 64 bit platform.</span></span> <span data-ttu-id="34918-203">サード パーティ ソフトウェアを確認して、データ プロバイダーがインストール先のプラットフォームで動作するかどうか調べてください。</span><span class="sxs-lookup"><span data-stu-id="34918-203">Check your third-party software for information about whether the data provider will work on the installed platform.</span></span> <span data-ttu-id="34918-204">データ プロバイダーとプラットフォームのサポートの詳細については、「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34918-204">For more information about data providers and platform support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34918-205">参照</span><span class="sxs-lookup"><span data-stu-id="34918-205">See Also</span></span>  
 <span data-ttu-id="34918-206">[レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="34918-206">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="34918-207">[データ処理拡張機能の実装](../extensions/data-processing/implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="34918-207">[Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="34918-208">[Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="34918-208">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="34918-209">Reporting Services のコード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="34918-209">Code Access Security in Reporting Services</span></span>](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
