---
title: RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35a01e12fa4016d03717b008e4241c3be5e55236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741637"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a><span data-ttu-id="7d166-102">RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7d166-102">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>
  <span data-ttu-id="7d166-103">RSReportServer 構成ファイルで表示拡張機能パラメーターを設定すると、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーで実行されるレポートについて、既定のレポート表示動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="7d166-103">You can specify rendering extension parameters in the RSReportServer configuration file to override default report rendering behavior for reports that run on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="7d166-104">表示拡張機能パラメーターは、次のように目的に応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="7d166-104">You can modify rendering extension parameters to achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="7d166-105">レポート ツール バーのエクスポートの一覧での表示拡張機能の名前の表示方法を変更します (たとえば、"Web アーカイブ" を "MHTML" に変更する処理など)。または、別の言語に名前をローカライズします。</span><span class="sxs-lookup"><span data-stu-id="7d166-105">Change how the rendering extension name appears in the Export list of the report toolbar (for example, to change "Web archive" to "MHTML"), or localize the name to a different language.</span></span>  
  
-   <span data-ttu-id="7d166-106">異なる複数のレポート表示オプションをサポートするには、同じ表示拡張機能の複数のインスタンスを作成します (画像表示拡張機能の横モードと縦モードなど)。</span><span class="sxs-lookup"><span data-stu-id="7d166-106">Create multiple instances of the same rendering extension to support different report presentation options (for example, a portrait and landscape mode version of the Image rendering extension).</span></span>  
  
