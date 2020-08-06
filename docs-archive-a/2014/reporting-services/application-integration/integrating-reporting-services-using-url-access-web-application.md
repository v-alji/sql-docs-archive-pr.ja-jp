---
title: Web アプリケーションでの URL アクセスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd31f76658f8160cbb2a576debc335588f77e72c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630809"
---
# <a name="using-url-access-in-a-web-application"></a><span data-ttu-id="376ba-102">Web アプリケーションでの URL アクセスの使用</span><span class="sxs-lookup"><span data-stu-id="376ba-102">Using URL Access in a Web Application</span></span>
  <span data-ttu-id="376ba-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の URL アクセスは、ネットワークを介して各レポートにアクセスできるように特別に設計されています。</span><span class="sxs-lookup"><span data-stu-id="376ba-103">URL access in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is specifically designed to enable access to individual reports over a network.</span></span> <span data-ttu-id="376ba-104">この種類のアクセスは、レポートの表示およびナビゲーションをカスタム Web アプリケーションに統合するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="376ba-104">This type of access is best for integrating report viewing and navigation into a custom Web application.</span></span> <span data-ttu-id="376ba-105">Web アプリケーションで URL アクセスを使用するには、次の方法があります。</span><span class="sxs-lookup"><span data-stu-id="376ba-105">To use URL access in Web applications, you can:</span></span>  
  
-   <span data-ttu-id="376ba-106">Web サイトまたはポータルから特定のレポート サーバーへの URL を指定する。</span><span class="sxs-lookup"><span data-stu-id="376ba-106">Address a URL to a specific report server from a Web site or portal.</span></span>  
  
-   <span data-ttu-id="376ba-107">フォームの POST メソッドを使用する。さらに、フォーム フィールドを使用してクエリ文字列パラメーターをレポート サーバーの URL に渡す。</span><span class="sxs-lookup"><span data-stu-id="376ba-107">Use a form POST method and pass query string parameters to a report server URL using form fields.</span></span>  
  
