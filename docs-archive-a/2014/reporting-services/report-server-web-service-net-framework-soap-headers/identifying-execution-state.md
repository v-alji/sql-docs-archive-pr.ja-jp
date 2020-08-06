---
title: 実行状態の識別 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe53254a5da39c4e7d003ba37d5812ad130293e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644299"
---
# <a name="identifying-execution-state"></a><span data-ttu-id="ab247-102">実行状態の識別</span><span class="sxs-lookup"><span data-stu-id="ab247-102">Identifying Execution State</span></span>
  <span data-ttu-id="ab247-103">Hypertext Transfer Protocol (HTTP) はコネクションレスおよびステートレス プロトコルです。つまり、同じクライアントから異なる要求が来ているかどうかは自動的に検出されません。さらに、ページまたはサイトを表示している 1 つのブラウザーが現在アクティブであるかどうかも、自動的には示されません。</span><span class="sxs-lookup"><span data-stu-id="ab247-103">Hypertext Transfer Protocol (HTTP) is a connectionless and stateless protocol, which means that it does not automatically indicate whether different requests come from the same client or even whether a single browser instance is still actively viewing a page or site.</span></span> <span data-ttu-id="ab247-104">セッションが論理接続を作成し、HTTP を介したサーバーとクライアント間の状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="ab247-104">Sessions create a logical connection to maintain state between server and client over HTTP.</span></span> <span data-ttu-id="ab247-105">特定のセッションに関連するユーザー固有情報は、セッション状態と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ab247-105">The user-specific information relevant to a particular session is known as the session state.</span></span>

 <span data-ttu-id="ab247-106">セッション管理には、HTTP 要求を同じセッションから生成された他の以前の要求と相関させることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ab247-106">Session management involves correlating an HTTP request with other previous requests generated from the same session.</span></span> <span data-ttu-id="ab247-107">セッション管理を使用しないと、HTTP プロトコルがコネクションレスでステートレスな性質であるため、このような要求がレポート サーバー Web サービスと関係なく表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab247-107">Without session management, these requests appear unrelated to the Report Server Web service because of the connectionless and stateless nature of the HTTP protocol.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ab247-108">には、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] におけるようなセッション状態の全体的な概念はありません。</span><span class="sxs-lookup"><span data-stu-id="ab247-108">does not expose a holistic concept of session state such as that exposed by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="ab247-109">ただし、レポートを実行する場合に、レポート サーバーは**実行**の形式でメソッド呼び出し間で状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="ab247-109">However, when executing reports, the report server maintains state between method calls in the form of an **execution**.</span></span> <span data-ttu-id="ab247-110">実行によって、レポート サーバーからレポートを読み込む、レポートの資格情報とパラメーターを設定する、レポートを表示するなど、ユーザーが複数の方法でレポートと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="ab247-110">An execution allows the user to interact with the report in several ways - including loading the report from the report server, setting credentials and parameters for the report, and rendering the report.</span></span>

 <span data-ttu-id="ab247-111">レポート サーバーと通信中は、クライアントが実行を使用して、レポートの表示、ユーザーによるレポートの他のページへのナビゲーション、およびレポートのセクションの表示と非表示を管理します。</span><span class="sxs-lookup"><span data-stu-id="ab247-111">While they are communicating to a report server, clients use the execution to manage report viewing and user navigation to other pages in a report, and to show or hide sections of a report.</span></span> <span data-ttu-id="ab247-112">クライアント アプリケーションが実行しているレポートごとに、固有の実行が存在します。</span><span class="sxs-lookup"><span data-stu-id="ab247-112">A unique execution exists for each report the client application is running.</span></span>

 <span data-ttu-id="ab247-113">一般的に、ユーザーがブラウザーまたはクライアント アプリケーションにナビゲートし、表示するレポートを選択したときに、実行の有効期間が開始します。</span><span class="sxs-lookup"><span data-stu-id="ab247-113">In general, the lifetime of an execution starts when a user navigates to a browser or client application and selects a report to view.</span></span> <span data-ttu-id="ab247-114">実行に対する最後の要求が受信された後にタイムアウト時間が経過すると、実行が破棄されます。既定のタイムアウトは 20 分です。</span><span class="sxs-lookup"><span data-stu-id="ab247-114">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="ab247-115">Web サービスのタイムアウトが開始するのは、レポート サーバー Web サービス <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>、<xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>、または <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドが呼び出されたときです。</span><span class="sxs-lookup"><span data-stu-id="ab247-115">From a Web service perspective, the lifetime starts when the Report Server Web service <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>, or <xref:ReportExecution2005.ReportExecutionService.Render%2A> methods are called.</span></span> <span data-ttu-id="ab247-116">アプリケーションは、他のメソッドを使用してアクティブな実行を操作できます (パラメーターの設定やデータ ソースの設定など)。</span><span class="sxs-lookup"><span data-stu-id="ab247-116">The application can use other methods to manipulate the active execution (for example, setting parameters and setting data sources).</span></span> <span data-ttu-id="ab247-117">実行に対する最後の要求が受信された後にタイムアウト時間が経過すると、実行が破棄されます。既定のタイムアウトは 20 分です。</span><span class="sxs-lookup"><span data-stu-id="ab247-117">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="ab247-118">アプリケーションは、<xref:ReportExecution2005.ReportExecutionService.Render%2A> (<xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> メソッドと <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A> メソッドの SOAP ヘッダーで返される) を保存することによって、Web サービスの <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> メソッドと <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> メソッド間の複数のアクティブな実行を追跡します。</span><span class="sxs-lookup"><span data-stu-id="ab247-118">An application keep track of multiple active executions between calls to the Web service <xref:ReportExecution2005.ReportExecutionService.Render%2A> and <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> methods by saving the <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>, which is returned in the SOAP header from the <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> and <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> methods.</span></span>

 <span data-ttu-id="ab247-119">次のダイアグラムは、レポートに対する処理と表示のパスを示しています。</span><span class="sxs-lookup"><span data-stu-id="ab247-119">The following diagram shows the processing and rendering path for reports.</span></span>

 <span data-ttu-id="ab247-120">![レポートの処理および表示 パス](../../../2014/reporting-services/media/rs-render-process-diagram.gif "レポートの処理および表示パス")</span><span class="sxs-lookup"><span data-stu-id="ab247-120">![Report processing/rendering path](../../../2014/reporting-services/media/rs-render-process-diagram.gif "Report processing/rendering path")</span></span>

 <span data-ttu-id="ab247-121">上記のような関数をサポートするために、現在の SOAP Render メソッドを複数のメソッドに分割して、初期化フェーズ、処理フェーズ、および表示フェーズの実行を網羅しました。</span><span class="sxs-lookup"><span data-stu-id="ab247-121">To support the functions described above, the current SOAP Render method has been split into multiple methods encompassing execution initialization, processing, and rendering phases.</span></span>

 <span data-ttu-id="ab247-122">プログラムによってレポートを表示するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab247-122">To programmatically render a report, you must:</span></span>

