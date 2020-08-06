---
title: 表示拡張機能の配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1c70d9cdc947134c682132b0baea02274ddf4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641496"
---
# <a name="deploying-a-rendering-extension"></a><span data-ttu-id="f68d7-102">表示拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="f68d7-102">Deploying a Rendering Extension</span></span>
  <span data-ttu-id="f68d7-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のレポート表示拡張機能は、作成して [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ライブラリにコンパイルした後、レポート サーバーおよびレポート デザイナーで検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-103">After you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report rendering extension into a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="f68d7-104">それには、拡張機能を適切なディレクトリにコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-104">To do so, copy the extension to the appropriate directory and add entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-rendering-extension-element"></a><span data-ttu-id="f68d7-105">構成ファイルの表示拡張機能要素</span><span class="sxs-lookup"><span data-stu-id="f68d7-105">Configuration File Rendering Extension Element</span></span>  
 <span data-ttu-id="f68d7-106">表示拡張機能を .DLL にコンパイルした後、rsreportserver.config ファイルにエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-106">Once a rendering extension has been compiled into a .DLL, you add an entry into the rsreportserver.config file.</span></span> <span data-ttu-id="f68d7-107">既定では、場所は%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。 \<InstanceName>\ レポート Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="f68d7-107">By default, the location is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="f68d7-108">親要素が \<Render> です。</span><span class="sxs-lookup"><span data-stu-id="f68d7-108">The parent element is \<Render>.</span></span> <span data-ttu-id="f68d7-109">Render 要素の下には、各表示拡張機能の Extension 要素があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-109">Under the Render element is an Extension element for each rendering extension.</span></span> <span data-ttu-id="f68d7-110">`Extension` 要素には、Name と Type という 2 つの属性があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-110">The `Extension` element contains two attributes, Name and Type.</span></span>  
  
 <span data-ttu-id="f68d7-111">次の表では、 `Extension` 表示拡張機能の要素の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-111">The following table describes the attributes for the `Extension` element for rendering extensions:</span></span>  
  
|<span data-ttu-id="f68d7-112">Attribute</span><span class="sxs-lookup"><span data-stu-id="f68d7-112">Attribute</span></span>|<span data-ttu-id="f68d7-113">説明</span><span class="sxs-lookup"><span data-stu-id="f68d7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f68d7-114">**Name**</span><span class="sxs-lookup"><span data-stu-id="f68d7-114">**Name**</span></span>|<span data-ttu-id="f68d7-115">拡張機能の一意の名前。</span><span class="sxs-lookup"><span data-stu-id="f68d7-115">A unique name for the extension.</span></span> <span data-ttu-id="f68d7-116">**Name** 属性の最大文字数は 255 文字です。</span><span class="sxs-lookup"><span data-stu-id="f68d7-116">The maximum length for the **Name** attribute is 255 characters.</span></span> <span data-ttu-id="f68d7-117">名前は、構成ファイルの **Extensions** 要素内のすべてのエントリの中で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-117">The name must be unique among all entries within the **Extensions** element of a configuration file.</span></span> <span data-ttu-id="f68d7-118">重複する名前がある場合には、レポート サーバーによってエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-118">If a duplicate name is present, the report server returns an error.</span></span>|  
|<span data-ttu-id="f68d7-119">**Type**</span><span class="sxs-lookup"><span data-stu-id="f68d7-119">**Type**</span></span>|<span data-ttu-id="f68d7-120">アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="f68d7-120">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|<span data-ttu-id="f68d7-121">**[表示]**</span><span class="sxs-lookup"><span data-stu-id="f68d7-121">**Visible**</span></span>|<span data-ttu-id="f68d7-122">値が `false` の場合、表示拡張機能がユーザー インターフェイスに表示されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-122">A value of `false` indicates that the rendering extension should not be visible in user interfaces.</span></span> <span data-ttu-id="f68d7-123">この属性が指定されない場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-123">If the attribute is not included, the default value is `true`.</span></span>|  
|<span data-ttu-id="f68d7-124">**LogAllExecutionRequests**</span><span class="sxs-lookup"><span data-stu-id="f68d7-124">**LogAllExecutionRequests**</span></span>|<span data-ttu-id="f68d7-125">値が `false` の場合、エントリがログに記録されるのは、セッションでレポートが最初に実行されるときのみであることを示します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-125">A value of `false` indicates that an entry is logged for only the first report execution in a session.</span></span> <span data-ttu-id="f68d7-126">この属性が指定されない場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-126">If the attribute is not included, the default value is `true`.</span></span><br /><br /> <span data-ttu-id="f68d7-127">この設定によって、レポートに最初に表示されるページについてのみエントリをログに記録するか (`false` の場合)、レポートに表示されるページごとにエントリをログに記録するか (`true` の場合) が決まります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-127">For example, this setting determines whether to log an entry for only the first page rendered in a report (when `false`) or an entry for each page rendered in the report (when `true`).</span></span>|  
  
 <span data-ttu-id="f68d7-128">詳しくは、「 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f68d7-128">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
