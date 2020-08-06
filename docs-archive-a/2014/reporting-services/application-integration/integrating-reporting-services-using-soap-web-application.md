---
title: Web アプリケーションでの SOAP API の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e228f01915df633f50b23bf93e892446863c28ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712829"
---
# <a name="using-the-soap-api-in-a-web-application"></a><span data-ttu-id="63dcf-102">Web アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="63dcf-102">Using the SOAP API in a Web Application</span></span>
  <span data-ttu-id="63dcf-103">Reporting Services SOAP API からは、レポート サーバーのすべての機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="63dcf-104">SOAP API は Web サービスであるため、容易にアクセスし、エンタープライズ レポート機能をカスタム ビジネス アプリケーションに取り入れることができます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-104">Because it's a Web service, the SOAP API can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="63dcf-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーションから SOAP API にアクセスするのと同じように、Web アプリケーションからレポート サーバー Web サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="63dcf-105">You access the Report Server Web service from a Web application in much the same way that you access the SOAP API from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="63dcf-106">を使用すると [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 、レポートサーバー Web サービスのプロパティとメソッドを公開するプロキシクラスを生成できます。また、使い慣れたインフラストラクチャとツールを使用して、テクノロジでビジネスアプリケーションを構築することができ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Report Server Web service and enables you to use a familiar infrastructure and tools to build business applications on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="63dcf-107">レポート管理機能は、Windows アプリケーションからと同様に、Web アプリケーションからも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-107">report management functionality is just as easily accessed from a Web application as from a Windows application.</span></span> <span data-ttu-id="63dcf-108">Web アプリケーションから、レポート サーバー データベースのアイテムの追加と削除、アイテム セキュリティの設定、レポート サーバー データベースのアイテムの変更、スケジューリングと配信の管理などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-108">From a Web application, you can add and remove items from the report server database, set item security, modify report server database items, manage scheduling and delivery, and more.</span></span>  
  
## <a name="enabling-impersonation"></a><span data-ttu-id="63dcf-109">権限借用の有効化</span><span class="sxs-lookup"><span data-stu-id="63dcf-109">Enabling Impersonation</span></span>  
 <span data-ttu-id="63dcf-110">Web アプリケーションを構成する最初の手順は、Web サービス クライアントからの権限借用を有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="63dcf-110">The first step in configuring your Web application is to enable impersonation from the Web service client.</span></span> <span data-ttu-id="63dcf-111">権限借用により、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションは代行するクライアントの ID を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-111">With impersonation, [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications can execute with the identity of the client on whose behalf they are operating.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="63dcf-112">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) を使用してユーザーを認証し、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションに認証済みトークンを渡すか、ユーザーを認証できない場合は未認証トークンを渡します。</span><span class="sxs-lookup"><span data-stu-id="63dcf-112">relies on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to authenticate the user and either pass an authenticated token to the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application or, if unable to authenticate the user, pass an unauthenticated token.</span></span> <span data-ttu-id="63dcf-113">どちらの場合も、権限借用が有効であれば、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションで受け取ったトークンの権限を借用します。</span><span class="sxs-lookup"><span data-stu-id="63dcf-113">In either case, the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] application impersonates whichever token is received if impersonation is enabled.</span></span> <span data-ttu-id="63dcf-114">クライアントの権限借用を有効にするには、次のようにクライアント アプリケーションの Web.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="63dcf-114">You can enable impersonation on the client, by modifying the Web.config file of the client application as follows:</span></span>  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="63dcf-115">既定では、権限借用は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="63dcf-115">Impersonation is disabled by default.</span></span>  
  
 <span data-ttu-id="63dcf-116">権限借用の詳細については [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 、SDK のドキュメントを参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63dcf-116">For more information about [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] impersonation, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="managing-the-report-server-using-soap-api"></a><span data-ttu-id="63dcf-117">SOAP API を使用したレポート サーバーの管理</span><span class="sxs-lookup"><span data-stu-id="63dcf-117">Managing the Report Server using SOAP API</span></span>  
 <span data-ttu-id="63dcf-118">Web アプリケーションを使用してレポート サーバーとその内容を管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-118">You can also use your Web application to manage a report server and its contents.</span></span> <span data-ttu-id="63dcf-119">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共に含まれているレポート マネージャーは、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] と Reporting Services SOAP API を使用して完全に構築された Web アプリケーションの一例です。</span><span class="sxs-lookup"><span data-stu-id="63dcf-119">Report Manager, included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], is an example of a Web application that is completely built using [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] and the Reporting Services SOAP API.</span></span> <span data-ttu-id="63dcf-120">レポート マネージャーのレポート管理機能はカスタム Web アプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-120">You can add the report management functionality of Report Manager to your custom Web applications.</span></span> <span data-ttu-id="63dcf-121">たとえば、レポートサーバーデータベースで使用可能なレポートの一覧を返し、ユーザーが選択できるようにコントロールに表示することができ [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` ます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-121">For example, you might want to return a list of available reports in the report server database and display them in a [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` control for your users to choose from.</span></span> <span data-ttu-id="63dcf-122">次のコードでは、レポート サーバー データベースに接続し、レポート サーバー データベースのアイテムの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="63dcf-122">The following code connects to the report server database and returns a list of items in the report server database.</span></span> <span data-ttu-id="63dcf-123">利用可能なレポートは Listbox コントロールに追加され、各レポートのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63dcf-123">The available reports are then added to a Listbox control, which displays the path of each report.</span></span>  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="63dcf-124">参照</span><span class="sxs-lookup"><span data-stu-id="63dcf-124">See Also</span></span>  
 <span data-ttu-id="63dcf-125">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="63dcf-125">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="63dcf-126">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="63dcf-126">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="63dcf-127">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="63dcf-127">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="63dcf-128">Windows アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="63dcf-128">Using the SOAP API in a Windows Application</span></span>](integrating-reporting-services-using-soap-windows-application.md)  
  
  
