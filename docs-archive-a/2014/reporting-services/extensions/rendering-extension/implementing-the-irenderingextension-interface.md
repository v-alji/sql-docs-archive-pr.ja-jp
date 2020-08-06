---
title: IRenderingExtension インターフェイスの実装 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f57c4aa41ccfed165b69581cbf3917e4dfbb4960
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641493"
---
# <a name="implementing-the-irenderingextension-interface"></a><span data-ttu-id="6ca81-102">IRenderingExtension インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="6ca81-102">Implementing the IRenderingExtension Interface</span></span>
  <span data-ttu-id="6ca81-103">表示拡張機能では、実際のデータと組み合わされるレポート定義から出力結果を取得し、その結果データを使用可能な形式で表示します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-103">The rendering extension takes the results from a report definition that is combined with the actual data and renders the resulting data to a format that is useable.</span></span> <span data-ttu-id="6ca81-104">組み合わされたデータの変換と書式設定は、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> を実装する共通言語ランタイム (CLR) クラスを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-104">The transformation of the combined data and formatting is done by using a common language runtime (CLR) class that implements <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>.</span></span> <span data-ttu-id="6ca81-105">これにより、オブジェクト モデルは、ビューアーやプリンターなどの出力先で使用できる出力形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-105">This transforms the object model into an output format that is consumable by a viewer, printer, or other output target.</span></span>  
  
 <span data-ttu-id="6ca81-106"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> には、コーディングが必要なメソッドが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="6ca81-106">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> has three methods that must be coded:</span></span>  
  
-   <span data-ttu-id="6ca81-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> : レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - renders the report.</span></span>  
  
-   <span data-ttu-id="6ca81-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> : レポートの特定のストリームを表示します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - renders a specific stream from the report.</span></span>  
  
-   <span data-ttu-id="6ca81-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> : アイコンなどのレポートに必要な追加情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - gets additional information, such as icons, that are required for the report.</span></span>  
  
 <span data-ttu-id="6ca81-110">ここでは、これらのメソッドについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-110">The following sections discuss these methods in more detail.</span></span>  
  
## <a name="render-method"></a><span data-ttu-id="6ca81-111">Render メソッド</span><span class="sxs-lookup"><span data-stu-id="6ca81-111">Render Method</span></span>  
 <span data-ttu-id="6ca81-112"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> メソッドには、次のオブジェクトを表す引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-112">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> method contains arguments that represent the following objects:</span></span>  
  
-   <span data-ttu-id="6ca81-113">*report*: 表示するレポート。</span><span class="sxs-lookup"><span data-stu-id="6ca81-113">The *report* that you want to render.</span></span> <span data-ttu-id="6ca81-114">このオブジェクトには、レポートのプロパティ、データ、およびレイアウト情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-114">This object contains properties, data, and layout information for the report.</span></span> <span data-ttu-id="6ca81-115">レポートは、レポート オブジェクト モデル ツリーのルートです。</span><span class="sxs-lookup"><span data-stu-id="6ca81-115">The report is the root of the report object model tree.</span></span>  
  
