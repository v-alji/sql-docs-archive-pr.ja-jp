---
title: 配信拡張機能の配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4a4e33266c8d3a27ce2a4ab5f568bdee349720f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646053"
---
# <a name="deploying-a-delivery-extension"></a><span data-ttu-id="8a159-102">配信拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="8a159-102">Deploying a Delivery Extension</span></span>
  <span data-ttu-id="8a159-103">配信拡張機能では、その構成情報を XML 構成ファイルの形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="8a159-103">Delivery extensions supply their configuration information in the form of an XML configuration file.</span></span> <span data-ttu-id="8a159-104">XML ファイルは、配信拡張機能に定義された XML スキーマに従います。</span><span class="sxs-lookup"><span data-stu-id="8a159-104">The XML file conforms to the XML schema defined for delivery extensions.</span></span> <span data-ttu-id="8a159-105">配信拡張機能により、構成ファイルを設定および変更するためのインフラストラクチャが提供されます。</span><span class="sxs-lookup"><span data-stu-id="8a159-105">Delivery extensions provide infrastructure for setting and modifying the configuration file.</span></span>  
  
 <span data-ttu-id="8a159-106">配信拡張機能を置き換えたり、アップグレードしたりしても、配信拡張機能を参照するすべてのサブスクリプションは有効なままです。</span><span class="sxs-lookup"><span data-stu-id="8a159-106">If a delivery extension is replaced or upgraded, all subscriptions that reference the delivery extension remain valid.</span></span>  
  
 <span data-ttu-id="8a159-107">ご自分の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能を [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のライブラリに書き込み、コンパイルした後、レポート サーバーがその拡張機能を検出できるように、その拡張機能を適切なディレクトリにコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の構成ファイルにエントリを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-107">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you must copy the extension to the appropriate directory and add an entry to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration file so the report server can locate it.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="8a159-108">構成ファイルの Extension 要素</span><span class="sxs-lookup"><span data-stu-id="8a159-108">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="8a159-109">構成ファイルでは、レポート サーバーに配置する配信拡張機能を `Extension` 要素として入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-109">Delivery extensions that you deploy to the report server need to be entered as `Extension` elements in the configuration file.</span></span> <span data-ttu-id="8a159-110">レポート サーバーの構成ファイルは、RSReportServer.config です。</span><span class="sxs-lookup"><span data-stu-id="8a159-110">The configuration file for the report server is RSReportServer.config.</span></span>  
  
 <span data-ttu-id="8a159-111">次の表では、配信拡張機能の `Extension` 要素の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a159-111">The following table describes the attributes for the `Extension` element for delivery extensions.</span></span>  
  
|<span data-ttu-id="8a159-112">Attribute</span><span class="sxs-lookup"><span data-stu-id="8a159-112">Attribute</span></span>|<span data-ttu-id="8a159-113">説明</span><span class="sxs-lookup"><span data-stu-id="8a159-113">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="8a159-114">拡張機能の一意な名前 (たとえば、電子メール配信拡張機能の場合は "レポート サーバーの電子メール"、ファイル共有配信拡張機能の場合は "レポート サーバーのファイル共有")。</span><span class="sxs-lookup"><span data-stu-id="8a159-114">A unique name for the extension (for example, "Report Server E-Mail" for the e-mail delivery extension or "Report Server FileShare" for the file share delivery extension).</span></span> <span data-ttu-id="8a159-115">`Name` 属性の最大文字数は 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="8a159-115">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="8a159-116">名前は、構成ファイルの `Extension` 要素内のすべてのエントリの中で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-116">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="8a159-117">重複する名前がある場合には、レポート サーバーによってエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="8a159-117">If a duplicate name is present, the report server returns an error.</span></span>|  
|`Type`|<span data-ttu-id="8a159-118">アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="8a159-118">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="8a159-119">`false` の値は、配信拡張機能がユーザー インターフェイスに表示されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="8a159-119">A value of `false` indicates that the delivery extension should not be visible in user interfaces.</span></span> <span data-ttu-id="8a159-120">この属性が指定されない場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="8a159-120">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="8a159-121">RSReportServer.config ファイルの詳細については、「[Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a159-121">For more information about the RSReportServer.config file, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="8a159-122">レポート サーバーへの拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="8a159-122">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="8a159-123">レポート サーバーでは、通知またはレポートを処理して配信するために配信拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a159-123">The report server uses delivery extensions for processing and delivering notifications or reports.</span></span> <span data-ttu-id="8a159-124">レポート サーバーには、プライベート アセンブリとして配信拡張機能アセンブリを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-124">You should deploy your delivery extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="8a159-125">また、レポート サーバーの構成ファイル RSReportServer.config にエントリを作成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="8a159-125">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a><span data-ttu-id="8a159-126">配信拡張機能アセンブリをレポート サーバーに配置するには</span><span class="sxs-lookup"><span data-stu-id="8a159-126">To deploy a deliver extension assembly to a report server</span></span>  
  
1.  <span data-ttu-id="8a159-127">ステージング場所から、配信拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="8a159-127">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the delivery extension.</span></span> <span data-ttu-id="8a159-128">レポートサーバーの bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。 \<InstanceName>\ レポートます。</span><span class="sxs-lookup"><span data-stu-id="8a159-128">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8a159-129">既存の配信拡張機能アセンブリを上書きする場合、まず、レポート サーバー サービスを停止してから、更新済みのアセンブリをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-129">If you are attempting to overwrite an existing delivery extension assembly, you must first stop the Report Server service before copying the updated assembly.</span></span> <span data-ttu-id="8a159-130">そのアセンブリをコピーした後で、サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="8a159-130">Restart your service after the assembly is through copying.</span></span>  
  
2.  <span data-ttu-id="8a159-131">アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a159-131">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="8a159-132">RSReportServer.config ファイルは、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にあります。 \<InstanceName>\ レポート Services\ReportServer ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="8a159-132">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="8a159-133">配信拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-133">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="8a159-134">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]またはメモ帳などの簡単なテキストエディターを使用して、構成ファイルを開くことができ [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8a159-134">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="8a159-135">RSReportServer.config ファイルで `Delivery` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="8a159-135">Locate the `Delivery` element in the RSReportServer.config file.</span></span> <span data-ttu-id="8a159-136">新しく作成した配信拡張機能のエントリは、次の場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-136">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="8a159-137">配信拡張機能のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a159-137">Add an entry for your delivery extension.</span></span> <span data-ttu-id="8a159-138">エントリには、`Extension` および `Name` の値で構成される `Type` 要素を含める必要があります。このエントリは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8a159-138">Your entry should include an `Extension` element with values for `Name` and `Type`, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="8a159-139">`Name` の値は、配信拡張機能の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="8a159-139">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="8a159-140">`Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前 (.dll ファイル拡張子は付けない) が続きます。</span><span class="sxs-lookup"><span data-stu-id="8a159-140">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="8a159-141">既定では、配信拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a159-141">By default, delivery extensions are visible.</span></span> <span data-ttu-id="8a159-142">レポート マネージャーなどのユーザー インターフェイスで拡張機能を非表示にするには、`Visible` 属性を `Extension` 要素に追加し、それを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a159-142">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="8a159-143">最後に、配信拡張機能の `FullTrust` 権限を与えるカスタム アセンブリのコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a159-143">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="8a159-144">これを行うには、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 に既定で格納されている rssrvpolicy.config ファイルにコードグループを追加します。 \<InstanceName>\ レポート Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="8a159-144">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="8a159-145">このコード グループは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8a159-145">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="8a159-146">URL 構成要素は、配信拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="8a159-146">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="8a159-147">[!INCLUDE[ssRS](../../../includes/ssrs.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a159-147">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see.[Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="deploying-the-extension-to-report-manager"></a><span data-ttu-id="8a159-148">レポート マネージャーへの配信拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="8a159-148">Deploying the Extension to Report Manager</span></span>  
 <span data-ttu-id="8a159-149">配信拡張機能によって <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装した場合、レポート マネージャーの [サブスクリプション] ページで配信拡張機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a159-149">If your delivery extension implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, your delivery extension can be used with the Report Manager Subscription page.</span></span> <span data-ttu-id="8a159-150">サブスクリプションのユーザー インターフェイスを有効にするには、拡張機能をレポート マネージャーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-150">To make the subscription user interface available, you need to deploy your extension to Report Manager.</span></span>  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a><span data-ttu-id="8a159-151">配信拡張機能アセンブリをレポート マネージャーに配置するには</span><span class="sxs-lookup"><span data-stu-id="8a159-151">To deploy a deliver extension assembly to Report Manager</span></span>  
  
1.  <span data-ttu-id="8a159-152">ステージング場所からレポート マネージャーの bin ディレクトリにアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="8a159-152">Copy your assembly from your staging location to the bin directory of Report Manager.</span></span> <span data-ttu-id="8a159-153">レポートマネージャー bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。 \<InstanceName>\ レポート Services\reportmanager\bin です。</span><span class="sxs-lookup"><span data-stu-id="8a159-153">The default location of the Report Manager bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager\bin.</span></span>  
  
2.  <span data-ttu-id="8a159-154">アセンブリ ファイルをコピーした後、RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a159-154">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="8a159-155">RSReportServer.config ファイルは、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にあります。 \<InstanceName>\ レポート Services\ReportServer ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="8a159-155">The RSReportServer.config file is located in the %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer directory.</span></span> <span data-ttu-id="8a159-156">配信拡張機能アセンブリ ファイルの構成ファイルにエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-156">You need to make an entry in the configuration file for your delivery extension assembly file.</span></span> <span data-ttu-id="8a159-157">Visual&#xA0;Studio .NET またはメモ帳などの簡単なテキスト エディターを使用して、構成ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="8a159-157">You can open the configuration file with Visual Studio .NET or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="8a159-158">RSReportServer.config ファイルで `DeliveryUI` 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="8a159-158">Locate the `DeliveryUI` element in the RSReportServer.config file.</span></span> <span data-ttu-id="8a159-159">新しく作成した配信拡張機能のエントリは、次の場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-159">An entry for your newly created delivery extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="8a159-160">配信拡張機能のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a159-160">Add an entry for your delivery extension.</span></span> <span data-ttu-id="8a159-161">エントリには `Extension` 、との値を持つ要素が含まれている必要があり、 `Name` `Type` 次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8a159-161">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="8a159-162">`Name` の値は、配信拡張機能の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="8a159-162">The value for `Name` is the unique name of the delivery extension.</span></span> <span data-ttu-id="8a159-163">`Type` の値は、<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装するクラスの完全修飾名前空間のエントリを含むコンマ区切りの一覧であり、その後にアセンブリの名前 (.dll ファイル拡張子は付けない) が続きます。</span><span class="sxs-lookup"><span data-stu-id="8a159-163">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> interface, followed by the name of your assembly (not including the .dll file extension).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8a159-164">`Name` 属性の値は、レポート サーバーとレポート マネージャーの両方の構成ファイルのエントリに対して同一にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a159-164">The value of the `Name` attribute must be identical for both the Report Server and Report Manager configuration file entries.</span></span> <span data-ttu-id="8a159-165">それらのエントリが同一でない場合は、サーバー構成が無効になります。</span><span class="sxs-lookup"><span data-stu-id="8a159-165">If they are not identical, your server configuration is not valid.</span></span>  
  
     <span data-ttu-id="8a159-166">最後に、配信拡張機能の `FullTrust` 権限を与えるカスタム アセンブリのコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a159-166">Finally, add a code group for your custom assembly that grants `FullTrust` permission for your delivery extension.</span></span> <span data-ttu-id="8a159-167">これを行うには、コードグループを既定で C:\Program の SQL Server \ MSRS10_50 にある RSmgrpolicy.config ファイルに追加します。 \<InstanceName>\ レポート Services\reportmanager</span><span class="sxs-lookup"><span data-stu-id="8a159-167">You do this by adding the code group to the RSmgrpolicy.config file located by default in C:\Program Files\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportManager.</span></span> <span data-ttu-id="8a159-168">このコード グループは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8a159-168">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     <span data-ttu-id="8a159-169">URL 構成要素は、配信拡張機能に選択できる多くの構成要素条件のうちの 1 つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="8a159-169">URL membership is only one of many membership conditions you might choose for your delivery extension.</span></span> <span data-ttu-id="8a159-170">のコードアクセスセキュリティの詳細について [!INCLUDE[ssRS](../../../includes/ssrs.md)] は、「[セキュリティで保護された開発 &#40;Reporting Services](../secure-development/secure-development-reporting-services.md) 」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="8a159-170">For more information about code access security in [!INCLUDE[ssRS](../../../includes/ssrs.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="8a159-171">デプロイの確認</span><span class="sxs-lookup"><span data-stu-id="8a159-171">Verifying the Deployment</span></span>  
 <span data-ttu-id="8a159-172">配信拡張機能が正常にレポート サーバーに配置されたかどうかを確認するには、Web サービスの <xref:ReportService2010.ReportingService2010.ListExtensions%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a159-172">You can verify whether your delivery extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="8a159-173">また、レポート マネージャーを開き、配信拡張機能がサブスクリプションに有効な配信拡張機能の一覧に含まれていることを確認する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="8a159-173">You can also open Report Manager and verify that your extension is included in the list of available delivery extensions for a subscription.</span></span> <span data-ttu-id="8a159-174">レポートマネージャーとサブスクリプションの詳細については、「[サブスクリプションと配信 &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a159-174">For more information about Report Manager and subscriptions, see [Subscriptions and Delivery &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a159-175">参照</span><span class="sxs-lookup"><span data-stu-id="8a159-175">See Also</span></span>  
 <span data-ttu-id="8a159-176">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="8a159-176">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="8a159-177">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8a159-177">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
