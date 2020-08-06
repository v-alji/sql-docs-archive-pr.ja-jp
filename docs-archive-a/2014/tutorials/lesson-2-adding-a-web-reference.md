---
title: 'レッスン 2: Web 参照の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 02ca614cb042211ac468246c3003efaa5f2e8fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717114"
---
# <a name="lesson-2-adding-a-web-reference"></a><span data-ttu-id="753b2-102">レッスン 2 : Web 参照の追加</span><span class="sxs-lookup"><span data-stu-id="753b2-102">Lesson 2: Adding a Web Reference</span></span>
  <span data-ttu-id="753b2-103">Web サービスの探索とは、クライアントが Web サービスを検索し、そのサービス記述を取得する処理です。</span><span class="sxs-lookup"><span data-stu-id="753b2-103">Web service discovery is the process by which a client locates a Web service and obtains its service description.</span></span> <span data-ttu-id="753b2-104">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の Web サービス探索処理では、事前に定義されたアルゴリズムに従って、Web サイトの問い合わせが行われます。</span><span class="sxs-lookup"><span data-stu-id="753b2-104">The process of Web service discovery in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] involves interrogating a Web site following a predetermined algorithm.</span></span> <span data-ttu-id="753b2-105">この処理の目的はサービス記述を見つけることです。サービス記述とは、WSDL (Web サービス記述言語) を使用する XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="753b2-105">The goal of the process is to locate the service description, which is an XML document that uses the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="753b2-106">サービス記述には、利用可能なサービスとこれらのサービスとの対話方法が記述されています。</span><span class="sxs-lookup"><span data-stu-id="753b2-106">The service description describes what services are available and how to interact with those services.</span></span> <span data-ttu-id="753b2-107">サービス記述がない場合は、プログラムから Web サービスと対話することはできません。</span><span class="sxs-lookup"><span data-stu-id="753b2-107">Without a service description, it is impossible to programmatically interact with a Web service.</span></span>  
  
 <span data-ttu-id="753b2-108">アプリケーションには、Web サービスと通信する方法とランタイムで Web サービスを検出する方法を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="753b2-108">Your application must have a means to communicate with the Web service and to locate it at run time.</span></span> <span data-ttu-id="753b2-109">これを実現するには、プロジェクトに Web サービス用の Web 参照を追加します。その結果、プロキシ クラスが生成されます。プロキシ クラスは、Web サービスとのインターフェイスとなり、Web サービスのローカル表記を提供します。</span><span class="sxs-lookup"><span data-stu-id="753b2-109">Adding a Web reference to your project for the Web service does this by generating a proxy class that interfaces with the Web service and provides a local representation of the Web service.</span></span> <span data-ttu-id="753b2-110">詳細については、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ドキュメントの「方法 : XML Web サービス プロキシを生成する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="753b2-110">For more information, see "How to: Generate an XML Web Service Proxy" in your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] documentation.</span></span>  
  
### <a name="to-add-a-web-reference"></a><span data-ttu-id="753b2-111">Web 参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="753b2-111">To add a Web reference</span></span>  
  
1.  <span data-ttu-id="753b2-112">[**プロジェクト**] メニューの [**サービス参照の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-112">On the **Project** menu, click **Add Service Reference**.</span></span>  
  
2.  <span data-ttu-id="753b2-113">[**サービス参照の追加**] ダイアログボックスで、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-113">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
3.  <span data-ttu-id="753b2-114">[**サービス参照の設定**] ダイアログボックスで、[ **Web 参照の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-114">In the **Service Reference Settings** dialog box, click **Add Web Reference**.</span></span>  
  
4.  <span data-ttu-id="753b2-115">[ **Web 参照の追加**] ダイアログボックスの [ **url** ] ボックスに、レポートサーバー Web サービスのサービスの説明を取得するための url を入力します (など) http://localhost/reportserver/reportservice2010.asmx 。</span><span class="sxs-lookup"><span data-stu-id="753b2-115">In the **URL** box of the **Add Web Reference** dialog box, type the URL to obtain the service description of the Report Server Web service, such as http://localhost/reportserver/reportservice2010.asmx.</span></span> <span data-ttu-id="753b2-116">次に、[実行] ボタンをクリックし**て、Web**サービスに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="753b2-116">Then click the **Go** button to retrieve information about the Web service.</span></span>  
  
     <span data-ttu-id="753b2-117">\- または</span><span class="sxs-lookup"><span data-stu-id="753b2-117">\- or -</span></span>  
  
     <span data-ttu-id="753b2-118">レポートサーバー Web サービスがローカルコンピューターに存在する場合は、ブラウザーペインの [**ローカルコンピューター] リンクで web サービス**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-118">If the Report Server Web service exists on the local machine, click the **Web services on the local machine** link in the browser pane.</span></span> <span data-ttu-id="753b2-119">次に、表示された一覧から ReportService2010 Web サービスのリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-119">Then click the link for the ReportService2010 Web service from the list provided.</span></span>  
  
5.  <span data-ttu-id="753b2-120">[ **Web 参照名**] ボックスで、web 参照の名前を ReportService2010 に変更します。これは、この web 参照に使用する名前空間です。</span><span class="sxs-lookup"><span data-stu-id="753b2-120">In the **Web reference name** box, rename the Web reference to ReportService2010, which is the namespace you will use for this Web reference.</span></span>  
  
6.  <span data-ttu-id="753b2-121">[**参照の追加**] をクリックして、ターゲット web サービスの web 参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="753b2-121">Click **Add Reference** to add a Web reference for the target Web service.</span></span>  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="753b2-122">により、サービス記述がダウンロードされ、アプリケーションとレポート サーバー Web サービス間のインターフェイスとなるプロキシ クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="753b2-122">downloads the service description and generates a proxy class to interface between your application and the Report Server Web service.</span></span> <span data-ttu-id="753b2-123">また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="753b2-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
7.  <span data-ttu-id="753b2-124">[プロジェクト] メニューの **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-124">On the Project menu, click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="753b2-125">[**参照の追加**] ダイアログボックスの [ **.net** ] タブで、[ **system.web. Services**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753b2-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
 <span data-ttu-id="753b2-126">詳細については、「[SOAP API へのアクセス](../reporting-services/report-server-web-service/accessing-the-soap-api.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="753b2-126">For more information, see [Accessing the SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753b2-127">参照</span><span class="sxs-lookup"><span data-stu-id="753b2-127">See Also</span></span>  
 <span data-ttu-id="753b2-128">[レポート サーバー Web サービス](../reporting-services/report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="753b2-128">[Report Server Web Service](../reporting-services/report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="753b2-129">[レッスン 3: Web サービスへのアクセス](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="753b2-129">[Lesson 3: Accessing the Web Service](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span></span>  
 [<span data-ttu-id="753b2-130">Visual Basic または Visual C&#35; &#40;SSRS チュートリアルを使用したレポートサーバー Web サービスへのアクセス&#41;</span><span class="sxs-lookup"><span data-stu-id="753b2-130">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
