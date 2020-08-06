---
title: レポートビルダーのスタンドアロンバージョンをインストールする (レポートビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ba8c132125f56ad833a71a1c82221e2bf28d13e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642593"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="f91cf-102">スタンドアロン バージョンのレポート ビルダーのインストール (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="f91cf-102">Install the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="f91cf-103">レポートビルダーは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=53613)の feature pack から、またはレポートビルダーの Windows インストーラーパッケージ ReportBuilder3_x86.msi がダウンロードされているパブリックフォルダなどの場所にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-103">You can install Report Builder from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack on the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613) or a location such as public folder to which the ReportBuilder3_x86.msi, the Windows Installer Package for Report Builder, has been downloaded.</span></span>  
  
 <span data-ttu-id="f91cf-104">また、レポート ビルダーのインストールをコマンド ラインから実行し、引数を指定してインストールをカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-104">You can also perform a command line installation of Report Builder and provide arguments to customize the installation.</span></span> <span data-ttu-id="f91cf-105">標準の MSI 固有パラメーターに加えて、レポート ビルダーに用意されているカスタム パラメーターの RBINSTALLDIR と REPORTSERVERURL も使用できます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-105">In addition to the standard MSI intrinsic parameters, you can use the custom parameters that Report Builder provides: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="f91cf-106">RBINSTALLDIR では、レポート ビルダーのルート インストール フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-106">RBINSTALLDIR specifies the root installation folder for Report Builder.</span></span> <span data-ttu-id="f91cf-107">REPORTSERVERURL では、レポート ビルダーがサーバーにレポートを保存するときに使用する既定のレポート サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-107">REPORTSERVERURL specifies the default report server that Report Builder uses to save reports on the server.</span></span>  
  
 <span data-ttu-id="f91cf-108">ユーザー インターフェイスをまったく操作しない完全なサイレント インストールを実行する場合は、 **/quiet** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-108">If you want a completely silent installation, with no user interface interaction at all, specify the **/quiet** option.</span></span> <span data-ttu-id="f91cf-109">quiet オプション フラグを使用するとインストール エラーが抑制されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="f91cf-109">By design, the quiet option flag suppresses installation errors.</span></span> <span data-ttu-id="f91cf-110">そのため、quiet オプションを使用する場合は、ログ記録を指定する **/l** オプションを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-110">It is therefore recommended that you include the **/l** option, which specifies logging, when you use the quiet option.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f91cf-111">Windows Vista および Windows 7 でコマンド ライン操作を実行するには、セキュリティ機能に基づいて高度な権限が必要となり、コマンド ラインの実行権限が要求されます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-111">Windows Vista and Windows 7 security features require elevated permissions to run command line operations and will prompt for permission to run the command line.</span></span> <span data-ttu-id="f91cf-112">インストールはサイレント モードになりません。</span><span class="sxs-lookup"><span data-stu-id="f91cf-112">The installation is not silent.</span></span> <span data-ttu-id="f91cf-113">インストールをサイレント モードにするには、管理者としてコマンド ラインを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f91cf-113">To make the installation silent, you need to run the command line as an administrator.</span></span>  
  
### <a name="to-install-report-builder-from-the-download-site"></a><span data-ttu-id="f91cf-114">ダウンロード サイトからレポート ビルダーをインストールするには</span><span class="sxs-lookup"><span data-stu-id="f91cf-114">To install Report Builder from the download site</span></span>  
  