## <a name="url-access-through-direct-addressing"></a><span data-ttu-id="376ba-108">直接アドレス指定による URL アクセス</span><span class="sxs-lookup"><span data-stu-id="376ba-108">URL Access Through Direct Addressing</span></span>  
 <span data-ttu-id="376ba-109">URL を使用してレポート サーバーまたはレポート サーバー データベースのアイテムにアクセスする場合は、Web ブラウザーまたはアプリケーション内から URL アドレスを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="376ba-109">To access a report server or report server database item using a URL, simply provide the URL address from within a Web browser or application.</span></span> <span data-ttu-id="376ba-110">また、アクセス中のレポートまたはリソースの外観に影響を与える可能性がある URL にパラメーターを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="376ba-110">You can also supply parameters to the URL that can affect the appearance of the report or resource that is being accessed.</span></span> <span data-ttu-id="376ba-111">Web ブラウザーのアドレス バーで URL を指定してレポート サーバーを対象としたり、URL を大規模な Web アプリケーションまたはポータルの一部である **IFrame** のソースにしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="376ba-111">A URL can target a report server through the address bar of a Web browser, or a URL can be the source of an **IFrame** that is part of a larger Web application or portal.</span></span> <span data-ttu-id="376ba-112">レポートの特定のフレームを対象としたり、その過程で新しいブラウザー ウィンドウを開いたりするだけでなく、ポータルの Web ページでレポートのハイパーリンクを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="376ba-112">You can include hyperlinks to reports on various Web pages of your portal, as well as target a specific frame for the report or open a new browser window in the process.</span></span>  
  
 <span data-ttu-id="376ba-113">次の例では、ハイパーリンクは "main" という名前のフレームを対象とし、ハイパーリンクを含むハイパーリンクとは異なります。</span><span class="sxs-lookup"><span data-stu-id="376ba-113">In the following example, the hyperlink targets a frame named "main", which might be different from the one that includes the hyperlink.</span></span> <span data-ttu-id="376ba-114">ハイパーリンクは、Web ポータルの一部となる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="376ba-114">The hyperlink might be part of Web portal.</span></span>  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 <span data-ttu-id="376ba-115">前の例では、URL のクエリ文字列の "main" の値を使用して、デバイス情報設定 **LinkTarget** が渡されます。</span><span class="sxs-lookup"><span data-stu-id="376ba-115">In the previous example, the device information setting **LinkTarget** is passed with a value of "main" in the query string of the URL.</span></span> <span data-ttu-id="376ba-116">これにより、レポートのドリルスルー ハイパーリンクも確実に "main" という名前のフレームを対象とします。</span><span class="sxs-lookup"><span data-stu-id="376ba-116">This ensures that any drillthrough hyperlinks in the report also target the frame named "main".</span></span>  
  
 <span data-ttu-id="376ba-117">デバイス情報設定の詳細については、「[表示拡張機能にデバイス情報設定を渡す](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="376ba-117">For more information about device information settings, see [Passing Device Information Settings to Rendering Extensions](../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
 <span data-ttu-id="376ba-118">多くのサーバーおよびブラウザーでは、URL に使用可能な文字数が制限されているので注意してください。</span><span class="sxs-lookup"><span data-stu-id="376ba-118">Note that many servers and browsers limit the number of characters allowed in a URL.</span></span> <span data-ttu-id="376ba-119">場合によっては、256 文字の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="376ba-119">In some cases, a 256-character limit is imposed.</span></span> <span data-ttu-id="376ba-120">この制限を回避するには、フォーム送信による POST 要求を使用できます。</span><span class="sxs-lookup"><span data-stu-id="376ba-120">To get around this limitation, you can use POST requests using form submission.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="376ba-121">Internet Explorer の URL の最大文字数は 2,083 文字です。</span><span class="sxs-lookup"><span data-stu-id="376ba-121">Internet Explorer has a maximum URL length of 2,083 characters.</span></span> <span data-ttu-id="376ba-122">この制限は、URL を要求する POST および GET に適用されます。</span><span class="sxs-lookup"><span data-stu-id="376ba-122">This limit applies to both POST and GET request URLs.</span></span> <span data-ttu-id="376ba-123">ただし、フォームの一部として名前と値の組を送信する場合、POST は URL のサイズによる制限を受けません。これは、名前と値の組が URL でなくヘッダーで転送されるためです。</span><span class="sxs-lookup"><span data-stu-id="376ba-123">POST, however, is not limited by the size of the URL for submitting name/value pairs as part of a form, because they are transferred in the header and not the URL.</span></span>  
  
## <a name="url-access-through-a-form-post-method"></a><span data-ttu-id="376ba-124">フォームの POST メソッドを使用した URL アクセス</span><span class="sxs-lookup"><span data-stu-id="376ba-124">URL Access Through a Form POST Method</span></span>  
 <span data-ttu-id="376ba-125">URL アクセスを使用してレポート サーバーからデータを要求する場合、HTTP 要求では GET メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="376ba-125">When a user requests data from a report server using URL access, the HTTP request uses the GET method.</span></span> <span data-ttu-id="376ba-126">これは、METHOD="GET" の場合のフォーム送信と同じです。</span><span class="sxs-lookup"><span data-stu-id="376ba-126">This is equivalent to a form submission where METHOD="GET".</span></span> <span data-ttu-id="376ba-127">METHOD="GET" を使用した URL 要求またはフォーム送信は、サーバーまたは Web ブラウザーが処理できる最大文字数による制限を受けます。</span><span class="sxs-lookup"><span data-stu-id="376ba-127">URL requests or form submissions that use METHOD="GET" are limited by the maximum number of characters that a server or Web browser can process.</span></span>  
  
 <span data-ttu-id="376ba-128">POST 要求 (METHOD="POST" と入力フィールド) の場合、名前と値の組が URL ではなくヘッダーで転送されます。</span><span class="sxs-lookup"><span data-stu-id="376ba-128">With POST requests (METHOD="POST" and input fields), the name/value pairs are transferred in the header and not the URL.</span></span> <span data-ttu-id="376ba-129">したがって、クエリ文字列の名前と値の組は URL の一部ではないため、より長い、かつ複雑なパラメーター リストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="376ba-129">Therefore, the name/value pairs of the query string are not part of the URL, thus enabling you to provide much longer and more complex parameter lists.</span></span>  
  
 <span data-ttu-id="376ba-130">ユーザーは直接アクセスを使用して、レポート サーバーの URL を表示したり、クエリ文字列を変更したり、後で使用するために特定の URL 要求とレポート サーバー パラメーターを書き留めたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="376ba-130">Using direct access, a user can see the URL for the report server, and may be able to modify the  query string or note the particular URL request and report server parameters for later use.</span></span>  
  
 <span data-ttu-id="376ba-131">次の HTML サンプルは、特定の URL を使用してレポート サーバーを対象とし、クエリ文字列パラメーターをフォームの入力フィールドの一部として渡すことができるフォームの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="376ba-131">The following sample HTML demonstrates the use of a form that you can use to target a report server with a specific URL and pass query string parameters as part of the form's input fields.</span></span>  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 <span data-ttu-id="376ba-132">前の例では、フォームのボタンをクリックすると、レポート サーバーによって、現在のフレームで対象となっている HTML で表示されたレポートが返されます。</span><span class="sxs-lookup"><span data-stu-id="376ba-132">In the previous example, if a user clicks the button on the form, the report server returns an HTML-rendered report targeted at the current frame.</span></span> <span data-ttu-id="376ba-133">前の例に対して、この例での URL アクセスの文字列は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="376ba-133">A comparable URL access string might look like the following:</span></span>  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a><span data-ttu-id="376ba-134">参照</span><span class="sxs-lookup"><span data-stu-id="376ba-134">See Also</span></span>  
 <span data-ttu-id="376ba-135">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="376ba-135">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="376ba-136">[URL アクセスを使用した Reporting Services の統合](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="376ba-136">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="376ba-137">[Windows アプリケーションでの URL アクセスの使用](integrating-reporting-services-using-url-access-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="376ba-137">[Using URL Access in a Windows Application](integrating-reporting-services-using-url-access-windows-application.md) </span></span>  
 [<span data-ttu-id="376ba-138">URL アクセス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="376ba-138">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