## <a name="deploying-the-extension-to-the-report-server"></a><span data-ttu-id="f68d7-129">レポート サーバーへの拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="f68d7-129">Deploying the Extension to the Report Server</span></span>  
 <span data-ttu-id="f68d7-130">レポート サーバーでは、レポートを他の形式にエクスポートするとき、表示拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-130">The report server uses rendering extensions to export reports to other formats.</span></span> <span data-ttu-id="f68d7-131">レポート サーバーにプライベート アセンブリとして表示拡張機能アセンブリを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-131">You should deploy your rendering extension assembly to the report server as a private assembly.</span></span> <span data-ttu-id="f68d7-132">また、レポート サーバーの構成ファイル rsreportserver.config にエントリを作成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-132">You also need to make an entry in the report server configuration file, rsreportserver.config.</span></span>  
  
### <a name="to-deploy-the-assembly"></a><span data-ttu-id="f68d7-133">アセンブリを配置するには</span><span class="sxs-lookup"><span data-stu-id="f68d7-133">To deploy the assembly</span></span>  
  
1.  <span data-ttu-id="f68d7-134">ステージング場所から、表示拡張機能を使用するレポート サーバーの bin ディレクトリにアセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f68d7-134">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the rendering extension.</span></span> <span data-ttu-id="f68d7-135">レポートサーバーの Bin ディレクトリの既定の場所は、%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 です。 \<InstanceName>\ レポートます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-135">The default location of the report server Bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\Bin.</span></span>  
  
2.  <span data-ttu-id="f68d7-136">アセンブリ ファイルをコピーした後、rsreportserver.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-136">After the assembly file is copied, open the rsreportserver.config file.</span></span> <span data-ttu-id="f68d7-137">rsreportserver.config ファイルもレポート サーバーの bin ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-137">The rsreportserver.config file is also located in the report server bin directory.</span></span> <span data-ttu-id="f68d7-138">構成ファイルに拡張機能アセンブリ ファイルのエントリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-138">You need to make an entry in the configuration file for your extension assembly file.</span></span> <span data-ttu-id="f68d7-139">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] または簡単なテキスト エディターを使用して、ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-139">You can open the file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor.</span></span>  
  
     <span data-ttu-id="f68d7-140">詳しくは、「 [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f68d7-140">For more information, see [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
3.  <span data-ttu-id="f68d7-141">Rsreportserver.config ファイルで **Render** 要素を探します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-141">Locate the **Render** element in the Rsreportserver.config file.</span></span> <span data-ttu-id="f68d7-142">新しく作成した拡張機能のエントリは、次の場所に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-142">An entry for your newly created extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="f68d7-143">表示拡張機能のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="f68d7-143">Add an entry for your rendering extension.</span></span> <span data-ttu-id="f68d7-144">エントリには、 **Name** および **Type**の値で構成される要素を含める必要があります。このエントリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f68d7-144">Your entry should include an element that has values for **Name** and **Type**, and might look like the following:</span></span>  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     <span data-ttu-id="f68d7-145">**Name** の値は、表示拡張機能の一意な名前です。</span><span class="sxs-lookup"><span data-stu-id="f68d7-145">The value for **Name** is the unique name of the rendering extension.</span></span> <span data-ttu-id="f68d7-146">**Type** の値は、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 実装の完全修飾名前空間に続けて、アセンブリの名前 (.dll ファイル拡張子を含まない) をコンマで区切って指定したものです。</span><span class="sxs-lookup"><span data-stu-id="f68d7-146">The value for **Type** is a comma-separated list that includes an entry for the fully qualified namespace of your <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> implementation, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="f68d7-147">既定では、表示拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-147">By default, rendering extensions are visible.</span></span> <span data-ttu-id="f68d7-148">レポートマネージャーなどのユーザーインターフェイスから拡張機能を非表示にするには、要素に**Visible**属性を追加 `Extension` し、それをに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-148">To hide an extension from user interfaces, such as Report Manager, add a **Visible** attribute to the `Extension` element, and set it to `false`.</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="f68d7-149">配置の確認</span><span class="sxs-lookup"><span data-stu-id="f68d7-149">Verifying the deployment</span></span>  
 <span data-ttu-id="f68d7-150">また、レポート マネージャーを開き、配信拡張機能がレポートに有効なエクスポートの種類の一覧に含まれていることを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="f68d7-150">You can also open Report Manager and verify that your extension is included in the list of available export types for a report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f68d7-151">参照</span><span class="sxs-lookup"><span data-stu-id="f68d7-151">See Also</span></span>  
 <span data-ttu-id="f68d7-152">[表示拡張機能の実装](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="f68d7-152">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="f68d7-153">[表示拡張機能の概要](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="f68d7-153">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="f68d7-154">[IRenderingExtension インターフェイスの実装](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="f68d7-154">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 [<span data-ttu-id="f68d7-155">拡張機能のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f68d7-155">Security Considerations for Extensions</span></span>](../security-considerations-for-extensions.md)  
  
  
