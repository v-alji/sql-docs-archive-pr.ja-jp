---
title: Reporting Services のクライアント側印刷機能の有効化と無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642541"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a><span data-ttu-id="43a29-102">Reporting Services のクライアント側印刷機能の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="43a29-102">Enable and Disable Client-Side Printing for Reporting Services</span></span>
  <span data-ttu-id="43a29-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]ActiveX コントロール ( **Rsclientprint**) は、ブラウザーに表示されるレポートのクライアント側印刷機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="43a29-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX control, **RSClientPrint**, provides client-side printing for reports viewed in a browser.</span></span> <span data-ttu-id="43a29-104">このコントロールによって表示されるカスタム印刷ダイアログ ボックスでは、一般的な印刷ダイアログ ボックスの機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="43a29-104">The control displays a custom print dialog box that supports features common to other print dialog boxes.</span></span> <span data-ttu-id="43a29-105">この機能には、印刷プレビュー、特定のページや範囲を指定するためのページ選択、ページ余白、ページの向きなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="43a29-105">The features include print preview, page selections for specifying specific pages and ranges, page margins, and orientation.</span></span> <span data-ttu-id="43a29-106">クライアント側印刷機能は既定で有効になっていますが、無効にして使用できないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="43a29-106">Although client-side printing is enabled by default, you can disable the feature to prevent it from being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43a29-107">ActiveX コントロールをダウンロードするには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="43a29-107">Downloading ActiveX controls requires administrator permissions.</span></span>  
  
## <a name="downloading-the-activex-control"></a><span data-ttu-id="43a29-108">ActiveX コントロールのダウンロード</span><span class="sxs-lookup"><span data-stu-id="43a29-108">Downloading the ActiveX Control</span></span>  
 <span data-ttu-id="43a29-109">印刷機能を使用する各ユーザーは、クライアント側印刷機能を提供する ActiveX コントロールをダウンロードしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43a29-109">Each user who wants to use the print feature must download and install the ActiveX control that provides client print functionality.</span></span> <span data-ttu-id="43a29-110">ユーザーがレポートツールバーの [**プリンター** ] アイコンを初めてクリックすると、Microsoft ActiveX コントロールがコンピューターにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="43a29-110">The first time a user clicks the **Printer** icon on the report toolbar, the Microsoft ActiveX control is downloaded to the computer.</span></span> <span data-ttu-id="43a29-111">コントロールがダウンロードされると、ユーザーが**プリンター**アイコンをクリックするたびに [**印刷**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43a29-111">After the control is downloaded, the **Print** dialog box displays whenever the user clicks the **Printer** icon.</span></span>  
  
 <span data-ttu-id="43a29-112">ブラウザーの設定によって、コントロールをインストールするかどうかを確認するメッセージが表示される場合と、コントロールをインストールできない場合と、ユーザーへの通知を行わずにコントロールがバックグラウンドでインストールされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="43a29-112">Depending on browser settings, the user may be prompted to install the control, be prevented from installing the control, or have the control install transparently in the background.</span></span>  
  
 <span data-ttu-id="43a29-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer の場合、activex コントロールのダウンロードとインストールに影響を与える設定は、Web コンテンツゾーンの [セキュリティの**設定**] ページの [ **activex コントロールとプラグイン**] ノードで指定します。</span><span class="sxs-lookup"><span data-stu-id="43a29-113">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, settings that affect ActiveX control download and installation are specified through the **ActiveX controls and plug-ins** node in the **Security Settings** page for the Web content zone.</span></span> <span data-ttu-id="43a29-114">印刷コントロールをダウンロードして実行できるかどうかは、Web ゾーンの以下のセキュリティ設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="43a29-114">The following settings determine whether users can download and run the print control, based on Web zone security preferences:</span></span>  
  
-   <span data-ttu-id="43a29-115">署名済み ActiveX コントロールのダウンロード。</span><span class="sxs-lookup"><span data-stu-id="43a29-115">Download signed ActiveX controls.</span></span>  
  
-   <span data-ttu-id="43a29-116">スクリプトを実行しても安全とマークされている ActiveX コントロールのスクリプトの実行。</span><span class="sxs-lookup"><span data-stu-id="43a29-116">Script ActiveX controls marked safe for scripting.</span></span>  
  
-   <span data-ttu-id="43a29-117">ActiveX コントロールとプラグインの実行。</span><span class="sxs-lookup"><span data-stu-id="43a29-117">Run ActiveX controls and plug-ins.</span></span>  
  
 <span data-ttu-id="43a29-118">**Rsclientprint**を使用してクライアント側印刷を実行するユーザーは、次の機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43a29-118">Users who want to use **RSClientPrint** to perform client-side printing must enable the following:</span></span>  
  
-   <span data-ttu-id="43a29-119">署名された**activex コントロールをダウンロード**し、スクリプト用に安全とマークされた**スクリプト activex コントロール**をインストールのためにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="43a29-119">**Download signed ActiveX controls** and **Script ActiveX control marked safe for scripting** for installation purposes.</span></span>  
  