1.  <span data-ttu-id="f91cf-115">[Microsoft SQL Server 2012 レポートビルダー](https://go.microsoft.com/fwlink/?LinkID=219138)に移動し、Web ページの [レポートビルダー] セクションを探します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-115">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section of the Web page.</span></span>  
  
2.  <span data-ttu-id="f91cf-116">[ **X86 パッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-116">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="f91cf-117">[**ファイルのダウンロード**] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-117">In the **File Download** dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f91cf-118">信頼できるソースのファイル以外はダウンロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="f91cf-118">Download only files from trusted sources.</span></span>  
  
4.  <span data-ttu-id="f91cf-119">[Internet Explorer] ダイアログボックスで、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-119">In the Internet Explorer dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f91cf-120">信頼できるソースのファイル以外は実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="f91cf-120">Run only files from trusted sources.</span></span>  
  
5.  <span data-ttu-id="f91cf-121">Microsoft SQL Server レポート ビルダー ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-121">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
6.  <span data-ttu-id="f91cf-122">[**インストールウィザードへようこそ**] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-122">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="f91cf-123">[**使用許諾契約**書] ページで、契約を読み、[**使用許諾契約書に同意**します] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-123">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="f91cf-124">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-124">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f91cf-125">個人名と会社名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-125">Provide your personal name and company name.</span></span> <span data-ttu-id="f91cf-126">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f91cf-127">[**機能の選択**] ページで、必要に応じて [**参照**] または [**ディスクコスト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-127">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="f91cf-128">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-128">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="f91cf-129">[**参照**] をクリックしてレポートビルダーの既定の場所を表示し、更新します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-129">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f91cf-130">レポートビルダーの既定のインストールフォルダーは、 \<drive> Program の SQL Server です。</span><span class="sxs-lookup"><span data-stu-id="f91cf-130">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="f91cf-131">[**ディスクコスト**] をクリックして、レポートビルダー使用するディスク領域の量を確認します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-131">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f91cf-132">ボリュームに十分な空きディスク領域がない場合は、ボリュームが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-132">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
10. <span data-ttu-id="f91cf-133">**[既定のターゲット サーバー]** ページで、必要に応じて対象レポート サーバーの URL を指定します (既定の URL と異なる場合)。</span><span class="sxs-lookup"><span data-stu-id="f91cf-133">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="f91cf-134">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-134">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f91cf-135">レポート ビルダーをレポート サーバーに接続して使用する場合は、ここでサーバーの URL を指定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="f91cf-135">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="f91cf-136">ただし、レポートビルダーで作業している場合は、[**オプション**] ダイアログボックスから実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-136">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
11. <span data-ttu-id="f91cf-137">[**インストール**] をクリックしてレポートビルダーのインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-137">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-a-share"></a><span data-ttu-id="f91cf-138">共有からレポート ビルダーをインストールするには</span><span class="sxs-lookup"><span data-stu-id="f91cf-138">To install Report Builder from a share</span></span>  
  
1.  <span data-ttu-id="f91cf-139">レポート ビルダーをローカル コンピューターにインストールするために実行する ReportBuilder3_x86.msi の場所については、管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="f91cf-139">Contact your administrator for the location of ReportBuilder3_x86.msi.msi that you run to install Report Builder on your local computer.</span></span>  
  
2.  <span data-ttu-id="f91cf-140">レポート ビルダーの Windows インストーラー パッケージ (MSI) である ReportBuilder3_x86.msi の場所を参照してクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-140">Browse to locate the ReportBuilder3_x86.msi.msi, the Windows Installer Package (MSI) for Report Builder, and click it.</span></span>  
  
     <span data-ttu-id="f91cf-141">Microsoft SQL Server レポート ビルダー ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-141">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
3.  <span data-ttu-id="f91cf-142">[**インストールウィザードへようこそ**] ページで、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-142">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="f91cf-143">[**使用許諾契約**書] ページで、契約を読み、[**使用許諾契約書に同意**します] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-143">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="f91cf-144">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-144">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="f91cf-145">個人名と会社名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-145">Provide your personal name and company name.</span></span> <span data-ttu-id="f91cf-146">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f91cf-147">[**機能の選択**] ページで、必要に応じて [**参照**] または [**ディスクコスト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-147">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="f91cf-148">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-148">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="f91cf-149">[**参照**] をクリックしてレポートビルダーの既定の場所を表示し、更新します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-149">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f91cf-150">レポートビルダーの既定のインストールフォルダーは、 \<drive> Program の SQL Server です。</span><span class="sxs-lookup"><span data-stu-id="f91cf-150">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="f91cf-151">[**ディスクコスト**] をクリックして、レポートビルダー使用するディスク領域の量を確認します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-151">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f91cf-152">ボリュームに十分な空きディスク領域がない場合は、ボリュームが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-152">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
7.  <span data-ttu-id="f91cf-153">**[既定のターゲット サーバー]** ページで、必要に応じて対象レポート サーバーの URL を指定します (既定の URL と異なる場合)。</span><span class="sxs-lookup"><span data-stu-id="f91cf-153">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="f91cf-154">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-154">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f91cf-155">レポート ビルダーをレポート サーバーに接続して使用する場合は、ここでサーバーの URL を指定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="f91cf-155">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="f91cf-156">ただし、レポートビルダーで作業している場合は、[**オプション**] ダイアログボックスから実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f91cf-156">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
8.  <span data-ttu-id="f91cf-157">[**インストール**] をクリックしてレポートビルダーのインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-157">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-the-command-line"></a><span data-ttu-id="f91cf-158">コマンド ラインからレポート ビルダーをインストールするには</span><span class="sxs-lookup"><span data-stu-id="f91cf-158">To install Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="f91cf-159">[Microsoft SQL Server 2012 レポートビルダー](https://go.microsoft.com/fwlink/?LinkID=219138)に移動し、[レポートビルダー] セクションを探します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-159">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section.</span></span>  
  
2.  <span data-ttu-id="f91cf-160">[ **X86 パッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-160">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="f91cf-161">[保存] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-161">Click Save.</span></span>  
  
4.  <span data-ttu-id="f91cf-162">必要に応じて、保存先の場所を参照し、[名前を付け**て保存**] オプションが**Windows インストーラーパッケージ**であることを確認して、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-162">Optionally, browse to the location to save to, verify the **Save as** option is **Windows Installer Package**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="f91cf-163">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91cf-163">On the **Start** menu, click **Run**.</span></span>  
  
6.  <span data-ttu-id="f91cf-164">[名前] ボックスに「」と入力します。`cmd.`</span><span class="sxs-lookup"><span data-stu-id="f91cf-164">In the Open text box, type `cmd.`</span></span>  
  
7.  <span data-ttu-id="f91cf-165">コマンド プロンプト ウィンドウで、ReportBuilder3_x86.msi を保存したフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-165">In the Command Prompt window, navigate to the folder where you saved ReportBuilder3_x86.msi.</span></span>  
  
8.  <span data-ttu-id="f91cf-166">次の形式のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-166">Type a command with the following format:</span></span>  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     <span data-ttu-id="f91cf-167">レポート ビルダーのインストールに固有のオプションは、RBINSTALLDIR と REPORTSERVERURL の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="f91cf-167">The two options specific to installing Report Builder are: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="f91cf-168">コマンド ラインにこれらの引数を含めることは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="f91cf-168">It not required that you include these arguments in the command line.</span></span> <span data-ttu-id="f91cf-169">標準的なコマンド ラインは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f91cf-169">The following is the baseline command:</span></span>  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. <span data-ttu-id="f91cf-170">コマンドを実行するには、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f91cf-170">To run the command, press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91cf-171">参照</span><span class="sxs-lookup"><span data-stu-id="f91cf-171">See Also</span></span>  
 <span data-ttu-id="f91cf-172">[インストール、アンインストール、およびレポートビルダーサポート](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="f91cf-172">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="f91cf-173">レポートビルダー &#40;レポートビルダーのスタンドアロンバージョンをアンインストールする&#41;</span><span class="sxs-lookup"><span data-stu-id="f91cf-173">Uninstall the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