-   <span data-ttu-id="7d166-107">既定の表示拡張機能パラメーターを変更して、別の値を使用します (たとえば、画像表示拡張機能で既定の出力形式として TIFF を使用している場合、拡張機能パラメーターを変更して EMF を使用できます)。</span><span class="sxs-lookup"><span data-stu-id="7d166-107">Change the default rendering extension parameters to use different values (for example, the Image rendering extension uses TIFF as the default output format; you can modify the extension parameters to use EMF instead).</span></span>  
  
 <span data-ttu-id="7d166-108">表示拡張機能パラメーターへの変更は、レポート サーバーの表示操作にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="7d166-108">Changing the rendering extension parameters only affects rendering operations on the report server.</span></span> <span data-ttu-id="7d166-109">レポート デザイナーのレポート プレビューで表示拡張機能の設定はオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="7d166-109">You cannot override rendering extension settings in report preview in Report Designer.</span></span>  
  
 <span data-ttu-id="7d166-110">構成ファイルでの表示拡張機能パラメーターの設定は、表示拡張機能全体に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="7d166-110">Specifying rendering extension parameters in the configuration files affects rendering extensions globally.</span></span> <span data-ttu-id="7d166-111">構成ファイルの設定は、特定の表示拡張機能が使用されるたびに既定値に代わって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7d166-111">The settings in the configuration files are used in place of default values whenever a particular rendering extension is used.</span></span> <span data-ttu-id="7d166-112">特定のレポートまたは表示操作の表示拡張機能パラメーターを設定する場合は、 <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを使用するか、レポート URL にデバイス情報設定を指定することにより、デバイス情報をプログラムで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-112">If you want to set rendering extension parameters for a specific report or render operation, you must specify device information programmatically using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method or by specifying device information settings on a report URL.</span></span> <span data-ttu-id="7d166-113">表示操作のデバイス情報設定の詳細について、およびデバイス情報設定の一覧表示については、 [「表示拡張機能にデバイス情報設定を渡す」](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d166-113">For more information about specifying device information settings for a render operation, and to view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a><span data-ttu-id="7d166-114">RSReportServer.config の検索および変更</span><span class="sxs-lookup"><span data-stu-id="7d166-114">Finding and Modifying RSReportServer.config</span></span>  
 <span data-ttu-id="7d166-115">レポート出力形式の構成設定は、RSReportServer.config ファイルで表示拡張機能パラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="7d166-115">Configuration settings for report output formats are specified as rendering extension parameters in the RSReportServer.config file.</span></span> <span data-ttu-id="7d166-116">構成ファイルの表示拡張機能パラメーターを指定するには、表示パラメーターを設定する XML 構造の定義方法を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-116">To specify rendering extension parameters in the configuration files, you must know how to define the XML structures that set rendering parameters.</span></span> <span data-ttu-id="7d166-117">変更できる XML 構造は次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="7d166-117">There are two XML structures that you can modify:</span></span>  
  
-   <span data-ttu-id="7d166-118">`OverrideNames` 要素は、表示拡張機能の表示名と言語を定義しています。</span><span class="sxs-lookup"><span data-stu-id="7d166-118">The `OverrideNames` element defines the display name and language of the rendering extension.</span></span>  
  
-   <span data-ttu-id="7d166-119">`DeviceInfo` XML 構造は、表示拡張機能で使用するデバイス情報設定を定義しています。</span><span class="sxs-lookup"><span data-stu-id="7d166-119">The `DeviceInfo` XML structure defines the device information settings that are used by a rendering extension.</span></span> <span data-ttu-id="7d166-120">ほとんどの表示拡張機能パラメーターは、デバイス情報設定として指定されます。</span><span class="sxs-lookup"><span data-stu-id="7d166-120">Most rendering extension parameters are specified as device information settings.</span></span>  
  
 <span data-ttu-id="7d166-121">テキスト エディターでファイルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="7d166-121">You can use a text editor to modify the file.</span></span> <span data-ttu-id="7d166-122">RSReportServer.config ファイルは、\Reporting Services\Report Server\Bin フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="7d166-122">The RSReportServer.config file can be found in the \Reporting Services\Report Server\Bin folder.</span></span> <span data-ttu-id="7d166-123">構成ファイルの変更方法の詳細については、「[Reporting Services の構成ファイルの変更 &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d166-123">For more information about modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span>  
  
## <a name="changing-the-display-name"></a><span data-ttu-id="7d166-124">表示名の変更</span><span class="sxs-lookup"><span data-stu-id="7d166-124">Changing the Display Name</span></span>  
 <span data-ttu-id="7d166-125">表示拡張機能の表示名は、レポート ツール バーのエクスポート一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d166-125">The display name for a rendering extension appears in the Export list of the report toolbar.</span></span> <span data-ttu-id="7d166-126">既定の表示名の例として、Web アーカイブ、TIFF ファイル、Acrobat (PDF) ファイルなどがあります。</span><span class="sxs-lookup"><span data-stu-id="7d166-126">Examples of default display names include Web archive, TIFF file, and Acrobat (PDF) file.</span></span> <span data-ttu-id="7d166-127">構成ファイルで `OverrideNames` 要素を指定すると、既定の表示名をカスタム値に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="7d166-127">You can replace the default display name with a custom value by specifying the `OverrideNames` element in the configuration files.</span></span> <span data-ttu-id="7d166-128">また、単一の表示拡張機能の 2 つのインスタンスを定義する場合は、`OverrideNames` 要素を使用して、エクスポート一覧の各インスタンスを区別できます。</span><span class="sxs-lookup"><span data-stu-id="7d166-128">In addition, if you are defining two instances of a single rendering extension, you can use the `OverrideNames` element to distinguish each instance in the Export list.</span></span>  
  
 <span data-ttu-id="7d166-129">表示名はローカライズされるので、既定の表示名をカスタム値に置き換える場合は `Language` 属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-129">Because display names are localized, you must set the `Language` attribute if you are replacing the default display name with a custom value.</span></span> <span data-ttu-id="7d166-130">この設定を行わないと、指定した名前が無視されます。</span><span class="sxs-lookup"><span data-stu-id="7d166-130">Otherwise, any name that you specify will be ignored.</span></span> <span data-ttu-id="7d166-131">このとき、レポート サーバーのコンピューターに対して有効な言語値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-131">The language value that you set must be valid for the report server computer.</span></span> <span data-ttu-id="7d166-132">たとえば、フランス語のオペレーティング システムでレポート サーバーを実行している場合は、属性値に "fr-FR" を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-132">For example, if the report server is running on a French operating system, you should specify "fr-FR" as the attribute value.</span></span>  
  
 <span data-ttu-id="7d166-133">次の例は、英語のレポート サーバーにカスタム名を設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d166-133">The following example illustrates how to provide a custom name on an English report server:</span></span>  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a><span data-ttu-id="7d166-134">デバイス情報設定の変更</span><span class="sxs-lookup"><span data-stu-id="7d166-134">Changing Device Information Settings</span></span>  
 <span data-ttu-id="7d166-135">レポート サーバーに既に配置されている表示拡張機能で使用される既定のデバイス情報設定を変更するには、`DeviceInfo` XML 構造を構成ファイルに入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-135">To modify default device information settings that are used by a rendering extension that is already deployed on your report server, you must type the `DeviceInfo` XML structure into the configuration files.</span></span> <span data-ttu-id="7d166-136">各表示拡張機能は、その拡張機能に一意のデバイス情報設定をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7d166-136">Every rendering extension supports device information settings that are unique to that extension.</span></span> <span data-ttu-id="7d166-137">デバイス情報設定の完全な一覧については、 [「表示拡張機能にデバイス情報設定を渡す」](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d166-137">To view the complete list of device information settings, see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="7d166-138">次の例は、画像表示拡張機能の既定の設定を変更する XML 構造および構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d166-138">The following example provides an illustration of the XML structure and syntax that modifies the default settings of the Image rendering extension:</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a><span data-ttu-id="7d166-139">表示拡張機能に対する複数のエントリの構成</span><span class="sxs-lookup"><span data-stu-id="7d166-139">Configuring Multiple Entries for a Rendering Extension</span></span>  
 <span data-ttu-id="7d166-140">異なる複数のレポート表示オプションをサポートするために、同じ表示拡張機能の複数のインスタンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7d166-140">You can create multiple instances of the same rendering extension to support different report presentation options.</span></span> <span data-ttu-id="7d166-141">定義する各インスタンスには、さまざまな組み合わせのパラメーター値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7d166-141">Each instance that you define can have a different combination of parameter values.</span></span> <span data-ttu-id="7d166-142">既存の表示拡張機能の新しいインスタンスを定義する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d166-142">When defining new instances of an existing rendering extension, be sure to do the following:</span></span>  
  
-   <span data-ttu-id="7d166-143">拡張機能の一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d166-143">Specify a unique name for the extension.</span></span>  
  
     <span data-ttu-id="7d166-144">各インスタンスは、`Name` 属性に一意な値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d166-144">Each instance must have a unique value for the `Name` attribute.</span></span> <span data-ttu-id="7d166-145">次の例では、"IMAGE (EMF Landscape)" と "IMAGE (EMF Portrait)" を使用して、2 つのインスタンスを区別しています。</span><span class="sxs-lookup"><span data-stu-id="7d166-145">The following example uses the names "IMAGE (EMF Landscape)" and "IMAGE (EMF Portrait)" to distinguish between the two instances.</span></span>  
  
     <span data-ttu-id="7d166-146">既に配置されている表示拡張機能の名前を変更する場合は、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d166-146">Use caution when changing the name of a rendering extension that is already deployed.</span></span> <span data-ttu-id="7d166-147">表示拡張機能がプログラム内で指定されている場合は、特定の表示操作に使用するインスタンスの識別に、拡張名が使用されています。</span><span class="sxs-lookup"><span data-stu-id="7d166-147">Developers who specify rendering extensions programmatically use the extension name to identify which instance to use for a particular render operation.</span></span> <span data-ttu-id="7d166-148">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のカスタム アプリケーションをレポート サーバーで実行する場合、既存の拡張機能名を変更したり、新しい拡張機能名を追加した際には、必ず開発者に知らせてください。</span><span class="sxs-lookup"><span data-stu-id="7d166-148">If you are running custom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applications on your report server, make sure that the developer knows if you modify an existing extension name or add a new one.</span></span>  
  
-   <span data-ttu-id="7d166-149">各出力形式の違いをユーザーが理解できるように、一意な表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d166-149">Specify a unique display name so that users can understand the differences for each output format.</span></span>  
  
     <span data-ttu-id="7d166-150">同じ拡張機能の複数のバージョンを構成している場合、`OverrideNames` に値を設定して、各バージョンに一意な名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7d166-150">If you are configuring multiple versions of the same extension, you can give each version a unique name by providing a value for `OverrideNames`.</span></span> <span data-ttu-id="7d166-151">このように指定しなかった場合は、すべてのバージョンの拡張機能が、レポート ツール バーのエクスポート オプションの一覧に同じ名前で表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d166-151">Otherwise, all versions of the extension will appear to have the same name in the Export options list on the report toolbar.</span></span>  
  
 <span data-ttu-id="7d166-152">次の例では、既定の画像表示拡張機能 (TIFF 出力を生成) を使用して縦モードの EMF を出力する方法と共に、横モードの EMF にレポートを出力する 2 番目のインスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="7d166-152">The following example illustrates how to use the default Image rendering extension (which produces TIFF output) to output EMF in Portrait mode alongside a second instance that outputs reports in EMF in Landscape mode.</span></span> <span data-ttu-id="7d166-153">各拡張機能名が一意であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d166-153">Notice that each extension name is unique.</span></span> <span data-ttu-id="7d166-154">この例をテストする際には、表示/非表示オプション、マトリックス、ドリルスルー リンクなどの対話機能が含まれないレポートを選択してください (対話機能は、画像表示拡張機能で動作しません)。</span><span class="sxs-lookup"><span data-stu-id="7d166-154">When testing this example, remember to choose reports that do not contain interactive features such as show/hide options, matrices, or drillthrough links (interactive features do not work in the Image rendering extension):</span></span>  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d166-155">参照</span><span class="sxs-lookup"><span data-stu-id="7d166-155">See Also</span></span>  
 <span data-ttu-id="7d166-156">[RSReportServer 構成ファイル](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-156">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="7d166-157">[RSReportDesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-157">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="7d166-158">[CSV デバイス情報設定](csv-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-158">[CSV Device Information Settings](csv-device-information-settings.md) </span></span>  
 <span data-ttu-id="7d166-159">[Excel デバイス情報設定](excel-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-159">[Excel Device Information Settings](excel-device-information-settings.md) </span></span>  
 <span data-ttu-id="7d166-160">[HTML デバイス情報設定](html-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-160">[HTML Device Information Settings](html-device-information-settings.md) </span></span>  
 <span data-ttu-id="7d166-161">[画像デバイス情報設定](image-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-161">[Image Device Information Settings](image-device-information-settings.md) </span></span>  
 <span data-ttu-id="7d166-162">[MHTML デバイス情報設定](mhtml-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-162">[MHTML Device Information Settings](mhtml-device-information-settings.md) </span></span>  
 <span data-ttu-id="7d166-163">[PDF デバイス情報の設定](pdf-device-information-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7d166-163">[PDF Device Information Settings](pdf-device-information-settings.md) </span></span>  
 [<span data-ttu-id="7d166-164">XML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="7d166-164">XML Device Information Settings</span></span>](xml-device-information-settings.md)  
  
  
