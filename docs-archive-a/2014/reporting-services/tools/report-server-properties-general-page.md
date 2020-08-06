---
title: '[サーバーのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66199e35c180790cba5120cb839be67e43052be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742826"
---
# <a name="server-properties-general-page"></a><span data-ttu-id="383cf-102">[サーバーのプロパティ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="383cf-102">Server Properties (General Page)</span></span>
  <span data-ttu-id="383cf-103">このページを使用すると、レポート マネージャーで使用されるタイトルの表示と変更、個人用レポートの有効化と無効化、個人用レポートのセキュリティに関するロール定義の選択、およびクライアントの印刷コントロールの有効化または無効化ができます。</span><span class="sxs-lookup"><span data-stu-id="383cf-103">Use this page to view or modify the title used in Report Manager, enable or disable My Reports, select a role definition for My Reports security, and enable or disable the client print control.</span></span>  
  
 <span data-ttu-id="383cf-104">このページを開くには、を起動して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] レポートサーバーインスタンスに接続し、レポートサーバー名を右クリックして、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="383cf-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and then select **Properties**.</span></span>  
  
 <span data-ttu-id="383cf-105">サーバー モードによって、設定できるサーバー プロパティが決まります。</span><span class="sxs-lookup"><span data-stu-id="383cf-105">The server mode determines which server properties you can set.</span></span> <span data-ttu-id="383cf-106">SharePoint 統合モード用に構成されたレポート サーバーを管理している場合は、個人用レポートを有効にしたり、レポート マネージャーのアプリケーション タイトルを設定することができません。</span><span class="sxs-lookup"><span data-stu-id="383cf-106">If you are managing a report server that is configured for SharePoint integrated mode, you cannot enable My Reports or set the application title for Report Manager.</span></span>  
  
## <a name="options"></a><span data-ttu-id="383cf-107">Options</span><span class="sxs-lookup"><span data-stu-id="383cf-107">Options</span></span>  
 <span data-ttu-id="383cf-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="383cf-108">**Name**</span></span>  
 <span data-ttu-id="383cf-109">レポート マネージャーで表示されるアプリケーション名を入力します。</span><span class="sxs-lookup"><span data-stu-id="383cf-109">Type an application name that appears in Report Manager.</span></span> <span data-ttu-id="383cf-110">既定では、この値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="383cf-110">By default, this value is [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="383cf-111">指定した名前は、レポート マネージャーでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="383cf-111">The name that you specify appears only in Report Manager.</span></span>  
  
 <span data-ttu-id="383cf-112">**Version**</span><span class="sxs-lookup"><span data-stu-id="383cf-112">**Version**</span></span>  
 <span data-ttu-id="383cf-113">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="383cf-113">This property is read-only.</span></span> <span data-ttu-id="383cf-114">使用しているのバージョンを指定し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="383cf-114">Specifies the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that you are using.</span></span>  
  
 <span data-ttu-id="383cf-115">**エディション**</span><span class="sxs-lookup"><span data-stu-id="383cf-115">**Edition**</span></span>  
 <span data-ttu-id="383cf-116">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="383cf-116">This property is read-only.</span></span> <span data-ttu-id="383cf-117">現在のレポート サーバー インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="383cf-117">Specifies the current report server instance.</span></span> <span data-ttu-id="383cf-118">レポート マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="383cf-118">Report Manager is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="383cf-119">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="383cf-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="383cf-120">**認証モード**</span><span class="sxs-lookup"><span data-stu-id="383cf-120">**Authentication Mode**</span></span>  
 <span data-ttu-id="383cf-121">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="383cf-121">This property is read-only.</span></span> <span data-ttu-id="383cf-122">レポート サーバー インスタンスで受け入れられる認証要求の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="383cf-122">It identifies the types of authentication requests accepted by the report server instance.</span></span> <span data-ttu-id="383cf-123">認証モードを変更するには、RSReportServer.config ファイルを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="383cf-123">To change the authentication mode, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="383cf-124">詳細については、「 [レポート サーバーでの認証](../security/authentication-with-the-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="383cf-124">For more information, see [Authentication with the Report Server](../security/authentication-with-the-report-server.md).</span></span>  
  
 <span data-ttu-id="383cf-125">**URL**</span><span class="sxs-lookup"><span data-stu-id="383cf-125">**URL**</span></span>  
 <span data-ttu-id="383cf-126">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="383cf-126">This property is read-only.</span></span> <span data-ttu-id="383cf-127">レポート サーバー Web サービスへの URL を示します。</span><span class="sxs-lookup"><span data-stu-id="383cf-127">Specifies the URL to the Report Server Web service.</span></span> <span data-ttu-id="383cf-128">この値は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで指定されます。</span><span class="sxs-lookup"><span data-stu-id="383cf-128">This value is specified in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="383cf-129">詳細については、「[URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="383cf-129">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="383cf-130">**[ユーザーごとに個人用レポート フォルダーを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="383cf-130">**Enable a My Reports folder for each user**</span></span>  
 <span data-ttu-id="383cf-131">ユーザーが個人用レポートを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="383cf-131">Make My Reports available to users.</span></span> <span data-ttu-id="383cf-132">このオプションはネイティブ モードのレポート サーバーでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="383cf-132">This option is only available for native mode report servers.</span></span>  
  
 <span data-ttu-id="383cf-133">**[個人用フォルダーごとに適用するロールを選択します]**</span><span class="sxs-lookup"><span data-stu-id="383cf-133">**Select the role to apply to each My Reports folder**</span></span>  
 <span data-ttu-id="383cf-134">個人用レポートのセキュリティに使用するロール定義を指定します。</span><span class="sxs-lookup"><span data-stu-id="383cf-134">Specify a role definition to use for My Reports security.</span></span> <span data-ttu-id="383cf-135">ロール定義は、各個人用レポート フォルダーでサポートされるタスクのセットを特定します。</span><span class="sxs-lookup"><span data-stu-id="383cf-135">The role definition identifies the set of tasks that are supported in each My Reports folder.</span></span>  
  
 <span data-ttu-id="383cf-136">**[ActiveX クライアントの印刷コントロールのダウンロードを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="383cf-136">**Enable download for the ActiveX client print control**</span></span>  
 <span data-ttu-id="383cf-137">`EnableClientPrinting` レポート サーバー システム プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="383cf-137">Sets the `EnableClientPrinting` report server system property.</span></span> <span data-ttu-id="383cf-138">クライアント側の印刷を有効にすると、ローカル管理者の権限を持つユーザーは、HTML レポートを印刷するための署名済み ActiveX コントロールをダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="383cf-138">If you enable client printing, users who have local administrator permissions have the option of downloading a signed ActiveX control for printing HTML reports.</span></span> <span data-ttu-id="383cf-139">詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="383cf-139">For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383cf-140">参照</span><span class="sxs-lookup"><span data-stu-id="383cf-140">See Also</span></span>  
 <span data-ttu-id="383cf-141">[レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="383cf-141">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="383cf-142">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="383cf-142">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="383cf-143">[個人用レポートを有効または無効にする](../report-server/enable-and-disable-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="383cf-143">[Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md) </span></span>  
 <span data-ttu-id="383cf-144">[Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="383cf-144">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="383cf-145">個人用レポートをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="383cf-145">Secure My Reports</span></span>](../security/secure-my-reports.md)  
  
  
