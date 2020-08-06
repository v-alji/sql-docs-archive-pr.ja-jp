---
title: Windows アプリケーションでの SOAP API の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- Windows applications [Reporting Services]
- Windows Forms [Reporting Services]
- SOAP [Reporting Services], Windows applications
ms.assetid: e4804792-20cd-4df2-9257-fb958ff447b4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 115ce02da69a8adb2c7a3de4175e528f281eb2b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630814"
---
# <a name="using-the-soap-api-in-a-windows-application"></a><span data-ttu-id="2c80e-102">Windows アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="2c80e-102">Using the SOAP API in a Windows Application</span></span>
  <span data-ttu-id="2c80e-103">Reporting Services SOAP API からは、レポート サーバーのすべての機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-103">You can access the full functionality of the report server through the Reporting Services SOAP API.</span></span> <span data-ttu-id="2c80e-104">SOAP API は Web サービスです。したがって、SOAP API に容易にアクセスし、エンタープライズ レポート機能をカスタム ビジネス アプリケーションに取り入れることができます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-104">The SOAP API is a Web service and, as such, can be easily accessed to provide enterprise reporting features to your custom business applications.</span></span> <span data-ttu-id="2c80e-105">Windows アプリケーションの Web サービスにアクセスするには、サービスへの呼び出しを作成するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-105">You can access the Web service in a Windows application simply by writing code that makes calls to the service.</span></span> <span data-ttu-id="2c80e-106">を使用すると [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 、Web サービスのプロパティとメソッドを公開するプロキシクラスを生成し、使い慣れたインフラストラクチャとツールを使用して、テクノロジに基づいて構築されたビジネスアプリケーションを構築でき [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-106">Using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can generate a proxy class that exposes the properties and methods of the Web service and enables you to use a familiar infrastructure and tools to build business applications built on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technology.</span></span>  
  
## <a name="integrating-report-management-functionality-using-windows-forms"></a><span data-ttu-id="2c80e-107">Windows フォームを使用したレポート管理機能の統合</span><span class="sxs-lookup"><span data-stu-id="2c80e-107">Integrating Report Management Functionality Using Windows Forms</span></span>  
 <span data-ttu-id="2c80e-108">SOAP API は、URL アクセスとは異なり、レポート サーバーで使用できる管理機能の完全なセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-108">Unlike URL access, the SOAP API exposes the complete set of management functions that are available through the report server.</span></span> <span data-ttu-id="2c80e-109">つまり、SOAP を使用すれば、開発者はレポート マネージャーのすべての管理機能を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-109">This means that the entire administrative functionality of Report Manager is available to developers through SOAP.</span></span> <span data-ttu-id="2c80e-110">したがって、Windows フォームを使用して完全な管理ツールを開発できます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-110">As such, you can develop a complete management and administration tool using Windows Forms.</span></span> <span data-ttu-id="2c80e-111">たとえば、Windows アプリケーションにおいて、レポート サーバー名前空間のコンテンツをユーザーが取得できるようにするとします。</span><span class="sxs-lookup"><span data-stu-id="2c80e-111">For example, in your Windows application, you might want to enable your users to retrieve the contents of the report server namespace.</span></span> <span data-ttu-id="2c80e-112">そのためには、Web サービス <xref:ReportService2010.ReportingService2010.ListChildren%2A> メソッドを使用してレポート サーバー データベースの全アイテムを一覧表示した後、Listview、Treeview、または Combobox コントロールを使用してアイテムをユーザーに表示します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-112">To do this, you could use the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method to list all the items in the report server database and then use a Listview, Treeview, or Combobox control to display those items to your users.</span></span> <span data-ttu-id="2c80e-113">次の Web サービス コードを使用した場合、ユーザーがフォームのボタンをクリックすると、ユーザーの [個人用レポート] フォルダー内にある使用可能なレポートの現在の一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-113">The following Web service code might be used to retrieve the current list of available reports in a user's My Reports folder when a user clicks a button on a form:</span></span>  
  
