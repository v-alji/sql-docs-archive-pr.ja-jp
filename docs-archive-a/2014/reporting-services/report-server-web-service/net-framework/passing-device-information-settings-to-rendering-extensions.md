---
title: 表示拡張機能にデバイス情報設定を渡す | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713810"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a><span data-ttu-id="dce92-102">表示拡張機能にデバイス情報設定を渡す</span><span class="sxs-lookup"><span data-stu-id="dce92-102">Passing Device Information Settings to Rendering Extensions</span></span>
  <span data-ttu-id="dce92-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]では、デバイス情報設定を使用して、表示パラメーターを表示拡張機能に渡します。</span><span class="sxs-lookup"><span data-stu-id="dce92-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="dce92-104">レポート サーバー Web サービスの設定は **DeviceInfo** XML 要素として渡し、レポート サーバーで処理されます。</span><span class="sxs-lookup"><span data-stu-id="dce92-104">Settings in the Report Server Web service are passed as a **DeviceInfo** XML element and processed by the report server.</span></span> <span data-ttu-id="dce92-105">デバイス情報設定には既定値があるため、表示プロセスでは省略可能な引数と見なされます。</span><span class="sxs-lookup"><span data-stu-id="dce92-105">Because device information settings have default values, they are considered optional arguments in the rendering process.</span></span> <span data-ttu-id="dce92-106">しかし、デバイス情報設定を使用して、表示をカスタマイズし、サーバーで提供される既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="dce92-106">However, you can use device information settings to customize rendering and to override the default values that are supplied by the server.</span></span>  
  
 <span data-ttu-id="dce92-107">デバイス情報設定はさまざまな方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="dce92-107">You can specify device information settings in a variety of ways.</span></span> <span data-ttu-id="dce92-108">プログラムでは Render メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dce92-108">Programmatically, you can use the Render method.</span></span> <span data-ttu-id="dce92-109">URL によりレポートにアクセスする場合、URL パラメーターとしてデバイス情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dce92-109">If you are accessing a report through its URL, you can specify device information as URL parameters.</span></span> <span data-ttu-id="dce92-110">また、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルのデバイス情報設定を編集し、表示パラメーターをグローバルに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="dce92-110">You can also edit the device information settings in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files to specify rendering parameters globally.</span></span> <span data-ttu-id="dce92-111">表示パラメーターをグローバルで指定する方法については、「[RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce92-111">For more information about specifying rendering parameters globally, see [Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).</span></span>  
  
## <a name="passing-device-information-using-the-render-method"></a><span data-ttu-id="dce92-112">Render メソッドを使用してデバイス情報を渡す</span><span class="sxs-lookup"><span data-stu-id="dce92-112">Passing Device Information Using the Render Method</span></span>  
 <span data-ttu-id="dce92-113">表示拡張機能にデバイス情報設定を渡すには、<xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dce92-113">To pass device information settings to a rendering extension, use the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="dce92-114">たとえば、HTML に表示するときに HTML 断片を作成するには、次の XML 文字列を <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="dce92-114">For example, the following XML string can be passed to the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to create an HTML fragment when rendering to HTML.</span></span>  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 <span data-ttu-id="dce92-115">レポートが HTML 断片として表示される場合、レポートの内容は TABLE 要素内に含まれ、HTML または BODY 要素は使用されません。</span><span class="sxs-lookup"><span data-stu-id="dce92-115">When a report is rendered as an HTML fragment, the content of the report is contained within a TABLE element without the use of an HTML or BODY element.</span></span> <span data-ttu-id="dce92-116">HTML 断片を使用して、既存の HTML ドキュメントにレポートを組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="dce92-116">You can use the HTML fragment to incorporate the report into an existing HTML document.</span></span> <span data-ttu-id="dce92-117">HTML 出力のデバイス情報設定の詳細については、「[HTML デバイス情報設定](../../html-device-information-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce92-117">For more information about device information settings for HTML output, see [HTML Device Information Settings](../../html-device-information-settings.md).</span></span>  
  
## <a name="passing-device-information-using-url-access"></a><span data-ttu-id="dce92-118">URL アクセスを使用してデバイス情報を渡す</span><span class="sxs-lookup"><span data-stu-id="dce92-118">Passing Device Information Using URL Access</span></span>  
 <span data-ttu-id="dce92-119">URL アクセスを使用してデバイス情報設定を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="dce92-119">You can also pass device information settings through URL access.</span></span> <span data-ttu-id="dce92-120">デバイス情報設定は URL パラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="dce92-120">Device information settings are passed as URL parameters.</span></span> <span data-ttu-id="dce92-121">次の URL アクセス文字列をレポート サーバーに渡すと、HTML ビューアー ツール バーなしで表示するレポートを生成できます。</span><span class="sxs-lookup"><span data-stu-id="dce92-121">The following URL access string can be passed to the report server to generate a rendered report without the HTML viewer toolbar.</span></span>  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 <span data-ttu-id="dce92-122">詳細については、「[URL でデバイス情報設定を指定する](../../specify-device-information-settings-in-a-url.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dce92-122">For more information, see [Specify Device Information Settings in a URL](../../specify-device-information-settings-in-a-url.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce92-123">参照</span><span class="sxs-lookup"><span data-stu-id="dce92-123">See Also</span></span>  
 <span data-ttu-id="dce92-124">[表示拡張機能のデバイス情報設定 &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="dce92-124">[Device Information Settings for Rendering Extensions &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md) </span></span>  
 <span data-ttu-id="dce92-125">[RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="dce92-125">[Customize Rendering Extension Parameters in RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="dce92-126">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="dce92-126">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