-   <span data-ttu-id="6ca81-116">*ServerParameters*: 文字列辞書オブジェクト、およびレポート サーバーのパラメーター (存在する場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-116">The *ServerParameters* that contain the string dictionary object, with the parameters for the report server, if any.</span></span>  
  
-   <span data-ttu-id="6ca81-117">*deviceInfo*: デバイス設定を含むパラメーター。</span><span class="sxs-lookup"><span data-stu-id="6ca81-117">The *deviceInfo* parameter that contain the device settings.</span></span> <span data-ttu-id="6ca81-118">詳細については、「[表示拡張機能にデバイス情報設定を渡す](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ca81-118">For more information, see [Passing Device Information Settings to Rendering Extensions](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
-   <span data-ttu-id="6ca81-119">*clientCapabilities* パラメーター: 表示先クライアントに関する情報を格納している <xref:System.Collections.Specialized.NameValueCollection> 辞書オブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-119">The *clientCapabilities* parameter that contains a <xref:System.Collections.Specialized.NameValueCollection> dictionary object that has information about the client to which you are rendering.</span></span>  
  
-   <span data-ttu-id="6ca81-120">*RenderProperties*: 表示結果に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-120">The *RenderProperties* that contains information about the rendering result.</span></span>  
  
-   <span data-ttu-id="6ca81-121">*createAndRegisterStream*: 表示するストリームを取得するために呼び出すデリゲート関数。</span><span class="sxs-lookup"><span data-stu-id="6ca81-121">The *createAndRegisterStream* is a delegate function to be called to get a stream to render into.</span></span>  
  
### <a name="deviceinfo-parameter"></a><span data-ttu-id="6ca81-122">deviceInfo パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ca81-122">deviceInfo Parameter</span></span>  
 <span data-ttu-id="6ca81-123">*deviceInfo* パラメーターには、レポート パラメーターではなく、表示パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-123">The *deviceInfo* parameter contains rendering parameters, not report parameters.</span></span> <span data-ttu-id="6ca81-124">表示パラメーターは表示拡張機能に渡されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-124">These rendering parameters are passed to the rendering extension.</span></span> <span data-ttu-id="6ca81-125">*deviceInfo* 値は、レポート サーバーによって <xref:System.Collections.Specialized.NameValueCollection> オブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-125">The *deviceInfo* values are converted into a <xref:System.Collections.Specialized.NameValueCollection> object by the report server.</span></span> <span data-ttu-id="6ca81-126">*deviceInfo* パラメーターのアイテムは、大文字と小文字を区別しない値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-126">Items in the *deviceInfo* parameter are treated as case-insensitive values.</span></span> <span data-ttu-id="6ca81-127">URL アクセスによる表示要求が行われると、形式 `rc:key=value` の URL パラメーターが *deviceInfo* 辞書オブジェクトのキーと値のペアに変換されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-127">If the render request came as a result of URL access, the URL parameters in the form `rc:key=value` are converted to key/value pairs in the *deviceInfo* dictionary object.</span></span> <span data-ttu-id="6ca81-128">ブラウザー検出コードは、*clientCapabilities* 辞書のEcmaScriptVersion、JavaScript、MajorVersion、MinorVersion、Win32、Type および AcceptLanguage の項目も提供しています。</span><span class="sxs-lookup"><span data-stu-id="6ca81-128">The browser detection code also provides the following items in the *clientCapabilities* dictionary: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type, and AcceptLanguage.</span></span> <span data-ttu-id="6ca81-129">*deviceInfo* パラメーターに表示拡張機能が認識しない名前と値のペアがある場合は、すべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-129">Any name/value pair in the *deviceInfo* parameter that is not understood by the rendering extension is ignored.</span></span> <span data-ttu-id="6ca81-130">次のコード サンプルは、アイコンを取得する <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-130">The following code sample shows a sample <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method that retrieves icons:</span></span>  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a><span data-ttu-id="6ca81-131">RenderStream メソッド</span><span class="sxs-lookup"><span data-stu-id="6ca81-131">RenderStream Method</span></span>  
 <span data-ttu-id="6ca81-132"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> メソッドは、レポート内の特定のストリームを表示します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-132">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> method renders a particular stream from the report.</span></span> <span data-ttu-id="6ca81-133">最初の <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 呼び出しですべてのストリームが作成されますが、ストリームは最初はクライアントに返されません。</span><span class="sxs-lookup"><span data-stu-id="6ca81-133">All streams are created during the initial <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> call, but the streams are not returned to the client initially.</span></span> <span data-ttu-id="6ca81-134">このメソッドは、HTML 表示における画像などのセカンダリ ストリームや、画像 (EMF) などの複数ページ表示拡張機能の追加ページに使用します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-134">This method is used for secondary streams, such as images in HTML rendering, or additional pages of a multi-page rendering extension, such as Image/EMF.</span></span>  
  
## <a name="getrenderingresource-method"></a><span data-ttu-id="6ca81-135">GetRenderingResource メソッド</span><span class="sxs-lookup"><span data-stu-id="6ca81-135">GetRenderingResource Method</span></span>  
 <span data-ttu-id="6ca81-136"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドは、レポート全体を表示せずに情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ca81-136">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method retrieves the information without executing an entire rendering of the report.</span></span> <span data-ttu-id="6ca81-137">レポートに情報は必要だが、レポート自体を表示する必要がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ca81-137">There are times when the report requires information that does not require the report itself to be rendered.</span></span> <span data-ttu-id="6ca81-138">たとえば、表示拡張機能に関連付けられたアイコンが必要な場合は、1つのタグを含む*deviceInfo*パラメーターを使用し **\<Icon>** ます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-138">For example, if you need the icon associated with the rendering extension, use the *deviceInfo* parameter containing the single tag **\<Icon>**.</span></span> <span data-ttu-id="6ca81-139">このような場合に、<xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ca81-139">In these cases, you can use the <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca81-140">参照</span><span class="sxs-lookup"><span data-stu-id="6ca81-140">See Also</span></span>  
 <span data-ttu-id="6ca81-141">[表示拡張機能の実装](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="6ca81-141">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 [<span data-ttu-id="6ca81-142">表示拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="6ca81-142">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
  
  