```vb  
' Button click event that retrieves a list of reports from  
' the My Reports folder and displays them in a combo box  
Private Sub listReportsButton_Click(sender As Object, e As System.EventArgs)  
   ' Create a new Web service object and set credentials  
   ' to Windows Authentication  
   Dim rs As New ReportingService2010()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return the list of items in My Reports  
   Dim items As CatalogItem() = rs.ListChildren("/Adventureworks 2008 Sample Reports", False)  
  
   Dim ci As CatalogItem  
   For Each ci In  items  
      ' If the item is a report, add it to   
      ' a combo box  
      If ci.TypeName = "Report" Then  
         catalogComboBox.Items.Add(ci.Name)  
      End If  
   Next ci  
End Sub 'listReportsButton_Click  
```  
  
```csharp  
// Button click event that retrieves a list of reports from  
// the My Reports folder and displays them in a combo box  
private void listReportsButton_Click(object sender, System.EventArgs e)  
{  
   // Create a new Web service object and set credentials  
   // to Windows Authentication  
   ReportingService2010 rs = new ReportingService2010();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return the list of items in My Reports  
   CatalogItem[] items = rs.ListChildren("/Adventureworks 2008 Sample Reports", false);  
  
   foreach (CatalogItem ci in items)  
   {  
      // If the item is a report, add it to   
      // a combo box  
      if (ci.TypeName == "Report")  
         catalogComboBox.Items.Add(ci.Name);  
   }  
}  
```  
  
 <span data-ttu-id="2c80e-114">その後で、ユーザーがコンボ ボックスからレポートを選択し、Web ブラウザー コントロールまたは画像コントロールを使用してフォームのレポートをプレビューできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2c80e-114">From there, you might enable users to select the report from the Combo box and preview the report on the form either using a Web browser control or an image control.</span></span>  
  
## <a name="enabling-report-viewing-and-navigation-using-windows-forms"></a><span data-ttu-id="2c80e-115">Windows フォームを使用したレポートの表示とナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2c80e-115">Enabling Report Viewing and Navigation Using Windows Forms</span></span>  
 <span data-ttu-id="2c80e-116">レポートを Windows フォーム アプリケーションに統合する場合に使用できるメソッドは、2 つあります。</span><span class="sxs-lookup"><span data-stu-id="2c80e-116">There are two methods available for integrating reports into your Windows Forms applications.</span></span>  
  
 <span data-ttu-id="2c80e-117">SOAP API を使用してサポートされている表示形式でレポートを表示するには、<xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-117">You can use the SOAP API to render reports to any of the supported rendering formats using the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method.</span></span> <span data-ttu-id="2c80e-118">SOAP を使用してレポートの表示とナビゲーションを有効化する方法には、次のようなわずかな欠点があります。</span><span class="sxs-lookup"><span data-stu-id="2c80e-118">There are slight disadvantages to enabling report viewing and navigation through SOAP:</span></span>  
  
-   <span data-ttu-id="2c80e-119">URL アクセスによる HTML ビューアーで使用できるレポート ツール バーの組み込み機能を利用できません。</span><span class="sxs-lookup"><span data-stu-id="2c80e-119">You cannot take advantage of the built-in functionality of the report toolbar that is included with the HTML Viewer through URL access.</span></span>  
  
-   <span data-ttu-id="2c80e-120">HTML で表示する場合は、<xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> メソッドを使用して画像やリソースを追加ストリームとして個別に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c80e-120">If you render to HTML, you must separately render any images or resources as additional streams using the <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> method.</span></span>  
  
