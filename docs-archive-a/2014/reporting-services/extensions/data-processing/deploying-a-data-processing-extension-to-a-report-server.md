---
title: データ処理拡張機能をレポート サーバーに配置する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741614"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a><span data-ttu-id="a71e9-102">データ処理拡張機能をレポート サーバーに配置する方法</span><span class="sxs-lookup"><span data-stu-id="a71e9-102">How to: Deploy a Data Processing Extension to a Report Server</span></span>
  <span data-ttu-id="a71e9-103">レポート サーバーは、表示レポートのデータを取得および処理するためにデータ処理拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-103">Report servers use data processing extensions for retrieving and processing data in rendered reports.</span></span> <span data-ttu-id="a71e9-104">データ処理拡張機能のアセンブリは、プライベート アセンブリとしてレポート サーバーに配置してください。</span><span class="sxs-lookup"><span data-stu-id="a71e9-104">You should deploy your data processing extension assembly to a report server as a private assembly.</span></span> <span data-ttu-id="a71e9-105">また、レポート サーバーの構成ファイル RSReportServer.config にエントリを作成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-105">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a71e9-106">手順</span><span class="sxs-lookup"><span data-stu-id="a71e9-106">Procedures</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="a71e9-107">データ処理拡張機能のアセンブリを配置するには</span><span class="sxs-lookup"><span data-stu-id="a71e9-107">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="a71e9-108">ステージング場所から、データ処理拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="a71e9-108">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the data processing extension.</span></span> <span data-ttu-id="a71e9-109">レポートサーバーの bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。 \<*Instance Name*>\ レポートます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-109">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a71e9-110">この手順により、SQL Server の新しいインスタンスへのアップグレードが回避されます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-110">This step will prevent an upgrade to a newer instance of SQL Server.</span></span> <span data-ttu-id="a71e9-111">詳細については、「 [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a71e9-111">For more information, see [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
2.  <span data-ttu-id="a71e9-112">アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-112">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="a71e9-113">RSReportServer.config ファイルは、ReportServer ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-113">The RSReportServer.config file is located in the ReportServer directory.</span></span> <span data-ttu-id="a71e9-114">データ処理拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-114">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="a71e9-115">Visual Studio またはメモ帳などの簡単なテキスト エディターを使用して、構成ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-115">You can open the configuration file with Visual Studio or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="a71e9-116">RSReportServer.config ファイルで `Data` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-116">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="a71e9-117">新しく作成したデータ処理拡張機能のエントリは、次の場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-117">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="a71e9-118">データ処理拡張機能のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-118">Add an entry for your data processing extension.</span></span> <span data-ttu-id="a71e9-119">エントリには `Extension` 、との値を持つ要素が含まれている必要があり、 `Name` `Type` 次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-119">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     <span data-ttu-id="a71e9-120">`Name` の値は、データ処理拡張機能の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="a71e9-120">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="a71e9-121">`Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスおよび <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前が続きます。.dll ファイル拡張子は付けません。</span><span class="sxs-lookup"><span data-stu-id="a71e9-121">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="a71e9-122">既定では、データ処理拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-122">By default, data processing extensions are visible.</span></span> <span data-ttu-id="a71e9-123">レポート マネージャーなどのユーザー インターフェイスで拡張機能を非表示にするには、`Visible` 属性を `Extension` 要素に追加し、それを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-123">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="a71e9-124">拡張機能に `FullTrust` 権限を付与するカスタム アセンブリのコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-124">Add a code group for your custom assembly that grants `FullTrust` permission for your extension.</span></span> <span data-ttu-id="a71e9-125">これを行うには、%ProgramFiles%\Microsoft SQL Server<MSRS10_50 に既定で格納されている rssrvpolicy.config ファイルにコードグループを追加し \\ ます。 \<*Instance Name*>\ レポート Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="a71e9-125">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="a71e9-126">このコード グループは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a71e9-126">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="a71e9-127">URL 構成要素は、データ処理拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="a71e9-127">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="a71e9-128">[!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a71e9-128">For more information about code access security in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="a71e9-129">デプロイの確認</span><span class="sxs-lookup"><span data-stu-id="a71e9-129">Verifying the Deployment</span></span>  
 <span data-ttu-id="a71e9-130">データ処理拡張機能がレポート サーバーに正常に配置されたかどうかを確認するには、Web サービス <xref:ReportService2010.ReportingService2010.ListExtensions%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a71e9-130">You can verify whether your data processing extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="a71e9-131">レポート マネージャーを開いて、拡張機能が使用可能なデータ ソース一覧に含まれていることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="a71e9-131">You can also open Report Manager and verify that your extension is included in the list of available data sources.</span></span> <span data-ttu-id="a71e9-132">レポート マネージャーとデータ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a71e9-132">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a71e9-133">参照</span><span class="sxs-lookup"><span data-stu-id="a71e9-133">See Also</span></span>  
 <span data-ttu-id="a71e9-134">[データ処理拡張機能の配置](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="a71e9-134">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="a71e9-135">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a71e9-135">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="a71e9-136">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="a71e9-136">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="a71e9-137">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a71e9-137">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