-   <span data-ttu-id="43a29-120">**ActiveX コントロールとプラグインを実行して、実行**中の印刷操作を行います。</span><span class="sxs-lookup"><span data-stu-id="43a29-120">**Run ActiveX controls and plug-ins** for ongoing print operations.</span></span>  
  
 <span data-ttu-id="43a29-121">**Rsclientprint** ActiveX コントロールは署名されています。これは、からの有効なデジタル証明書が含まれていることを意味し [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="43a29-121">The **RSClientPrint** ActiveX control is signed, meaning it contains a valid digital certificate from [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="enabling-and-disabling-client-side-printing"></a><span data-ttu-id="43a29-122">クライアント側印刷機能の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="43a29-122">Enabling and Disabling Client-Side Printing</span></span>  
 <span data-ttu-id="43a29-123">レポートサーバーの管理者は、レポートサーバーのシステムプロパティ**EnableClientPrinting**をに設定して、印刷機能を無効にすることが `false` できます。</span><span class="sxs-lookup"><span data-stu-id="43a29-123">Report server administrators have the option of disabling the print feature by setting the report server system property **EnableClientPrinting** to `false`.</span></span> <span data-ttu-id="43a29-124">これにより、サーバーが管理しているすべてのレポートでクライアント側印刷機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="43a29-124">This will disable client-side printing for all reports managed by that server.</span></span> <span data-ttu-id="43a29-125">既定では、 **EnableClientPrinting**はに設定されて `true` います。</span><span class="sxs-lookup"><span data-stu-id="43a29-125">By default, **EnableClientPrinting** is set to `true`.</span></span> <span data-ttu-id="43a29-126">クライアント側印刷機能は、次の方法で無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="43a29-126">You can disable client-side printing in the following ways:</span></span>  
  
-   <span data-ttu-id="43a29-127">**ネイティブ モードのレポート サーバー**の場合:</span><span class="sxs-lookup"><span data-stu-id="43a29-127">For a **Native mode report server**:</span></span>  
  
    1.  <span data-ttu-id="43a29-128">管理者特権を使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開始します。</span><span class="sxs-lookup"><span data-stu-id="43a29-128">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    2.  <span data-ttu-id="43a29-129">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でレポート サーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="43a29-129">Connect to a report server instance in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
    3.  <span data-ttu-id="43a29-130">レポート サーバー ノードを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-130">Right-click the report server node, and then click **Properties**.</span></span> <span data-ttu-id="43a29-131">**[プロパティ]** オプションが無効になっている場合は、管理者特権を使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開始したことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43a29-131">If the **Properties** option is disabled, verify you started [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    4.  <span data-ttu-id="43a29-132">[ **ActiveX クライアントの印刷コントロールのダウンロードを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43a29-132">Select **Enable download for the ActiveX client print control**.</span></span>  
  
    5.  <span data-ttu-id="43a29-133">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-133">Click **OK**.</span></span>  
  
-   <span data-ttu-id="43a29-134">**SharePoint モードのレポート サーバー**の場合:</span><span class="sxs-lookup"><span data-stu-id="43a29-134">For a **SharePoint mode report server**:</span></span>  
  
    1.  <span data-ttu-id="43a29-135">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-135">In SharePoint Central Administration, click **Application Management**.</span></span>  
  
    2.  <span data-ttu-id="43a29-136">**[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-136">Click **Manage service applications**.</span></span>  
  
    3.  <span data-ttu-id="43a29-137">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前をクリックし、SharePoint リボンで **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-137">Click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, and then click **Manage** in the SharePoint ribbon.</span></span>  
  
    4.  <span data-ttu-id="43a29-138">**[システム設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-138">Click **System Settings**.</span></span>  
  
    5.  <span data-ttu-id="43a29-139">**[クライアントの印刷を有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="43a29-139">Select **Enable Client Printing**.</span></span> <span data-ttu-id="43a29-140">**[クライアントの印刷を有効にする]** オプションは、ページの下部付近にあります。</span><span class="sxs-lookup"><span data-stu-id="43a29-140">The **Enable Client Printing** option is near the bottom of the page.</span></span>  
  
    6.  <span data-ttu-id="43a29-141">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43a29-141">Click **OK**.</span></span>  
  
-   <span data-ttu-id="43a29-142">レポートサーバーのシステムプロパティ**EnableClientPrinting**を設定するスクリプトまたはコードを作成します。`false.`</span><span class="sxs-lookup"><span data-stu-id="43a29-142">Write script or code to set the report server system property **EnableClientPrinting** to `false.`</span></span>  
  
 <span data-ttu-id="43a29-143">次のサンプル スクリプトは、クライアント側印刷機能を無効にする方法の一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="43a29-143">The following sample script illustrates one approach for disabling client-side printing.</span></span> <span data-ttu-id="43a29-144">この [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コードをコンパイルして実行すると、**EnableClientPrinting** プロパティが **False** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43a29-144">Compile and then run the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code to set the **EnableClientPrinting** property to **False**.</span></span> <span data-ttu-id="43a29-145">コードの実行後、IIS を再起動してください。</span><span class="sxs-lookup"><span data-stu-id="43a29-145">After you run the code, restart IIS.</span></span>  
  
### <a name="sample-script"></a><span data-ttu-id="43a29-146">サンプル スクリプト</span><span class="sxs-lookup"><span data-stu-id="43a29-146">Sample Script</span></span>  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