-   <span data-ttu-id="2c80e-121">URL アクセスによってレポートを表示した場合、SOAP API を使用する場合よりもパフォーマンスが多少向上します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-121">There is a slight performance advantage to rendering reports using URL access over using the SOAP API.</span></span>  
  
 <span data-ttu-id="2c80e-122">ただし、SOAP API の <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを使用すると、プログラムによってさまざまな出力形式でレポートを表示および保存できます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-122">However, the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method of the SOAP API can be used to render reports and save them to various output formats programmatically.</span></span> <span data-ttu-id="2c80e-123">これは、ユーザーとの対話を必要とする URL アクセスよりも優れた点です。</span><span class="sxs-lookup"><span data-stu-id="2c80e-123">This is an advantage over URL access, which requires user interaction.</span></span> <span data-ttu-id="2c80e-124">SOAP API の <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを使用してレポートを表示すると、サポートされている出力形式のいずれでも表示できます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-124">When you render a report using the SOAP API <xref:ReportExecution2005.ReportExecutionService.Render%2A> method, you can render to any of the supported output formats.</span></span>  
  
 <span data-ttu-id="2c80e-125">に含まれている、自由に配布可能な ReportViewer コントロールを使用することもでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-125">You can also use the freely distributable ReportViewer controls that are included with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span> <span data-ttu-id="2c80e-126">ReportViewer コントロールでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能をカスタム アプリケーションに容易に埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-126">The ReportViewer controls make it easy to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality into custom applications.</span></span> <span data-ttu-id="2c80e-127">ReportViewer コントロールは、事前にデザインして完全な形にしあげたレポートを、アプリケーションの機能セットの一部として提供することを予定している開発者を対象にしています (たとえば、Web サイト管理アプリケーションであれば、企業の Web サイトに関するクリックストリーム分析を表示するレポートなどが考えられます)。</span><span class="sxs-lookup"><span data-stu-id="2c80e-127">The ReportViewer controls are intended for developers who want to provide predesigned, fully authored reports as part of an application feature set (for example, a Web site management application might include reports that show click-stream analysis on company Web sites).</span></span> <span data-ttu-id="2c80e-128">これらのコントロールをアプリケーションに埋め込む方法は、アプリケーションの配置に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバー コンポーネントを組み込む方法を簡略化したものと言えます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-128">Embedding the controls in an application provides a streamlined alternative to including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server components in your application deployment.</span></span> <span data-ttu-id="2c80e-129">これらのコントロールではレポート機能が提供されますが、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に含まれる他の機能 (レポートの作成、パブリッシュ、配布、配信のためのサポート) はありません。</span><span class="sxs-lookup"><span data-stu-id="2c80e-129">The controls provide report functionality, but without the additional report authoring, publication, or distribution and delivery support that you find in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2c80e-130">ReportViewer コントロールには 2 つのバージョンがあります。1 つは Windows リッチ クライアント アプリケーション、もう 1 つは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションを対象にしています。</span><span class="sxs-lookup"><span data-stu-id="2c80e-130">There are two versions of the ReportViewer controls, one for rich Windows client applications and one for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications.</span></span> <span data-ttu-id="2c80e-131">また、これらのコントロールは、ローカル処理モードとリモート処理モードの両方をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2c80e-131">The controls support both local processing and remote processing modes.</span></span> <span data-ttu-id="2c80e-132">ローカル処理モードの場合は、アプリケーションによってレポートの定義とデータセットを提供し、レポートの処理を起動します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-132">In local processing mode, your application provides the report definition and datasets and triggers report processing.</span></span> <span data-ttu-id="2c80e-133">リモート処理モードの場合は、データの取得とレポートの処理をレポート サーバー側で実行し、これらのコントロールをレポートの表示とナビゲーションのために使用します。</span><span class="sxs-lookup"><span data-stu-id="2c80e-133">In remote processing mode, data retrieval and report processing happen on the report server and the control is used for display and report navigation.</span></span> <span data-ttu-id="2c80e-134">このモデルを使用すれば、デスクトップの規模にもエンタープライズの規模にも対応できるスケーラビリティの高いリッチ アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2c80e-134">This model allows you to build rich applications that can be scaled from desktop to the enterprise.</span></span>  
  
 <span data-ttu-id="2c80e-135">ReportViewer コントロールの説明は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のオンライン ヘルプにあります。</span><span class="sxs-lookup"><span data-stu-id="2c80e-135">ReportViewer controls are documented in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] online Help.</span></span> <span data-ttu-id="2c80e-136">詳細については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の製品ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c80e-136">For more information, see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] product documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c80e-137">参照</span><span class="sxs-lookup"><span data-stu-id="2c80e-137">See Also</span></span>  
 <span data-ttu-id="2c80e-138">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="2c80e-138">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="2c80e-139">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2c80e-139">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="2c80e-140">Web アプリケーションでの SOAP API の使用</span><span class="sxs-lookup"><span data-stu-id="2c80e-140">Using the SOAP API in a Web Application</span></span>](integrating-reporting-services-using-soap-web-application.md)  
  
  