-   <span data-ttu-id="ab247-123"><xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> または <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> を使用して、レポートまたはレポート定義を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ab247-123">Load the report or the report definition using <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.</span></span>

-   <span data-ttu-id="ab247-124">レポートに資格情報またはパラメーターが必要かどうかを確認します。このとき、<xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> または <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> によって返された <xref:ReportExecution2005.ExecutionInfo> オブジェクトの <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> プロパティと <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="ab247-124">Check to see if the report needs credentials or parameters by checking the values of the <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> and <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> properties of the <xref:ReportExecution2005.ExecutionInfo> object returned by <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A></span></span>

-   <span data-ttu-id="ab247-125">必要に応じて、<xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> メソッドおよび <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> メソッドを使用して、資格情報またはパラメーター、あるいはその両方を設定します。</span><span class="sxs-lookup"><span data-stu-id="ab247-125">If necessary, set the credentials and/or parameters using the <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> and <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> methods.</span></span>

-   <span data-ttu-id="ab247-126"><xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを呼び出してレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="ab247-126">Call the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to render the report.</span></span>

 <span data-ttu-id="ab247-127">レポートがセッション中の間は、レポート サーバー データベースに格納された基になるレポートを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ab247-127">While a report is in session, the underlying report stored in the report server database can change.</span></span> <span data-ttu-id="ab247-128">たとえば、レポート定義の変更、レポートの削除や移動、ユーザー権限の変更ができます。</span><span class="sxs-lookup"><span data-stu-id="ab247-128">For example, the report definition can change, the report can be deleted or moved, and user permissions can change.</span></span> <span data-ttu-id="ab247-129">レポートがアクティブなセッション中の場合は、基になるレポート (レポート サーバー データベースに格納されたレポート) への変更による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ab247-129">If the report is in an active session, it is not affected by changes made to the underlying report (that is, the report stored in the report server database).</span></span>

 <span data-ttu-id="ab247-130">URL アクセス コマンドを使用して、レポート セッションを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab247-130">You can also manage a report session using URL access commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab247-131">参照</span><span class="sxs-lookup"><span data-stu-id="ab247-131">See Also</span></span>
 <span data-ttu-id="ab247-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A>[REPORTING SERVICES SOAP ヘッダーを使用し](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)た[SSRS&#41;&#40;テクニカルリファレンス](../../../2014/reporting-services/technical-reference-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="ab247-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A> [Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) [Using Reporting Services SOAP Headers](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)</span></span>


